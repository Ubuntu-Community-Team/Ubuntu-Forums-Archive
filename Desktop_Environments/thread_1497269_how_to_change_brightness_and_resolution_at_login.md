---
title: "how to change brightness and resolution at login"
date: 2010-05-30
forum: Desktop Environments
---

### Post by Adsg on 2010-05-30
Hi,
I'm able to configure the resolution and brightness with 10.04.
for example :

```
sudo echo -n 100 > /proc/acpi/video/VGA/LCDD/brightness
```But I can do it only for the user's parameters i.e resolution and brightness features are set up AFTER I log in.
I would like to change the resolution and brightness when ubuntu starts and at the login page

I've googled during 30 min but found only thing dealing with the xorg.conf file ... but we have not anymore this file with lucid lynx :S
anyone having an idea please ?

PS : I'm not speaking about the grub resolution :)

---

### Post by ajgreeny on 2010-05-30
If you make a new empty xorg.conf file and fill it with the text that you have found, that file will be read and used, so it is worth trying that solution.  There is no xorg.conf by default as it is not normally needed any more, but there are many situations where one is made and needed, eg when an nvidia proprietary driver is installed.

---

### Post by Adsg on 2010-05-30
thank you ajgreeny for your help :)

well so ... unfortunately (or fortunately ;) ) I have an ATI graphic card lol

so I tried to create my xorg.conf.new  (after stopping gdm of course) with the command
```
Xorg -configure
```and got
```
 Fatal server error:
  Cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"
```so I searched something else and finally I successed with
```
 X -configure
```I moved it in /etc/X11 and renamed it xorg.conf

I tried first to change to decrease the brightness  when the login window appears:
I located the "Monitor" section in xorg.conf and add the text:
```
Gamma 0.1
```then I rebooted .... but nothing changed. my gamma when login window appears was still max.


I tried to decrease resolution :
I in Section "Screen" I added
```
SubSection "Display"
       Depth        16
       Modes      "1024x768_75.00"
     EndSubSection
```I rebooted ... but this time ... my computer was completly stuck. Ctrl+Alt+f1 did nothing .... I had to launch the ubuntu CD-live to remove my xorg.conf file xD lol

---

### Post by Adsg on 2010-05-30
... wrong manipulation ... I thought I had found something ... but finally  it ended to nothing.
damned I can't delete my message?
sorry

---

### Post by ajgreeny on 2010-05-31
What ati card have you got in your machine?

I run an ati 9200SE, and have to have an xorg.conf to get a decent display.  Here's the working part of mine; try editing it to suit your system and monitor, and see if that helps.

For your current problem of being stuck, boot into the cli, if needed and there you can rename your xorg.conf as xorg.confbak, and try starting gnome again with ```
startx
```
Then try your version of my xorg.conf with the added gamma details if you need to.
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
    Option         "AccelMethod" "UXA"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by Adsg on 2010-06-05
Thank you [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") :)
my graphic is an ATI Mobility Radeon HD 3650.
But my screen is a LCD one and by seeing the numbers in your xorg.conf, I think you have a CRT monitor right?. with LCD there is no HorizSync or Vertival Refresh so I fear that I might damage my screen if I try such configuration :s
But xorg is quite obscure for me and I don't really like to try things that I don't understand xD I'm a bit paranoid lol ^^

How do boot into the cli (command line interface I guess ^^) ? 
.., ok I've searched in google

I found this: [http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html/comment-page-1#comment-5094](http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html/comment-page-1#comment-5094)
> To disable the login manager from automatically running at boot up, run the following command as root

#update-rc.d -f gdm remove

To reset your login manager so that it runs at boot up, do

#update-rc.d -f gdm defaults
but this is complelty useless ... I did the remove and rebooted ... still directly to gnome -.-
in /etc/init.d/ I still had gdm link ... it reapeared automatically ....


after more searching : 
> 
You need to open the /etc/default/grub file, locate the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"

and don&#8217;t forget to run &#8216;update-grub&#8217; afterwards to update.
this time It worked I went to the text mode ... BUT just before arriving to the text mode, I've seen during few second the ubuntu loading image ... so If I set my xorg.conf file ... I'm stuck even before arriving to text mode ...

grrr problem lol 
linux is so complicated sometimes .... so different manipulations depending on the linux distribution you use omg xD I sometimes Hate it lol
thinking to go back to windows ... lol ... no jocking ;)

---

