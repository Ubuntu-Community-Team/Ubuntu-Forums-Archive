---
title: "Alienware Area 51m Laptop X Input Freezes"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dburgan on 2010-07-08
Hey everyone, I'm trying to turn on a friend of mine to use Ubuntu, so I just installed 10.04 using WUBI inside his Windows XP SP3 partition on his Alienware Area 51m laptop. The install went smooth as silk and everything seemed to go swimmingly. Until I tried to start using the machine.

The keyboard and touchpad/mouse seem to be very unstable. They will work for a few minutes, albeit in a herky jerky fashion, and then all of a sudden the mouse freezes and the keyboard is unresponsive. This happens at the login page, or anytime after login.

Things I've done:

- Verified that the machine responds to pings when the lockup occurs. Definitely seems that Linux itself is happy, but it is X that is having the problem. Interestingly, the laptop screen saver even kicks in. Doesn't seem to be a hard freeze, just seems like X gets stuck.

- Booted into recovery mode root prompt/networking and done "apt-get upgrade" and "apt-get dist-upgrade" to ensure the latest/greatest is installed.

- Connected a USB mouse to see if it worked better than the touchpad. The USB mouse seems to work longer before the freeze happens, but it happens nonetheless.

- I looked at the /var/log/Xorg.0.log to see if anything suspicious was in there. Lots of information messages, one warning about dropping back to "old VESA probe mode", but no errors or anything that looked like a problem to me.

- I've searched both ubuntuforum.org and the net at large to see if anybody else has this trouble. Seems I'm the only one?

Not sure what to try next. Does anyone have any pointers or suggestions? I'd love to turn on my friend to Ubuntu, but I can't give it to him in this state. Help!

Thanks!
Darrell

---

### Post by dburgan on 2010-07-08
One additional data point: usually after the lockup happens if I press the power button, the "Shut Down the Computer" window pops up and prompts me to click on "Shut Down" , "Restart", etc. Since I can't click on anything, I have to wait for it to time out, at which point it does a graceful shutdown of the laptop, as it should.

So X itself is not completely stuck. Just the keyboard and mouse. Does this suggest anything?

---

### Post by tja1618 on 2010-07-29
I am having the same exact problem. I think we should compare specs on our laptops.

I have an older Area51m 766 with the nVidia 5700 Go 128MB video card. I will post the complete specs when I get to the laptop later today, but in the meantime, have you made any progress?

I used to run older versions of Linux on this laptop with no problem. When I had issues the other day with Ubuntu, I installed Fedora 13, and the same problem exists. So I believe the issues are with a driver and/or the actual Linux kernel.

EDIT: more info: upon booting up, i opened a terminal and began to type the ifconfig command. I got as far as typing 'i' and then input froze, the terminal program continuously kept spamming the 'i' character to the screen. After this went on for a few minutes, I got one of those gnome messages saying something like "a crash in package kernel has occurred". Unfortunately I was not able to get more details. Also, it seems as though my interface went down because I cannot ping the machine.

---

### Post by tja1618 on 2010-07-29
Some more:

I tried booting the system directly to the command line (adding 3 to the end of the kernel line in grub). Got there, but then the system promptly locked up again. When pressing the power button it did a normal shutdown. The system is so unstable I am not sure how I can debug this.

---

### Post by dburgan on 2010-07-29
Sorry, but I never could get it resolved and gave up.:(

---

### Post by tja1618 on 2010-08-24
I just wanted to share with others my solution to get a stable distribution.

Simply adding "noapic" as a kernel option upon boot.

For those who don't know how to do this, from grub you can simply type "noapic", without the quotes, to the end of the kernel command line.

As for why this became an issue, I am not sure.

---

