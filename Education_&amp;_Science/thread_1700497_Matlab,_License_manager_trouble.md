---
title: "Matlab, License manager trouble"
date: 2011-03-05
forum: Education &amp; Science
---

### Post by jondaeh on 2011-03-05
I am trying to install Matlab R2010bon my Ubuntu 10.10 64-bit system, but the  license manager is giving me trouble. I have modified the license.dat  file to containing the right hostname. I also had to change the host-ID  number to make license manager at all accept the license, and changed  the line that states the line to the daemon MLM. 

Now I'm stuck as licensemanger says it wait for some sort of MATLAB  vendor daemon to come up. This is the terminal as I execute lmstart:

```
jon@jonnis:/usr/local/MATLAB/R2010b/etc$ sh lmstart
 
Checking license file for local hostname and local hostid . . .
 
Taking down any existing license manager daemons . . .
 
    No license manager daemons running . . .
 
Starting license manager . . .
 
    Debug logfile = /var/tmp/lm_TMW.log
    Waiting 300 secs for MATLAB vendor daemon to come up . . .
            Type your interrupt character (usually CTRL-C) to quit.
    Time = 3 secs  :  still waiting . . .
    Time = 30 secs  :  still waiting . . .
------------------------------------------------------------------------
lø. 05. mars 10:57:36 +0100 2011    LM_LOGFILE (last 2 lines)
205 10:57:09 (lmgrd) is the license file you want to use.
206 10:57:09 (lmgrd)
------------------------------------------------------------------------
^C------------------------------------------------------------------------
lø. 05. mars 10:57:47 +0100 2011    LM_LOGFILE (last 10 lines)
197 10:57:09 (lmgrd) MLM exited with status 36 (No features to serve)
198 10:57:09 (lmgrd) MLM daemon found no features.  Please correct
199 10:57:09 (lmgrd) license file and re-start daemons.
200 10:57:09 (lmgrd)
201 10:57:09 (lmgrd) This may be due to the fact that you are using
202 10:57:09 (lmgrd) a different license file from the one you expect.
203 10:57:09 (lmgrd) Check to make sure that:
204 10:57:09 (lmgrd) /var/tmp/lm_TMW.dat
205 10:57:09 (lmgrd) is the license file you want to use.
206 10:57:09 (lmgrd)
------------------------------------------------------------------------

Please hit return for more help . . . > 
------------------------------------------------------------------------
Notes: 1. To print more of the debug logfile use the '-e nlines' option
          on lmstart or lmboot commands. Use the -help option on any
          command for help.
       2. To check that the daemons are up run the 'lmstat -a' command.
       3. Use the '-wait secs' option on lmstart or lmboot commands
          to increase the wait time in batch.
       4. If you are getting 'socket bind' errors in the logfile output
          first run 'lmdown' and then 'lmstart -k' to verify that all
          ports are clear. This is CRITICAL when using redundant
          servers. You must get nothing back from 'lmstart -k' on all
          servers before you are ready to run 'lmstart' to restart the
          license manager. This can take up to 5 minutes. If some of
          the ports do not clear in this time then they could be in 
          use and you should change the port number on the SERVER line
          in your license file.
------------------------------------------------------------------------
jon@jonnis:/usr/local/MATLAB/R2010b/etc$ ^C
jon@jonnis:/usr/local/MATLAB/R2010b/etc$ 

```And this is the logfile lm_TMW.log:

```
10:57:09 (lmgrd) -----------------------------------------------
10:57:09 (lmgrd)   Please Note:
10:57:09 (lmgrd)
10:57:09 (lmgrd)   This log is intended for debug purposes only.
10:57:09 (lmgrd)   In order to capture accurate license
10:57:09 (lmgrd)   usage data into an organized repository,
10:57:09 (lmgrd)   please enable report logging. Use Acresso Software Inc.'s
10:57:09 (lmgrd)   software license administration  solution,
10:57:09 (lmgrd)   FLEXnet Manager, to  readily gain visibility
10:57:09 (lmgrd)   into license usage data and to create
10:57:09 (lmgrd)   insightful reports on critical information like
10:57:09 (lmgrd)   license availability and usage. FLEXnet Manager
10:57:09 (lmgrd)   can be fully automated to run these reports on
10:57:09 (lmgrd)   schedule and can be used to track license
10:57:09 (lmgrd)   servers and usage across a heterogeneous
10:57:09 (lmgrd)   network of servers including Windows NT, Linux
10:57:09 (lmgrd)   and UNIX. Contact Acresso Software Inc. at
10:57:09 (lmgrd)   www.acresso.com for more details on how to
10:57:09 (lmgrd)   obtain an evaluation copy of FLEXnet Manager
10:57:09 (lmgrd)   for your enterprise.
10:57:09 (lmgrd)
10:57:09 (lmgrd) -----------------------------------------------
10:57:09 (lmgrd)
10:57:09 (lmgrd)
10:57:09 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
10:57:09 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
10:57:09 (lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.2355, errno: 2
10:57:09 (lmgrd) FLEXnet Licensing (v11.6.1.0 build 66138 amd64_re3) started on jonnis (linux) (3/5/2011)
10:57:09 (lmgrd) Copyright (c) 1988-2008 Acresso Software Inc. All Rights Reserved.
10:57:09 (lmgrd) US Patents 5,390,297 and 5,671,412.
10:57:09 (lmgrd) World Wide Web:  http://www.acresso.com
10:57:09 (lmgrd) License file(s): /var/tmp/lm_TMW.dat
10:57:09 (lmgrd) lmgrd tcp-port 27000
10:57:09 (lmgrd) Starting vendor daemons ...
10:57:09 (lmgrd) Started MLM (internet tcp_port 46469 pid 2357)
10:57:09 (MLM) FLEXnet Licensing version v11.6.1.0 build 66138 amd64_re3
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT MATLAB MLM 24 01-jan-0000 25  BDCE64A22A1DEF56F919      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE=product=MATLAB SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT SIMULINK MLM 24 01-jan-0000 25  4D7EA40277FA73618FA1      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE=product=Simulink SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Communication_Blocks MLM 24  01-jan-0000 25     2D0E1402032D480F0067      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Communications Blockset" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Communication_Toolbox MLM 24  01-jan-0000 25     4D0E5402A43B1DEFADD0      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Communications Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Control_Toolbox MLM 24 01-jan-0000 25  4DDEB4C24B43BC64C786      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Control System Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Data_Acq_Toolbox MLM 24 01-jan-0000  25 FD7EA4422A8381316CB8      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Data Acquisition Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Database_Toolbox MLM 24 01-jan-0000  25 FD7EA482CA06F325DDA4      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Database Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Fuzzy_Toolbox MLM 24 01-jan-0000 25  4D2E745223556CB1E480      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Fuzzy Logic Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT GADS_Toolbox MLM 24 01-jan-0000 10  9D9E94B2C8047A5CC220      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Global Optimization Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Image_Acquisition_Toolbox MLM 24  01-jan-0000 10     EDEEB4427783DE90F04C      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Image Acquisition Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Image_Toolbox MLM 24 01-jan-0000 25  7D0EF4223A14EA7BB784      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Image Processing Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT MAP_Toolbox MLM 24 01-jan-0000 10  9D6E0412265E0D4CF985      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Mapping Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT MPC_Toolbox MLM 24 01-jan-0000 25  8DCEF4525E948D889EFE      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Model Predictive Control Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Neural_Network_Toolbox MLM 24  01-jan-0000 25     FD0EF422DF41E2740791      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Neural Network Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Optimization_Toolbox MLM 24  01-jan-0000 10     2D7E54820D1EE2CEDB2F      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Optimization Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Distrib_Computing_Toolbox MLM 24  01-jan-0000 25     4D8E2492F3C4D548D2DD      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Parallel Computing Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Signal_Blocks MLM 24 01-jan-0000 25  1DBEA4F272881F412B63      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Signal Processing Blockset" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Signal_Toolbox MLM 24 01-jan-0000 25  4D8EB462EAA21069C229      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Signal Processing Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT SimHydraulics MLM 24 01-jan-0000 10  DD2E7472613C04A31F7E      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE=product=SimHydraulics SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Simscape MLM 24 01-jan-0000 10  BD5E749292DFD445C901      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE=product=Simscape SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Virtual_Reality_Toolbox MLM 24  01-jan-0000 25     9DFED422CD25DD405F81      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Simulink 3D Animation" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Simulink_Control_Design MLM 24  01-jan-0000 25     ADAEB442D48CE50B5A12      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Simulink Control Design" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Excel_Link MLM 24 01-jan-0000 10  4D4E24829C0BCEDF4FDD      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Spreadsheet Link EX" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Identification_Toolbox MLM 24  01-jan-0000 25     6D9E04A234746AD96B1F      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=System Identification Toolbox" SN=685559
10:57:09 (MLM) Invalid license key (inconsistent authentication code)
10:57:09 (MLM)     ==>INCREMENT Wavelet_Toolbox MLM 24 01-jan-0000 25  2DDED472EA80EF72906D      VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1:      DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011      NOTICE="product=Wavelet Toolbox" SN=685559
10:57:09 (MLM) License server system started on jonnis
10:57:09 (MLM) No features to serve, exiting
10:57:09 (MLM) EXITING DUE TO SIGNAL 36 Exit reason 4
10:57:09 (lmgrd) MLM exited with status 36 (No features to serve)
10:57:09 (lmgrd) MLM daemon found no features.  Please correct
10:57:09 (lmgrd) license file and re-start daemons.
10:57:09 (lmgrd)
10:57:09 (lmgrd) This may be due to the fact that you are using
10:57:09 (lmgrd) a different license file from the one you expect.
10:57:09 (lmgrd) Check to make sure that:
10:57:09 (lmgrd) /var/tmp/lm_TMW.dat
10:57:09 (lmgrd) is the license file you want to use.
10:57:09 (lmgrd)
```From this it may seems like my license isn't good  or something, but I know I have a valid license as I downloades this  from my account from mathworks.com.

And this is my license.dat file(took away the host-ID, maybe this shouldn't be published..):
```
SERVER jonnis xxxxxxxxxxxx xxxxxxxxxxxxx 27000  
DAEMON MLM /usr/local/MATLAB/R2010b/etc/lm_matlab 
# BEGIN--------------BEGIN--------------BEGIN 
# MathWorks license passcode file. 
# LicenseNo: 685559   HostID: xxxxxxxxxxxx xxxxxxxxxxxxx 
# 
# R2010b 
# 
INCREMENT MATLAB MLM 24 01-jan-0000 25 BDCE64A22A1DEF56F919 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE=product=MATLAB SN=685559 
INCREMENT SIMULINK MLM 24 01-jan-0000 25 4D7EA40277FA73618FA1 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE=product=Simulink SN=685559 
INCREMENT Communication_Blocks MLM 24 01-jan-0000 25 \ 
    2D0E1402032D480F0067 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Communications Blockset" SN=685559 
INCREMENT Communication_Toolbox MLM 24 01-jan-0000 25 \ 
    4D0E5402A43B1DEFADD0 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Communications Toolbox" SN=685559 
INCREMENT Control_Toolbox MLM 24 01-jan-0000 25 4DDEB4C24B43BC64C786 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Control System Toolbox" SN=685559 
INCREMENT Data_Acq_Toolbox MLM 24 01-jan-0000 25 FD7EA4422A8381316CB8 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Data Acquisition Toolbox" SN=685559 
INCREMENT Database_Toolbox MLM 24 01-jan-0000 25 FD7EA482CA06F325DDA4 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Database Toolbox" SN=685559 
INCREMENT Fuzzy_Toolbox MLM 24 01-jan-0000 25 4D2E745223556CB1E480 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Fuzzy Logic Toolbox" SN=685559 
INCREMENT GADS_Toolbox MLM 24 01-jan-0000 10 9D9E94B2C8047A5CC220 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Global Optimization Toolbox" SN=685559 
INCREMENT Image_Acquisition_Toolbox MLM 24 01-jan-0000 10 \ 
    EDEEB4427783DE90F04C \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Image Acquisition Toolbox" SN=685559 
INCREMENT Image_Toolbox MLM 24 01-jan-0000 25 7D0EF4223A14EA7BB784 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Image Processing Toolbox" SN=685559 
INCREMENT MAP_Toolbox MLM 24 01-jan-0000 10 9D6E0412265E0D4CF985 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Mapping Toolbox" SN=685559 
INCREMENT MPC_Toolbox MLM 24 01-jan-0000 25 8DCEF4525E948D889EFE \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Model Predictive Control Toolbox" SN=685559 
INCREMENT Neural_Network_Toolbox MLM 24 01-jan-0000 25 \ 
    FD0EF422DF41E2740791 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Neural Network Toolbox" SN=685559 
INCREMENT Optimization_Toolbox MLM 24 01-jan-0000 10 \ 
    2D7E54820D1EE2CEDB2F \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Optimization Toolbox" SN=685559 
INCREMENT Distrib_Computing_Toolbox MLM 24 01-jan-0000 25 \ 
    4D8E2492F3C4D548D2DD \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Parallel Computing Toolbox" SN=685559 
INCREMENT Signal_Blocks MLM 24 01-jan-0000 25 1DBEA4F272881F412B63 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Signal Processing Blockset" SN=685559 
INCREMENT Signal_Toolbox MLM 24 01-jan-0000 25 4D8EB462EAA21069C229 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Signal Processing Toolbox" SN=685559 
INCREMENT SimHydraulics MLM 24 01-jan-0000 10 DD2E7472613C04A31F7E \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE=product=SimHydraulics SN=685559 
INCREMENT Simscape MLM 24 01-jan-0000 10 BD5E749292DFD445C901 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE=product=Simscape SN=685559 
INCREMENT Virtual_Reality_Toolbox MLM 24 01-jan-0000 25 \ 
    9DFED422CD25DD405F81 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Simulink 3D Animation" SN=685559 
INCREMENT Simulink_Control_Design MLM 24 01-jan-0000 25 \ 
    ADAEB442D48CE50B5A12 \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Simulink Control Design" SN=685559 
INCREMENT Excel_Link MLM 24 01-jan-0000 10 4D4E24829C0BCEDF4FDD \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Spreadsheet Link EX" SN=685559 
INCREMENT Identification_Toolbox MLM 24 01-jan-0000 25 \ 
    6D9E04A234746AD96B1F \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=System Identification Toolbox" SN=685559 
INCREMENT Wavelet_Toolbox MLM 24 01-jan-0000 25 2DDED472EA80EF72906D \ 
    VENDOR_STRING=vi=0:at=200:ae=1:lu=200:lo=CN:ei=1284703:classroom=1: \ 
    DUP_GROUP=UH asset_info=685559 ISSUED=02-Mar-2011 \ 
    NOTICE="product=Wavelet Toolbox" SN=685559 
# END-----------------END-----------------END
```I don't know if this  is the right forum to post this on, but I hope someone here is happely  using matlab and can give me a little guidance:smile:

thanks,
Jon, Norway.


edit:
The logfile stated 
```

10:57:09 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)
10:57:09 (lmgrd) Can't make directory /usr/tmp/.flexlm, errno: 2(No such file or directory)

```

This seems to be because /usr isn't writable for users. Resolved it by making a new folder named tmp in /usr and giving all users all permissions, like this:
```

sudo mkdir /usr/tmp

sudo chmod ugo+rwx /usr/tmp

```

I don't think this has anything to do with my license problem, as it didn't help much, but if anyone wonders..

---

