---
title: "ut2004 installation fails"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by rgp-02 on 2007-01-10
i followed instructions here:

[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

game installed “successfully”.........then i entered ut2004 in terminal and got:

rp@rgp-02:~$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error
rp@rgp-02:~$

---

### Post by Perfect Storm on 2007-01-10
Looks like you havn't installed the 3D driver for your graphic card.

---

### Post by rgp-02 on 2007-01-10
how do i do that?

---

### Post by Perfect Storm on 2007-01-10
Depends which card you have.

---

### Post by rgp-02 on 2007-01-10
GeForce 7600 GS

i had posted this earlier under a different topic:

rp@rgp-02:~$ sudo apt-get install nvidia-glx nvidia-kernel-common
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
nvidia-kernel-common is already the newest version.
Suggested packages:
nvidia-kernel-source
The following NEW packages will be installed:
nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.7-10.1 [4066kB]
Fetched 4066kB in 3s (1129kB/s)
Selecting previously deselected package nvidia-glx.
(Reading database ... 88784 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb) ...
Setting up nvidia-glx (1.0.8776+2.6.17.7-10.1) ...

rp@rgp-02:~$ 

and was told that it succeeded

---

### Post by Perfect Storm on 2007-01-10
You need to activate it also. Editing the xorg.conf file.

```
sudo nano /etc/X11/xorg.conf
```

Find the Section "Device" and change "nv" to "nvidia", save and exit. restart X.

---

### Post by rgp-02 on 2007-01-10
i have NO IDEA how to do that!

can you please expand on that a bit so a retard can follow you?

---

### Post by rgp-02 on 2007-01-10
CAN SOMEBODY PLEASE HELP ME?

PLEASE TELL ME HOW TO FIND xorg.conf so i can edit it!

C'MON GUYS, PLEASE BE A LITTLE MORE UNDERSTANDING! I DON'T HAVE ANYONE HERE TO TEACH ME THIS STUFF. ALL I WANT TO DO IS RUN THIS STUPID GAME PROGRAM AND I'LL LEAVE YOU ALONE, OK?

---

### Post by Tuna-Fish on 2007-01-10
just open terminal and type ```
sudo nvidia-xconfig
```
And post what is says here.

That should do the editing for you.

anyway, the xorg.conf is located, as AI told you in /etc/X11/xorg.conf

If you want to navigate to it graphically, just go "file system", "etc" and "X11". However, as it is an important configuration file, modifying it is restricted.

---

### Post by rgp-02 on 2007-01-11
THANK YOU VERY MUCH!

now the game finally works (sigh of relief)

i got this after closing game:

rp@rgp-02:~$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

anybody know what it means and what to do?

---

### Post by rgp-02 on 2007-01-12
ok......game works and i want to load megapak and patch

i followed instructions here:

[http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

downloaded and saved pack to desktop, then went to terminal and:

rp@rgp-02:~$ cd && cd Desktop
rp@rgp-02:~/Desktop$ sudo sh ut2004.megapack-english-2.run
Password:
sh: Can't open ut2004.megapack-english-2.run
rp@rgp-02:~/Desktop$ 

any suggestions?

---

### Post by Perfect Storm on 2007-01-12
Check if the name is correct.

---

### Post by rgp-02 on 2007-01-12
this is really getting frustrating..............and i think i'm getting ready to throw the damn towel in. i really like ubuntu, but i need to find an operating system that can run game programs without crapping out.

i installed:

/home/rp/Desktop/ut2004.megapack-english-2.run

now i get:

rp@rp-desktop:~$ ut2004
bash: ut2004: command not found
rp@rp-desktop:~$ 

what do i do now?

if i'm beating a dead horse here, can one of you please direct me to a site where i can find an OS that supports gaming?

---

### Post by handy on 2007-01-12
> **rgp-02 said:**
> this is really getting frustrating..............and i think i'm getting ready to throw the damn towel in. i really like ubuntu, but i need to find an operating system that can run game programs without crapping out.

if i'm beating a dead horse here, can one of you please direct me to a site where i can find an OS that supports gaming?

[_**This will link you to the easy one...**_]("http://www.microsoft.com/en/us/default.aspx")

---

### Post by rgp-02 on 2007-01-12
i knew someone would respond quickly with something original like that. my advice to you is if you don't have anything  constructive to contribute DON'T POST!

---

### Post by slowdeath on 2007-01-12
not to overstep any boundaries. but in this great day of the internet. there is a wonderful site called [www.google.com](www.google.com). im my beginning days of ubuntu, all i had to do was copy and paste whatever error i was getting to the search. and 99% of the time i got the answer. and if u do a search for ut 2004 install's on ubuntu. there are an abundance of great how-to's out there. so please do not get impatient when you arent getting your answers as quickly as you want them.

---

### Post by rgp-02 on 2007-01-12
another original masterpiece!

but can you help with this?

i installed:

/home/rp/Desktop/ut2004.megapack-english-2.run

now i get:

rp@rp-desktop:~$ ut2004
bash: ut2004: command not found
rp@rp-desktop:~$

---

### Post by handy on 2007-01-13
Try including the path to the executable as well:

/home/handy/ut2004/ut2004

I use that same command to start UT2k4 from the Gnome menu, (this is Gnome - Ubuntu -  specific.)

If you don't know about that & you want to try it?  Then right mouse click on the **Applications** *Menu* in the top left corner of the panel, & choose **Edit Menus**, after **Alacarte Menu Editor** opens you can use it's **File** *Menu*  to add UT2k4 to the Games Submenu, or whatever...  & use the command line that includes *your* path to the executable.

I hope that helps...

---

### Post by foxmulder881 on 2007-01-13
> **rgp-02 said:**
> i knew someone would respond quickly with something original like that. my advice to you is if you don't have anything  constructive to contribute DON'T POST!

For future reference, you need to calm down as many people aren't responding because of the attitude in the way you're asking your questions. I advise you to read the Ubuntu Code of Conduct if you haven't already and you may understand why people aren't responding. ;)

---

### Post by rgp-02 on 2007-01-13
ok ok ok..........i accept your apologies............now, can we get to business?

i now have game and megapack/patch installed!

1.i still cannot get res to 1600x1050 (that it used to get); i went to settings/display and only gets
1280x1024 

2.cannot get ctrl key to make player jump; i went to settings/input/configure controls  with no ability to make changes

anyone know how to fix these?

---

### Post by Perfect Storm on 2007-01-13
Make sure that 1600x1050 is added to your xorg.conf. You can run **sudo dpkg-reconfigure -phigh xserver-xorg** (best done outside X) or edit the xorg.conf with nano and add the desire resolution.

---

### Post by handy on 2007-01-13
@rgp-02:

***Please*** & ***thankyou***, go a really long way in this forum.

But I won't SHOUT IT!

I don't like to think about how you would treat someone who wasn't **volunteering** their precious time to help you to be able to play a game!

If you have a problem there are lots of people here who will do their best to help you, until they are put off by rudeness & disrespect, then they do the normal thing & walk away.

There is a **big** difference between having a problem & being one.

---

### Post by desijays on 2007-01-14
> **handy said:**
> 

There is a **big** difference between having a problem & being one.

I couldn't have said that any better. 

But none the less, i hope the guys gets his game to work the way he wants it to. 

One more thing.

I use a dell m1710 laptop and it has a "NVIDIA GeForce Go 7900 GS" graphics card. Could you please tell me what device driver to use for this card on Ubuntu. There are drivers for this card on Windows XP. But i don't plan on using it with windows. I want to install ubuntu on my laptop.

I also use a "NVIDIA GeForce 6600 GT" on my desktop. Could you please tell me what device driver to use for this card on Ubuntu. I want to install ubuntu on my desktop as well.

---

### Post by slowdeath on 2007-01-14
> **desijays said:**
> I couldn't have said that any better. 

But none the less, i hope the guys gets his game to work the way he wants it to. 

One more thing.

I use a dell m1710 laptop and it has a "NVIDIA GeForce Go 7900 GS" graphics card. Could you please tell me what device driver to use for this card on Ubuntu. There are drivers for this card on Windows XP. But i don't plan on using it with windows. I want to install ubuntu on my laptop.

I also use a "NVIDIA GeForce 6600 GT" on my desktop. Could you please tell me what device driver to use for this card on Ubuntu. I want to install ubuntu on my desktop as well.

i have a NVIDIA PCI express 7300 LE, and the drivers i got through automatix2 seem to work quite well.

---

### Post by desijays on 2007-01-14
NVIDIA 7900GS is a mobile video card meaning it is meant for the laptops on the go. Thats why Im confused as to whether it might have a different set of drivers, or if NVIDIA corp provides linux drivers themselves. 

I checked their website and i see a set of drivers for this series but not the exact model number. 

any help would be kind

---

### Post by handy on 2007-01-15
I allways use [***Automatix2***]("http://www.getautomatix.com/") for my nVidia drivers because it is so easy, as it was created to be.

I hope it works as beautifuly for you too!

---

