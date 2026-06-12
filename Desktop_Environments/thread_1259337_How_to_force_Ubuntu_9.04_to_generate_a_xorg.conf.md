---
title: "How to force Ubuntu 9.04 to generate a xorg.conf"
date: 2009-09-06
forum: Desktop Environments
---

### Post by zong1 on 2009-09-06
Problem description:

  Have Vaio SZ dual graphics card PC (Intel & nvidia). Installed with nvidia gfx card running and xorg.conf was generated.  Fine.  I forgot about the Intel card when I installed the O/S. 

I had a copy of the xorg.conf I used for the same PC in Ubuntu 8.10 & copied into /etc/X11 and rebooted with th INtel card and if was sick. 

Deleted the xorg.conf file and all was well.  However, with a working Intel environment I now have to copy the xorg.conf file so that I can use a script to flip between the gfx cards, but there is no xorg.conf file in /etc/X11.  Perhaps, this latter release of Ubuntu does not need one.  However, it uses one for the nvidia card.

Question: 

  How can I generate the xorg.conf?  I thought that there was a problem called xorgconfig, but its not in my installation of Ubuntu 9.04, or not in the PATH.

Cheers, z.

PS. Please resist writing comments like:  Why are you doing this? and Why not stick to one gfx card? and so on. There is reason that is beyond the scope of this post and irrelevant to the solution ;)

---

### Post by zong1 on 2009-09-06
Update:  I used this command to generate a default xorg.conf:

dpkg-reconfigure -phigh xserver-xorg

It created this:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



Sadly, now, when I tell the notebook to shutdown, the system hangs.  Love Ubuntu...

---

### Post by simonyee on 2009-09-06
Hi,

Try updating the drivers from Nvidia website and do a repair of the installation.

---

### Post by zong1 on 2009-09-06
> **simonyee said:**
> Hi,

Try updating the drivers from Nvidia website and do a repair of the installation.

Dear Simonyee, please do tell me why you would update Nvidia drivers for an Intel card?

This has nothing to do with nvidia other than that is the "other" gfx card.  I have two gfx card.  I wanted to generate a vanilla xorg.conf for *current* gfx card, which is an Intel and not an nvidia card.  

 Anyway, please dear **mod**, please close this thread because I have managed anyway with dpkg-reconfigure -phigh xserver-xorg. The system hang is beyond the scope of here.


As ever with this forum, no reader analyses the original posters' questions and then answers the question they would like to have answered. ha he. Bye.

---

### Post by zong1 on 2009-09-09
Just for completeness for other readers who happen on this thread,

After the default Intel xorg.conf was created by the dkg-reconfigure command the following took place:

cd /etc/X11
cp xorg.conf xorg.stamina
# xorg.speed was copied from xorg.conf whilst using the nvidia card.

The following was added to init.d and linked to /etc/rc2.d/S200xorg_conf:

```

# cat /etc/init.d/org_conf 
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi

```

This'll check which gfx card is active during start up and copy the correct xorg.conf as required.

---

