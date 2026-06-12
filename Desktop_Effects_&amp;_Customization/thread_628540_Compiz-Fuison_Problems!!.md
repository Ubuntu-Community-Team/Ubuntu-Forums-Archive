---
title: "Compiz-Fuison Problems!!"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by zlegge08638 on 2007-12-01
Hi,
I installed Compiz-Fusion on my Ubuntu 7.10.  I have all the options and programs like emarld, GL desktop, e.t.c  I go to enable the settings I want but nothing happens??  Like wobbly windows I enable in Advanced Desktop Settings and then close it but "Where are the wobbly windows??  Please help!!

---

### Post by SunnyRabbiera on 2007-12-01
hmm, well compiz is stil rough around the edges so I am not surprised by your problem
but tell me what exactly did you install?
I find your post a little lacking in details.

---

### Post by macaholic on 2007-12-01
> **zlegge08638 said:**
> Hi,
I installed Compiz-Fusion on my Ubuntu 7.10.  I have all the options and programs like emarld, GL desktop, e.t.c  I go to enable the settings I want but nothing happens??  Like wobbly windows I enable in Advanced Desktop Settings and then close it but "Where are the wobbly windows??  Please help!!
Can you give some specifics on your hardware, like what type of graphics card you have? It is possible you don't have the correct drivers installed. Also, what is the output of "compiz" in terminal?

---

### Post by zlegge08638 on 2007-12-01
Compiz in terminal?? How do I do that? And I have an ATI accelerated radeon graphics card...  I installed Compiz-config-settings or somthing like that, i installed emarld, and gnome-compiz-manager, and thats it.  Then I went into those things applied what I wanted, restarted the computer and nothing worked.  I also tried this again, but still nothing.  I even tried it without restarting it but nothing worked.

---

### Post by macaholic on 2007-12-01
> **zlegge08638 said:**
> Compiz in terminal?? How do I do that? And I have an ATI accelerated radeon graphics card...  I installed Compiz-config-settings or somthing like that, i installed emarld, and gnome-compiz-manager, and thats it.  Then I went into those things applied what I wanted, restarted the computer and nothing worked.  I also tried this again, but still nothing.  I even tried it without restarting it but nothing worked.
To run anything in terminal, first open terminal, Applications > Accessories > Terminal. Then type compiz, and give the output. However, I don't think you have even installed compiz, just because you have installed compiz-config-settings-manager, doesn't mean you have compiz installed. To make sure you have them installed type
```
sudo apt-get install compiz emerald
``` in terminal.

---

### Post by zlegge08638 on 2007-12-01
This is what I got in terminal....    zlegge@zlegge-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5a62 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Thanks, I looked in Synpatics Pack manager and it says Compiz Fusion is already installed.  Does the terminal output tell you anything?

---

### Post by macaholic on 2007-12-01
What is your output of fglrxinfo in terminal?

---

### Post by Faud on 2007-12-01
>  And I have an ATI accelerated radeon graphics card


> **zlegge08638 said:**
> This is what I got in terminal....    zlegge@zlegge-laptop:~$ compiz
Checking for Xgl: not present. 


Shouldnt you be running an XGL session with an ATI card or is that no longer valid in 7.10. I dont have an ATI card just thought I rememberd this from somewhere

---

### Post by zlegge08638 on 2007-12-01
zlegge@zlegge-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

zlegge@zlegge-laptop:~$

---

### Post by macaholic on 2007-12-01
Well, it looks like you don't have the ATI driver installed, to install it go to System > Administration > Restricted Driver Manager and enable Ati accelerated graphics driver.
Then, type sudo apt-get install xserver-xgl in terminal.

---

### Post by zlegge08638 on 2007-12-01
Wow! I think something happened!!  This is what I got in the notification area...

Xgl server setup changed

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable


this is what I got in terminal....

zlegge@zlegge-laptop:~$ sudo apt-get install xserver-xgl
[sudo] password for zlegge:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1843kB of archives.
After unpacking 4854kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libglitz1 0.5.6-1 [76.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB]
Fetched 1843kB in 2s (826kB/s)        
Selecting previously deselected package libglitz1.
(Reading database ... 100254 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
zlegge@zlegge-laptop:~$

---

### Post by macaholic on 2007-12-01
Restart your computer and then log back in, see if compiz works, if not paste the output of compiz from terminal again.

---

### Post by zlegge08638 on 2007-12-01
Ahhhh! I'm so excited!! Stuff is working like, transparency, wobbly windows and stuff but I don't know if it's emerald or compiz.  This is what I got for compiz....

zlegge@zlegge-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


also how do you do the cube thing you see people doing on Youtube??  like switching between windows

---

### Post by macaholic on 2007-12-01
The default key binding is control + alt + drag to free rotate, and the default for rotate is ctrl + alt + left/right arrows. Also, just wondering, is compiz starting when you log in, or does it have to be run?

---

### Post by zlegge08638 on 2007-12-01
It started when I logged in and I was like, Whoa!  Also, when I edited the settings in "Advance Desktop settings"  I can't switch between workspaces and I have Desktop cube enabled.

---

### Post by macaholic on 2007-12-01
Do you have "rotate cube" enabled?

---

### Post by Bheegerji on 2007-12-01
I've ATI accelerated driver enabled. Thats the o/p I get when I type sudo apt-get install xserver-xgl in terminal.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package in

---

### Post by airxart on 2007-12-01
Hi , I am running 7.10 ubuntu &  kubuntu.
I can get the screen to flip & thats about it.
I have an old nvidia 5200 fx

Here is a screenshot of compiz in terminal.
Does it look right?[IMG][IMG]http://img115.imageshack.us/img115/2389/screenshothe5.png[/IMG]
By [airxart](http://profile.imageshack.us/user/airxart) at 2007-12-01[/IMG]

---

### Post by zlegge08638 on 2007-12-01
Yea, I have it enabled, even when I try to switch workspaces on the bottom right it won't let me.

---

### Post by Bheegerji on 2007-12-01
Any way I can get the advanced desktop setings enabled?

---

### Post by macaholic on 2007-12-01
> **airxart said:**
> Hi , I am running 7.10 ubuntu &  kubuntu.
I can get the screen to flip & thats about it.
I have an old nvidia 5200 fx

That looks normal, are you sure everything is set in compiz-config-setting-manager? (ccsm)

---

### Post by macaholic on 2007-12-01
> **Bheegerji said:**
> Any way I can get the advanced desktop setings enabled?
sudo apt-get install compizconfig-settings-manager

---

### Post by airxart on 2007-12-01
> **macaholic said:**
> That looks normal, are you sure everything is set in compiz-config-setting-manager? (ccsm)


Yes, I've set cube with reflections.
Ctrl+alt+LMB works, but I don't know how to add more desktops in ubuntu.
Kubuntu I figured out. Or is it even possible?
 :)

Also I've seemed to change the window settings.
If I ucheck everything in windows managment will I get the Min / Max / Close frame around the window?
nevermind.I logged out ,  back in & it came back.

---

### Post by macaholic on 2007-12-01
> **airxart said:**
> Yes, I've set cube with reflections.
Ctrl+alt+LMB works, but I don't know how to add more desktops in ubuntu.
Kubuntu I figured out. Or is it even possible?
 :)
Wait, dod you mean you only have 2 desktops? If so then you can go into CCSM, general options, desktop size and change it there.

---

### Post by airxart on 2007-12-01
O.K. Thanks
:)Got the cube.Here's how I had to set it  to get it to work.
[IMG]http://img142.imageshack.us/img142/3450/screenshotcompizconfigsoq0.png[/IMG]
By [airxart](http://profile.imageshack.us/user/airxart) at 2007-12-01

**How do you turn it all off? If I ever wanted to?**

---

### Post by Bheegerji on 2007-12-01
Hey It's working .Thanks.

---

### Post by airxart on 2007-12-01
Note: setting the stroke size too large in annotate made my computer lock up.
Seems to be a little glitchy.
Still I think it great.

---

### Post by metalpancake on 2007-12-01
Yeah, I have a similar problem. wobbly windows works fine, but when I tick the Cube box, simply nothing happens. maybe the same sort of problem?

---

### Post by thoman on 2007-12-24
Having the same problem with compiz

using intel 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)



compiz output

:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I do have the compiz manager but all the setting cannot be changed, already skip check the blacklist card.

3d test using win+e, 3d effect flashes and top bar missing

---

