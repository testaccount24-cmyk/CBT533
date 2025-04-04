# CBT533
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 533 is from Sam Golob, and contains the VTT2TAPE and      *   FILE 533
//*           VTT2DISK programs, in their "free versions".          *   FILE 533
//*                                                                 *   FILE 533
//*           The programs in this package are part of the          *   FILE 533
//*           Virtual Tape Transportation System (VTTS), which      *   FILE 533
//*           is copyrighted (c) 2001 - 2005 by Sam Golob.          *   FILE 533
//*                                                                 *   FILE 533
//*           Copyright notices are present in the source and       *   FILE 533
//*           load modules, but the versions of these programs      *   FILE 533
//*           that are on the CBT Tape, ARE ALLOWED TO BE RUN       *   FILE 533
//*           BY ANYONE, because the copyright holder has given     *   FILE 533
//*           full permission.  The copyright holder retains all    *   FILE 533
//*           ownership rights to the software.                     *   FILE 533
//*                                                                 *   FILE 533
//*           Member M370VTT2 has been added, which contains        *   FILE 533
//*           a version of VTT2TAPE and VTT2DISK which can be       *   FILE 533
//*           assembled using the XF assembler (IFOX00).            *   FILE 533
//*           (This is courtesy of Gerhard Postpischil.)            *   FILE 533
//*                                                                 *   FILE 533
//*           Unless otherwise mentioned, AWS-format "virtual tape" *   FILE 533
//*           files on an MVS system, have been folded over into    *   FILE 533
//*           Fixed Blocked 80-byte record format.  AWS-format      *   FILE 533
//*           files on other systems are just long strings of data. *   FILE 533
//*           This can't happen on MVS--all data has to be blocked  *   FILE 533
//*           on MVS.  So I chose FB-80 blocking for the AWS-format *   FILE 533
//*           and FAKETAPE (TM) format "virtual tape" files on MVS. *   FILE 533
//*                                                                 *   FILE 533
//*           The FAKETAPE file format is a published interface     *   FILE 533
//*           of Fundamental Software Inc. and they say in their    *   FILE 533
//*           documentation that anyone has permission to use the   *   FILE 533
//*           format, although Fundamental Software reserves the    *   FILE 533
//*           right to change the format at any time.               *   FILE 533
//*                                                                 *   FILE 533
//*           FAKETAPE (TM) and FLEX-ES (TM) are registered         *   FILE 533
//*           trademarks of Fundamental Software Inc.               *   FILE 533
//*                                                                 *   FILE 533
//*       Program Names:                                            *   FILE 533
//*                                                                 *   FILE 533
//*           VTT2TAPE - Program to convert AWS-format tape files   *   FILE 533
//*                      to real tapes.  Any CHUNKSIZE is           *   FILE 533
//*                      supported, up to the 65535-byte limit.     *   FILE 533
//*           VTT2DISK - Program to create an AWS-format virtual    *   FILE 533
//*                      tape file from a real tape.  Any           *   FILE 533
//*                      CHUNKSIZE tape can be created.  Default    *   FILE 533
//*                      chunksize is 65535 but that can be either  *   FILE 533
//*                      changed at assembly time, or with a SYSIN  *   FILE 533
//*                      CHUNKSIZE=nnnnn parameter.                 *   FILE 533
//*           VTT2CNVU - Program to convert a VB-format AWS-format  *   FILE 533
//*                      tape (such as the one produced by Brandon  *   FILE 533
//*                      Hill's AWSUTIL program on CBT File 467)    *   FILE 533
//*                      to FB-80 format on MVS, so that VTT2TAPE   *   FILE 533
//*                      can be used subsequently to convert the    *   FILE 533
//*                      data to a real tape.                       *   FILE 533
//*           VTT2T2FK - Like VTT2DISK, except a real tape is       *   FILE 533
//*                      converted to a FAKETAPE (TM) format tape.  *   FILE 533
//*           VTT2FK2T - Like VTT2TAPE, except a FAKETAPE (TM)      *   FILE 533
//*                      tape image, folded over on MVS into FB-80  *   FILE 533
//*                      format, is converted into a real tape.     *   FILE 533
//*                                                                 *   FILE 533
//*           These programs run on an MVS system, and allow        *   FILE 533
//*           real tapes to be converted to disk files, and         *   FILE 533
//*           these disk files, back to real tapes.  These          *   FILE 533
//*           programs do not require a P/390 or a FLEX-ES (TM)     *   FILE 533
//*           system.  ANY MVS system will run these programs!      *   FILE 533
//*                                                                 *   FILE 533
//*           The VTT2DISK program reads a real tape, and           *   FILE 533
//*           converts it to an AWS-format "virtual tape" file      *   FILE 533
//*           on an MVS system, folded over into FB-80 format.      *   FILE 533
//*           VTT2DISK now takes SYSIN input in column 1.           *   FILE 533
//*           Allowed keywords are:                                 *   FILE 533
//*                                                                 *   FILE 533
//*           CHUNKSIZE=nnnn     Default is 65535 if not coded.     *   FILE 533
//*                              This can be changed with an        *   FILE 533
//*                              assembler global variable.         *   FILE 533
//*           NEWVOL=volser   -  Changes the VOLSER on VOL1 label   *   FILE 533
//*           READ            -  Produces READ only run, no AWSOUT  *   FILE 533
//*           IDRCOFF         -  Turns off "data is compressed"     *   FILE 533
//*                              "P" indicators in the tape labels  *   FILE 533
//*                                                                 *   FILE 533
//*           The VTT2TAPE program takes this "folded over" FB-80   *   FILE 533
//*           AWS-format file on an MVS system, and cuts a real     *   FILE 533
//*           tape from it, on a real tape drive.                   *   FILE 533
//*                                                                 *   FILE 533
//*           The VTT2FK2T program does a job similar to the        *   FILE 533
//*           VTT2TAPE program, except that it takes an FB-80       *   FILE 533
//*           folded image of a FLEX-ES FAKETAPE, and cuts a        *   FILE 533
//*           real tape from it, on a real tape drive.  Therefore   *   FILE 533
//*           a FAKETAPE image produced on a FLEX-ES system can     *   FILE 533
//*           be uploaded in BINARY to an FB-80 format disk file    *   FILE 533
//*           ON ANY MVS SYSTEM, and a real tape can be cut from    *   FILE 533
//*           it.                                                   *   FILE 533
//*                                                                 *   FILE 533
//*           And VTT2T2FK creates a FAKETAPE file (folded into     *   FILE 533
//*           FB-80 format) from a real tape.  If this file is      *   FILE 533
//*           downloaded to the server machine on which FLEX-ES     *   FILE 533
//*           is running, FLEX-ES can read this image as though     *   FILE 533
//*           it were a tape.                                       *   FILE 533
//*                                                                 *   FILE 533
//*           The disk files which are in FB-80 folded AWS or       *   FILE 533
//*           FAKETAPE format, can be FTP'ed back to the PC, OS/2   *   FILE 533
//*           or LINUX server, and read by a P/390 or FLEX-ES or    *   FILE 533
//*           HERCULES system as a tape.                            *   FILE 533
//*                                                                 *   FILE 533
//*           See member $VTT2DOC for details.                      *   FILE 533
//*                                                                 *   FILE 533
//*           VTT2TAPE has now been updated to be able to read      *   FILE 533
//*           a folded AWS tape file that has its chunk size        *   FILE 533
//*           smaller than the block size, and to produce a         *   FILE 533
//*           real output tape from it.  Such AWS-format tapes      *   FILE 533
//*           are created by FLEX-ES systems and the old (very      *   FILE 533
//*           very very old) P/390 systems.                         *   FILE 533
//*                                                                 *   FILE 533
//*           And VTT2DISK can now produced a "chunked" AWS tape    *   FILE 533
//*           file from a real tape.  FAKETAPE (TM) architecture    *   FILE 533
//*           does not have provision to produced chunked output    *   FILE 533
//*           (i.e. the tape blocks being divided into smaller      *   FILE 533
//*           pieces, and the blocks being pieced together later).  *   FILE 533
//*                                                                 *   FILE 533
//*           These programs can now be run with PARM=READ in       *   FILE 533
//*           the EXEC card, which is a "READ ONLY" execution       *   FILE 533
//*           that produces reports about the input tape, or        *   FILE 533
//*           disk file.                                            *   FILE 533
//*                                                                 *   FILE 533
//*           PARM=READ will read the AWS or tape inputs, and       *   FILE 533
//*           produce these programs' abundant stats.  If you       *   FILE 533
//*           want to "measure a tape" or an AWS-format tape file   *   FILE 533
//*           on disk, you can use the PARM=READ facility, which    *   FILE 533
//*           doesn't open the output file.  VTT2CNVU does not      *   FILE 533
//*           (yet) support PARM=READ.                              *   FILE 533
//*                                                                 *   FILE 533
//*           PARM=IDRCOFF in VTT2DISK, will turn off the IDRC      *   FILE 533
//*           indicators in VOL1, HDR2, EOF2, and EOV2 labels.      *   FILE 533
//*                                                                 *   FILE 533
//*           The contents of this file, are part of VTTS           *   FILE 533
//*           (Virtual Tape Transportation System), which           *   FILE 533
//*           is copyrighted by Sam Golob, but the versions         *   FILE 533
//*           of the VTTS programs which are in the CBT Tape        *   FILE 533
//*           collection, may be used without charge by anyone,     *   FILE 533
//*           and the copyright owner grants permission.  Same      *   FILE 533
//*           for the VTT2FK2T and VTT2T2FK programs.               *   FILE 533
//*                                                                 *   FILE 533
//*              Sam Golob  -  email:   sbgolob@cbttape.org         *   FILE 533
//*                                                                 *   FILE 533
//*           I've included a free C program from Leland Lucius,    *   FILE 533
//*           called strippad.c (member STRIPPAD), which strips     *   FILE 533
//*           off the padding bytes that VTT2DISK adds to the       *   FILE 533
//*           last FB-80 record on MVS, if it is short.  It seems   *   FILE 533
//*           that when you copy the FB-80 AWS-format disk file     *   FILE 533
//*           back to the PC, Hercules has some problems handling   *   FILE 533
//*           the padding bytes.  The P/390 doesn't.                *   FILE 533
//*                                                                 *   FILE 533
//*              Leland Lucius     email:  llucius@moneygram.com    *   FILE 533
//*                                        llucius@homerow.net      *   FILE 533
//*                                        hackules@digicron.com    *   FILE 533
//*                                                                 *   FILE 533
```
