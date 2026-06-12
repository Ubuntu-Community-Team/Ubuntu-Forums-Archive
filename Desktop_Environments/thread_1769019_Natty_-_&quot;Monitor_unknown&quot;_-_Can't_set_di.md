---
title: "Natty - &quot;Monitor: unknown&quot; - Can't set display resolution"
date: 2011-05-27
forum: Desktop Environments
---

### Post by yug_matt on 2011-05-27
Hi,

   I have done a scratch install of Ubuntu 11.04 (Natty) successfully today. I am facing problem while adjusting my monitor resolution.

   My motherboard is pretty old, **Kobian 845GLNDSMx. **When I tried to adjust the resolution from **Preferences -> Monitors, **the resolution is shown as 800x600 (4:3), Refresh Rate - 0Hz and Rotaion as normal. "Monitor Unknown" is highlighted on the window. Moreover, "Detect Monitors" doesn't work.


Could you help resolve this issue.

Regards
Yug
PS: I faced similar issue with fiesty too.

---

### Post by yug_matt on 2011-05-29
While searching Ubutu forum for the solution, I have found the below link which gives the .rpm driver from Intel for 845G/GL and steps to install it. 

[http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux](http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux)

However, I am stuck at the step "sudo alien <filename.rpm>" due to following errors. 

[COLOR=Magenta][COLOR=Purple]yug@yug-M903LR:~/Downloads$ sudo alien dri-I915-v1.1-20041217.i386.rpm 
[sudo] password for yug: 
Warning: Skipping conversion of scripts in package dri-I915: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_prep
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/dri-i915
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package dri-i915: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: error: parsing file 'debian/dri-i915/DEBIAN/control' near line 2 package 'dri-i915':
 error in Version string 'v1.1-20041218': version number does not start with digit
dh_builddeb: dpkg-deb --build debian/dri-i915 .. returned exit code 2
make: *** [binary-arch] Error 9
yug@yug-M903LR:~/Downloads$ 
[/COLOR]

[/COLOR]Could anyone know the solution to bypass this error "[COLOR=Magenta][COLOR=Purple] version number does not start with digit"[/COLOR][/COLOR]

Thanks in advance.

Regards
Yug

---

### Post by wildmanne39 on 2011-05-29
> **yug_matt said:**
> While searching Ubutu forum for the solution, I have found the below link which gives the .rpm driver from Intel for 845G/GL and steps to install it. 

[http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux](http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux)

However, I am stuck at the step "sudo alien <filename.rpm>" due to following errors. 

[COLOR=Magenta][COLOR=Purple]yug@yug-M903LR:~/Downloads$ sudo alien dri-I915-v1.1-20041217.i386.rpm 
[sudo] password for yug: 
Warning: Skipping conversion of scripts in package dri-I915: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_prep
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/dri-i915
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package dri-i915: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: error: parsing file 'debian/dri-i915/DEBIAN/control' near line 2 package 'dri-i915':
 error in Version string 'v1.1-20041218': version number does not start with digit
dh_builddeb: dpkg-deb --build debian/dri-i915 .. returned exit code 2
make: *** [binary-arch] Error 9
yug@yug-M903LR:~/Downloads$ 
[/COLOR]

[/COLOR]Could anyone know the solution to bypass this error "[COLOR=Magenta][COLOR=Purple] version number does not start with digit"[/COLOR][/COLOR]

Thanks in advance.

Regards
Yug
Hi, you can not install an rpm file in ubuntu, it uses .debs. Have you went into additional drivers to see if there is a driver for your video card there?

---

### Post by yug_matt on 2011-06-02
Hi, 
     sudo alien command is used to convert .rpm to .deb. But this conversion is failing due to the error related to version number. Morever, I am not able to find latest .rpm on the intel download page.

      Actually, my motherboard manufacturer is kobian (Mercury). There is no linux graphic driver supported for the motherboad. Hence I raised a support ticket to Mercury  with no response from them as yet.

I am giving try if intel driver would work as the chipset is same 845GL. 

   Will configuring xorg.conf work in this situation. Any thoughts on this.

Thanks
Yug

---

### Post by dino99 on 2011-06-02
please dont add mess to a clean installation: your driver is part of kernel, so let it do its job itself

sudo rm /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by yug_matt on 2011-06-08
There is no  /etc/X11/xorg.conf in my system. However, I did the steps you mentioned with no success. I still find that "Display" setttings show "Monitor Unknown".

---

### Post by joey787 on 2011-06-09
i'm having the same exact problem, i've been trying to update my graphics drivers and i get the same exact message. any help would be appreciated

---

### Post by zivley on 2011-06-11
I have a solution for you, but you must be sure you know what you're doing before you try this. You need to know for sure the mode you're choosing is supported by your monitor!
All this is done via command line, so fire up a terminal.

I'll give my case as example, I wanted to display a mode that wasn't listed (1280X960) which is a mode I'm sure my monitor used in the past.
To know which output we want to use and how exactly it's called, run a query to xrandr
```
xrandr -q
```
The output is something like this
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
[COLOR="Red"]VGA1 connected[/COLOR] 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1280x1024      60.0  
   1024x768       85.0*    75.1     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        87.8     70.1
```
As you can see, the mode I want isn't listed, but we know now how is my monitor output called
We start by creating a new mode using a tool called cvt
```
cvt [COLOR="red"]1280 960[/COLOR]
```
The syntax is "cvt [COLOR="red"]width height[/COLOR]", use your desired settings
The output is something like the following
```
# 1280x960 59.94 Hz (CVT 1.23M3) hsync: 59.70 kHz; pclk: 101.25 MHz
Modeline [COLOR="red"]"1280x960_60.00"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync[/COLOR]
```
Now select and copy everything after **Modeline** (all the red text)
Now we need to add this new mode to xrandr to be able to use it later
Instead of using the weird name given by default, I preferred to call it "CUSTOM"
```
xrandr --newmode [COLOR="red"]"CUSTOM"[/COLOR]  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
```
Then we add this new mode to our desired output
```
xrandr --addmode VGA1 [COLOR="red"]"CUSTOM"[/COLOR]
```

Now we're able to change the mode of our screen to the newly added mode
```
xrandr --output VGA1 --mode "CUSTOM"
```

To make it permanent we can add the last command to the gdm startup script
```
gksu gedit /etc/gdm/Init/Default &
```
Find the line
**/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm**
and add all the previous xrandr commands right before it
```

xrandr --newmode "CUSTOM" 101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
```
xrandr --addmode VGA1 "CUSTOM"
xrandr --output VGA1 --mode "CUSTOM"
[/code]

Save, exit and restart
If for some reason the computer doesn't start with the newly added settings, don't worry, at least it will be now available for you to chose it via the "System Settings>Monitors"
(Check the screenshot below)
[ATTACH]194873[/ATTACH]

I hope this helps

If someone knows a better way, please let me know.

Ziv

---

### Post by bkratz on 2011-06-12
@zivley--thanks for the step by step description.  I had tried xrandr before (apparently poorly), but your method made it work this time--still not sure why--you know what was different. Anyway, thanks again.

---

### Post by zivley on 2011-06-12
U R welcome!
I'm glad I could help someone with it

---

### Post by bkratz on 2011-06-12
Are you sure the & symbol should be there in

gksu gedit /etc/gdm/Init/Default  &

I had to leave it off

Also, since I had switched to Xubuntu with the new version ( Ubuntu seems bloated) I did have to use nano instead of gedit. Just learning Xubutu though ( I am sure everyone else knows this though!)

---

### Post by mister_playboy on 2011-06-13
The & symbol just allows further terminal input while the chosen program is running.  Leaving it off the quoted command just means you would have to close the gedit/mousepad window before typing in the terminal.

---

### Post by zivley on 2011-06-14
> **mister_playboy said:**
> The & symbol just allows further terminal input while the chosen program is running.  Leaving it off the quoted command just means you would have to close the gedit/mousepad window before typing in the terminal.

Exactly!
that is just a way I'm used to run commands on terminal, so I can release it for further input while the program is still running.
It's only useful for me when I'm opening a GUI program from terminal, for command line processes I prefer to use "screen"

To your question, you don't have to use it, is not a must

---

### Post by yug_matt on 2011-06-25
Hi ,

 Thanks for the reply, I have tried the steps as below. But I couldn't proceed further because of the error "xrandr: Failed to get size of gamma for output default". 
```

yug@yug-M903LR:~/myprograms$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
yug@yug-M903LR:~/myprograms$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
yug@yug-M903LR:~/myprograms$ xrandr --newmode "CUSTOM" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default


```

---

### Post by zivley on 2011-06-25
Please paste the output of the following command:
```
lspci -nn | grep VGA
```

---

### Post by michaelam on 2011-07-14
I am also having a similar problem, my screen resolution should be 1366x768 and have tried all solutions to no avail. Below is my xrandr -q & lspci -nn | grep VGA output information

mich@mAM:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)

mich@mAM:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0*

hope you can give help. thanks

---

### Post by zivley on 2011-07-14
first of all, make sure you have the intel display drivers installed
```
sudo apt-get install xserver-xorg-video-intel
```

Have you tried the steps I gave on my previous post [here]("http://ubuntuforums.org/showpost.php?p=10929081&postcount=8")?

---

### Post by yug_matt on 2011-07-16
Here is the output 

yug@yug-M903LR:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)

---

### Post by zivley on 2011-07-17
> **yug_matt said:**
> Here is the output 

yug@yug-M903LR:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)

My post above about installing the intel driver could help you too

---

### Post by moopere on 2011-07-17
Unbelievable.  Seriously.  Its July 2011 and after all these years there still doesn't seem to be a simple tool for end users to set their monitor and display resolution.

Its just laughable.

---

### Post by Rodney9 on 2011-07-17
> **moopere said:**
> Unbelievable.  Seriously.  Its July 2011 and after all these years there still doesn't seem to be a simple tool for end users to set their monitor and display resolution.

Its just laughable.

I found lxrandr, works well so far.

---

### Post by UrBob on 2011-08-16
Thanks for the excellent walkthrough. At least the commands worked for me, even if it didn't do the job.
I read a message elsewhere which was supposed to do the same thing, but the newmode and addmode lines failed. Here is what I did.
[HTML]/etc/X11$ sudo xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
  640x480    50.0*
  320x240    51.0
/etc/X11$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
/etc/X11$ sudo xrandr --newmode "CUSTOM800" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
xrandr: Failed to get size of gamma for output default
/etc/X11$ sudo xrandr --addmode default "CUSTOM800"
xrandr: Failed to get size of gamma for output default
/etc/X11$ sudo xrand --output default --mode CUSTOM800
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
/etc/X11$ 
[/HTML]As you can see, I'm working at 640x480 (which messes up an awful lot of dialogs which expect at least 800x600.
Also, I was not able to select the newly added modes from the GUI interface as they were not listed, even though I tried to make them permenant as directed in the original walkthrough.
My problems started when I gave the go-ahead to update to the nVidia drivers, and it seems that they do not like my monitor at all.
lspci shows the following:
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV36 [GeForce FX 5700LE] [10de:0343] (rev al)
Hope someone has some ideas, or knows how to go back to the default display drivers.
 
I managed to get back to the default drivers. I had the original problem on 10.10 and upgraded to 11.04 which does allow me to resise more of the dialogs and also had an option to get rid of the nVidia drivers. Unfortunately it also has a problem where sometimes the screen is broken into three areas which do not line up correctly. This sometimes sorts itself out after logging in, and sometimes needs me to change the resolution a couple of times, so not very handy. (1024x768 is available so an improvement).

---

### Post by thyraios on 2011-08-29
just for the record:
system: dell inspiron 1420 + lg flatron via vga
de: gnome 3 via ppa on top of xubuntu 11.04
above xrandr settings work great for dual, but when I try to disable laptop monitor something goes wrong and it reverts to original dual screen settings after time expires

---

### Post by gordintoronto on 2011-08-29
> **moopere said:**
> Unbelievable.  Seriously.  Its July 2011 and after all these years there still doesn't seem to be a simple tool for end users to set their monitor and display resolution.

Its just laughable.

There's a terrific simple tool if you have an Nvidia video card. And a different good one for people with ATI video cards. And another one which works in many other cases, but there are a handful of video adapters which are nasty and poorly supported.

---

### Post by mrdragon333 on 2011-09-18
```
user@OM-MS-6714:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```
can anyone please help me install the correct Intel driver for unbuntu 11.04
I am able to get resolution higher than 800*600 also unbuntu does not detect my monitor
I have checked my xconfig file it empty

---

### Post by bkratz on 2011-09-18
> **mrdragon333 said:**
> ```
user@OM-MS-6714:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```can anyone please help me install the correct Intel driver for unbuntu 11.04
I am able to get resolution higher than 800*600 also unbuntu does not detect my monitor
I have checked my xconfig file it empty


since you have the Brookdale, many people experience problems. Here is a good starting place (esp. post  8  )

[http://ubuntuforums.org/showthread.php?t=1748717](http://ubuntuforums.org/showthread.php?t=1748717)

Then just googlubuntu.com and search for like experiences.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Brookdale&as_qdr=m6&sa=Google+Search&lang=en#866]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Brookdale&as_qdr=m6&sa=Google+Search&lang=en#866")

---

### Post by mrdragon333 on 2011-09-18
WOW! it worked


```
gksudo gedit /etc/X11/xorg.conf
```

This creates an empty file; paste the following into the file and save:

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


```

---

### Post by bkratz on 2011-09-18
> **mrdragon333 said:**
> WOW! it worked


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


```


Sure glad it did!  --( I had my doubts)

---

### Post by mrdragon333 on 2011-09-19
it worked... but now Ubutu keeps on[SIZE=3] freezing   [/SIZE]without any reason?
do you know why is it freezing ?

---

