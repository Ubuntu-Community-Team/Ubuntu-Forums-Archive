---
title: "Inopportune keyboard layout change"
date: 2010-07-12
forum: Desktop Environments
---

### Post by NarsilAnduril on 2010-07-12
Hi all,

Need a little help on this magical one ...

My mother's desktop (she's 84) is a Koala totally useless stuff expurgated : no menu, no admin rights, one dock with needed softwares (evolution, firefox, skype, openoffice, that's it). Her keyboard's layout is swiss french (CH_FR)

From time to time, I get a call from her : "My keyboard's keys have changed, I can't type anymore ! Help me !!!"

When I look to the GUI's settings, I can find that the keyboard is back to US, so I set it back to CH_FR and delete the US keyboard (not disable, delete), but a few days later, the keyboard goes back to US ... and so on.

There is no shortcut configured to change the layout.

I tried to find the /etc/X11/xorg.conf there isn't one !? Where are these settings now ?

Does somebody have an idea about this case, I'm loosed !

Pleeeease !](*,)

Diego

---

### Post by NarsilAnduril on 2010-07-14
up ! please ...

---

### Post by simosx on 2010-07-14
> **NarsilAnduril said:**
> Hi all,

Need a little help on this magical one ...

My mother's desktop (she's 84) is a Koala totally useless stuff expurgated : no menu, no admin rights, one dock with needed softwares (evolution, firefox, skype, openoffice, that's it). Her keyboard's layout is swiss french (CH_FR)

From time to time, I get a call from her : "My keyboard's keys have changed, I can't type anymore ! Help me !!!"

When I look to the GUI's settings, I can find that the keyboard is back to US, so I set it back to CH_FR and delete the US keyboard (not disable, delete), but a few days later, the keyboard goes back to US ... and so on.

There is no shortcut configured to change the layout.

I tried to find the /etc/X11/xorg.conf there isn't one !? Where are these settings now ?

Does somebody have an idea about this case, I'm loosed !

Pleeeease !](*,)

Diego

This is really weird, and requires some debugging to figure out what changes.
For example, does she shutdown properly the computer? Does she kill the power which might erase the settings file?
Does she press buttons while the system is booting?

You may need to observe her while on the computer.

I have seen quite a few reports of this situation in these forums, however noone yet managed to provide information as to what action can reliably cause the problem.

---

### Post by NarsilAnduril on 2010-07-14
Yep, in fact, the main problem is that I can't observe her on the computer, I'm quiet far away and only act remote on the OS.

But the suggestion that she could shutdown "savagely" is plausible, I'll check this first.

---

### Post by dimitrisdad on 2011-11-01
Ubuntu 11.10  Swiss french was not an option during install.  Swiss German was, but whenI selected it, the install hung.

---

