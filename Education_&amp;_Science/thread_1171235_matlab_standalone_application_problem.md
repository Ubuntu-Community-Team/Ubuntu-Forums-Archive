---
title: "matlab standalone application problem"
date: 2009-05-27
forum: Education &amp; Science
---

### Post by alsmat on 2009-05-27
Hi,
I compiled a matlab (R14)  application with mcc (with options -R -nojvm -R -nojit -R -nodisplay) to obtain a standalone application.
 I generatad the MCR installer and installed the application and the installer  on a ubuntu  8.04.2 machine . 
I run the stand-alone application from the command line successfully, but  I would like to call   the application  from  a php script   with a system call (I  tried it sucessfuly on a fedora  8 machine) . 
I added the LD_LIBRARY_PATH and PATH pointing to the right paths  in  /etc/apache2/envvar and added   PassEnv LD_LIBRARY_PATH PATH to  /etc/apache2/mods-enabled/php5.conf and restarted apache.
 When I call the application from my php script I get  a segmentation fault (see below - I cut and pasted from the html page as I was not  able to reproduce the error from the command line) - and the string "segmentation fault"  is the only information I get from the error.log file). Do you have any hints ?  
Could  the problem be  related to the fact that the  ubuntu machine ia a virtual machine?

Thank you for your help.

_______________________________________

------------------------------------------------------------------------ Segmentation violation detected at Wed May 27 13:04:23 2009 ------------------------------------------------------------------------ Configuration: MATLAB Version: 7.0.4.352 (R14) Service Pack 2 MATLAB License: unknown Operating System: Linux 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 Current Visual: None Processor ID: x86 Family 6 Model 7 Stepping 7, GenuineIntel Virtual Machine: Java is not enabled Default Charset: US-ASCII Register State: eax = 00000000 ebx = b67f7020 ecx = ffffffff edx = 00000002 esi = b6d5c280 edi = 00000000 ebp = bfee5d58 esp = bfee5d40 eip = b67eebb4 flg = 00210246 Stack Trace: [0] libmwmpath.so:mpCombinePathName~(0xb6d5c280, 0, 0xb6d3a740 "toolbox_cache-7.0.4-glnx86.xml", 0) + 32 bytes [1] libmwservices.so:svGetToolboxCacheFile~(0, 0, 0, 0xbfee6ec0) + 96 bytes [2] libmwbridge.so:0xb6784c0d(0xb6d8d51c, 0x0812c080, 0xbfee6ff8, 0xb6d83b60) [3] libmwbridge.so:mnRunPathDependentInitialization()~(0xb6c8dd58, 0xb6c96ed8, 0xbfee6f84, 0xbfee706d) + 37 bytes [4] libmwmcr.so:0xb6d83b60(0xbfee7060, 0x080adc20 "h_Ý¶", 1, 0xb6e4ed70 "/usr/local/matlab/v72/toolbox") [5] libmwmcr.so:mcrInstance::mcrInstance(mcrOptions&, MfileReader*)~(0x080af3d0, 0xbfee71b0, 0x080adc20 "h_Ý¶", 0xbfee0000) + 530 bytes [6] libmwmclmcr.so:mclInitializeComponentInstance~(0x0804a3b0, 0x080489c0 "30819D300D06092A864886F70D010101..", 0x080489ae "contributors_web", 0x080489ad) + 2222 bytes [7] libmwmclmcrrt.so.7.2:mclInitializeComponentInstance~(0x0804a3b0, 0x080489c0 "30819D300D06092A864886F70D010101..", 0x080489ae "contributors_web", 0x080489ad) + 84 bytes [8] contributors_web:0x08048802(0x08048671, 0x080486f7, 0xbfee72e8, 0x08048871) [9] contributors_web:0x08048828(0x0804a374, 4, 0xbfee72f8, 0x0804

---

### Post by alsmat on 2009-05-28
Solved!
It  is necessary to setup the environment variable HOME inside the php script: putenv('HOME=/var/www')

---

### Post by diamondnular on 2009-07-21
> **alsmat said:**
> Solved!
It  is necessary to setup the environment variable HOME inside the php script: putenv('HOME=/var/www')

Hi alsmat, would you mind sharing your experience on making matlab standalone application?

Thanks,

D.

---

