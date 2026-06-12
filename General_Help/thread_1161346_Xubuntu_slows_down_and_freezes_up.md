---
title: "Xubuntu slows down and freezes up"
date: 2009-05-16
forum: General Help
---

### Post by squiggly_crayon on 2009-05-16
While playing videos and often parallely surfing, xUbuntu often starts slowing down (video also starts skipping), and if i do not restart immediately, the system freezes.
I have 1. 5GB Ram and a Centrino Duo processor on Dell Latitude D620 laptop.

Can someone please help in narrowing down the problem and advise how to fix this ?

---

### Post by paradigm2 on 2009-05-16
Might be graphics related, or possibly due to temperatures.

```

lspci

```

To give us an idea of hardware.

When you play a video next time, open a terminal window and do:

```

top

```

Let us know what you see.

---

### Post by Raffles10 on 2009-05-16
It does that because Xubuntu is lightweight like an elephant. Use Arch + Xfce4.6.

---

### Post by Pbethe on 2009-05-16
I know Ubuntu.com has documents about debugging systems freezes.  It sounds like you have some warning before total freeze up, so that helps.  I would think you would want to close down apps that are causing the problem. Ctl+alt+F1 should take you to a command prompt, and Ctl+alt+backspace will do the same and kill your GUI.  Once you get a prompt, I would want to do this:

cd /var/log
ls -l *.log

You should have a list of files that you can look at and get some idea what the problem is.  They are plain text, so this should work:

less kern.log

---

### Post by squiggly_crayon on 2009-05-23
Thanks a ton for helping. I was out of town for a few days, and my bro just shifted away to simplyMepis. For now, it seems quite fine. Am sure will start missing ubuntu soon, but for now it is Mepis ):P

---

