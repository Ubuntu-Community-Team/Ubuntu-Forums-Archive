---
title: "intermittent freezing"
date: 2005-09-11
forum: Desktop Environments
---

### Post by chazmo on 2005-09-11
I recently purchased a Dell C600 laptop and installed Hoary. Everything seems to be working fine but I have one irritating glitch. The laptop freezes for about 1 second every minute or two. It seems like something is running in the background and while it's running the laptop won't respond. The freeze only lasts for about a second but it's get's to be irritating, especially when I'm on the web and my mouse freezes while I'm moving across the screen or trying to type in an ID or password.

Any Ideas?  ](*,)

---

### Post by jdong on 2005-09-11
Dell Latitudes with Intel Speedsteps will freeze momentarily when the CPU frequency adjuster changes the frequency to save power.

Try **sudo /etc/init.d/powernowd stop** and see if the problem disappears until you reboot.

If so, then run **apt-get remove --purge powernowd**. APT will tell you it's removing 'ubuntu-desktop' along with powernowd, but that's fine.


If you look in your system logs ('dmesg'), you can see evidence of this problem by psmouse lost sync messages.

---

### Post by chazmo on 2005-09-11
You are the man. Your recommendations fixed my problem and my laptop now runs great.

Thanks,  :)

---

### Post by efreddi on 2005-11-19
[QUOTE=jdong]Dell Latitudes with Intel Speedsteps will freeze momentarily when the CPU frequency adjuster changes the frequency to save power.

Try **sudo /etc/init.d/powernowd stop** and see if the problem disappears until you reboot.

If so, then run **apt-get remove --purge powernowd**. APT will tell you it's removing 'ubuntu-desktop' along with powernowd, but that's fine.
[/QUOTE]


Great! Now my Dell C600 is ok.
Immediately after the installation the behavior of the mouse was herratic when the load for the CPU increases (for example launching openOffice).

Thanks a lot and best regards :) 



Elia Freddi

---

### Post by efreddi on 2005-11-19
[QUOTE=efreddi]Great! Now my Dell C600 is ok.
[/QUOTE]

Ops! 
I forgot some detail:

Dell C600 with bios version A23, Ubuntu 5.10




Elia Freddi

---

### Post by RichGags on 2006-02-16
How can I stop powernowd everytime the computer starts without removing it?  Or does that not make sense?

---

