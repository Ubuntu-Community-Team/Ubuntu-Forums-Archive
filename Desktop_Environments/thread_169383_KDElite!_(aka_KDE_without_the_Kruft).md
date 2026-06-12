---
title: "KDElite! (aka: KDE without the Kruft)"
date: 2006-05-02
forum: Desktop Environments
---

### Post by charlie. on 2006-05-02
In a last-gasp attempt to screw up my PC, because I am really trying to push this Dapper Beta to breaking point, I am trying to install KDE with as little as possible.

Firstly, I tried installing kubuntu-desktop on top of a server install. That worked, but the ton of extra applications that it loaded on my PC did not really count as a minimal install, so I tried this...

Install a server.
Upgrade the kernel to linux-k7-smp for my AMD X2 4400+.
Install kde-core, xserver-xorg and x-window-system-core.
Install xorg-driver-fglrx and do the aticonfig thing.
startx

... and it worked. I now have KDE up and running with very little installed: Konqueror, Konsole and Kate. (Ideally Konqueror should not be part of it, but if Microsoft can make IE part of Windows...)

It is not perfect however. While I have no problems with the initial KDE styles, themes, behavior and icons - all of which are easy to change - X-windows does not start automatically at boot time. Instead, I have to login in text mode and enter "startx". What have I missed?

In order to create a complete, bare-bones KDE desktop, I must fix the graphical login problem. Please help!

---

### Post by shakin on 2006-05-02
install kdm

---

### Post by njf on 2006-05-03
I suggest install the kubuntu-default-settings package too.

---

### Post by charlie. on 2006-05-04
As far as I know, KDM is part of kde-core. Is that not so?

---

### Post by charlie. on 2006-05-04
I installed KDM, it was clearly not part of kde-core. When I booted, it gave an error about not finding the Kubuntu theme. To fix this, I installed kubuntu-default-settings.

Unfortunately, kubuntu-default-settings did exactly what I did not want: it installed a whole bunch of themes (not a big issue) some annoying sounds (more of an issue) and completely reconfigured my KDE menu! (a rather big issue)

As far as I can tell, KDM is configured in the file /etc/kde3/kdm/kdmrc. Surely, all I need is a version of that file that does not refer to the Kubuntu theme - then I will not require kubuntu-default-settings. Apparently, the 'kdm' package comes standard with a version of kdmrc that refers to the kubuntu theme, so I would have to find a clean one elsewhere.

If I can manage to fix this, without installing kubuntu-default-settings, I will have achieved a perfectly clean, minimal KDE installation on my Ubuntu system. Any suggestions?

---

### Post by Parkotron on 2006-05-05
Just open up /etc/kde3/kdm/kdmrc as root, find the "UseTheme=true" line, change it to "UseTheme=false", save and close the file. Then fire up kcontrol and configure KDM using the Login Manager module.

Oh, and with respect to Konqueror being part of kde-core, I would imagine it's included because it's a file manager not because KDE wants to bundle their own web browser. Also, I think Konqueror is used to display the shortcuts and files on the desktop, but I might be wrong on that.

---

### Post by charlie. on 2006-05-05
I dug aroung in kdmrc for a while. I had not read your post yet, so I did not change the value of UseTheme. Instead, I commented out the "Theme=..." line and added a "Theme=" line, effectively settings "Theme" to "", the default according to the comment. This method worked too.

I was also interested in some other settings, like the Num Lock status option and the ability to make my PC welcome me to my own PC. (Who can do without that feature? For the expense of about ten keystrokes, not me!)

I would not be surprised to find that Konqueror does do that. I expect that it is about as integral to KDE as Internet Explorer is to Windows. Konqueror is not proprietary, however, so this is acceptable.

All is now well. My KDE system rocks!

Would anyone be interested in my method, now complete and consisting of several modifications to my initial post, as a Wiki article or am I the only idiot who likes a clean KDE installation?

---

### Post by NetMatrix on 2006-05-05
sounds good charlie, lets see the steps... :D

---

### Post by Luke on 2006-05-22
charlie,

a step by step would be great. i'm very interested in setting up my system this way.

thanks!

---

### Post by Iarwain ben-adar on 2006-05-22
Hi,
I'd like a step-by-step aswell :-)

Sounds like something new to do with my pc... :D


Iarwain

---

