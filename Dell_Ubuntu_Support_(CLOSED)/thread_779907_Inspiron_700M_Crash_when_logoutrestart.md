---
title: "Inspiron 700M Crash when logout/restart"
date: 2008-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by breaddawson on 2008-05-03
Hi,all.
i've posted this in hardware/laptop, but got few replies(only 1 actually). So i reposted here and excuse me for the duplicated post.

I'm using Dell inspiron 700m and i tried to installed linux on my laptop these days. I've installed 8.04 on it but found Black Screen showed up immediately after i click "Logout"/"Restart"/"Power Off". Keyborad did not respond, so did Hard Disk led. Actually, only power led and the cpu fan is still working. I have to press the power button several seconds to reboot it.

1. At first i think maybe xserver is down, but i can not switch to other terminals using Ctrl+Alt+F(1/2/3....)

2. The display card is Intel i855GM , and the driver was installed automatically by Ubuntu, i can get a 1280*800 resolution and compiz was performing quite well.

3. I checked the system log but found nothing. Actually , there're few messages during the black screen and next restart.

4. I'm using gnome,and i thought it may be caused by GDM, so i configured unbuntu to boot to a prompt line mode. and then startx manually. After this , "Restart" & "Power Off" is gone, but i can still get black screen after i click "Logout". I tired to using KDM, the problem remains.

5. Actually , the same problem was there when i tried Debian 4.0 Etch. I tried XFCE , Gnome & FVWM, only fvwm worked fine for me. And that's why i alter to Ubuntu.

6. I don't know if the infos below will help:

1) i've installed Winxp SP2,too.
2) Swap is 1G and on hda7
Ubuntu is 6G andon hda8
3) I installed ssh server, and tried to use another pc to login to my machine. The connection is broken after Black Screen.


Did someone encounter the same problem? Or does someone is delight to help me? Thank u very much!....and if there's some infomation i should offer, plz let me know.

I really want to run Ubuntu on my laptop.

Thank u very much again.

---

### Post by snap on 2008-05-05
I have the same issues with Hardy (Assuming you are running Hardy) on the same laptop (Dell 700m)

maybe you want to have a look at this thread

[http://ubuntuforums.org/showthread.php?t=767833&highlight=Dell+700m]("http://ubuntuforums.org/showthread.php?t=767833&highlight=Dell+700m")

My take is switching to i810 driver from "intel" driver and using the old xorg.conf from 7.10 could help. I cannot confirm since I have totally ruined my older installation of 7.10, (I am dual booting between a updraded 8.04 and a clean 8.04 installation currently.)

---

### Post by breaddawson on 2008-05-05
thank u for your reply, yes, i'm using Hardy

1. did adding "lapic" work?

2. Does the crash when logging out/restarting fixed on your computer by switching to i810 & using 7.10 xorg.conf?

If so, would u plz send me a copy? Actually i'm using "intel" now, because i can not get 1280*800 under i810, i just don't know why.:(

Thank u again.

---

### Post by snap on 2008-05-05
I didn't use "lapic"

yes it fixed my crash problems or I have yet to see it happen again ;).
however an old issue from my first attempt at upgrading 7.10 to 8.04 resurfaced

After a logout and immediate login, sometimes, i get only a coloured background with nothing else on my desktop and and killing X at this point sometimes crashes the laptop while other times GDM reloads and I can login fine.

but in that state I can still switch VTs, next time it happens i'll try switching VTs and restarting GDM manually from commandline.


You need to install 915resolution when using "i810" driver to get 1280x800 resolution.

```
sudo aptitude install 915resolution
```

and then configure

/etc/default/915resolution
here is mine

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=800
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

and attached is my xorg.conf

and finally a reboot.

---

### Post by breaddawson on 2008-05-06
Thank u for you guide and xorg.conf
i'm using your xorg.conf but i found i can not use compiz now
is this a must or i810 does not support this?

---

### Post by snap on 2008-05-06
I am sorry I use XFCE and  i have not used compositing in Hardy yet but it used to work fine in 7.10

Can you try selecting a lower setting for effects in compiz and see if that works? 

As far as I know in gnome you have the "Desktop effects" tool where you can select three settings for compiz, try the lowest to see if that works and then work your ways upwards.

EDIT: Compositing in hardy works fine for me in XFCE but then again i think XFCE has it's own compositing manager sognome might still have issues.

---

### Post by breaddawson on 2008-05-07
> **snap said:**
> I am sorry I use XFCE and  i have not used compositing in Hardy yet but it used to work fine in 7.10

Can you try selecting a lower setting for effects in compiz and see if that works? 

As far as I know in gnome you have the "Desktop effects" tool where you can select three settings for compiz, try the lowest to see if that works and then work your ways upwards.

EDIT: Compositing in hardy works fine for me in XFCE but then again i think XFCE has it's own compositing manager sognome might still have issues.
thank u for ur help.
i tried again and found i can use desktop effects now. :)
and what's more, i found that a newer version of the driver "intel" was out. 
i don't know if it can fix our bug ,though.

P.S.: Has sb. report our bug to xorg?

---

### Post by alperyilmaz on 2008-07-06
Hi breaddawson,
Is switching to i810 solved all the problems? You specifically mentioned problems during logout/restart, I'm having big trouble with suspend, did the workaround fix that problem too?

---

