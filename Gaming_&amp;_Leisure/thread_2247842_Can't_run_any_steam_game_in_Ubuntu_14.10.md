---
title: "Can't run any steam game in Ubuntu 14.10"
date: 2014-10-10
forum: Gaming &amp; Leisure
---

### Post by lip25022 on 2014-10-10
Hi guys,

I am currently testing Ubuntu 14.10, the next linux  distribution that will be released in a few weeks. But I can't run any  game on it.

On startup I get this error : 

OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).

The thing is that I have checked and glxinfo says I am indeed using direct rendering !?! :mad:

[IMG]http://image.noelshack.com/fichiers/2014/41/1412848037-direct-rendering.png[/IMG]


Any idea on how to make it work again ?

FYI :
I have an old graphics card ATI Mobility Radeon HD 3450 which is not supported by AMD anymore since 12.10 so I can't install fglrx drivers.

---

### Post by oldrocker99 on 2014-10-10
This thread here may help you out:[http://ubuntuforums.org/showthread.php?t=2221109](http://ubuntuforums.org/showthread.php?t=2221109).

From what I have heard, you're better off with the open source drivers anyway, than might have been, if you could install fglrx.

This is the main reason why most Linux gamers, and in fact nongamers as well, recommend nVidia. While ATI may be the slightly superior hardware for Windows, the fglrx Linux drivers have caused problem after problem for their owners. Then, the company adds insult to injury by declaring whole chipsets "legacy," meaning, "We don't support these any more." I will also add that I've seen Steam threads that specifically recommend the open source drivers for ATI.

In a nutshell: ATI cards have problematic support in their proprietary Linux drivers, and for many users, the open source drivers are superior, and for a lot of ATI owners, the only option. nVidia cards have very good support in their proprietary Linux drivers, and the open source drivers are 50% slower, etc.

---

### Post by dannyboy79 on 2014-10-10
one of the opengl files isn't properly symlinked I am betting. i've had this issue in the past but don't exactly recall how i fixed it. rad number 2 of the link you actually posted and go through each of those commands. let me see if i can find the thread that i created which had a similar issue when I was constantly swapping AMD drivers from fglrx to open source. (PS i know you didn't install fglrx but I am guessing you're missing a proper symlink for 32bit opengl because steam runs in 32bit compatibility mode)

---

### Post by lip25022 on 2014-10-11
Hi folks,

Thanks for the answer.

I have gone ahead and copied and pasted every single command mentionned in the steam help.

I get this for 'ldd glxinfo' but unfortunately I am not able to interpret it... :(

```
lip@lip-laptop:/usr/bin$ ldd glxinfo 
    linux-gate.so.1 =>  (0xf774c000)
    libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf768e000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7543000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7394000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf736c000)
    libglapi.so.0 => /usr/lib/i386-linux-gnu/libglapi.so.0 (0xf7353000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf7340000)
    libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf733c000)
    libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf7334000)
    libX11-xcb.so.1 => /usr/lib/i386-linux-gnu/libX11-xcb.so.1 (0xf7331000)
    libxcb-glx.so.0 => /usr/lib/i386-linux-gnu/libxcb-glx.so.0 (0xf7319000)
    libxcb-dri2.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri2.so.0 (0xf7313000)
    libxcb-dri3.so.0 => /usr/lib/i386-linux-gnu/libxcb-dri3.so.0 (0xf730f000)
    libxcb-present.so.0 => /usr/lib/i386-linux-gnu/libxcb-present.so.0 (0xf730a000)
    libxcb-sync.so.1 => /usr/lib/i386-linux-gnu/libxcb-sync.so.1 (0xf7303000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf72e1000)
    libxshmfence.so.1 => /usr/lib/i386-linux-gnu/libxshmfence.so.1 (0xf72de000)
    libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xf72d8000)
    libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0xf72c8000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7282000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7265000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7260000)
    /lib/ld-linux.so.2 (0xf774f000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf725c000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7254000)


```

Does it help find the issue ?

---

### Post by dannyboy79 on 2014-10-11
i never checked, so are you running the default radeon driver which is included by default with 14.10? if so, i wonder if the oibaf ppa has an updated radeonsi driver for 14.10?

did you first ensure you're using the 32 bit version of glxinfo?
```
which glxinfo
```

---

### Post by lip25022 on 2014-10-11
Hey danny,

Here is the result of 'which glxinfo'

```
lip@lip-laptop:~$ which glxinfo 
/usr/bin/glxinfo

```

I have activated oibaf ppa, I'll update my packages and come back to you right away.

---

### Post by lip25022 on 2014-10-11
nope still not good

---

### Post by dannyboy79 on 2014-10-12
hmmm, i looked at a few of your files and they do appear to be in the i386 folders like the following example from above: libGL.so.1 => /usr/lib/i386-linux-gnu/mesa/libGL.so.1 (0xf768e000). 

When I view mine i get: libGL.so.1 => /usr/lib/libGL.so.1 (0x00007fd4c1eb6000)

i never asked you, are you running a 32bit or 64bit Ubuntu installation? can you please also post the output from this command
```
sudo lshw -C display
```

---

### Post by lip25022 on 2014-10-12
Ok so is that why steam does not recognise OpenGL ? Do I need to make a link in /usr/bin/lib ?

Cause I have been testing games outside of Steam and they are running just fine. Minecraft is running smoothly for instance.

I have a 64 bits install, which is by the way the recommended download by now.

Here is the result of your command on my system :

```
*-display               
       description: VGA compatible controller
       product: RV620/M82 [Mobility Radeon HD 3450/3470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:c0000000-cfffffff ioport:6000(size=256) memory:d6300000-d630ffff memory:d6320000-d633ffff


```

Thanks again for your help !

---

### Post by dannyboy79 on 2014-10-12
it doesn't appear like you're running the radeonsi driver from oibaf's ppa because of this line "configuration: driver=radeon" . are you sure you did both
```
sudo apt-get update
```
AND
```
sudo apt-get dist-upgrade
```

---

### Post by lip25022 on 2014-10-12
Yep I'm pretty sure I did both. You know what I am gonna purge my ppa and do it all over again to make sure everything has been done correctly

---

### Post by lip25022 on 2014-10-12
So I have done basically every step all over again.

1/ Added oibaf PPA
2/  sudo apt-get update && sudo apt-get dist-upgrade

But I still get radeon for 
sudo lshw -C display

---

### Post by dannyboy79 on 2014-10-12
hmmm, can you report back what this command shows please
```
sudo aptitude show xserver-xorg-video-ati
```
if you don't have aptitude install than just install it with
```
sudo apt-get install aptitude
```

OR

we can check via the glxinfo information 
```
glxinfo | grep OpenGL
```
it should print the driver type and version with the PPA custom string. Maybe I am wrong in thinking the radeonsi driver is what you need because your GPU is old as you stated, i'm still digging into the radeon vs radeonsi issue i'll post back when I find something out.

UPDATE: The RadeonSI Gallium3D driver supports the AMD Radeon HD 7000 series / GCN graphics processors and newer. RadeonSI is officially developed by open-source AMD developers with community support and can be found in a working state within recent versions of Mesa.

---

### Post by lip25022 on 2014-10-12
Hey danny,

Here is the result of the first command

```

Package: xserver-xorg-video-ati          
State: installed
Automatically installed: no
Version: 1:7.5.99+git1410021930.c854b4~gd~u
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 95,2 k
Depends: libc6 (>= 2.4), libpciaccess0, xorg-video-abi-18, xserver-xorg-core (>=
         2:1.15.99.903), xserver-xorg-video-r128, xserver-xorg-video-mach64,
         xserver-xorg-video-radeon
Conflicts: xserver-xorg-video-ati
Provides: xorg-driver-video
Description: X.Org X server -- AMD/ATI display driver wrapper
 This package provides the 'ati' driver for the AMD/ATI Mach64, Rage128, Radeon,
 FireGL, FireMV, FirePro and FireStream series. This driver is actually a
 wrapper that loads one of the 'mach64', 'r128' or 'radeon' sub-drivers
 depending on the hardware. These sub-drivers are brought through package
 dependencies. 
 
 Users of Rage, Mach, or Radeon boards may remove this package only if they use
 Driver "r128", "mach64", or "radeon" in /etc/X11/xorg.conf instead of relying
 on autodetection. 
 
 More information about X.Org can be found at: <URL:http://www.X.org> 
 
 This package is built from the X.org xf86-video-ati driver module.

```

And here is the grepped glxinfo result

```

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV620
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.4.0-devel (git-5bffc5e 2014-10-12 utopic-oibaf-ppa)
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.4.0-devel (git-5bffc5e 2014-10-12 utopic-oibaf-ppa)
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.4.0-devel (git-5bffc5e 2014-10-12 utopic-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0
OpenGL ES profile extensions:

```

But I am a little bit confused with the result. Wasn't I supposed to be running mir on 14.10 ? Why is the driver managed by Xorg ?

---

### Post by dannyboy79 on 2014-10-12
alright, you look to be running the oibaf ppa. the drivers are good, now we just need to figure out why steam is complaining. 14.10 will NOT include MIR cause it's not ready as far as I know. ([http://www.zdnet.com/ubuntu-14-10-utopic-unicorn-beta-1-preview-no-big-changes-7000033019/](http://www.zdnet.com/ubuntu-14-10-utopic-unicorn-beta-1-preview-no-big-changes-7000033019/))

Are you still getting the same error from steam? have you tried launching steam from the command line? if not, please do and paste back all the output from the terminal onto pastebin and then paste the pastebin link here please.

---

### Post by lip25022 on 2014-10-12
Ah ok, I thought mir was first introduced on top of Xorg and then completely remove untill 15.04 / 16.04.

So I have tried running steam again after a reboot, same error pops up.

Here is the terminal log for steam

[http://pastebin.com/0z3mtzrA](http://pastebin.com/0z3mtzrA)

---

### Post by dannyboy79 on 2014-10-12
ok, i'm not sure if this will help but try to move these 2 files into your trash (i don't want you to delete them in case we want to put them back). Im hoping that the Trash folder is in the same location for you (14.10) as it is for me (14.04)
```
mv ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6 ~/.local/share/Trash/files/libstdc++.so.6
```
```
mv ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libgcc_s.so.1 ~/.local/share/Trash/files/libgcc_s.so.1
```

after you move those 2 files to the trash, launch steam again from the terminal and post teh output back into a new pastebin and we'll go from there. to be honest, i don't know why it's not working and all I'm doing is googling for answers. i wish I knew the answer but I don't know why it's failing. i believe it has something to do with some 32bit libraries missing. have you tried to remove and reinstall steam since you enabled the oibaf ppa, that may help also.

---

### Post by Peter09 on 2014-10-13
I am getting exactly the same problem but I am running an nvidea GPU.

---

### Post by Peter09 on 2014-10-13
This website seems to be looking at the same issue, I could not see if they had actually resolved it.
[http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p7](http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p7)

---

### Post by dannyboy79 on 2014-10-13
> **Peter09 said:**
> I am getting exactly the same problem but I am running an nvidea GPU.
which Nvidia GPU and which driver are you using? That steam forum post you linked should get you working again no problem. You can find out by using this command
```
lshw -C display
```

The OP has an older AMD card though so I am not exactly sure how to solve this. I know it has to do with the 32bit libraries of opengl

---

### Post by lip25022 on 2014-10-13
Hi folks, hey Danny,

I have done what you told me.

1/ Purged and reinstalled Steam from scratch

2/ Run your commands BUT for the second command it says that the file doesn't exist. How is that ?

> libgcc_s.so.1 No such file or directory

Here is the log I got by launching steam via command-line.

[http://pastebin.com/03iDrDWz](http://pastebin.com/03iDrDWz)

---

### Post by dannyboy79 on 2014-10-13
it's possible that file wasn't installed i guess. looking at your output from the terminal for starting steam i no longer see any mention about the missing libgl file and the other libswf or whatever it was it was complaining about in your last paste you submitted from starting steam. moving those files to the trash was a suggestion i found within an Arch Linux post so since it didn't work let's put it back where it was. the command would be
```
mv ~/.local/share/Trash/files/libstdc++.so.6 ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6
```
and you said the second file I was trying to have you move wasn't there so there is no second command.

i'm at a loss here. i've actually asked someone from the steam forums to help us, his name is MasterGeek and the thread is over here: [http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p4](http://steamcommunity.com/app/221410/discussions/5/828939163894026239/#p4)

he's very knowledgeable about this opengl stuff and he's been helping many people but it appears they all have nvidia cards so he may or may not be able to help you. in the mean time it will be helpful to gather a bunch of info about your ldconfig. It's a script that will dump the information we need to do that. And no, it won't look for any personal information or give you a virus. Save the script below into a file called ldconfig-settings-dumper.sh in your home directory. you may need to make the script executable with
```
chmod +x ldconfig-settings-dumper.sh
```
cd into your home directory where you saved the script and run it with this command

```
sudo bash ldconfig-settings-dumper.sh
```

```
#!/bin/bash                                                                                                                                                                                                                      
                                                                                                                                                                                                                                 
OUTPUT_FILE=$PWD/ldconfig-settings-dumper-output.txt                                                                                                                                                                             
                                                                                                                                                                                                                                 
echo "Ubuntu Version:                                                                                                                                                                                                            
" > $OUTPUT_FILE                                                                                                                                                                                                                 
lsb_release -a >> $OUTPUT_FILE 2>&1                                                                                                                                                                                              
                                                                                                                                                                                                                                 
echo "                                                                                                                                                                                                                           
                                                                                                                                                                                                                                 
Available Kernels:                                                                                                                                                                                                               
" >> $OUTPUT_FILE                                                                                                                                                                                                                
ls /boot >> $OUTPUT_FILE                                                                                                                                                                                                         
                                                                                                                                                                                                                                 
#commented out this stuff due to AMD drivers, NOT nvidia
#echo "
#
#dpkg-reconfigure $1
#" >> $OUTPUT_FILE
#dpkg-reconfigure $1 >> $OUTPUT_FILE 2>&1

echo "

apt-get install mesa-utils:i386
" >> $OUTPUT_FILE
apt-get -y install mesa-utils:i386 >> $OUTPUT_FILE 2>&1

echo "

ldd /usr/bin/glxinfo
" >> $OUTPUT_FILE
ldd /usr/bin/glxinfo >> $OUTPUT_FILE

echo "

Now dumping ldconfig settings...
" >> $OUTPUT_FILE
echo "*****/etc/ld.so.conf*****

" >> $OUTPUT_FILE
cat /etc/ld.so.conf >> $OUTPUT_FILE

echo "

*****/etc/ld.so.conf.d directory listing*****

" >> $OUTPUT_FILE
ls -a -l /etc/ld.so.conf.d >> $OUTPUT_FILE

find /etc/ld.so.conf.d -name *.conf -printf "\n\n*****%p*****\n\c" -exec cat '{}' \; >> $OUTPUT_FILE

echo "

*****/usr/lib/$1/alt_ld.so.conf*****

" >> $OUTPUT_FILE
cat /usr/lib/$1/alt_ld.so.conf >> $OUTPUT_FILE



echo '

**************************************************
Now running ldconfig and dumping ldconfig cache...

ldconfig -v 2>&1 | grep GL

' >> $OUTPUT_FILE

ldconfig -v 2>&1 | grep GL >> $OUTPUT_FILE

echo '

ldconfig -p 2>&1 | grep GL

' >> $OUTPUT_FILE

ldconfig -p 2>&1 | grep GL >> $OUTPUT_FILE


echo '

Running ldd /usr/bin/glxinfo again incase that fixed something...

' >> $OUTPUT_FILE

ldd /usr/bin/glxinfo >> $OUTPUT_FILE
```

The script will not output anything to your shell, as all the output is redirected to a file. Once it finishes, post the contents of the file ldconfig-settings-dumper-output.txt which will appear in the same directory you saved the script into.

---

### Post by lip25022 on 2014-10-13
Waow ! Thank you so much for your help danny. You're putting much effort that's so kind of you.

Regarding the script, don't worry I am still able to understand it, although I may not be the most knowledgable person out there !

I have executed it in super user mode, but at some point it stopped displaying this message.

> cat: /usr/lib//alt_ld.so.conf: No such file or directory

EDIT : Actually it may be because of the double '/', let me trying and fix that. Nope never mind there is a variable in between.

Here is the file created, I have pasted it on pastebin, I hope you don't mind.

[URL="http://pastebin.com/hY7XH9Qz"]http://pastebin.com/hY7XH9Qz
[/URL]

---

### Post by dannyboy79 on 2014-10-13
i don't really know how to interpret the output so i'm hoping MasterGeek is going to help with this BUT in the mean time do you have a package with this name or similar name? mesa-libs:i386 

and you've already added your user to the video group right?
```
sudo usermod -a -G video <Your username>
```

hopefully we'll get this figured out sooner or later. LOL

UPDATE: i think i figured it out (maybe) edit the file /etc/ld.so.conf.d/i386-linux-gnu.conf
by adding the following to it
/usr/lib/i386-linux-gnu/mesa/
and then run
```
sudo ldconfig
```

---

### Post by Peter09 on 2014-10-14
for information - here is the output of lshw

lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 620 OEM]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0

---

### Post by dannyboy79 on 2014-10-14
> **Peter09 said:**
> 
       product: GF119 [GeForce GT 620 OEM]
 driver=nouveau latency=0you're currently using the open source nvidia driver which is basically **** compared to the proprietary driver. you have choices though, you can either install whatever latest nvidia driver ubuntu provides in their repository (recommended) OR you can install the latest nvidia driver from nvidia's website.

i would suggest installing the nvidia driver from ubuntu repo's, you should be able to find out how to do that using these forums or google. that should fix it for you, if it doesn't than you should be able to use MasterGeek's suggestions in that steam forum thread that you linked earlier as your scenario is exactly what he solves (nvidia drivers and 32bit opengl libraries)

good luck

---

### Post by lip25022 on 2014-10-14
Hey guys,

Back from work I have executed your commands Danny, added mesa to the conf file, but nothing has changed.

---

### Post by dannyboy79 on 2014-10-14
can you rerun the script and post the results please

---

### Post by lip25022 on 2014-10-15
Sure there you go !

[http://pastebin.com/MWLg3aZw](http://pastebin.com/MWLg3aZw)

---

### Post by dannyboy79 on 2014-10-15
run 
```
locate libGL.so.1
```
and paste back what it returns.
also please paste the output from trying to run steam from the terminal BUT this time run it using
```
env LIBGL_DEBUG=verbose steam
```
PS i'm honestly just guessing how to solve this, i honestly don't understand how steam doesn't work in 14.10 with your AMD gpu.

UPDATE: i found this thread which looks very promising. [https://github.com/ValveSoftware/steam-for-linux/issues/3273](https://github.com/ValveSoftware/steam-for-linux/issues/3273)

---

### Post by lip25022 on 2014-10-15
So here you go

Locate libGL gives :

> /usr/lib/libGL.so.1
/usr/lib/i386-linux-gnu/mesa/libGL.so.1
/usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0


And here is my steam log when launched in verbose mode.

> lip-laptop:~$ env LIBGL_DEBUG=verbose steam
Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
[2014-10-15 21:05:03] Startup - updater built Sep 22 2014 20:17:04
[2014-10-15 21:05:04] Verifying installation...
[2014-10-15 21:05:11] Verification complete
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
Error: OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).
Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/lip/.steam/ubuntu12_32/steam-runtime


Let me go check your link

UPDATE : I ran some additional tests by trying to run some of my games directly from the command line to try and spot the errors.

Apparently some shared libraries are missing or not found (libGLU.so.1)

I found this thread and installed libGLU:i386 but it did not do any good...

---

### Post by dannyboy79 on 2014-10-15
something doesn't seem right, it doesn't appear like the  verbose setting took, try to launch steam with
```
LIBGL_DEBUG=verbose steam
```
also, when you issue
```
ls -la /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
```
and
```
ls -la /usr/lib/i386-linux-gnu/mesa/libGL.so.1
```
what do they return?
you need to install the 64bit version of that library (libGLU) because your system is 64bit. it's only steam that's 32bit. im rather perplexed by this whole ordeal to be honest. would you be inclined to install ubuntu 14.10 from scratch, enable the oibaf ppa, do the updates to get the oibaf files installed, then restart your computer and then install steam? in that specific order please. if not, then we'll just keep picking away little by little at this. i was hoping that MasterGeek guy would've responded in that steam forum post but he hasn't yet that I noticed.

---

### Post by lip25022 on 2014-10-15
Nope I did it again same result when using  : LIBGL_DEBUG=verbose steam

And

> lip@lip-laptop:~$ ls -la /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
-rw-r--r-- 1 root root 695836 oct.  12 07:52 /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0



> lip@lip-laptop:~$ ls -la /usr/lib/i386-linux-gnu/mesa/libGL.so.1
lrwxrwxrwx 1 root root 14 oct.  12 07:52 /usr/lib/i386-linux-gnu/mesa/libGL.so.1 -> libGL.so.1.2.0 

And yeah that's probably what I am gonna end up doing, install Ubuntu from scratch again although I already have installed a lot of stuff here. I just hope I won't get the same issues after that.

Because I have messed with a lot of stuff here to try and resolve the problem so maybe I should try again from a clean setup, even if it's a pain in the butt ! I'll do it tomorrow probably, I'll keep you posted. Thanks a lot.

---

### Post by dannyboy79 on 2014-10-15
yeah, your libGL libraries are just all screwed up and honestly i don' t know how to fix them. sorry, i tried to help but it's just over my head and I don't know how to properly diagnose the issue and would just be guessing. Good luck! Definitely post back if you reinstall and it works or doesn't work and we'll go from there.

---

### Post by oldrocker99 on 2014-10-16
Rather than enduring the grief, it would probably be faster to reinstall. Many Linux users, including myself, have borked their system to that point:oops:...

---

### Post by solitudefields on 2014-10-17
Actually the issue happens on a clean fully updated 14.10 beta install with only Steam installed. I'd say it's a Steam issue if anything.

---

### Post by dannyboy79 on 2014-10-17
> **solitudefields said:**
> Actually the issue happens on a clean fully updated 14.10 beta install with only Steam installed. I'd say it's a Steam issue if anything.could you please let us know which graphics card you have?
```
sudo lshw -C video
```

maybe we can submit a sub report to the steam dev's

---

### Post by solitudefields on 2014-10-17
```
       description: VGA compatible controller       product: Hawaii XT [Radeon R9 290X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:a0000000-afffffff memory:b0000000-b07fffff ioport:e000(size=256) memory:de600000-de63ffff memory:de640000-de65ffff
```

Of course I've since tried the Oibaf PPA + Linux 3.17 (for better 290X support). Still the same regardless. I'm sure Valve will notice users complaining about the issue once 14.10's final. :P

---

### Post by dannyboy79 on 2014-10-17
> **solitudefields said:**
> ```
       description: VGA compatible controller       product: Hawaii XT [Radeon R9 290X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:a0000000-afffffff memory:b0000000-b07fffff ioport:e000(size=256) memory:de600000-de63ffff memory:de640000-de65ffff
```

Of course I've since tried the Oibaf PPA + Linux 3.17 (for better 290X support). Still the same regardless. I'm sure Valve will notice users complaining about the issue once 14.10's final. :Pthe difference between you and the original poster is that your using a brand new r9-290x and he's using a way older amd card. i'm not even sure if the radeon open source driver has support for your card yet.

---

### Post by solitudefields on 2014-10-17
The 290X (Hawaii) is supported if you're using the 3.17 kernel + Mesa 10.4 Git builds. In comparison with the same setup (3.17 kernel + Mesa 10.4 Git from Oibaf's PPA) on Ubuntu 14.04, Steam works perfectly fine.

I'm beginning to wonder if the problem may lie elsewhere like perhaps with Xorg Server 1.16 or maybe something else? Nonetheless there's something in 14.10 in conjunction with Steam that's causing these issues. Hopefully Valve is able to reproduce it and fix it if it's indeed a Steam issue. One final note, like the OP even though Steam says I'm not using direct rendering, glxinfo says otherwise. ;)

---

### Post by lip25022 on 2014-10-18
Hey guys I'm back with a fresh ubuntu 14.10 RC 64 bits install from today. I have fully update my system and activated oibaf PPA. Then, I have installed Steam but the issues is still there :'( !

Here is my new script, I don't know if this can help in diagnosis...

[http://pastebin.com/ikcXqkNq](http://pastebin.com/ikcXqkNq)

---

### Post by dannyboy79 on 2014-10-18
> **lip25022 said:**
> Hey guys I'm back with a fresh ubuntu 14.10 RC 64 bits install from today. I have fully update my system and activated oibaf PPA. Then, I have installed Steam but the issues is still there :'( !

Here is my new script, I don't know if this can help in diagnosis...

[http://pastebin.com/ikcXqkNq](http://pastebin.com/ikcXqkNq)
this is rather alarming and i'm shocked more people aren't complaining about it. i'll check around the github steam page about 14.10. can you launch steam from the terminal using
```
env LIBGL_DEBUG=verbose steam
```
and post back the results

---

### Post by lip25022 on 2014-10-18
Yep sure ! There you go : [http://pastebin.com/fAmuFvsD](http://pastebin.com/fAmuFvsD)

There are a lot of errors in here.

And I am very surprised too, we already have reached the Release Candidate, the final release is scheduled for next week so ... I don't know. Maybe the problem comes from Steam, but if it is, it's high time they did something about it. I'm not saying that everyone will upgrade to 14.10, but a fairly large number of users probably will.

---

### Post by dannyboy79 on 2014-10-18
i would suggest trying to solutions in this link: [https://github.com/ValveSoftware/steam-for-linux/issues/3273](https://github.com/ValveSoftware/steam-for-linux/issues/3273)

---

### Post by solitudefields on 2014-10-19
Running these commands 'fixes' the issue for me with the latest Steam;

```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libgcc_s.so.1
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1
```

However Left 4 Dead 2 isn't launching/working yet. I'll do a fully clean install and try again.

EDIT: Okay, fixed Left 4 Dead 2 by using the following commands;

```
chmod 777 ~/.local/share/Steam/SteamApps/common/Left 4 Dead 2/hl2.sh
chmod 777 ~/.local/share/Steam/SteamApps/common/Left 4 Dead 2/hl2_linux
```

All is well now! :)

---

### Post by lip25022 on 2014-10-19
Awesome ! That fixed the problem. It's working just fine now.

Special thanks to Solitudefields for the solution, and to Dannyboy for his wonderful help !

---

### Post by dannyboy79 on 2014-10-19
Im fricking so HAPPY it's finally solved. However, I believe every time steam updates it's going to put those files right back so make sure you favorite this forum post in your browser so you can easily get back to it. LOL  I;m really curious to know how Ubuntu 14.10 is going to solve this issue because the steam installer will always put those files in people's home drives. I don't know when valve is going to get their ass in gear and just make the steam client 64bit compatible. THat's why this is all a huge issue because steam is still only 32bit and installs those libraries thinking it needs them but looking on my system look how many i found. LOL
[http://gyazo.com/80446cf5f09943fe760216145949ddf1](http://gyazo.com/80446cf5f09943fe760216145949ddf1)

---

### Post by nikosal2 on 2014-11-12
> **solitudefields said:**
> Running these commands 'fixes' the issue for me with the latest Steam;

```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libgcc_s.so.1
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1
```

All is well now! :)

I would like to report that I had the exact same problem after upgrading to 14.10 and was solved with these 5 commands. I have an ATI EAH5450 GPU.

---

### Post by kenneth-thorell on 2015-01-11
Thank you for solving this !!!:guitar:

---

### Post by molgrum on 2015-01-15
Hey instead of removing stuff, this one worked for me:

Installed steam using .deb from their homepage.
Steam installs lots of 32-bit libs.
gedit startsteam.sh or something and put:
```
#!/bin/bash

export LD_PRELOAD="/usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/lib/i386-linux-gnu/libstdc++.so.6"
~/.local/share/Steam/ubuntu12_32/steam-runtime/run.sh steam
```
No complaints anymore and TF2 works like a charm using the free drivers for Radeon.

---

