---
title: "Radeon drivers cause problem"
date: 2010-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joseph5800 on 2010-04-24
[LIST]
[*]Dell Dimension C521
[*]AMD Athlon X2 Dual Core Processor 4200+
[*]3GB RAM
[*]ATI Radeon X1300/X1550 series
[*]Ubuntu 10.04 Beta 2
[/LIST]


Ubuntu was running fine until I discovered Compiz, and then installed the Linux ATI Radeon drivers from [http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml]("http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml") and installed them via sudo bash in Terminal. Things seemed to be running fine after the successful install, but then my pc seemed to hang when I changed the Visual Effects to the highest setting, so I hit alt+ctrl+f1, and ctrl+alt+del, and I got a DOS like screen up (recovery console?) asking me to login which I did, I didn't think I needed this console so I hit ctrl+alt+del which initiated  a reboot. After booting into Ubuntu from GRUB, it got to the purple Ubuntu load screen and crashed. The screen resolution was also lower than normal. It is now like this every time I boot.

Any solutions?

Many thanks in advance,
Joseph.

---

### Post by Rrogers on 2010-04-24
Can you get to a terminal: Alt-F1 ?
I can send you a link to  get rid of the alternate drivers; and then you can reinstall the xfree ones.  Be aware getting rid of the Radeon drives is a little lengthy; 5-10 steps.
Don't rush, somebody else can probably (hopefully!) give better advice.
I only get these alerts once a day (unless I explicitly logon), so I will leave this window open till the morning then go back to once a day.

Ray

---

### Post by joseph5800 on 2010-04-25
Hello Ray, and thank you for your fast response. Since it crashed on boot every time, I decided to format the whole PC and start again. I reinstalled windows XP and got it updated and set up correctly. I then installed Ubuntu 10.04 on the LiveCD again successfully, but it doesn't boot right. I sometimes get a white screen, but most of the time it boots to a DOS like screen with 'Ubuntu lucid (development branch) [MY PC NAME] Tty1' and asks me to login which I can but it is just a command prompt. I read that Alt F7 skipped this. But if I do this I just get a blank black screen with a blinking rectangle in the corner forever. All I can do is alt F7 back to the aforementionedlogin bit, or press power button which initiates poweroff .

Many thanks in advance,
J. McCowie.

---

### Post by Rrogers on 2010-04-25
I have no experience yet with 10.04, but there are some items.
If you boot off of the Live CD and run (not install)  that way, do you get the xwindows screens?
That would mean that your installation didn't match the Live CD start up.  Which in turn would mean your installation procedure went astray.   Either your fault or Ubuntu's; but the setup is supposed to be easy so it's really theirs unless you went out of your way to confuse things; like choosing Radion drivers over the xfree drivers.  Choosing the defaults should get you a working system, but I don't know if it would overwrite XP.
I have a xorg.conf that works in 9.10 with two monitors.  There were problems with the dual monitor setup that I had to override.
You should send a report via apport-collect; unfortunately you probably don't have a mail server running.  Once you get to the console you could collect relevant files together on a USB stick (or somewhere xp will see them) and then submit them to the Ubuntu bug reporting system.
Alternately you could send me the /var/log/Xorg.0.log file; and /var/log/messages :(.  I would be faster at saying "I don't know" than the bug system:)
If you find somebody more competant than me: Go for it!  It's been a long time since I really knew what went on inside these distributions.

Ray
[FONT=monospace][/FONT]

---

### Post by Rrogers on 2010-04-25
Oh yes; you could try "startx" at the console.  It shouldn't be necessary and probably won't work, but it's always interesting to me when this happens.

---

### Post by Rrogers on 2010-04-25
I'm not being disrespectful; just going down the troubleshooting tree that I would follow.
Did you do the DVD chkdsk before installing?
Ray

---

### Post by joseph5800 on 2010-04-26
After many unsuccessful reinstalls, I found that by letting the Ubuntu partition take up it's preset amount of space (near 270GB, yikes!) it booted fine. Funny PC, mine. Haven't tried rebooting yet after this install so it may fail! Trying to avoid a reboot in case.

J. McCowie.

---

### Post by Rrogers on 2010-05-02
Still on the mailing list.  I tried a 10.04 livedvd on my system, with X1300 card, and failed.  Guess I will wait until some others have success; such as  you.  Let me know.
I'll tell you that I believe in luck more than a 270GB partition requirement.
Ray

---

