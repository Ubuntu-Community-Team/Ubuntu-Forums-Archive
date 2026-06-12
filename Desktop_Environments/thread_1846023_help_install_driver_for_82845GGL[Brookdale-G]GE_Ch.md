---
title: "help install driver for 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
date: 2011-09-18
forum: Desktop Environments
---

### Post by mrdragon333 on 2011-09-18
[B][SIZE=3]
  [/SIZE][/B][SIZE=3][COLOR=Red]How to install "Intel Corporation 82845G/GL[Brookdale-G]/GE "[/COLOR][/SIZE][SIZE=3][COLOR=Red]  drivers?[/COLOR][/SIZE]

[SIZE=3]I am new Linux user r[/SIZE][SIZE=3]ight now i am using Ubuntu 11.04[/SIZE],
[SIZE=3]I have searched many forums but did not found any solution[/SIZE]


[B][SIZE=3]Can anybody please help me install the correct graphics driver ?? 
please tell me how to install driver in Ubuntu

can anyone please guide me how to compile drivers from this site???

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

 [/SIZE][/B]git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
git://anongit.freedesktop.org/git/mesa/mesa
git://git.kernel.org/pub/scm/linux/kernel/git/keithp/linux-2.6

 ```

*-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0000000-d7ffffff memory:de000000-de07ffff

```Additional info:
the xconf file is empty , 
the monitor is not detected : unknown monitor


I have tried this solution 


```
gksudo gedit /etc/X11/xorg.conf
```This creates an empty file; paste the following into the file and save:

```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection 

```[SIZE=4][COLOR=Red]
Now my ubuntu os freezes or hangs after 4-5 minutes [/COLOR][/SIZE]

help me solve this problem once and for all

---

### Post by revnobody on 2011-09-18
I am having the same issue. Could someone please assist me. When I try to save the file I am getting this:

(gedit:2650): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2650): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9VSS1V': No such file or directory

(gedit:2650): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2650): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.X7CV1V': No such file or directory

(gedit:2650): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by Krytarik on 2011-09-18
revnobody, just create the stated directory:
```
sudo mkdir -p /root/.local/share
```Hope this helps to solve your issue, too.

---

### Post by revnobody on 2011-09-18
That did it! Thank you very much, [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")

---

### Post by mrdragon333 on 2011-09-19
i still have this problem&#8252;
can anyone please guide me

---

### Post by JSchultheis on 2011-09-19
> **mrdragon333 said:**
> [B][SIZE=3]
  [/SIZE][/B][SIZE=3][COLOR=Red]How to install "Intel Corporation 82845G/GL[Brookdale-G]/GE "[/COLOR][/SIZE][SIZE=3][COLOR=Red]  drivers?[/COLOR][/SIZE]
I have tried this solution 


```
gksudo gedit /etc/X11/xorg.conf
```This creates an empty file;

I am working on the same problem :confused:

I know that this code is trying to create a new file, but many of the threads I read instruct that the Xorg.conf is a 'configurable' file, and that it should already be in the X11 folder. (I'm just hoping to adjust the screen size)

I am running Ubuntu 11.04

When I navigate to Places>Computer>File System>etc/X11, xorg.conf is not there. 
Same if I go to terminal ```
cd /etc/X11
dir
```--> xorg.conf is not found.](*,)

**However, there is a shortcut file "X", which is a 'link to executable(application/x-executable).  The link target: /usr/bin/Xorg


So running the 'gedit' command for a file that is in another folder seems that it will never work, so I tried:```
sudo gedit /usr/bin/xorg.conf
``` still opening a blank new file.


Anybody want to be the hero today?!?!? :D

---

### Post by Krytarik on 2011-09-19
> **JSchultheis said:**
> but many of the threads I read instruct that the Xorg.conf is a 'configurable' file, and that it should already be in the X11 folder. (I'm just hoping to adjust the screen size)
Since Ubuntu 10.04, there is no mandatory, fully configured 'xorg.conf' by default anymore, see here:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Now, for any settings that aren't specified in an - optional - 'xorg.conf' X is pulling the defaults. So, if you just want to specify the screen resolution, you just need to add those specific settings.

Hope it helps!

---

### Post by djturbojp7 on 2012-03-09
I have a problem with the same 82845g setup and ubuntu 11.10 wondering if there any updates?

---

### Post by poco377 on 2012-03-15
Could someone please give me step by step instructions please? I am kind of new to all this Ubuntu stuff. :(

---

### Post by mrdragon333 on 2013-02-04
anyone found any workaround!?  its 2013 . Should consider my old PC dead?!  with no window 7 or ubuntu support

---

### Post by wildmanne39 on 2013-02-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

