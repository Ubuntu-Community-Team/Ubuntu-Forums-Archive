---
title: "New AMD driver 13.11 v9.4 released 11-22-13"
date: 2013-11-22
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-11-22
Hey guys, AMD just released catalyst version 13.11 version 9.4. I think the last 13.11 BETA catalyst was referred as beta6. [http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx]("http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx")
```
Resolved Issues:
[372656] : Resolves crash when resizing Konsole
[388325] : Resolves brightness adjustment issues
[388818] : Resolves kernel module compile failure when CONFIG_UIDGID_STRICT_TYPE_CHECKS is enabled
[388335] : Avoids the new GPL symbol acpi_bus_get_device for new kernel support
[386897] : Resolves system hang on resume from S4 with OpenGL screen saver running
```

I have an HD5750 and am going to make the jump tonight. I will post back what I find out. Im guessing it added better support for the 290x and other newer cards but you never know if you can squeeze an additional FPS out of your card it's worth a shot. :)

NOTE: if you're going from a previous AMD driver downloaded from the website, to properly remove the old driver from your system before installing the new version. I always just go to tty1, log in, issue ```
sudo service lightdm stop
``` or use whatever display manager you use ie: gdm - Gnome Display Manager, ldm - LSTP Display Manager, xdm - X Display Manager, sdm - Secure Display Manager, wdm - WINGs Display Manager, kdm - KDE Display Manager, slim - Simple login manager. run the installer script with the --uninstall switch, so it would be ```
sudo ./amd-catalyst-13.11-beta6-linux-x86.x86_64.run --uninstall
``` 
 and then make the .run file executable using ```
chmod a+x blahblahblah.run
```. And then run the script with sudo like this ```
sudo ./amd-catalyst-13.11-beta V9.4-linux-x86.x86_64.run
```

**[SIZE=4]NOTE: read my latest post for an update. Basically if theres no mention of your specific card and improvements listed in the change log I would stick with the driver you're currently using if it works.[/SIZE]**

---

### Post by oldrocker99 on 2013-11-22
Good luck. It would be nice to see ATI start achieving parity with nVidia in their Linux drivers.

---

### Post by dannyboy79 on 2013-11-23
BAD NEWS. lol  

I did my normal routine of going to tty1 and logging in. I then chmod'd the new .run installer and noticed a space in the final filename being amd-catalyst-13.11-beta V9.4-linux-x86.x86_64.run did AMD really just do that? how stupid, so I renamed it to be amd-catalyst-13.11-beta_v9.4.run. I then ran the --uninstall on the current BETA driver which was amd-catalyst-13.11-beta6-linux-x86.x86_64.run. That seemed to uninstall just fine. I proceeded to perform the installation of the new BETA driver which is amd-catalyst-13.11-beta_v9.4.run and after clicking ok a few times I was presented with this screen
[IMG]https://lh4.googleusercontent.com/-WIIZCuVgEp4/UpA8E8sMxiI/AAAAAAAACOg/UBk3huKEVbg/s640/image_2013-11-22_23%253A24.jpg[/IMG]
and was curious why that appeared since I already installed the older version. So apparently the uninstaller must have missed some files so now I am stuck within tty1 and can't launch lightdm. I try to remove my xorg.conf file and start lightdm hoping it would boot using the default VESA driver but still would not boot. I viewed the /var/log/Xorg.0.log file and towards the end of the log it showed 
```
[  2165.281] (II) RADEON(0): RADEONScreenInit c0000000 0 0
[  2165.282] (EE) RADEON(0): Unable to map FB aperture. Resource temporarily unavailable (11)
[  2165.282] 
Fatal server error:
[  2165.282] AddScreen/ScreenInit failed for driver 0
[  2165.282] 
[  2165.282] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  2165.282] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2165.282] 
[  2165.417]  ddxSigGiveUp: Closing log
[  2165.417] Server terminated with error (1). Closing log file.

```
and I really didn't know what to do at this point. hmmmm, why oh why did I mess with my GPU driver (13.11-beta6) if it was working just fine? lol  I performed the following removal as well from my googling and not sure if this had any effect to get me back into my window manager at a minimum ```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
``` So then I rebooted the machine using ```
sudo shutdown -r now
``` and to my surprise I was presented with lightdm log in manager. So now here I am logged into my desktop manager and all is well except I am now using the default VESA driver, no fglrx. I am going to do some more googling to see if I can find a solution to the AMD web based installer thinking there's a previous installation already. I will note that I did see the --force option but since it states it's best NOT to perform that I wasn't going to push my luck. I will post updates as to what I finally do to get myself back onto 1 of the AMD website drivers instead of the stock VESA module. I will point out as well that many sites I am reading suggest making a proper .deb file from the .run installer using the following command ```
sh amd-driver-installer-catalyst-13-4-x86.x86_64.run --buildpkg Ubuntu/precise
``` or whatever version of Ubuntu you're using. I may just try that next. 

Stay tuned........

OK, im back and did end up creating 3 .deb's from the run installer file from the AMD website. The command I ran was 
```
sudo sh amd-catalyst-13.11-beta\ V9.4-linux-x86.x86_64.run --buildpkg Ubuntu/precise
```
after that successfully created the 3 deb's (NOTE: the first time I tried to create the deb's it failed and they weren't created. I believe it hadn't ran the command with sudo) I then issued ```
sudo dpkg -i fglrx*.deb
``` and received a bunch of errors (you can see what transpired in the code box below) but the one that stuck out was about a missing package which was lib32gcc1 so I merely ran ```
sudo apt-get install lib32gcc1
``` and when I ran that command it just automagically performed/finished the 3 AMD .deb's installation and it showed the following on screen
```
**sudo dpkg -i fglrx*.deb**
Selecting previously unselected package fglrx.
(Reading database ... 461909 files and directories currently installed.)
Unpacking fglrx (from fglrx_13.250-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_13.250-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_13.250-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on lib32gcc1; however:
  **Package lib32gcc1 is not installed**.
dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
ubu@core2duo:~/Desktop$ **sudo apt-get install lib32gcc1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lib32gcc1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 54.1 kB of archives.
After this operation, 145 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32gcc1 amd64 1:4.6.3-1ubuntu5 [54.1 kB]
Fetched 54.1 kB in 0s (120 kB/s)   
Selecting previously unselected package lib32gcc1.
(Reading database ... 462214 files and directories currently installed.)
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx (2:13.250-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-13.250 DKMS files...
First Installation: checking all kernels...
Building only for 3.7.0-030700-generic
Building for architecture x86_64
Building initial module for 3.7.0-030700-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.7.0-030700-generic/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:13.250-0ubuntu1) ...
Setting up fglrx-dev (2:13.250-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-030700-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169

```

So, after all that I am now running the latest AMD BETA 13.11 V9.4 driver and this is what ```
dmesg | grep fglrx
``` shows: module loaded - fglrx 13.25.5 [Nov 22 2013] with 1 minors

I am running benchmarks now to see if there was any improvement over the 13.11beta6 driver. They'll be posted in the glmark2 thread as well as the new GPUTest thread I created within the gaming section.

---

### Post by DanglingPointer on 2013-11-23
> **dannyboy79 said:**
> Hey guys, AMD just released catalyst version 13.11 version 9.4. I think the last 13.11 BETA catalyst was referred as beta6. I have an HD5750 and am going to make the jump tonight. I will post back what I find out. Im guessing it added better support for the 290x and other newer cards but you never know if you can squeeze an additional FPS out of your card it's worth a shot. :)

NOTE: if you're going from a previous AMD driver downloaded from the website, to properly remove the old driver from your system before installing the new version. I always just go to tty1, log in, issue ```
sudo service lightdm stop
``` or use whatever display manager you use ie: gdm - Gnome Display Manager, ldm - LSTP Display Manager, xdm - X Display Manager, sdm - Secure Display Manager, wdm - WINGs Display Manager, kdm - KDE Display Manager, slim - Simple login manager. run the installer script with the --uninstall switch, so it would be ```
sudo ./amd-catalyst-13.11-beta6-linux-x86.x86_64.run --uninstall
``` 
 and then make the .run file executable using ```
chmod a+x blahblahblah.run
```. And then run the script with sudo like this ```
sudo ./amd-catalyst-13.11-beta V9.4-linux-x86.x86_64.run
```

Woops I duplicated your post!  haha

I'm too slow!

---

### Post by dannyboy79 on 2013-11-23
HUGE UPDATE: Installing the AMD driver straight from the website only using the .run file for both installation and removal using --uninstall switch has caused some serious opengl lib's to get all mixed up (if you read to the end you'll see that there is something still unexplained). This is crucial for steam to work properly. Whenever I launched steam after I did all these driver changes back and forth finally an error popped up like this:
[IMG]https://lh4.googleusercontent.com/--EWq14uDH40/UpCshANfw1I/AAAAAAAACPE/FmUmwa9YHl4/s643/opengl_glx_steam_error.png[/IMG]
and some opengl steam games weren't working at all. I tried googling and after 4 hours of failed attempts to ensure steam was launching with the applicable OpenGL 32bit libraries I gave up and restored my / root partition with an image I had taken recently using clonezilla. (can't speak highly enough of making images of your / root partition cause you never know when you'll need it to get you out of a bind) I am now running the latest stable AMD driver from their website (currently Catalyst 13.4). 

I performed the installation by running the amd-driver-installer-catalyst-13-4-x86.x86_64.run file using sudo. Now I know I said earlier that there is an issue with using the .run directly, I believe the issue arises when you use the .run to perform an uninstallation of the driver because I don't think it removes itself properly. I think it leaves various symlinks which is what causes Steam to not be able to use 32bit opengl drivers that have direct rendering **NOTE:** I did attempt to create the deb packages from the .run file and then I installed those .debs but believe it or not that resulted in the same error as above. So for some reason turning the .run file into 3 different deb packages results in extra or erroneous symlinked library files that get put within /usr/lib/ and /usr/lib32/ and no matter what I tried I could not get direct rendering to work. You could launch steam using LD_PRELOAD of course and direct rendering would work for Steam but no other applications due to the symlink sanfu from hell!

So I would say the moral of the story is that if your current setup works and you read the change notes of the new driver that just released and it doesn't specifically list your card and possibly any improvement than just leave well enough alone. LOL

---

### Post by jw4165 on 2013-11-24
In almost all cases of running the Catalyst install from the .run file I have always encountered serious errors afterwards.

---

### Post by dannyboy79 on 2013-11-24
> **jw4165 said:**
> In almost all cases of running the Catalyst install from the .run file I have always encountered serious errors afterwards.not me, my system is running awesome right now.

As I said, I believe the problem is if I wanted to switch drivers now, I will most likely run into an issue but i'll cross that bridge when I get to it. It all has to do with the opengl 32bit and 64bit drivers. this is what's on my system right now
```
libgl1-mesa-dev					install
libgl1-mesa-dri					install
libgl1-mesa-dri:i386				install
libgl1-mesa-glx					install
libgl1-mesa-glx:i386				install
```
and all the sym linking that occurs.
```
ls -la /usr/lib/ | grep libGL
-rw-r--r--   1 root root            0 Nov 23 10:32 FGL.renamed.libGL.so.1.2
lrwxrwxrwx   1 root root           19 Nov 23 10:32 libGL.so -> /usr/lib/libGL.so.1
lrwxrwxrwx   1 root root           21 Nov 23 10:32 libGL.so.1 -> /usr/lib/libGL.so.1.2
lrwxrwxrwx   1 root root           33 Nov 23 10:32 libGL.so.1.2 -> /usr/lib/fglrx/fglrx-libGL.so.1.2

```
```

ls -la /usr/lib32/ | grep libGL
lrwxrwxrwx  1 root root     21 Nov 23 10:32 libGL.so -> /usr/lib32/libGL.so.1
lrwxrwxrwx  1 root root     23 Nov 23 10:32 libGL.so.1 -> /usr/lib32/libGL.so.1.2
lrwxrwxrwx  1 root root     48 Nov 23 10:32 libGL.so.1.2 -> /usr/lib/i386-linux-gnu/fglrx/fglrx-libGL.so.1.2

```

---

### Post by jw4165 on 2013-11-24
What an excellent reply!

Admittedly it is a little out of my depth at the current time! Still, I'll rise to the challenge of getting it done sometime hehe.

GL & HF!

---

