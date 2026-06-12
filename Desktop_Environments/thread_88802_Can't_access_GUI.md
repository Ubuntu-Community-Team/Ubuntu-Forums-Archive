---
title: "Can't access GUI"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Alex99 on 2005-11-11
Hi,
I'm a Linux-beginner and I'm having problems booting the system (Ubuntu 5.10). Starting the system works alright until the point where you usually would have to log in with the GUI. Instead, I can only log in with the text based prompt, and the following message appears:
"The display server has been shut down about 6 times in the last 90 seconds, it is likely that something bad is going on.  I will wait for 2 minutes before trying again on display this."
Any suggestions anyone?! I need my computer back...!
Alex99

---

### Post by vruum on 2005-11-11
try to reconfigure your xserver, like:
```

sudo dpkg-reconfigure xserver-xorg

```
and reboot, or restart gdm
```

sudo /etc/init.d/gdm restart

```
in case x is still broken, post your /var/log/Xorg.0.log

---

### Post by Alex99 on 2005-11-11
thx -
reconfiguring the xserver didn't make things work.
How do I see my /var/log/Xorg.0.log? (BTW, that's a zero in "...rg.0.log", right?)
If I enter this line (with "sudo"), I get the reply: "command not found".
Alex

---

### Post by vruum on 2005-11-11
yep, that's a zero, to view the file type:
sudo cat /var/log/Xorg.0.log

also, do you have any special hardware, like a 64 bit processor? and what is your graphics adapter?

[edit] the output of sudo cat... might be a little confusing, maybe try
sudo cat /var/log/Xorg.0.log | grep WW
sudo cat /var/log/Xorg.0.log | grep EE

---

### Post by jonny on 2005-11-11
Is this a new install?  If things previously worked, you probably have an automated backup of your X server settings that you can return to.

If so, try this:```
cd /etc/X11
ls
```If you can see a file called xorg.confxxxx where the xxxx represent the data and time that your system broke, try these commands```
sudo mv xorg.conf xorg.conf.backup
sudo cp xorg.confxxxx xorg.conf
```and then restart your PC

---

### Post by Alex99 on 2005-11-11
Hi,


thanks a lot for your replies.

What I haven't mentioned is that again and again, my computer shows a black screen all of a sudden and sometimes displays the mouse arrow in the shape it has in the gui when the computer's thinking (odd description... I guess you know what I mean). Then the blue screen shows up again, followed by the command prompt.

My system worked well until yesterday (Nov 10). I do not have a 64 bit-processor or any special hardware. I don't know what a graphics adapter is, though. I have an NV GeForce 5200 graphics card (is that the English term for it? I'm German) and a 17" TFT-display.

**- vruum:** 
The computer that crashed has a German keyboard, so I can't type the vertical line (|) that's part of the commands you recommended. The keyboard I'm using typing this is part of my American laptop. I tried switching to an American keyboard while reconfiguring the server, but it didn't work. Any suggestions?

**- jonny: the command **

> cd /etc/X11
ls

shows these files:

> app-defaults
config
fonts
gdm
ja_JP
rgb.txt
X
xinit
xkb
xorg.conf
xorg.conf200511060011
xorg.conf.200511111259
xorg.conf.200511111302
xorg.conf_backup
xorg.conf.backup
Xresources
xserver
xsession
Xsession.d
Xsession.options
Xwrapper.config

(system crashed on Nov 10 – 20051110 and worked well on Nov 6)

the command 

> sudo mv xorg.conf xorg.conf.backup

is followed by the message:

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?

followed by a long text I technically don’t understand: 

> Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 ...

Then I can choose to view a more detailed report of the same kind.
Then the message follows:

> The X server is now disabled. Restart GDM when it is configured correctly.

Entering the command 

> sudo cp xorg.conf200511060011 xorg.conf

and rebooting doesn’t change things.

Although my computer still doesn't yet run properly, I appreciate your help!
If nothing else works though, I think I'll do a completely new install, since I haven't had a lot of programs on the hard drive. My only question for this is: How do I save my Word-processing files and my Thunderbird-E-Mail-client-profile (incl. my messages?

But before I do so I'd still like to ask you for other suggestions to make the x-server run!

Alex

---

### Post by jonny on 2005-11-11
So you've restored your xorg.conf file to the status that it had when your computer used to work.  But you still have no GUI.

I guess that in the meatime you've probably either installed new hardware, changed your monitor, or installed some software packages?  In the first two cases, you can retrace your steps quite easily.  In the latter case you might be able to use apt-get remove to uninstall the packages that you added last... if you can remember what they were.

---

### Post by jonny on 2005-11-11
Forgot to say that if you decide to reinstall, the easiest way for you to backup your files would be to use a live CD (I'd suggest Knoppix as, unlike the ubuntu live CD, it'll automatically allow you to access your hard drive).  You can then use knoppix to save your files to another CD, a floppy disc, an mp3 player or a usb stick.  If you're really stuck, use Knoppix to email them to yourself and collect them later.

I don't use Thunderbird so don't know where it stores its data.  I'd guess that there's a hidden folder called something like .thunderbird in your home folder.

---

### Post by vruum on 2005-11-11
I guess a reinstall is probably the quickest, if you do that I think all mozilla stuff (firefox/thunderbird) is in the folder .mozilla in your home folder. if you have any free space on your harddrive, you might  also look into creating a new partition and mounting that as your home partition, it might be a little tricky, but it can save a lot of trouble whenever you mess things up enough to call for a reinstall.  
anyways, > followed by a long text I technically don’t understand:
 is basically the output of "cat /var/log/Xorg.0.log" and might give a hint as to what the trouble is. look for lines that have either (WW) or (EE) in them. 
lastly, to load a new keymap (eg a german or american one) the command is "sudo loadkeys en_US" or "sudo loadkeys de"

---

### Post by Alex99 on 2005-11-12
Hi,
just reinstalled the system and everything works fine - thanks for your help nevertheless!
Alex

---

### Post by meborc on 2005-11-12
always backup your files before reinstall... i know... i once didn't :rolleyes:  ... i would use knoppix and save my work on usb-stick... and then do a complete reinstall of ubuntu finest... hope u get everything to work soon

---

### Post by i_m_fletcher on 2005-11-15
Would I go through the same process if I just installed a new video card????  I went out yesterday and purchased a new nVidia GeForce 6200 AGP (replacing a nVidia GeForce 5200 PCI) and installed it.  When I boot up, it gets to the point where kdm usually starts, but instead it just kicks out to a console view with a blinking cursor (no command line prompt or anything).  Any ideas on how to get my box running again without a re-install?

---

### Post by codejunkie on 2005-11-15
[quote=i_m_fletcher]Would I go through the same process if I just installed a new video card????  I went out yesterday and purchased a new nVidia GeForce 6200 AGP (replacing a nVidia GeForce 5200 PCI) and installed it.  When I boot up, it gets to the point where kdm usually starts, but instead it just kicks out to a console view with a blinking cursor (no command line prompt or anything).  Any ideas on how to get my box running again without a re-install?[/quote]
from the terminal run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then run ```
sudo /etc/init.d/kdm restart
``` and reinstall the nvidia driver packages nvidia-glx & nvidia-settings.

---

### Post by i_m_fletcher on 2005-11-15
Thanks codejunkie!!!

---

