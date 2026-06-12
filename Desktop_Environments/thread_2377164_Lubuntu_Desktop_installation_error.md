---
title: "Lubuntu Desktop installation error"
date: 2017-11-10
forum: Desktop Environments
---

### Post by warmango on 2017-11-10
Recently i tried installing the Lubuntu Desktop, specifically on the Linux Subsystem for Windows and was planning to use it via Xming on the PC, except when I ran the command 
```
sudo apt-get install lubuntu-desktop
```

I received this error after 2 hours of downloading and configuring packages

```
 Errors were encountered while processing: blueman
 lubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 

I have since then run the Purge command on the two packages,

---

### Post by HankB on 2017-11-10
Did you see a blog post that indicated this was possible? My understanding is that the Windows Subsystem for Linux (what MS calls it - and I agree that Linux Subsystem For Windows makes more sense) is intended to run text mode programs only. I did a quick Google search on "lubuntu WSL" and saw that some people had success with this. One suggestion was to try to install lubuntu-core instead of lubuntu-desktop. You might also try xfce.

In any case, you are at the mercy of Microsoft and how faithfully they have emulated Linux. At present they have not announced support for a graphical desktop (that I have heard) and until they bring something like that out, you are trying something that is not supported.

Good luck!

---

### Post by warmango on 2017-11-10
they don't have NATIVE support for graphical, but with the X11 based program called Xming, you can run [code] export DISPLAY=:0 [code] and then run the command to launch the graphical program, and thanks, I ended up having to reinstall the Subsystem after a reboot because it wouldn't load

and thanks, I will try core

---

### Post by warmango on 2017-11-10
okay, It has installed properly, no error, but i cant start it, how do i start the Desktop GUI from the terminal?

---

### Post by HankB on 2017-11-10
The pattern I saw in the information I found was to run the X server on Windows and connect to the client on WSL.

---

### Post by warmango on 2017-11-11
thats what im doing, but i cant get it to show me the desktop

---

