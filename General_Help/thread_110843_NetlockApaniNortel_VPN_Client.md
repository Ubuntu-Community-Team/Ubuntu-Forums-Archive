---
title: "Netlock/Apani/Nortel VPN Client"
date: 2005-12-31
forum: General Help
---

### Post by remat457 on 2005-12-31
Has anybody gotten the above extranet/VPN client to work?
I downloaded the multi-OS client and can successfully build it but on launch or bootup it either hangs my PC or produces a Kernel panic.

I have built the generic Debian client, the SuSE and the RH variations all with the same result.

My work, unfortunately uses the Nortel Contivity Client...

Just wondering if it works with HH or if it was just me :)

thanks

---

### Post by imrumpf on 2006-01-06
if it doesn't work in HH have you tried installing/upgrading to BB to see if antyhing is different? ;)

---

### Post by remat457 on 2006-01-21
[QUOTE=imrumpf]if it doesn't work in HH have you tried installing/upgrading to BB to see if antyhing is different? ;)[/QUOTE]

I haven't migrated to BB yet. I did it on a test machine and had some problems with it. Probably will just wait for the next release...The VPN client is one of the few things that is still making me hang on to that other OS (that and Flash MX)..

Thanks for the thought though. Maybe I will clean install BB on the test box and see if the vpn  works!

---

### Post by deez0n on 2006-07-22
[SIZE="2"]I don't know if anyone still cares, but I managed to get the Apani Netlock software to work under Ubuntu Dapper. I hope someone else will find this useful, and maybe bring them back to Ubuntu. 

Here is how I did it:

It requires modifications to the linux_wrapper.c that ships with the client, and also requires a full kernel build.
The stock Ubuntu Dapper gcc-4.0.3 compiler should work fine for this. 

1: Follow the excellent kernel build directions listed below; (make sure you follow the xorg.conf instructions before the build) [COLOR="Red"]while on the make menuconfig step, turn on the[/COLOR] [COLOR="Blue"]"Use register arguments (CONFIG_REGPARAM)[/COLOR] [COLOR="Red"]under the[/COLOR] [COLOR="Blue"]"Processor type and features"[/COLOR] [COLOR="Red"]menu item[/COLOR]. Having this setting disabled is what is causing the kernel to lockup whenever the netlock module is inserted. The Dapper kernel build tutorial is located at the following
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

2: Reboot with the new kernel and make sure it works. Incidentally, your Ubuntu splash/progress screen will be gone but you shouldn't worry. You can hit CTRL-ALT-F1 to bring up the text console and watch the progress from there if there is an concern.

2a: I had to reinstall my proprietary video drivers (NVidia), you may need to do the same.

3: Untar the Redhat version of the client (cvc_linux-rh-gcc3-3.3.tar.gz) and then cd to the client directory.
The netlock client src file linux_wrapper.c makes a call to the kernel's ip_rcv function, which in 2.6.14 and above is "private" to the kernel and has an additional argument in it's function signature so it will no longer work with the netlock client. From searching forum posts, I found that the correct call should actually be to netif_rx.

edit the file using "sudo [favorite editor] src/linux_wrapper.c" (you will want to install the client under root priveleges anyway).
In the function definition nl_ip_rcv change this:
       [COLOR="Blue"]return ip_rcv(skb, skb->dev, pt); [/COLOR]

to this:
       [COLOR="Blue"]return netif_rx(skb);[/COLOR]

The wrapper also attempts to copy structure entries from one sk_buff to another and the names of some these entries have changed.
In two places, the wrapper attempts to copy the stamp field of one sk_buff to another, and in one place, attempts to copy the security field. stamp has been changed to tstamp, and I believe security has been changed to "sp" (security path). I just commented out the security field copy instructions, the still client works fine.
Change this:
 [COLOR="Blue"]new_skb->stamp = skb->stamp;[/COLOR]

to:
 [COLOR="Blue"]new_skb->tstamp = skb->tstamp;[/COLOR]

and this:
 [COLOR="Blue"]skb_to->stamp = skb_from->stamp;[/COLOR]

to:
 [COLOR="Blue"]skb_to->tstamp = skb_from->tstamp;[/COLOR]

and this:
 [COLOR="Blue"]new_skb->security = skb->security;[/COLOR]

to this:
  [COLOR="Blue"]/* new_skb->security = skb->security; */[/COLOR]

4: Save the linux_wrapper.c file and then run "sudo make" in the netlock client root folder.
After running successful make, cd to the src folder and and run "modinfo mishim.o" (this is the module that is crashing everyones kernels). Make sure the kernel portion of the vermagic matches the output from "uname -r"

5: Just for safety, I ran "tail -f /var/log/syslog in another terminal, and then ran "sudo insmod mishim.o" just to make sure it didn't crash the kernel before I ran the netlock install script.  I believe if your kernel does crash/lockup, you can use the sysrq commands to dump debug output to the syslog and reboot the computer: read the contents of /usr/src/linux/Documentation/sysrq.txt for more info.
If the kernel doesn't crash, you are safe to run the install script and then it's `happy working from home :)`.
You can run either "sudo install.sh" or "sudo make install"

The information that led me to a successful integration was found on a gentoo forums thread:
[http://forums.gentoo.org/viewtopic.php?t=275942&highlight=netlock](http://forums.gentoo.org/viewtopic.php?t=275942&highlight=netlock)[/SIZE]

---

### Post by mbeierl on 2006-07-28
One more thing to add:  I had to move the inclusion on net/route.h to outside the #if in src/linux_wrapper.c as well:

around line 85, change:

```

  #include <net/flow.h>
  struct rtable;
```
to
```

  #include <net/flow.h>
  #include <net/route.h>
  struct rtable;
```

---

### Post by deez0n on 2006-07-29
Which Kernel version are you using?  I'm using 2.6.15.x which didn't require me to did not have to that.

---

### Post by remat457 on 2006-08-01
Those instructions were great!! 
For the first time the install.sh ran correctly and I have the logon screen.

Much obliged!

---

### Post by fractule on 2006-10-27
Hi !

First, I must say this is a great tutorial !
When I was running Dapper with kernel 2.6.15.7 it worked at once.
Unfortunatly, I upgraded to edgy yesterday (keeping my custom kernel), and I can't make it work again: inserting the mishim.o freeze my system.

After upgrading, the netlock service didn't start automatically, and when I tried to start it myself with /etc/init.d/netlock restart, it complained that mishim.o and nlvcard.o didn't exist.

I tried to recompile the modules:
- it worked but inserting the module failed saying that this was an invalid module. I figured out that it was because GCC version changed, so recompiled with sudo make CC=gcc-4.0
- but when I inserted the module, my system froze immediatly

I tried to recompile my kernel to use the new version shipped with edgy (2.6.17.10), but:
- compiling netlock requiered a few hacks because there was compilation error at
```
line 603: skb->dst = &rt->u.dst;
```
something like "dereferencing pointer to an incomplete type"
- I figured out it was because of this piece of code:
```
#if (LINUX_VERSION_CODE >= 0x020500)

  #include <net/flow.h>
  struct rtable;
```
because struct rtable is declared but not defined
- I added #include <net/route.h>
- compilation was ok, but inserting the module failed again because it said the symbol RT_TOS was undefined
- I found RT_TOS was a macro defined in linux/in_route.h, so I included it like this:
```
#if (LINUX_VERSION_CODE >= 0x020500)

  #include <net/flow.h>
  #include <net/route.h>
  #include <linux/in_route.h>
  //struct rtable;
```
- compilation succeeded, but module insertion froze my system again ](*,) 

This time, I'm beginning to be really fed up with this damn VPN client !

Did anybody here try to upgrade to edgy and achieve to make this thing work ??

Thanks for your help !


PS: Each time I compile, I get a warning saying that .libmishim-2.6.a.cmd does not exist. I don't remember having this message when I compiled it under Dapper. Whatever the kernel 2.6.15.7 or 2.6.17.10 with Edgy, I got this message. Maybe it's related to the system lockup. Anybody has an idea why this file is not generated ?

---

### Post by chadd on 2006-10-27
I am having a similar problem, and would apreciate any help I can get.  Edgy finally fixed my wireless problems, now I just need this client to be able to use my wireless at work..  Please help!!!!!!!!!  Thanks in advance.  

P.S. I will post the error messages on Monday.

---

### Post by deez0n on 2006-10-27
I haven't upgraded to edgy yet. I'll try to make some time next week to try the upgrade, and see if I can get it to work..
Also, if anyone get's a chance before hand, they might want to try some gentoo forums or debian forums, since someone over there may have uncountered the same issue with the new kernel.  More than likely, the TCP stack developers have hidden another part of the ip functionality as they did with the ip_rcv function.

---

### Post by chadd on 2006-10-30
Ok, here is the whole build:

1.) I followed the instructions, but added this portion, because I ran into the same problem at line 603:

          #if (LINUX_VERSION_CODE >= 0x020500)

          #include <net/flow.h>
          #include <net/route.h>
          #include <linux/in_route.h>
          //struct rtable;


2.) After that, it was able to finish the build - here is the output:

chadd@chadd-laptop:/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3$ sudo make
cd src && make all
make[1]: Entering directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.o
  CC [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/../.libmishim-2.6.a.cmd for /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/../libmishim-2.6.a
  CC      /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.mod.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.ko
  CC      /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.mod.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: Leaving directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: Leaving directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
chadd@chadd-laptop:/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3$ 


I only see one 'Warning', but it looks harmless enough..

3.) Next I run the install.sh script.  This is were the problems occure:

Here is the output:

Do you accept the above license agreement? [y, n] y

Installing Nortel Networks Contivity VPN Client.  Please wait...

[: 148: ==: unexpected operator
[: 233: ==: unexpected operator

Couldn't find SysV startup environment: Netlock is not started at boot time.
Please use the scripts/netlock script to initialize the VPN client.


Thank you for choosing the Nortel Contivity VPN Client powered by Netlock.


Files seem to be installed, but no working netlock.

So when I run the netlock script: 'scripts/netlock' as instructed, I get the following output:

sudo sh scripts/netlock start
Starting Netlock services: scripts/netlock: 128: Syntax error: Bad fd number

I have no stability issues, or lockups, but again, no working netlock.

I also don't get a gnome menu item to start the client - though I suspect this is easily correctable.

Anyone else have any luck yet?  I am running Edgy with this kernel (2.6.17-10-generic).

---

### Post by deez0n on 2006-10-30
I'm not sure if this will work, but I think the netlock script is not compatible with edgy's new default shell, which is dash instead of bash
[http://diveintomark.org/archives/2006/09/19/bad-fd-number](http://diveintomark.org/archives/2006/09/19/bad-fd-number)
I don't have edgy, so I can't test, but try editing the netlock script to run using 
#!/bin/bash 
(or where ever bash actually is) 
Let us know if the modules insert without crashing the kernel.

ds

---

### Post by fractule on 2006-10-31
> **chadd said:**
> 
2.) After that, it was able to finish the build - here is the output:

chadd@chadd-laptop:/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3$ sudo make
cd src && make all
make[1]: Entering directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.o
  CC [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/../.libmishim-2.6.a.cmd for /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/../libmishim-2.6.a
  CC      /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.mod.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/mishim.ko
  CC      /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.mod.o
  LD [M]  /usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6/nlvcard.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: Leaving directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: Leaving directory `/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
chadd@chadd-laptop:/usr/src/software/ContivityClient/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3$ 


I only see one 'Warning', but it looks harmless enough..

3.) Next I run the install.sh script.  This is were the problems occure:



I have the same output (and thus the same warning), but before running install.sh, I try to insert mishim.o into the kernel, and it crashes.
Have you tried this too ? If not, it may explain why direct install doesn't work.


> **chadd said:**
> So when I run the netlock script: 'scripts/netlock' as instructed, I get the following output:

sudo sh scripts/netlock start
Starting Netlock services: scripts/netlock: 128: Syntax error: Bad fd number

I remember I had a similar error message each time I was trying to start the netlock service, after having upgraded to Edgy. However it was working perfectly on Dapper, and I kept the kernel.
Besides, that's why I tried recompiling the client. I thought it might have fixed the problem.

---

### Post by chadd on 2006-10-31
Thank you, Thank you!  That worked like a charm!  Well, I still need to go edit the startup scripts then I presume - to use bash instead of sh, but it worked!  No stability issues as of yet - as far as I know.  I will post back if I discover some.  

Next question.  Anyway to get around the 10 minute time restraint of the evaluation version?

---

### Post by fractule on 2006-10-31
> **chadd said:**
> Thank you, Thank you!  That worked like a charm!  Well, I still need to go edit the startup scripts then I presume - to use bash instead of sh, but it worked!  No stability issues as of yet - as far as I know.  I will post back if I discover some.

If I have understood well, the script trick fixed your issue ?
Well, that would mean the problem I had after upgrading could have been solved just by changing script interpretor in script headers...

I shouldn't have recompiled anything, it seems it caused more problems that it solved because now that I can't insert that damn module without crashing.
Nevertheless, I can't understand why my kernel crashes and not yours. I must have missed something. Maybe I'll try to revert to 2.6.15 kernel and recompile the module with gcc 4.0. At least I'm sure this kernel once made this module work, so it seems as good way to start.

---

### Post by mbeierl on 2006-10-31
I hate to say it, but you need to purchase it to get around the time limit.

Once you do purchase, there is a non-evaluation version of the software for download.  You will need to recompile that one too!

---

### Post by fractule on 2006-10-31
I finally managed to make it work again !
In fact, I reverted to the previous kernel, as I said earlier, and after a few unsuccessfull attemps, it worked. I changed #!/bin/sh to #!/bin/bash in the following scripts:
- netlock
- install.sh
- uninstall.sh

Still, it's strange because module insertion crashed several times before this. Crashes seem to be random. Anyway, the VPN is working smoothly.
I hope there won't be problems when the service will restart on the next boots.

---

### Post by deez0n on 2006-11-01
Fractule, if you haven't already, in addition to the script fix and the netlock client src fixes, you will have to recompile the new edgy kernel,  you'll also have to recompile the kernel if ubuntu sends down new replacement kernels during automatic upgrades (if you want to use the new kernel provided with edgy)
You have to enable "use register arguments" in the kernel configuration, or you'll lock up the kernel when you insert the mishim module.  see my howto: [http://ubuntuforums.org/showthread.php?t=222774&highlight=Nortel](http://ubuntuforums.org/showthread.php?t=222774&highlight=Nortel)

Chadd, you or your company will have to purchase a license for client.  

deez0n

---

### Post by chadd on 2006-11-01
That sucks!  We have a maintenance contract with Nortel, and get the Windows client for free -  so I don't know why they can't give us the linux one for free as well (or the pda one for that matter...).

BTW, the CONFIG_REGPARM was already enabled in the new kernel that comes with Edgy (for me anyway).  I did a fresh install from the .iso I downloaded from the Ubuntu site the day Edgy came out.

---

### Post by fractule on 2006-11-02
> **deez0n said:**
> Fractule, if you haven't already, in addition to the script fix and the netlock client src fixes, you will have to recompile the new edgy kernel,  you'll also have to recompile the kernel if ubuntu sends down new replacement kernels during automatic upgrades (if you want to use the new kernel provided with edgy)
You have to enable "use register arguments" in the kernel configuration, or you'll lock up the kernel when you insert the mishim module.  see my howto: [http://ubuntuforums.org/showthread.php?t=222774&highlight=Nortel](http://ubuntuforums.org/showthread.php?t=222774&highlight=Nortel)


Yes, it may seem weird, but I recompiled the kernel shipped with Edgy (2.6.17.13) enabling register arguments, yet I experience lockups with that kernel.
Even the Dapper kernel (2.6.15.7) recompiled with register arguments locked up a few times before actually working. I don't understand what's happening.

Chadd, how do you know the kernel shipped with Edgy has register arguments enabled ?
Is there a way to check if a kernel image really has this option ?

Thanks.

---

### Post by bzinger on 2006-11-02
Just wanted to say thanks to those of you who blazed the trail here. I followed the directions for my installation of Kubuntu Edgy on a Compaq R3000 and everything worked flawlessly. No need to recompile the kernel either. The install even added the Netlock to the KDE menu. Now I need to figure out how to get a version that doesn't time out after ten minutes. :-)

---

### Post by cporter71 on 2006-11-06
Wow - life is good.  Thanks to this thread I now too have my VPN working.  Wireless, VPN, and Linux all on a laptop - it is a brave new world!

Just wanted to add my process.  
1. Read through this entire thread.
2. Noted bzinger's comment that there was no need to recompile the kernel (using 2.6.17-10-generic with 6.10)- I borrowed this optimism.
3. Made the linux_wrapper.c changes suggested by chadd (and others that followed).
4. Compile still failed complaining as follows:
```

cd src && make all
make[1]: Entering directory `/downloads/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c: In function ‘nl_ip_rcv’:
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:421: error: too few arguments to function ‘ip_rcv’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c: In function ‘nl_skb_dup’:
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:529: error: ‘struct sk_buff’ has no member named ‘stamp’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:529: error: ‘struct sk_buff’ has no member named ‘stamp’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:530: error: ‘struct sk_buff’ has no member named ‘security’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:530: error: ‘struct sk_buff’ has no member named ‘security’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c: In function ‘nl_skb_hdr_copy’:
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:556: error: ‘struct sk_buff’ has no member named ‘stamp’
/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:556: error: ‘struct sk_buff’ has no member named ‘stamp’
make[4]: *** [/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/downloads/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/downloads/cvc_linux-rh-gcc3-3.3/src'
make: *** [all] Error 2

```
The following link helped me with this problem (thanks sbergens):
[http://forums.fedoraforum.org/showpost.php?p=458845&postcount=7]("http://forums.fedoraforum.org/showpost.php?p=458845&postcount=7")

I made the code changes as identified in blue. Recompiled and all was swell (had the same warning as chadd identified).

5. Made changes to scripts to source 'bash' - did the same also for scripts in the "scripts" dir.
6. Ran install.sh and all went relatively well (complained about netlock not being in init.d - no biggie).
7. cd scripts and ran "sudo ./netlock start" and a beautiful, welcoming message appeared to tell me all was swell.  
8. Pointed firefox at "http://127.0.0.1:9161", configured, connected.

Thanks everyone.
cporter

---

### Post by wcc11 on 2006-11-16
I am on Dapper and followed all the directions of deez0n.  However, when I ran "sudo make", I get the following error.  Your help is appreciated ](*,) 

wcc11@wcc11-laptop:~/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3$ sudo make
cd src && make all
make[1]: Entering directory `/home/wcc11/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/home/wcc11/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/wcc11/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/wcc11/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/wcc11/Desktop/download/cvc_all-3.3e/cvc_linux-rh-gcc3-3.3/src'
make: *** [all] Error 2

---

### Post by mbeierl on 2006-11-17
Could you repost that in [code] blocks?  I can't quite make out all the commands/output there.

---

### Post by sad on 2006-12-19
My company provides us the Windows version of the Nortel Contivity VPN client but will not provide the Linux version to us. Any idea where to get the latest Linux client code? If it requires a purchase any rough idea how much a 1 user license would cost or where I could go to research this?

---

### Post by deez0n on 2006-12-19
> **sad said:**
> My company provides us the Windows version of the Nortel Contivity VPN client but will not provide the Linux version to us. Any idea where to get the latest Linux client code? If it requires a purchase any rough idea how much a 1 user license would cost or where I could go to research this?

Try Apani's web site.. I believe it is $90 US and you can download a 10 day trial, though this may have changed by now. [http://www.apani.com/vpn-clients/nortel-overview](http://www.apani.com/vpn-clients/nortel-overview)

d

---

### Post by wcc11 on 2007-01-01
How do I put text in a code block?

I think the issue with the install is that it is not finding the build folder.  In Edgy, the folder is there (/lib/modules/2.6.17-10-generic/build)

In Dapper, there is no build folder under /lib/modules/2.6.15-26-386

Any ideas why this is?

thanks,
WCC

---

### Post by aparsons on 2007-02-09
Hello, I tried to install apani contivity in Ubuntu and am getting the following errors when compiling:

```

root@cfubuntu:/etc# ls -la|grep release
-rw-r--r--  1 root root      103 2006-08-03 03:20 lsb-release
root@cfubuntu:/etc# cat lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
root@cfubuntu:/etc# uname -r
2.6.15-26-386
root@cfubuntu:/etc# cd /tmp/cvc_linux-rh-gcc3-3.3
root@cfubuntu:/tmp/cvc_linux-rh-gcc3-3.3# whoami
root
root@cfubuntu:/tmp/cvc_linux-rh-gcc3-3.3# make
cd src && make all
make[1]: Entering directory `/tmp/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-26'
  CC [M]  /tmp/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o
/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c: In function âdo_checksum_offloadâ:
/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.c:747: error: dereferencing pointer to inco                                                                                mplete type
make[4]: *** [/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-26'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/tmp/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/cvc_linux-rh-gcc3-3.3/src'
make: *** [all] Error 2
root@cfubuntu:/tmp/cvc_linux-rh-gcc3-3.3#


```

I'm pretty much stuck, and I've made all of the change recommended in this forum, aside from recompiling my kernel.

-Allan

---

### Post by ilantz on 2007-02-16
Hi everyone , before i dive into re-compiling my kernel , did anyone tried to figure how to make this guide work in ubuntu ??

[http://www.novell.com/coolsolutions/feature/18321.html](http://www.novell.com/coolsolutions/feature/18321.html)

referenced by hickninja @ [http://ubuntuforums.org/showthread.php?t=350387](http://ubuntuforums.org/showthread.php?t=350387)

---

### Post by mbeierl on 2007-02-19
So I love living on the edge - I've just upgraded to 2.6.20 and now I'm getting the same error:
```

linux_wrapper.c:747: error: dereferencing pointer to incomplete type

```

I didn't get this in 2.6.19, oddly enough.  Whatever, I say to myself.  So off I go to google, which happily tells me the error is probably due to attempting to use the struct to dereference before the struct is defined.

Ok.

The struct is: struct tcphdr, and it's defined in net/tcp.h.  So I add the following:

Lines 74-76:
```

#include <net/ip.h>[B][COLOR="DarkRed"]
#include <net/tcp.h>[/COLOR][/B]
#include <linux/udp.h>

```

Code in bold/red added.  And suddenly it compiles nicely once again :)

Happy VPN to all. 
<rant>
And btw, I still love it that a company that sells VPN technology requires the use of an old kernel with known issues.  When are they ever going to release a new version ?!?  
</rant off>

---

### Post by mbeierl on 2007-02-21
:lolflag: I get to eat my words!

Apani just announced a new release for the Nortel client!  They're now shipping v3.5!

Btw, the #include <net/tcp.h> that I mentioned above is still required for v3.5, but NO OTHER CHANGES are necessary!

Woo Hoo!

Now maybe I'll be able to keep the connection alive just a little longer - it's been vaguely unstable for me - but that just might be my ISP.  (I'm rural running over a microwave link to a tower 5 kms away)

---

### Post by NobodySpecial on 2007-03-03
BIG thanks to all who helped on this project!  I am running Apani version 3.5 and it works great!  I followed all the instructions above.  I only made two changes:

There appears to be an error in the install script.  On line 49 of install.sh, find:
```
elif [-d /etc/rc0.d ]; then
```
Add a space in front of "-d":
```
elif [ -d /etc/rc0.d ]; then
```

Install now runs perfectly.  It will complain that it can't make several symlinks, but I don't believe they are needed on Ubuntu.

Only one other thing needed to make the Netlock links on the Applications menu work:
```
sudo chmod +x /usr/bin/start_cvc
```

mbeierl - Be sure you have port 500 forwarded on your router, or you can experience intermittent problems.

I hope some day we can have a free solution, but the present, this is the way to do it.  Now those who previously could not use Linux because they must connect to work via a Nortel switch finally have a way to join our family.  :)

---

### Post by rraiman on 2007-03-05
I started with Edgy and the instructions rock.  Everything just works.  I didn't have to build a custom kernel but I did have to edit the install file and the entry in /etc/init.d to change #!/bin/sh (really dash now) to #!/bin/bash.
Now my problem is that I am using 2.6.17-10-generic #2 SMP.  If I upgrade the system I will get 2.6.17-11 kernel.  I would like to do the update but.... Everything is running right now.
Do I leave well enough alone or has anyone tried this with 2.6.17-11 kernel?

I am an ex Fedora user and I assume I will have to do a reinstall if I update the kernel?

---

### Post by NobodySpecial on 2007-03-05
> **rraiman said:**
> I started with Edgy and the instructions rock.  Everything just works.  I didn't have to build a custom kernel but I did have to edit the install file and the entry in /etc/init.d to change #!/bin/sh (really dash now) to #!/bin/bash.
Now my problem is that I am using 2.6.17-10-generic #2 SMP.  If I upgrade the system I will get 2.6.17-11 kernel.  I would like to do the update but.... Everything is running right now.
Do I leave well enough alone or has anyone tried this with 2.6.17-11 kernel?

I am an ex Fedora user and I assume I will have to do a reinstall if I update the kernel?

You are right, you do **not** need to compile a custom kernel anymore.  I'm using Edgy with 2.6.17-11-generic and no problems.  I think at some point the devs must have noticed this issue and changed the way they compile the stock Ubuntu kernel, as no custom compiling is needed.

---

### Post by mbeierl on 2007-03-06
NobodySpecial - port 500, eh?  I do get intermittent problems, and don't have 500 forwarded. Is that tcp or udp?  And does anyone know why?

As an aside, I'm a kernel junkie (running 2.6.21-rc2 right now) and I recompile this all the time and have not had any problems.

So for anyone worried about going to 2.6.17-11, I'd say go for it.  Just keep the apani compile directory kicking around and do a make / sudo make install with every new kernel update.

---

### Post by NobodySpecial on 2007-03-07
mbeierl  - Yes, port 500.  I just set it up for TCP and it works fine.  I don't know all the specs for Nortel VPN, I just remember having problems where it would work, then suddenly not, and getting frustrated.  I called our IT guy at work and we did some troubleshooting and he had me open Port 500 TCP on my router and all has been well since!

A quick Google search shows that advanced firewall users must also allow protocols 50 and 51 (whatever that means - my hardware firewall doesn't list that).

---

### Post by Lumar on 2007-03-12
So I followed everyone advise in this thread.

For some reason I still get the 128: Syntax error: Bad fd number error.

I noticed that after I run the script it changes the /etc/init.d/netlock file back to sh instead of bash? Anyone know why it would change the file after running the script? grrrr](*,)

I got it to work... I didn't change the /script/netlock scripts sh to bash...

It says it's "done" installing... How to I use this software now? haha

---

### Post by Lumar on 2007-03-13
Nevermind... I didn't realize it worked out of a browser.

Thanks to everyone for this thread. =)

---

### Post by mbeierl on 2007-03-13
In the source directory (cvc_linux-rh-gcc3-3.5 or so) you will find two scripts called netlock:
```

$> ~/downloads/apani/cvc_linux-rh-gcc3-3.5$ find . -name 'netlock'
./netlock
./etc/netlock
./scripts/netlock

```
The ./etc/netlock is a directory, ingore it.  The other two (I can't remember which one is actually used) are the 'offending' scripts.  They replace the file in /etc/init.d whenever you recompile/reinstall the netlock client.

So, put the /bin/bash change into those files and you're good to go!

---

### Post by fractule on 2007-04-19
I just tried to make it work on Feisty fawn. After a few hacks it compiles, but module insertion crashes the kernel.
My new kernel version is 2.6.20-15-generic
If somebody want to try, here's what I did to make compilation work.

In linux_wrapper.c, before DECLARE_WAIT_QUEUE_HEAD(readq); I added this piece of code
```
#if LINUX_VERSION_CODE >= 0x020600
	#include <linux/utsrelease.h>
#endif
```


In k2.6/nlvcard.c, I replaced #include <linux/config.h> by
```
#include <linux/version.h>
#if LINUX_VERSION_CODE < 0x020600
	#include <linux/config.h>
#endif
```

After compiling, I ran sudo insmod mishim.o to test the compiled module, but it crashed the kernel. I retried a few times, without success.

Good luck.

---

### Post by chadd on 2007-04-26
Thanks for the additions.  I just successfully installed the latest netlock client from apani (cvc_linux-rh-gcc3-3.5) in the latest Ubuntu (2.6.20-15-generic feisty fawn)!  No crashes so far, and I can successfully connect through the VPN.  My Feisty is an upgrade from Edgy, if that makes any difference.  Good luck everyone!

---

### Post by imthemp3king on 2007-04-27
Hi, 

I'm using the 3.3 netlock client on Ubuntu 6.10.  I was able to compile and install the client ok and I am able to connect to the VPN device at my work, however I am unable to ping anything, not even the gateway of the subnet I get the address from .  Is there something else I need to do after connecting to the VPN to be able to communicate thru the VPN

---

### Post by wadageek on 2007-04-28
Just to let you know that the apani client works well with Feisty.  I did a clean install of Feisty, installed the needed packages, made the appropriate change to linux_wrapper.c and fixed the 'missing space on line 49' of install.sh and voila! the client is up and running.  Time to dish out some cash for the full version:guitar: 

Many thanks to all in this thread.

G.

---

### Post by rraiman on 2007-05-02
I just upgraded from Kubuntu Edgy to feisty.
I am trying to install cvc_linux-rh-gcc3-3.5.
I fixed the space in install.sh and the #!/bin/sh
make
make install

Fixed the #!/bin/sh to #!/bin/bash
in /etc/init.d/netlock  and restart

In konqueror:
[http://127.0.0.1:9161/](http://127.0.0.1:9161/)

I get:
Server Error
 The following error occurred:
 [code=CANT_CONNECT_LOOPBACK] Cannot connect due to potential loopback problems 
 Please contact the administrator.


Any suggestions?

---

### Post by rraiman on 2007-05-03
An answer to my own problem.
I had upgraded to 3.5 from 3.3 of Netlock after I upgraded from Kubintu 6.10 to 7.04.

I totally removed all of the client using the uninstall.sh script for both versions 3.5 and 3.3.

Then I reinstalled the 3.5 version:
make clean
make
make install

And tada!! all is well.  I wish I knew why but I am happy it works.

---

### Post by fractule on 2007-05-09
My problem may be that I still use version 3.3 because my company doesn't provide the 3.5 client yet.
Has anyone successfully made 3.3 work on Feisty ?

BTW, I do not believe that reinstalling a fresh Feisty Fawn full version would change anything.
Because after having reinstalled the OS and all my softwares, the package list and versions would just be the same, so there are no differences that could explain a different behaviour.

EDIT:
In fact, even though "insmod mishim.o" keeps crashing, I ran the installation, and well... the VPN just works fine !

---

### Post by haxor999 on 2007-05-11
Hi,

In looking for an open source solution for accessing a Nortel Contivity VPN I came across vpnc ([http://www.unix-ag.uni-kl.de/~massar/vpnc/]("http://www.unix-ag.uni-kl.de/~massar/vpnc/")). It started out as a Cisco client but they are in the process of adding support for Nortel.

You can check out the vpnc-nortel branch (based on an older version of vpnc, it is being integrated into the latest version) as follows:

svn co [http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/](http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/)

Unfortunately this version does not seem to be working with the Nortel Contivity VPN I use, but maybe one of you will have more luck :)

---

### Post by NobodySpecial on 2007-05-11
haxor999 - The vpnc way would be great.  Could you please post what you did to try to make it work?  People like me have no idea how to even get started.  You might even begin a new thread to discuss the issue.

Either way please let us know, so we can try to work on this.

---

### Post by haxor999 on 2007-05-12
Good idea NobodySpecial, please see the new thread at [http://ubuntuforums.org/showthread.php?p=2640346]("http://ubuntuforums.org/showthread.php?p=2640346")

I'm not that great at writing how-to's, but I hope it's a start.

---

### Post by ivotron on 2007-06-23
Hi,

Followed the great instructions here, everything goes fine except that I get a "negotiation with switch failed" message:

```
2007-06-23 18:40:02 (16,12e80008):Initiating negotiation with switch at xxx.xx.xx.1        
2007-06-23 18:41:07 (04,43040000):INM: MM Negotiation failed with result:SSH_IKE_NOTIFY_MESSAGE_TIMEOUT Local Address: 192.168.0.104 Remote Address: xxx.xx.xx.1
2007-06-23 18:41:07 (16,12e80008):<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<        
2007-06-23 18:41:07 (16,12e80008):Negotiation with switch at xxx.xx.xx.1 failed 
```

Using:
  - Apani 3.5
  - Edgy 2.6.17-11-386
  - Router configured to forward connections to tcp port 500
 
Anyone else that had this before and resolved it successfully? I'd really appreciate it. I hate living the irony of using Linux at work and Windows at home.

Thanks.

---

### Post by ivotron on 2007-06-23
forgot to say that I configured my D-Link's DI-624 router based on this page:

[http://support.dlink.com/faq/view.asp?prod_id=1153&question=nortel](http://support.dlink.com/faq/view.asp?prod_id=1153&question=nortel)

what I don't get is that step 3 says:

"... Find the IPSec Rule... Enable the rule, enter the IP address of the computer attempting to connect to the VPN in the Private IP field, then Apply the changes. "

then, step 5:

"...Disable IPSec Pass-through, then click Apply".

Isn't this contradictory?

Do you know if i need to open any other port?

Thanks.

---

### Post by trippinnik on 2007-06-26
Hi, I've tried following this howto but am still getting an error when I try to buil this:

geos@ubuntu:~/cvc_linux-rh-gcc3-3.5$ sudo make
Password:
cd src && make all
make[1]: Entering directory `/home/geos/cvc_linux-rh-gcc3-3.5/src'
cd k2.6 && make
touch: cannot touch `/lib/modules/2.6.20-15-server/build/include/linux/config.h': No such file or directory
make[2]: Entering directory `/home/geos/cvc_linux-rh-gcc3-3.5/src/k2.6'
make -C /lib/modules/2.6.20-15-server/build SUBDIRS=/home/geos/cvc_linux-rh-gcc3-3.5/src/k2.6 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.20-15-server/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/geos/cvc_linux-rh-gcc3-3.5/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/geos/cvc_linux-rh-gcc3-3.5/src'
make: *** [all] Error 2

I also tried using alien for both the red hat and suse versions, it installed but I got an error that the server could not be found in Firefox.

I really don't know why it can't touch the config.h this is a server install i setup today...

---

### Post by beckmerhagen on 2007-07-05
Did anybody successfully compile cvc_linux-rh-gcc3-3.5 on Linux 2.6.22?

When trying to build the app the compiler throws tons of messages like: 

make[3]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-7-generic'
  CC [M]  /home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In Funktion »init_misc«:
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: Fehler: »dev_base« nicht deklariert (erste Benutzung in dieser Funktion)
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:311: Fehler: für jede Funktion in der er auftritt.)
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In Funktion »nl_ip_rcv«:
/home/juergen/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:435: Fehler: »struct sk_buff« hat kein Element namens »nh«

On one of my machines I have Ubuntu Gutsy installed with 2.6.22 installed.

The other machine with Feisty (2.6.20) compiles and works fine.

Thanks.

---

### Post by JoeSchu on 2007-09-04
I'm able to compile in Feisty, but for some reason Firefox can't load the [http://127.0.0.1:9161](http://127.0.0.1:9161) page.  It says it can't connect to the server.  I'm not sure why I can't open that page on localhost.  Is there a default port setting I'm missing?

---

### Post by fractule on 2007-09-19
> **JoeSchu said:**
> I'm able to compile in Feisty, but for some reason Firefox can't load the [http://127.0.0.1:9161](http://127.0.0.1:9161) page.  It says it can't connect to the server.  I'm not sure why I can't open that page on localhost.  Is there a default port setting I'm missing?

Maybe the server has not started. Try
```
sudo /etc/init.d/netlock start
```
I remember it never starts automatically the first time. You have to start it manually, and afterwards it will start automatically on each boot.


By the way, on Feisty I experience random crashes on startup (the system freeze just before the screen switch to graphical mode), at first I thought it was an Xserver/video driver problem but I am now certain that the VPN is responsible for this mess. I had no choice but to get rid of it (it solved the problem), so be careful with that thing.

As the VPNC alternative did not work for me either, I gave up.

---

### Post by Prometheus7 on 2007-10-17
beckmerhagen, I am having a similar problem upon installing gutsy -- any success?

I posted my errors here...

[http://ubuntuforums.org/showthread.php?p=3547551#post3547551](http://ubuntuforums.org/showthread.php?p=3547551#post3547551)

---

### Post by wildbillnj1975 on 2007-10-25
I never saw any info on what to do if "insmod mishim.o" ***DOES ***crash your kernel :mad:.  The modprobe info does match my kernel.

What to do now?

---

### Post by mbeierl on 2007-10-25
Second post in this thread was

> **deez0n said:**
> [SIZE="2"]1: Follow the excellent kernel build directions listed below; (make sure you follow the xorg.conf instructions before the build) [COLOR="Red"]while on the make menuconfig step, turn on the[/COLOR] [COLOR="Blue"]"Use register arguments (CONFIG_REGPARAM)[/COLOR] [COLOR="Red"]under the[/COLOR] [COLOR="Blue"]"Processor type and features"[/COLOR] [COLOR="Red"]menu item[/COLOR]. Having this setting disabled is what is causing the kernel to lockup whenever the netlock module is inserted.[/SIZE]

What kernel are you using?

---

### Post by wildbillnj1975 on 2007-10-27
I saw that in the 2nd post, but other (later) posts said that you didn't have to recompile your kernel.  I have not had success trying that before, and was hoping to avoid it.

Running 'uname -a' returns:

Linux ubuntu 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686

---

### Post by mbeierl on 2007-10-27
I can't remember which kernel it was, but somewhere around 2.6.18 or so you no longer had to compile your own kernel.  Unfortunately with 15 you do need to make the change to the register parameters.

---

### Post by NobodySpecial on 2007-11-03
Some Fedora users made some progress with the 2.6.22 kernel issue, but not full success:
[http://forums.fedoraforum.org/showthread.php?p=863086]("http://forums.fedoraforum.org/showthread.php?p=863086")

I'm hoping some of the more programming-savvy users of this forum might try to see what they can do and post any suggestions back here.

---

### Post by digital_1 on 2007-11-06
Also hoping someone will take a look at this.  It could be quite a while if we have to wait for Apani to do something about it.  It's too bad that this thing always has to be this difficult.

---

### Post by mstamand on 2007-11-07
I got the contivity client to run on the Gibbon with the stock 2.6.22-14 kernel. No custom kernel needed. If you were able to run it on Feisty, all you would need is a slightly updated linux_wrapper.c (attached as linux_wrapper_2.6.22-14.c).

If you are starting from scratch I would recommend using the suse 3.3 tarball for gcc 3.x from Apani. Here is what I did:

[LIST=1]
[*]Edit install.sh and scripts/netlock and change the first line to read #!/bin/bash. 

[*]If you want to launch the contivity client through the install script, you may also want to :0,$:s/init.d\/init.d/init.d (i.e. remove the double init.d) in install.sh.

[*]Use the posted linux_wrapper_2.6.22-14.c file.

[*]Remove #include <linux/config.h> from the top of src/k2.6/nlvcard.c.

[*]Now make and make install.
[/LIST]

Marc St-Amand

---

### Post by kmikaz on 2007-11-07
Hi mstamand,
Thanks for sharing your experience. I have ubuntu 7.10 (kernel 2.6.22-14-generic) running on my 64bit home computer. I've try your recipe for running the contivity client, but got stuck at the step 5.
I downloaded the VPN Client for Nortel Contivity Demo from the Apani site, today.
I've unzip the linux_wrapper you provided, and copied it in cvc_linux-suse-gcc3-3.5/src directory, renaming it linux_wrapper.c .
When I do a make, I obtain the following error.
```

make: *** No targets specified and no makefile found.  Stop.
kmikaz@kmikaz:~/src$ cd cvc_linux-suse-gcc3-3.5/
kmikaz@kmikaz:~/src/cvc_linux-suse-gcc3-3.5$
kmikaz@kmikaz:~/src/cvc_linux-suse-gcc3-3.5$ sudo make
cd src && make all
make[1]: Entering directory `/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src'
cd k2.6 && make
make[2]: Entering directory `/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6/linux_wrapper.o
/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6/linux_wrapper.c: In function &#8216;nl_data_len&#8217;:
/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6/linux_wrapper.c:654: error: invalid operands to binary -
make[4]: *** [/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/kmikaz/src/cvc_linux-suse-gcc3-3.5/src'
make: *** [all] Error 2

```

I have the impression that maybe the linux_wrapper.c I downloaded from the Apani site is more recent than the one of your solution... Did you downloaded it some time ago? 
I'd hoped I could go the easy way...  :-(

---

### Post by NobodySpecial on 2007-11-07
mstamand - what new changes did you make in your wrapper file that haven't been posted here?  Thanks for contributing.

---

### Post by mstamand on 2007-11-07
> **kmikaz said:**
> Hi mstamand,
Thanks for sharing your experience. I have ubuntu 7.10 (kernel 2.6.22-14-generic) running on my 64bit home computer. I've try your recipe for running the contivity client, but got stuck at the step 5.


From the Apani info for the VPN client:

 System Requirements
    * Linux for Intel x86 or equivalent processors (32-bit)

I do not think you will be able to run the opaque nlvcard and mishim modules in a 64-bit environment.

> **kmikaz said:**
> 
I have the impression that maybe the linux_wrapper.c I downloaded from the Apani site is more recent than the one of your solution... Did you downloaded it some time ago? 
I'd hoped I could go the easy way...  :-(

Indeed. I used a 3.3 tarball for suse 9.3 that I downloaded from my work place two days ago (we have a site license). The linux_wrapper.c that I used is much older; I have hacked it up over the years to stay in synch with the various network stack changes in the kernel. I don't know what the 3.3-5 version entails, but I would guess it is more or less the same hacks up to FC6.

---

### Post by mstamand on 2007-11-07
I think you folks have already figured out the sk_buff header field changes, i.e.
[LIST]
[*]h.raw is now transport_header
[*]nh.raw is now network_header
[*]mac.raw is now mac_header
[/LIST]

The other change I had to make is to support the way network devices are linked in 2.6.22. In previous kernel versions, one would do something like:

```
struct net_device *dev;
for (dev = dev_base; dev; dev = dev->next)
{
   /* look for a device, compare addresses, do something */
}
```

I figured that nl_dev_base and dev_next() in the wrapper were put in place to do exactly this in the opaque Apani modules, but with no explicit coupling to dev_base and net_device.next. So I created a dummy device and modified dev_next():

```
net_device_t *dev_next (net_device_t *dev)
{
  /* return (dev->next); */
  if (&nl_dummy_dev == dev)
  {
    return first_net_device();
  }
  return next_net_device(dev);
}
```

I believe this was the missing part. As I mention in a previous post, I have been carrying the same linux_wrapper.c file for years, as I upgrade my home machine. Apologies for the lack of kernel version preprocessor directives; this is something Apani should put in if they are serious about keeping their CVC client up to date.

Personally, I would like to see the CVC key negotiation protocol published, so it could be implemented in an existing ipsec project. There would be no poking around in the dark every other kernel version, and we would not be limited to a 32-bit x86 PC to tunnel into work.

---

### Post by bald guy on 2007-11-08
> **mstamand said:**
> I think you folks have already figured out the sk_buff header field changes, i.e.

[B]
SNIP![/B]

I've figured out a lot less than that. :(

> **mstamand said:**
> 
I believe this was the missing part. As I mention in a previous post, I have been carrying the same linux_wrapper.c file for years, as I upgrade my home machine. Apologies for the lack of kernel version preprocessor directives; this is something Apani should put in if they are serious about keeping their CVC client up to date.

Could you possibly post diffs, and/or your linux_wrapper.c file?

> **mstamand said:**
> 
Personally, I would like to see the CVC key negotiation protocol published, so it could be implemented in an existing ipsec project. There would be no poking around in the dark every other kernel version, and we would not be limited to a 32-bit x86 PC to tunnel into work.

Absolutely.

I'm trying to get the Apani client (3.3.5) working under Fedora 7 (x86_64, kernel 2.6.23.1-10.fc7). (Yes, it's a F***ra system, but it looks like you might be the closest to having a working version of the Apani client...).

The best patches that I've found still produce a pile of bits, rather than something that compiles.  I'd be glad to help out any way I can (testing code, providing more details of my configuration, etc.).

Thanks!

---

### Post by oldcyberdude on 2007-11-08
Mstamand, thanks for posting your linux_wrapper.c   Using it as a guide I was able to make the modifications to version 3.5 wrapper and recompile for Gibbon. BTW, I will be posting the changes internally to my company crediting you :)  Thanks again

---

### Post by arielUBA on 2007-11-09
Thanks mstamand for your contribution.
I'm posting the modified linux_wrapper.c for Apani 3.5

It works well (in Gentoo)

Thanks

---

### Post by NobodySpecial on 2007-11-09
Yeah! It works!
BIG thanks to both mstamand and arielUBA

For those of you just joining us, here is a synopsis of how to make this work.
For Ubuntu Gutsy 7.10 running Apani 3.5
I use the purchased version, but the demo should work as well.

Instructions:
Start in directory with cvc_linux-3.5.tar.gz and [linux_wrapper-3.5-2.6.22.c.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=49666&d=1194658378")
```
tar xvf cvc_linux-3.5
cd cvc_linux-3.5
tar xvf cvc_linux-rh-gcc3-3.5.tar.gz
cd cvc_linux-rh-gcc3-3.5
cd src
tar xvf ../../../linux_wrapper-3.5-2.6.22.c.tar.gz
mv linux_wrapper.c linux_wrapper.c_old
mv linux_wrapper-3.5-2.6.22.c linux_wrapper.c
cd
chmod +w install.sh netlock uninstall.sh scripts/netlock scripts/start_cvc
```

There are five files to edit:
```
gedit install.sh
gedit netlock
gedit uninstall.sh
gedit scripts/netlock
gedit scripts/start_cvc
```
On the first line on each of these, change:
```
#!/bin/sh
```
to
```
#!/bin/bash
```
Then,
```
gedit install.sh
```
On line 49:
```
elif [-d /etc/rc0.d ]; then
```
Add space in front of -d
```
elif [ -d /etc/rc0.d ]; then
```
Then,
```
sudo make
sudo make install
sudo chmod +x /usr/bin/start_cvc
```
To start:
```
sudo /etc/init.d/netlock start
```
In Firefox:
```
http://127.0.0.1:9161
```

Enjoy!  :)

---

### Post by mstamand on 2007-11-09
The 3.5 wrapper posted by ArielUBA looks perfect. He should send a bill to Apani. :)

> **bald guy said:**
> 
Could you possibly post diffs, and/or your linux_wrapper.c file?


It may not be relevant at this point, but here you are. I have attached the 3.3 original linux_wrapper.c. IIRC it used to work unaltered up to kernel version 2.6.12.

> **bald guy said:**
> 
I'm trying to get the Apani client (3.3.5) working under Fedora 7 (x86_64, kernel 2.6.23.1-10.fc7). (Yes, it's a F***ra system, but it looks like you might be the closest to having a working version of the Apani client...).


ArielUBA's wrapper may work for you. The only thing I am not certain about is the 64-bit architecture; I could not find any documentation on it.

If you do have elf64 mishim and nlvcard object files in your client tarball, then I would advise caution regarding the sk_buff headers. From looking at the kernel code, I noticed that the transport, network and mac headers are interpreted either as 32-bit pointers, or as buffer offsets in 64-bit architectures. 

For example, this logic from nl_skb_dup works on a 32-bit kernel:

```

    int head_offset = new_skb->head - skb->head;
    new_skb->transport_header = skb->transport_header+head_offset;
    new_skb->network_header = skb->network_header+head_offset;
    new_skb->mac_header = skb->mac_header+head_offset;

```

On a 64-bit kernel, the headers are already interpreted as offsets. To achieve the same result as above (i.e. set the correct header offsets in new_skb), one would just do:

```

    new_skb->dev = skb->dev;
    new_skb->dst = dst_clone(skb->dst);
    new_skb->transport_header = skb->transport_header;
    new_skb->network_header = skb->network_header;
    new_skb->mac_header = skb->mac_header;

```

Is there a 64-bit evaluation tarball available from Apani? I may be able to get my paws on a 64-bit machine and give it a go.

Cheers,
Marc

---

### Post by bald guy on 2007-11-12
> **mstamand said:**
> The 3.5 wrapper posted by ArielUBA looks perfect. He should send a bill to Apani. :)



It's great that someone's doing development on the Contivity client! :)
> **mstamand said:**
> 



It may not be relevant at this point, but here you are. I have attached the 3.3 original linux_wrapper.c. IIRC it used to work unaltered up to kernel version 2.6.12.



ArielUBA's wrapper may work for you. The only thing I am not certain about is the 64-bit architecture; I could not find any documentation on it.


I've tried ArielUBA's wrapper...unfortunately it still fails to compile the client. The errors I get are:
```

cd src && make all
make[1]: Entering directory `/usr/src/apani/cvc_linux-rh-gcc3-3.5/src'
cd k2.6 && make
make[2]: Entering directory `/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6'
make -C /lib/modules/2.6.23.1-21.fc7/build SUBDIRS=/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6 modules
make[3]: Entering directory `/usr/src/kernels/2.6.23.1-21.fc7-x86_64'
  CC [M]  /usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o
/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ânl_unregister_chrdevâ:
/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:372: error: void value not ignored as it ought to be
/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ânl_data_lenâ:
/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:699: error: invalid operands to binary -
make[4]: *** [/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/kernels/2.6.23.1-21.fc7-x86_64'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/usr/src/apani/cvc_linux-rh-gcc3-3.5/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/apani/cvc_linux-rh-gcc3-3.5/src'
make: *** [all] Error 2

```

> **mstamand said:**
> 
If you do have elf64 mishim and nlvcard object files in your client tarball, then I would advise caution regarding the sk_buff headers. From looking at the kernel 

SNIP!

> **mstamand said:**
> 
On a 64-bit kernel, the headers are already interpreted as offsets. To achieve the same result as above (i.e. set the correct header offsets in new_skb), one would just do:

```

    new_skb->dev = skb->dev;
    new_skb->dst = dst_clone(skb->dst);
    new_skb->transport_header = skb->transport_header;
    new_skb->network_header = skb->network_header;
    new_skb->mac_header = skb->mac_header;

```

That's a big help, thanks!


Is there a 64-bit evaluation tarball available from Apani? I may be able to get my paws on a 64-bit machine and give it a go.
[/QUOTE]
Ha! That's the best laugh I've had recently.

Thanks again.

> **mstamand said:**
> 
Cheers,
Marc

---

### Post by DageonYar on 2007-11-15
Followed the above instructions, but when I try to make in the cvc folder, it chokes on the 1st line

~/cvc/cvc_linux-gcc2-3.3/src/k2.6$ make
make: *** No rule to make target `../libmishim-2.6.a', needed by `kmod_build'.  Stop.

:( Can someone help me out?

---

### Post by ceoxtc on 2007-11-15
> **DageonYar said:**
> Followed the above instructions, but when I try to make in the cvc folder, it chokes on the 1st line

~/cvc/cvc_linux-gcc2-3.3/src/k2.6$ make
make: *** No rule to make target `../libmishim-2.6.a', needed by `kmod_build'.  Stop.

:( Can someone help me out?

DageonYar, I probably know less than anyone here but if your above quote is accurate, you are executing the makefile in the src folder and not the one in the base folder.  You should be in:

~/cvc/cvc_linux-gcc2-3.3    In other words, your terminal prompt/command should look like:

~/cvc/cvc_linux-gcc2-3.3$ sudo make

I was getting the same error and it turns out, I was using the source code and not the SuSE rpm.  When I tarred  that file (cvc_linux-suse-gcc3-3.5e-0.src.rpm) and followed NobodySpecial's instructions above using the linux_wrapper.c file,  the source compiled fine and I'm up and running.  Good Luck!

---

### Post by wildbillnj1975 on 2007-11-16
mbeierl , I'm finally getting back to this.  So, I looked at [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") to see how to recompile my kernel, and I find this lovely piece of advice:

> Also note that this page describes how to do things for the Edgy (2.6.17) kernel and newer! Until this kernel source, we did not have any mechanisms in place that would allow people to build their own kernels easily. This was intentional.

Well, thanks a bunch, Ubuntu folks.  I have to recompile my kernel to get something to work (so that I can get some *WORK* done), but I'm intentionally thwarted in my efforts.  I don't think that really agrees with the whole Linux ethos...

So, what is 2.6.18?  Edgy?  Feisty? Gutsy?  I'm not a bleeding-edge user, so none of those sound interesting to me...

Anybody know of a good kernel-compile-howto for 2.6.15?

---

### Post by mbeierl on 2007-11-16
I'd just like to make sure I understand the context:  You're running an older kernel, say 2.6.15, under Edgy Eft, or what version of ubuntu?

Compiling the kernel isn't that tough, but I'd just like to make sure I know to give you the right advice :)

---

### Post by mbeierl on 2007-11-16
Doh - Sorry, went back and found your post.  Looking into it now...

---

### Post by ephoenix on 2007-11-21
> **NobodySpecial said:**
> Yeah! It works!
BIG thanks to both mstamand and arielUBA

For those of you just joining us, here is a synopsis of how to make this work.
For Ubuntu Gutsy 7.10 running Apani 3.5
I use the purchased version, but the demo should work as well.

...snip...


It works like a charm!!! Big thanks to you guys!

---

### Post by mbeierl on 2007-11-21
Odd, wildbillnj1975, it seems the regparam thing is not in 2.6.15.  So I don't know why you are having kernel hangs.

Did you try a simple compile?  Like so:

download the source from kernel.org and unpack it
```

cd /usr/src/linux
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.7.tar.bz2
tar xjvf linux-2.6.15.7.tar.bz2

```

now "edit the configuration"
```

cd linux-2.6.15.7
make menuconfig

```
now build it:
```

fakeroot make-kpkg --initrd kernel_headers kernel_image modules

```
you may need to install some packages (like fakeroot) and you probably need to add yourself to the "src" group in /etc/groups.

At the end of this you should have two .deb files in /usr/src that are your newly compiled kernel.  Use
```

cd /usr/src
dpkg -i <your-kernel-debs-here.deb>

```
It should show up in grub at next reboot.

---

### Post by delor on 2007-11-27
Very nice, NobodySpecial!  I ran through the instructions and got all of the makes complete without any visible errors.  This is the closest I've gotten to getting the VPN software working yet.

  Quick question for anyone who might know:

  When I run
```
sudo /etc/init.d/netlock start
```

  I get
```
Starting Netlock services: insmod: error inserting '/etc/netlock/mishim.o': -1 File exists
```

  Is this normal?  If not, is it a show stopper?  Despite getting that, when I go to [http://127.0.0.1:9161](http://127.0.0.1:9161) it gives me the VPN registration website.  It's not liking my license key, though- not sure if this is related to the error when I do netlock start or not.

  Any help would be greatly appreciated.

---

### Post by delor on 2007-11-27
> **DageonYar said:**
> Followed the above instructions, but when I try to make in the cvc folder, it chokes on the 1st line

~/cvc/cvc_linux-gcc2-3.3/src/k2.6$ make
make: *** No rule to make target `../libmishim-2.6.a', needed by `kmod_build'.  Stop.

:( Can someone help me out?

  If you're working with the same batch of files I am, you probably got a bunch of different versions of it.  (gcc2, rh, and suse in tar and RPM format)  Following Nobody's installation guide, I started with "cvc_linux-gcc2-3[2].5.tar.tar" and got the same error you did.  I then tried "cvc_linux-rh-gcc3-3[1].5.tar.tar" and it completed the make properly.

  So, if you have cvc_linux-rh-gcc3-3[1].5.tar.tar try working with that instead.

---

### Post by bald guy on 2007-12-14
I had an interesting talk with Apani support today, as a follow-up to my complaints about the lack of updates to the Contivity client for Linux and the fact that it doesn't run on modern Linux kernels or 64-bit architecture.

The Apani representative urged me to get as many people as possible to report their feedback and need for an updated Contivity client directly to Apani. He told me that they want to update the Linux client, but that they need to justify within Apani that there's a strong customer demand for on-going development.

**Please send mail to Apani Support <[email]support@apani.com[/email]> telling them how important it is to provide an updated Linux client.**

---

### Post by oldcyberdude on 2008-01-04
BTW, just a quick note to again thank mstamand for the changes to the client. Your changes also work on the new [Asus EeePC]("http://www.asus.com/products.aspx?l1=24&l2=0&l3=0&l4=0&model=1907&modelmenu=1") when running the simplified [eeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home").

All I had to do to get Apani running was copy over the already compiled client from my Kubuntu Gutsy Gibbon machine and run the install script.

I did not try to get the client running on a vanilla EeePC with the stock Xandros kernel. I have now tweaked the eeXubuntu install so much I'm not really interested in going back to the beginning. If anybody has experience with the Xandros kernel please post.

---

### Post by yl200001 on 2008-01-10
> **NobodySpecial said:**
> Yeah! It works!
BIG thanks to both mstamand and arielUBA

For those of you just joining us, here is a synopsis of how to make this work.
For Ubuntu Gutsy 7.10 running Apani 3.5
I use the purchased version, but the demo should work as well.

Instructions:
Start in directory with cvc_linux-3.5.tar.gz and [linux_wrapper-3.5-2.6.22.c.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=49666&d=1194658378")
...
...
Enjoy!  :)

Hi, I have Apani v3.3 working at Ubuntu 7.04.  Now i want to upgrade to 7.10 and Apani v3.5.  I do have license code for my Apani v3.3 which should work for v3.5 too. But I can only download evaluation copy without buying it.  Do you know where i can get the official Apani v3.5 and input my own license key?
(my email is [email]wawa579964@gmail.com[/email])

Another thing, i can boot from both 2.6.22-14-386 and 2.6.22-14-generic and normally run at 2.6.22-14-386 (2.6.22-14-generic doesnt recognize my display card well). But the directory /lib/modules/2.6.22-14-386/build is empty, so "sudo  make" has the following error:
make[3]: *** No rule to make target `/lib/modules/2.6.22-14-386/build/arch/i386/Makefile'. Stop.
make[3]: Leaving directory `/lib/modules/2.6.22-14-386/build'
...

But it is fine to be under 2.6.22-14-generic. Why is this?

---

### Post by whistlenuts on 2008-01-22
I used NobodySpecial's guide and was able to install, start and log into my company's network using the Netlock client (thanks for the help!), but this morning I tried to login to the network, something funky happened.

I started the service using ```
sudo /etc/init.d/netlock start
``` and it returned "Starting Netlock services:" and then returned me to the prompt.

So I figured everything was up and running, but when I go to [http://127.0.0.1:9161](http://127.0.0.1:9161) and it gives me the "page not found" error. 

I tried to check if the service is running and there's nothing running with the name 'netlock'...moreover, I looked at the log file and other than a timestamp, there's nothing there indicating an error occurred. 

Anyone have any ideas of how I can trouble-shoot this?

---

### Post by deybiluisi on 2008-02-08
Someone helps me I cannot install it, this error assumes me

I have sought various forums but in spite of testing some suggestions not it achievement


~/Escritorio/cvc_linux-gcc2-3.3$ sudo make
cd src && make all
make[1]: se ingresa al directorio `/home/deybi/Escritorio/cvc_linux-gcc2-3.3/src'
cd k2.6 && make
make[2]: se ingresa al directorio `/home/deybi/Escritorio/cvc_linux-gcc2-3.3/src/k2.6'
make[2]: *** No hay ninguna regla para construir el objetivo `../libmishim-2.6.a', necesario para `kmod_build'.  Alto.
make[2]: se sale del directorio `/home/deybi/Escritorio/cvc_linux-gcc2-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: se sale del directorio `/home/deybi/Escritorio/cvc_linux-gcc2-3.3/src'
make: *** [all] Error 2

---

### Post by wildbillnj1975 on 2008-02-18
mbeierl, I compiled the kernel today, and it all worked ok.  Rebooted with the new kernel.

Then I compiled the vpn client, and it went OK, except for the warning:

```
Warning: could not find /usr/local/cvc_linux-rh-gcc3-3.3/src/k2.6/../.libmishim-2.6.a.cmd for /usr/local/cvc_linux-rh-gcc3-3.3/src/k2.6/../libmishim-2.6.a
```

Installed/ran the vpn client, and I get the web portal at [http://localhost:9161](http://localhost:9161)

When I enter my info and try to connect, I get:

```
Negotiation with switch at *my-work-ip* failed
```

The log file /etc/netlock/agentlog.txt says:

```
<date/time> (04,43040000):INM: MM Negotiation failed with result:SSH_IKE_NOTIFY_MESSAGE_NO_PROPOSAL_CHOSEN Local Address: *my-local-ip *Remote Address: *my-work-ip*
```
I see another user has run into that problem previously; I have not seen any response to it suggesting a resolution...

Any of you bright folks have a suggestion for this problem?

I'm certain it's not purely a router issue, as I am able to use the Contivity VPN client for the same thing from my Windows machine on the same LAN.

---

### Post by richardhall on 2008-04-27
Hello, Has anybody got netlock to work with 8.04?  

I ran the upgrade to Hardy and then when I tried to start Netlock I got the message 'unable to connect to 127.0.0.1:9161' so ran make uninstall and then make install.

Make gave me numerous errors starting with ':372: error: void value not ignored as it ought to be' in linux_wrapper.c'

This was in cvc_linux-rh-gcc3.3-5, the download I used to make Netlock under 7.10.

Is there a new version I should look for?

Thanks,
Richard

---

### Post by bzinger on 2008-04-27
> **richardhall said:**
> Hello, Has anybody got netlock to work with 8.04?  

I ran the upgrade to Hardy and then when I tried to start Netlock I got the message 'unable to connect to 127.0.0.1:9161' so ran make uninstall and then make install.

Make gave me numerous errors starting with ':372: error: void value not ignored as it ought to be' in linux_wrapper.c'

This was in cvc_linux-rh-gcc3.3-5, the download I used to make Netlock under 7.10.

Is there a new version I should look for?

Thanks,
Richard


Unfortunately I and some others working with the 2.6.24 kernel on the Fedora forum were unable to make this work. One of the differences I found in kernel networking was the filter hook function takes a pointer to the sk_buff. In 2.6.22 it was a pointer to a pointer. Changing this will allow the driver to load without locking up the kernel. Unfortunately I was not able to establish a connection with the VPN switch. I have heard that a new version of the driver may be out in the third quarter of this year that will support new kernels. For the time being, I built a 2.6.22 version of the kernel and installed it on Heron when I need to use VPN.

Regards,

Mike

---

### Post by jaustinbea on 2008-04-30
Hello there,

I am pleased to say that I have managed to get the apani client working on 2.6.24. This is a combination of Mike's pointer regarding the change in netfilter interface and a re-write of nlvcard.c.

If you go to the postings on fedora forum, you'll be able to download the nlvcard.c and linux_Wrapper.c that works for 2.6.24.

Please note that this works on the fedora 2.6.24.5-85 release and the generic kernels released with Hardy Heron may have differences. All the same, it _should_ work ;-)

Good luck

James

---

### Post by wildbillnj1975 on 2008-04-30
James --

I don't see any other reference to netfilter in this thread.  Can you post a link to that message/thread so we can find that fix?  Or is that just the new linux_wrapper.c?

Same for nlvcard - the only reference in this thread does not seem to be a solution.

Also can you provide a link to that Fedora forum?

Thanks!

---

### Post by bzinger on 2008-04-30
> **wildbillnj1975 said:**
> James --

I don't see any other reference to netfilter in this thread.  Can you post a link to that message/thread so we can find that fix?  Or is that just the new linux_wrapper.c?

Same for nlvcard - the only reference in this thread does not seem to be a solution.

Also can you provide a link to that Fedora forum?

Thanks!

Here's the reference to James' post on the Fedora forum:

    [http://www.fedoraforum.org/forum/showthread.php?p=1003999]("http://www.fedoraforum.org/forum/showthread.php?p=1003999")

I have also installed and given this a try. It locks my machine up after establishing the connection. However, since I am having some problems with check-sum errors being reported by my network card, I cannot reliably test this. I am looking forward to some of you testing this and hearing your results.

Regards,

Mike

---

### Post by cabr1to on 2008-05-01
I've managed to build this on Ubuntu Hardy, having cobbled together a few forum posts from here, past releases, and Fedora forums.

Here is a tarball of changed files that you can use to patch the GCC3.3 suse installation for a one-shot install.  (I would post the whole source tarball here but not sure if that's kosher...)  :)

This is meant to be extracted over the "cvc_linux-suse-gcc3-3.3" version of the cvc distribution for Nortel Contivity VPN client.

Good luck!

--PK

---

### Post by jschwartz73 on 2008-05-15
Did anybody get this to work with apani version 3.5?

I tried the above patch, but I get the following error: 
./install.sh: line 223: /etc/rc.d/init.d/init.d/netlock: No such file or directory

If I correct the line so that it correctly points to the /etc/rc.d/init.d directory, then I get the following error:
Starting Netlock services: /etc/rc.d/init.d/netlock: 128: Syntax error: Bad fd number

Any suggestions?

Thanks in advance.

---

### Post by Zeratul7 on 2008-05-17
> **jschwartz73 said:**
> Did anybody get this to work with apani version 3.5?

I tried the above patch, but I get the following error: 
./install.sh: line 223: /etc/rc.d/init.d/init.d/netlock: No such file or directory

If I correct the line so that it correctly points to the /etc/rc.d/init.d directory, then I get the following error:
Starting Netlock services: /etc/rc.d/init.d/netlock: 128: Syntax error: Bad fd number

Any suggestions?

Thanks in advance.

```
sudo gedit /etc/init.d/netlock
```
change:
```
#!/bin/sh
```
into:
```
#!/bin/bash
```

Edit: This way I got it connected but it freeses my PC completelty after a few seconds/minutes.

---

### Post by jschwartz73 on 2008-05-19
Thanks, that worked!

---

### Post by mstamand on 2008-06-06
Thank you very much James for the nlv0 driver rewrite. I was hacking the cvc wrappers for 8.04 on my own, and stumbled upon your post. I ended up "borrowing" your version of nlvcard.c, massaging it a bit, and bingo, I was able connect to work through yet another network stack NUC.

Now about the massaging: with the posted code I saw kernel panics every time the nlvcard module was removed (through "/etc/init.d/netlock stop", or manually doing a rmmod). The root cause of the problem is the declaration of pernet_operations in __net_initdata. This puts the structure in the .init.data section, which gets freed once the init code has run. We also want to invoke unregister_pernet_device in the __exit function, to make sure the device is removed.

The updated file is attached. Feel free to "borrow" it back. :

---

### Post by bzinger on 2008-06-06
> **mstamand said:**
> Thank you very much James for the nlv0 driver rewrite. I was hacking the cvc wrappers for 8.04 on my own, and stumbled upon your post. I ended up "borrowing" your version of nlvcard.c, massaging it a bit, and bingo, I was able connect to work through yet another network stack NUC.

Now about the massaging: with the posted code I saw kernel panics every time the nlvcard module was removed (through "/etc/init.d/netlock stop", or manually doing a rmmod). The root cause of the problem is the declaration of pernet_operations in __net_initdata. This puts the structure in the .init.data section, which gets freed once the init code has run. We also want to invoke unregister_pernet_device in the __exit function, to make sure the device is removed.

The updated file is attached. Feel free to "borrow" it back. :

Bravo! mstamand. This is the first version that I have been able to get working reliable with the 2.6.24 kernel. I have been connected for the longest time without locking up. I can finally retire the 2.6.22 kernel that I have installed here just to VPN.

Thanks a lot!!!

Regards,

Mike

---

### Post by sjgarrettsdag on 2008-06-08
Is there a mastermind here who could make a Hardy-based .deb?

---

### Post by transfinite on 2008-06-20
Much thanks for all the updates.  I just upgraded some boxes to Hardy, as this was all that was holding them back.

One note- this version of linux_wrapper.c writes a **lot** of debug messages to /var/log/messages.

I commented out #define DEBUG and all the *printk(* messages, and that quieted it.

Kudos to the guys keeping this working on new kernels!

---

### Post by bluescreen10 on 2008-06-23
It keeps freezing my laptop, I'm using Apani 3.5 (compiled using gcc3) with Kernel 2.6.24-19. It work for a while then it freezes up the kernel. Has somebody make it work with newer kernels stable for long periods???

---

### Post by irregardlessly on 2008-06-30
Thanks everyone for doing all of this legwork.  Using Nortel is the only reason I still boot into Windows.  I would love to rid myself of this need.

Can someone post a comprehensive how-to getting this to work from scratch with Hardy?  It is hard to follow everything after the fact with patches on top of patches..

Thanks!

---

### Post by gmoore777 on 2008-07-02
I still cannot get Apani to work on HardyHeron. 

It will either disconnect in a few seconds and/or cause machine to freeze such that a power cycle is needed.

I do reboot after each deinstall, and after every install, prior to testing.

I am on HardyHeron with the latest 2.6.24.19.21 headers.

Using cvc_linux-rh-gcc3-3.5.tar from [https://support.apani.com/download/](https://support.apani.com/download/)

Using linux_wrapper.c.tar from jaustin at  [http://www.fedoraforum.org/forum/attachment.php?attachmentid=15806](http://www.fedoraforum.org/forum/attachment.php?attachmentid=15806)

Using nlvcard_2.6.24-17.c.gz from mstamand at [http://ubuntuforums.org/attachment.php?attachmentid=73136&d=1212760363](http://ubuntuforums.org/attachment.php?attachmentid=73136&d=1212760363)

and the latest word as of yesterday from Apani is that late Q3 there will be a newer version available that perhaps may work on Hardy but will still be an unsupported platform.

---

### Post by artships on 2008-07-11
cabr1to's patched files let me compile the suse client.  Had to go through all the suse scripts, changing #!/bin/sh to #!bin bash AND removing all the windows carriage-return/linefeeds.  However, start_cvc brings up the register screen.  I never got a CD so I've no number with which to register.  And the link to "obtain an evaluation licence code" goes nowhere.  So I can't really say this thing works.

So I'm going to go back to working on a script to let ubuntu communicate through the tunnel the Windows client successfully creates inside VirtualBox.

---

