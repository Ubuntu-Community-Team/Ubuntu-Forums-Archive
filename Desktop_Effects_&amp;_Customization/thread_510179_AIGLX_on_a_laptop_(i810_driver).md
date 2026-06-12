---
title: "AIGLX on a laptop (i810 driver)"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by schultz on 2007-07-26
Hello to everyone. I am quite new to Kubuntu. I own a HP ze4950 laptop with i810 graphics card.

In a previous experience, I have tried to run XGL in my box, but I noticed it was too slow, specially in stuff like pulling the firefox scrollbar down.

Then I read about it and people recommended me installing AIGLX and Compiz, but I could not find much decent help.

Then I ask, what is the best way (which runs faster) to make that cube work and windows shake?

As you see, I am a total ignorant in what comes to linux.

So, how can I have a hardware accelerated desktop which runs nicely in i810?

(Doing so shall give me the right to brag and my brother shall probably switch to Ubuntu as well).

---

### Post by Waappu on 2007-07-27
Hi

Try add these lines to your xorg.conf if not exist```
Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection
```

---

### Post by schultz on 2007-07-27
Thanks for answering, I really appreciated the help.

But still I have problems. Does AIGLX already come in the standard Ubuntu Feisty? If not, what is it that I need to do to install it? How is it I can login in a session with it?

I really needed a tutorial for AIGLX on i810 with Compiz, but could not find one.

Thanks again and in advance.

---

### Post by Waappu on 2007-07-27
Hi

I don't have any guide.

Aiglx is build in Xorg 7.2 and Feisty comes with Xorg 7.2
You should set xorg.conf file and just login to normal gnome session

---

### Post by schultz on 2007-07-27
Ah, nice, thanks for the instruction.

So just install compiz over AIGLX then, right?

---

### Post by schultz on 2007-07-27
I did the configuration in xorg.conf an logged off and in.

I felt absolutely no change after that.

To have the cube desktop, I must install Compiz, right?

How is it I do it in Feisty with a i810 video card?

---

### Post by menox on 2007-07-27
sudo apt-get install compiz compiz-fusion* compiz-kde compizconfig-settings-manager emerald

---

### Post by schultz on 2007-07-27
Thanks, but I need to know each step in detail, not the whole packages. That way I can not check out which are stable, which are compatible, etc...

---

