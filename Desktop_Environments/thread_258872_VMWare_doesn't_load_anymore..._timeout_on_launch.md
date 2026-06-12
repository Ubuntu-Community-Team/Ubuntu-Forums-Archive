---
title: "VMWare doesn't load anymore... timeout on launch"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Giggity on 2006-09-16
So, I'm running 6.06.1 and some applications are occasionally not loading properly (timing out) as of a few days ago.  The ones that exhibit this behavior are (so far) Firefox 1.5.0.7, Synaptic, and VMWare Workstation 5.5.2 v29772

Firefox and Synaptic usually load quickly and properly on the second attempt.  VMWare, however, is the real bummer.  It times out every time after about 20 seconds, and it used to load as quickly as everything else (fast!).  The same thing happens with VMWare Player.

If it helps you to know, I've recently updated my kernel, and installed nVidia's proprietary drivers as well as reinstalling MadWiFi using the current snapshot (it had stopped working yesterday, but now it's fixed).  Do you think any of these might have affected VMWare?

Since you'll probably want to know:
```
rob@rob-desktop:~$ uname -r
2.6.15-26-386
```

I have a 64-bit Athlon X2, but I'm using the 386 edition due to some proprietary software not being available for or compatible with the amd64 release.

Please let me know what other diagnostic information you might need, as I require VMWare in order to run a couple of Windows programs that don't work with Wine.

Looking forward to hearing from the experts... you've all been so helpful so far!

---

### Post by Giggity on 2006-09-16
Having guessed that the recent kernel upgrade might have done something to interfere with VMWare, I went ahead and reinstalled it, which allowed for a recompile.  *It still does not load*, with the taskbar button appearing (with a spinning hourglass in KDE), but the program not starting, and then giving up.

Attempting to start it via the console yields:

```
rob@rob-desktop:/usr/bin$ sudo vmware
Password:
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

I already have run the configuration script, as you can see in the install log.  This same thing happens in GNOME, KDE, and Xfce.  I can't for the life of me figure out what might have caused this behavior, and nobody else seems to have had this problem.  Does anyone have any input?

I've enclosed my install log sans EULA, in case it is of any use to you.

---

### Post by Giggity on 2006-09-16
I've now tried the patch vmware-any-any-update104.tar.gz from Czech Tech.  Nothing has changed, which isn't surprising given that the update file is dated August 14 2006.

So, still unable to start VMWare Workstation, and I've tried both updating the kernel header files as well as uninstalling, reinstalling and updating VMWare itself.  Nothing.

Is VMWare irreparably damaged due to the new kernel?  If so, can I go back to the old kernel that worked perfectly?  Can anyone help out, or have my newbie questions landed me on ignore lists?  At this point, even hate mail will be welcomed.

I've enclosed the log from the update attempt.

---

### Post by Anduu on 2006-09-17
Try launching vmware from a terminal and post any errors.

---

### Post by entangled on 2006-09-17
I have newly installed vmware server 1.0.1-29996 after download from vmware site. I previously had vmware player installed via synaptic but removed it (I hope) after I realised the kernel support was missing.
My kernel is 2.6.15-26-386 #1 PREEMP., just updated to build 47.

I followed vmware instructions and all feedback seemed good, but I am getting same error message as 'giggity' when I try to run from terminal.

I tried to set bridged networking but it says that is not configured. I tried to NOT set host-only networking and it says that is working!

Re-config from the terminal still looks OK.
Is there any better diagnostic?

Some module stuff, in case it is useful:

```
FATAL: Module vmnet0 not found.
peter@macbuntu:~$ sudo modprobe vmmon
peter@macbuntu:~$ sudo modinfo vmmon
filename:       /lib/modules/2.6.15-26-386/misc/vmmon.ko
author:         VMware, Inc.
description:    VMware Virtual Machine Monitor.
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:
srcversion:     015BEC53B16E5DD03801810
peter@macbuntu:~$ sudo vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

peter@macbuntu:~$ lsmod|grep vm
vmnet                  37412  6
vmmon                 112012  0
peter@macbuntu:~$ sudo modinfo vmnet
filename:       /lib/modules/2.6.15-26-386/misc/vmnet.ko
author:         VMware, Inc.
description:    VMware Virtual Networking Driver.
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:
peter@macbuntu:~$
```

---

### Post by dyoung66 on 2006-09-17
I also have this problem after the 2.6.15-26-686
kernel update. 
Vmware, kaffeine and amarok are the main offenders. I still start vmware by killing it the first time it hangs, then starting it again, waiting a while and it usually starts. Hardly a fix, but have you tried killing the process and restarting it a few (3-4)times?
I really think the new kernel and not vmware is at fault. Do you have the linux headers installed for that kernel? That should stop you from needing to recompile vmware everytime you upgrade your kernel(AFAIK).

Can you rollback to a previous kernel or select a previous kernel from your grub menu to get vmware going again?

---

### Post by Giggity on 2006-09-17
> **Anduu said:**
> Try launching vmware from a terminal and post any errors.

Yeah, like I said in post #2 in this thread (but I tried again to humor you, since I've reinstalled since then)...

```
rob@rob-desktop:/usr/bin$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

Just for the heck of it, here's the latest install log.  What seems to be happening is the bridged networking module is failing to load after configuration.

I'll be back in a couple of hours...

---

### Post by Giggity on 2006-09-17
> **dyoung66 said:**
> I also have this problem after the 2.6.15-26-686
kernel update. 
Vmware, kaffeine and amarok are the main offenders. I still start vmware by killing it the first time it hangs, then starting it again, waiting a while and it usually starts. Hardly a fix, but have you tried killing the process and restarting it a few (3-4)times?
I really think the new kernel and not vmware is at fault. Do you have the linux headers installed for that kernel? That should stop you from needing to recompile vmware everytime you upgrade your kernel(AFAIK).

Can you rollback to a previous kernel or select a previous kernel from your grub menu to get vmware going again?
Funny.  amaroK and Kaffeine are working fine for me.

As for killing the VMWare process and trying again a few times, that hasn't worked, which is to be expected since starting it from the terminal immediately yields that error message posted above.

And yes, I do have the latest linux headers installed if the enclosed screenshot isn't lying...

---

### Post by Giggity on 2006-09-17
> **dyoung66 said:**
> Can you rollback to a previous kernel or select a previous kernel from your grub menu to get vmware going again?
That's a good idea, but GRUB doesn't list the old kernel (I think it was 2.6.15-25.43 or something that looked like that).

1. What packages should I uninstall/reinstall in order to go back to the old kernel?

2. Since VMWare is unsupported by Ubuntu, and thus kernel updates might cause serious problems, how do I keep the new kernel from being installed until I ask it to?

Thanks for your consideration, the major helpers seem exceptionally busy this week!

---

### Post by Giggity on 2006-09-18
I took a wild guess as to which modules should be uninstalled/reinstalled to get to the previous kernel.  Now I'm at 2.6.15-25.43, 386 version.  I had to reinstall nVidia drivers and MadWifi as well since they didn't work after the switch.  Now they work, but:

When trying to start VMWare, the same problem is happening as with the new kernel!  Now I'm really confused! ](*,)

```
rob@rob-desktop:~$ uname -r
2.6.15-25-386
```

---

### Post by Giggity on 2006-09-18
I've returned to the new kernel (2.6.15-26.47, and had to again reinstall the nVidia drivers) and I've managed to get VMWare Workstation to at least start up, albeit without bridged networking.

To at least enable VMWare to start (still bridged networking failing), type:
```
sudo rm /etc/vmware/not_configured
```

Now, if I can only find out why the bridged networking is failing to load!  It does so in kernel 2.6.15-25.43 as well, so I don't know if it's the kernel responsible for this fresh hell.

Now, I'm looking at the MadWifi drivers as the culprit, as the failing module (vmnet0) is responsible for Bridged Networking, and is related to ath0, the wireless network interface.

Of course, any input will be appreciated!

---

### Post by Giggity on 2006-09-18
**TEMPORARY WORKAROUND!**

Okay, so far we've narrowed down the problem to the module vmnet0, responsible for bridged networking.  We've removed the "not_configured" flag responsible for not allowing VMWare to start at all.

What I've done to allow my WinXP to access the internet and my Samba Network drives is change the settings for my WinXP virtual machine.  You must make sure that you have set up NAT networking when installing/configuring VMWare.  It does so by default, so if you didn't fiddle when installing/configuring it, it should be set up properly.

Before booting up the virtual machine:

1. Double click in the settings panel on "Ethernet 1" (or whatever Network interface applies in your situation). (temporary-workaround-001.jpg)
2. In the window that pops up, see the "Bridged: Connected directly to the physical network" bullet selected under Network Connection?  Good. (temporary-workaround-002.jpg)
3. Right underneath is a bullet marked "NAT: Used to share the host's IP address".  Click that, and NAT networking will be used from now on to operate network functions in the virtual machine.
4. Click OK, and then Power On your virtual machine.

Now, Mozilla Firefox can access websites and my Samba Network drives are operating properly.  If anything else fails to work, I'll let you know, but I hope that this helps anyone having trouble.

**But still, it would be nice to find why bridged networking is not functioning!  On we go...**
Oh, and if a moderator happens to see this, I think that the title should be reworded to more specifically describe the problem.  I was a little more "in the dark" when I created this thread, but now that I've narrowed down the cause...

---

### Post by entangled on 2006-09-18
Mine seems to be working well now. I was getting the error message that vmware was not configured even though I have just finished a successful configuration.
After looking in the 'vmware' bash start-up script I found a file,
```
/etc/vmware/not-configured
```
and renamed it to not-configured.old.
After that I could start up and I have installed XP. Seems to run very well.
Bridged networking does work.

---

### Post by Giggity on 2006-09-18
Nice to hear that you're not having the same kind of trouble I'm having right now.  Is the bridged network connection you're using a wireless network connection using MadWiFi, or are you just bridging a standard eth0 connection?

---

### Post by techstop on 2006-09-19
I believe all the answers that you're looking for in this thread can be found in the Windows on VMWare HOWTO found here;

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

My VMWare stopped working today after a kernel update. I went to the thread above which suggests that after a kernel update you must install new kernel headers (either manually each time, or by downloading a new package that will do it automatically for you) and then running the VMWare config again which will need to be able to find the new headers. See the thread above, in the section called "Common Problems and Solutions"

Mine works perfectly after installing new kernel headers and running vmware-config.pl again.

HTH. Cheers.

---

### Post by Giggity on 2006-09-19
> **techstop said:**
> I believe all the answers that you're looking for in this thread can be found in the Windows on VMWare HOWTO found here;

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

My VMWare stopped working today after a kernel update. I went to the thread above which suggests that after a kernel update you must install new kernel headers (either manually each time, or by downloading a new package that will do it automatically for you) and then running the VMWare config again which will need to be able to find the new headers. See the thread above, in the section called "Common Problems and Solutions"

Mine works perfectly after installing new kernel headers and running vmware-config.pl again.

HTH. Cheers.

Thanks for giving it a shot, but I already knew very well about installing kernel headers.  Anyone installing VMWare for the first time has to go through this learning step, since I don't think headers come with the LiveCD/DVD installation package.  I make sure to install them at the same time I install the new kernel image.  Then I recompile nVidia and MadWiFi after rebooting, and then rerun sudo /usr/bin/./vmware-config.pl -- Sometimes I just go ahead and uninstall/reinstall VMWare straight up, since it doesn't take much longer.

Anyway, I've just upgraded to the newest kernel ( 2.6.15-27.48 ), thinking that there might have been a fix involved.  Bridged Networking module vmnet0 still fails to load.

NAT networking still works, though, so I'll just continue using the workaround I posted above.  I hope VMWare releases a fix for this soon, because it would be nice to have things working the same way they did before... and they're usually so good about releasing fixes in quick time.  This time they seem to be lagging.

I also wholeheartedly accept that I might be doing something wrong, and that no software fix is required.  Any suggestions?

---

### Post by Giggity on 2006-09-19
There's a new version of madwifi-ng-current.tar.gz (dated 19 September) listed at [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/) -- I'll install that tomorrow morning, and let y'all know how it works out.  Stay tuned.

---

### Post by techstop on 2006-09-19
So you have run vmware-config.pl again, and it asked you for the location of your kernel headers etc? I am certain this is the fix as it configures vmnet and vm something or other, the modules you guys are having issues with. You've said a couple of times that when you run vmware in a terminal it prompts you to run config again, but have you actually done it? 

I actually renamed my not-configure file and tried to run vmware. I got the errors, read about the fix in that other thread, renamed my not-configure file back to how it was, installed the kernel headers and ran the config.pl script again as prompted. Presto! It worked!

---

### Post by Giggity on 2006-09-19
> **techstop said:**
> So you have run vmware-config.pl again, and it asked you for the location of your kernel headers etc? I am certain this is the fix as it configures vmnet and vm something or other, the modules you guys are having issues with. You've said a couple of times that when you run vmware in a terminal it prompts you to run config again, but have you actually done it? 

I actually renamed my not-configure file and tried to run vmware. I got the errors, read about the fix in that other thread, renamed my not-configure file back to how it was, installed the kernel headers and ran the config.pl script again as prompted. Presto! It worked!
Yes.  It asks me for the location of my kernel headers, and by default selects the proper location of the new headers:
```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-386/build/include]
```
And yes.  I've run config again.  At least 50 times since last Wednesday.  I've even uninstalled/reinstalled the whole application.  No dice!

Thanks for giving it a shot, but I don't think the kernel header solution has anything to do with this.  I'm gonna just go ahead and try the new MadWiFi drivers tomorrow after this one thing I'm downloading finishes.  I'll let you know how that works.

Thanks for your input, though!  It's nice to see that someone cares!

---

### Post by ampop on 2006-09-19
Get version of your kernel: ```
uname -r
```
You will use the output from this step in the next step.
Install the linux headers for your kernel: ```
apt-get install linux-headers-{output of prev step here}
```.
This will install the linux headers VMWare needs to compile their tools.

Now:
```
sudo /usr/bin/vmware-config.pl
```
Folow the instructions.

Every time that the kernel is upgraded, you must do this.

---

### Post by techstop on 2006-09-19
OK, no worries, good luck!

I notice in your log that vmnet0 is already defined, but it is the only service that fails to start. Maybe scratch that network and start again?

> The following bridged networks have been defined:

. vmnet0 is bridged to ath0

Do you wish to configure another bridged network? (yes/no) [no]

> Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   **Bridged networking on /dev/vmnet0                                  failed**
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

Other than that I'm stumped... #-o

---

### Post by Giggity on 2006-09-19
> **ampop said:**
> Get version of your kernel: ```
uname -r
```
You will use the output from this step in the next step.
Install the linux headers for your kernel: ```
apt-get install linux-headers-{output of prev step here}
```.
This will install the linux headers VMWare needs to compile their tools.

Now:
```
sudo /usr/bin/vmware-config.pl
```
Folow the instructions.

Every time that the kernel is upgraded, you must do this.
**[SIZE="4"]I swear to god, the next time someone tells me to update my kernel header files, I'm going to flip out.  I know you're just trying to help, but I've already done that, and have said so *numerous* times.[/SIZE]** ](*,)

In other news, installing the new MadWiFi driver was to no avail.  Same failure to load the bridged networking module.

---

### Post by Giggity on 2006-09-19
> **techstop said:**
> OK, no worries, good luck!

I notice in your log that vmnet0 is already defined, but it is the only service that fails to start. Maybe scratch that network and start again?





Other than that I'm stumped... #-o
Oh, hey techstop... didn't notice you there at the top of a new page!  Yeah, I've tried to uninstall/reinstall the whole application suite from scratch, even after applying the new MadWiFi drivers... it just didn't do anything.

Thanks for your original input.

---

### Post by dentaku65 on 2006-09-19
> **Giggity said:**
> **[SIZE="4"]I swear to god, the next time someone tells me to update my kernel header files, I'm going to flip out.  I know you're just trying to help, but I've already done that, and have said so *numerous* times.[/SIZE]** ](*,)

In other news, installing the new MadWiFi driver was to no avail.  Same failure to load the bridged networking module.

mmm... but the headers are updated only if you have the previous one installed (dist-upgrade); if you don't have it in the previous kernel release and you did it the dist-upgrade it is normal this beaviour... in any case headers MUST always be installed ;)

---

### Post by Giggity on 2006-09-19
> **dentaku65 said:**
> mmm... but the headers are updated only if you have the previous one installed (dist-upgrade); if you don't have it in the previous kernel release and you did it the dist-upgrade it is normal this beaviour... in any case headers MUST always be installed ;)

I manually update the kernel header files myself.  I don't rely on something else to do it as a ride-along for another update.

I promise you, the kernel headers for kernel version 2.6.15-27.48 are installed.  Enclosed is a little cap of Synaptic to verify said fact for those of you who apparently think I'm lying.  Note the cute little green boxes.

---

### Post by dentaku65 on 2006-09-19
> **Giggity said:**
> I manually update the kernel header files myself.  I don't rely on something else to do it as a ride-along for another update.

I promise you, the kernel headers for kernel version 2.6.15-27.48 are installed.  Enclosed is a little cap of Synaptic to verify said fact for those of you who apparently think I'm lying.  Note the cute little green boxes.

I did not say that you don't have the 2.6.15-27 headers, I've say that *maybe* you didn't have the previous ones (2.6.15-26) and so the dist-upgrade did not "upgrade" packet thet you don't have... I dunno if this is the case...

---

### Post by Giggity on 2006-09-19
> **dentaku65 said:**
> I did not say that you don't have the 2.6.15-27 headers, I've say that *maybe* you didn't have the previous ones (2.6.15-26) and so the dist-upgrade did not "upgrade" packet thet you don't have... I dunno if this is the case...
Okay, but I did... I always install new kernel headers when I install a new kernel image.  Always Always Always.

Thanks for your input.

---

### Post by techstop on 2006-09-19
Maybe you haven't done this, but have you tried updating the kerne......



Oh, wait, I think you have. :p 

I found this thread which has a few different fixes;

[http://www.vmware.com/community/thread.jspa?threadID=47576&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=47576&tstart=0)

Something about updating gcc as well....

---

### Post by Giggity on 2006-09-19
> **techstop said:**
> Maybe you haven't done this, but have you tried updating the kerne......



Oh, wait, I think you have. :p 

I found this thread which has a few different fixes;

[http://www.vmware.com/community/thread.jspa?threadID=47576&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=47576&tstart=0)

Something about updating gcc as well....

Nice link.  I tried again with the vmware-any-any-update104, but it didn't solve the problem.

As for GCC, I'm currently using version 4.0.3, the latest version shown by Synaptic -- I see there's a version 4.1.1 available directly from the [official GCC site]("http://gcc.gnu.org/").

I'm a little wary as to installing it, because it's not listed in any of the Ubuntu package servers (or universe or multiverse).  It's also [not listed as a successful build]("http://gcc.gnu.org/gcc-4.1/buildstat.html") for the 2.6.15 kernel, so I wonder if using it would damage my computer.  I'll do a little more research before trying that.

---

### Post by toykilla on 2006-09-20
I ran:
sudo rm /etc/vmware/not_configured

which lets me launch VMWARE, but trying to power on a virtual machine yields this error now:

Unable to change virtual machine power state: The process exited with an error:
End of error message.

---

### Post by Giggity on 2006-09-20
> **toykilla said:**
> I ran:
sudo rm /etc/vmware/not_configured

which lets me launch VMWARE, but trying to power on a virtual machine yields this error now:

Unable to change virtual machine power state: The process exited with an error:
End of error message.Try running VMWare by just typing "vmware" in a terminal window.  That way, the errors encountered will be recorded when you try to Power On.  Copy and paste everything in the terminal window into a text file of some sort and then attach it to your next message, so that someone here could tell what the error is, and thus help you!

I'm afraid I probably won't be of much help as far as that goes, as I'm a real newbie with Linux.  It's amazing how complex software is, and it's really admirable for the developers to have gotten things working as well as they have!

---

### Post by entangled on 2006-09-26
Apologies Giggity, I have NOT got bridged networking working, I am using NAT. I misread the output when posting before.
 
However, I have had repeated problems with the not_configured file coming back.

The simplest solution to that, I think, is to chown the script file /usr/bin/vmware to your username and group.

```
sudo chown <username>:<username> /usr/bin/vmware
```

After that the file does not get written by root and it doesn't persist. Also I can now start up vmware as a normal user from the menu.

---

### Post by flipfone on 2006-09-26
I just had this problem too after a kernel update. Unfortunately it didnt get ner kernel headers for my system, so i went into synaptic and get the current headers for my system. Then i executed the vm script " sudo /usr/bin/vmware-config.pl" after this completed i started vmware. im kinda a newb so i dunno if thisll help you but it helped me. :)  good luck.

---

### Post by Giggity on 2006-09-27
> **entangled said:**
> However, I have had repeated problems with the not_configured file coming back.

The simplest solution to that, I think, is to chown the script file /usr/bin/vmware to your username and group.Good call, but I don't really ever have any *problems*, per se, with the not_configured file reappearing.  It only does so after running the configuration script (during which I get the bridged networking failure).  And since I'm not really trying to fix this anymore, I don't have to run the config script anymore... so the "not_configured" file doesn't reappear.

I'll definitely look into that, though, if I start pursuing this again.

> **flipfone said:**
> I just had this problem too after a kernel update. Unfortunately it didnt get ner kernel headers for my system, so i went into synaptic and get the current headers for my system. Then i executed the vm script " sudo /usr/bin/vmware-config.pl" after this completed i started vmware. im kinda a newb so i dunno if thisll help you but it helped me. :)  good luck.*Sigh*  Yeah, I guess you didn't really read the thread, as I've specifically stated numerous times that I have the current kernel headers installed.

Thanks for trying to help, though.  I've pretty much given up on getting this to work properly in Ubuntu, as commercial software is contrary to Ubuntu's modus operandi.  I can't fault the Ubuntu folk for my not being in their target demographic... to do so would be like criticizing the Lakers for not winning the Super Bowl.  It's just not their job!

Ubuntu works great if you stick to using the numerous supported packages, and its automated distribution system has been invaluable to me in exposing me to the world of Linux without having to really study anything.  But I'm willing to learn more in order to do more, and a less automated distro might be something that helps me do so out of necessity.  I'm currently looking at Gentoo and Linux From Scratch, as the procedures to get those up and running are good for learning a great deal about what goes into a Linux system.  I'll probably do Gentoo first, then move on to LFS.

---

### Post by bluevoodoo1 on 2006-12-11
I'm getting "Unable to change virtual machine power state: The process exited with an error: End of error message...." as well. I never got that on my previous Edgy install... Running that vmware-config.pl script and deleting the not_configured file works for now... (changing ownership does not help here). There must be a better way?

EDIT: I found this link... [http://www.linuxquestions.org/questions/showthread.php?t=488437](http://www.linuxquestions.org/questions/showthread.php?t=488437)

I haven't tried it yet..

---

