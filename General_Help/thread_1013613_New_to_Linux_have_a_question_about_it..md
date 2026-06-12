---
title: "New to Linux have a question about it."
date: 2008-12-17
forum: General Help
---

### Post by Tweakbl on 2008-12-17
I am fairly "new" to Linux.I have a question about the general nature of the OS.Does it learn about the hardware it is on as it goes?Let me explain.
I have a Dell C640,I installed Xubuntu on it and kicked the tires a little bit.The only "problem" I had was configuring the Dell Truemobile 1470 Wifi card.Not really a problem but a inconvenience as I had to work from the Command Terminal and black list the default driver.Then updated to the fwcutter tool B43 driver package.
I then installed Ubuntu as I like Gnome's Windows-ish nature a little better.I blacklisted again and also installed fwcutter driver again.Again a little bit of a pain but still no problems.

Now,my battery runs low while working,the machine precedes to go into suspend mode.Upon pluging in the power,it will not resume,or nothing,just blinking lights no screen.I then do a hard reset.Boots fine,I then Suspend the machine again on purpose,this time It suspends but when it resumes it has red strips all over it and no desktop.Again a hard reset.

I suspend and reset 2 or 3 more times,I also try Hibernation an equal number of times.The first couple times they fail,then they start working.
Then Suspend fails again with red strips,although I did ctrl+alt+backspace.I can hear the desktop music,but the display is still garbled red lines.
So again my question does the OS debug itself to make it work?

I am running Ubuntu 8.10 Ibex

---

### Post by Sam Lars on 2008-12-17
Some "learning" may go on, but I think suspend/resume is a weak spot that doesn't work on some (a lot?) hardware.  My Dell Inspiron 1525 does fine.

---

### Post by Tweakbl on 2008-12-19
Thanks,I was just wondering cause it seemed hit and miss.

Is there a difference in Xubuntu,Ubuntu,Kubuntu etc. that would affect this?
Is Gnome,KDE or XFce better at addressing suspend/Hibernate functionality or is it totally kernel based???

---

### Post by FuturePilot on 2008-12-19
> **Tweakbl said:**
> Thanks,I was just wondering cause it seemed hit and miss.

Is there a difference in Xubuntu,Ubuntu,Kubuntu etc. that would affect this?
Is Gnome,KDE or XFce better at addressing suspend/Hibernate functionality or is it totally kernel based???

Suspend/hibernate is related to the kernel. It won't matter what desktop environment you use.

---

