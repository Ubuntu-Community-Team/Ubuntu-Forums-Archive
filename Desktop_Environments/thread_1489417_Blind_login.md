---
title: "Blind login"
date: 2010-05-21
forum: Desktop Environments
---

### Post by dargaud on 2010-05-21
Hello all,
a simple question if somebody can check the steps for me.

The power supply of my monitor died and while I wait for a replacement I can use the PC via VNC. Problem is that it rebooted yesterday and VNC won't work with the login window (only once I'm logged in).

I tried to type my username and password in the blind but that didn't work, even with various combinations of [Tab] and [Enter]. Using only the keyboard, what must I type, precisely ?

(Yes, I did try the [x11vnc continuous login screen]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager") technique but that didn't work)
Thanks

---

### Post by Jakiejake on 2010-05-21
Press Enter Then Type your password then enter

---

### Post by krunge on 2010-05-21
> 
The power supply of my monitor died and while I wait for a replacement I can use the PC via VNC. Problem is that it rebooted yesterday and VNC won't work with the login window (only once I'm logged in).

Are you sure the X server is running without the monitor?  Sometimes the X server will exit if it can't detect the monitor modes.

---

### Post by Jakiejake on 2010-05-23
When you turn the computer on
Do you see anything (boot screen???) if so it is not your monitor

---

### Post by dargaud on 2010-05-24
I don't see a thing for the simple reason that the power supply is toast ! I can connect via ssh and remote-X, but I prefer to use VNC for some things. The key combination indicated above didn't work, probably because after several attempts the default box is probably off. Is there a (alt?) key to make sure I type in the username box ? Also bear in mind that this is kubuntu.

---

### Post by krunge on 2010-05-24
> **dargaud said:**
> I don't see a thing for the simple reason that the power supply is toast ! I can connect via ssh and remote-X, but I prefer to use VNC for some things. The key combination indicated above didn't work, probably because after several attempts the default box is probably off. Is there a (alt?) key to make sure I type in the username box ? Also bear in mind that this is kubuntu.

When you ssh in, do you see the X server process running (e.g. by looking for it in 'ps wwaux' output) ??

---

### Post by dargaud on 2010-05-24
Yes, X is running fine, but VNC won't unless I can get past the login screen with the local keyboard.

---

### Post by Jakiejake on 2010-05-25
> **dargaud said:**
> Yes, X is running fine, but VNC won't unless I can get past the login screen with the local keyboard.

Wireless Or USB
Just asking

---

### Post by dargaud on 2010-05-25
It's a USB keyboard, FWIW. And I just managed to get the monitor changed under warranty, so that's gonna take a while longer...

---

### Post by Jakiejake on 2010-05-26
> **dargaud said:**
> It's a USB keyboard, FWIW. And I just managed to get the monitor changed under warranty, so that's gonna take a while longer...

Good Luck
Just A Question
When you had the monitor could you see the POST screen
I assume you know what that is...

---

### Post by dargaud on 2010-05-26
Yes, I know what the post screen is... and I fail to see how that's relevant. The computer is up and running, I can ssh to it... OK, I give up, I'll keep working with X until the replacement arrives.

---

### Post by Jakiejake on 2010-05-27
> **dargaud said:**
> Yes, I know what the post screen is... and I fail to see how that's relevant. The computer is up and running, I can ssh to it... OK, I give up, I'll keep working with X until the replacement arrives.

I wanted to know that because if you could I was probally just the OS playing up... Mark As Solved if it is :KS :guitar:

---

