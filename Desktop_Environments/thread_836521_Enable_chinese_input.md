---
title: "Enable chinese input"
date: 2008-06-21
forum: Desktop Environments
---

### Post by mvaniersel on 2008-06-21
I'm trying to enable chinese input, following this howto: [http://ubuntuforums.org/showthread.php?p=124214](http://ubuntuforums.org/showthread.php?p=124214)

But I'm stuck. First of all, the package scim-server-socket doesn't exist anymore in Hardy. I'm assuming that it's obsolete.

I tried adding scim -d to the startup session, then tried to activate SCIM by pressing Ctrl+Space. that didn't do anything.

Then I tried starting SCIM from the command line, but I get this:

```
scim -d
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.
```

What am I doing wrong? How do I know when SCIM is working correctly?

---

### Post by tiga2001 on 2008-06-23
Have you tried this?
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

It's a good thing that you're using regular ubuntu with gnome, btw, because in kubuntu the asian language input is really hard to get to work properly. I had to install my OS in Traditional Chinese and then switch the user default language back to English.

---

### Post by mvaniersel on 2008-06-24
Thanks, that link got me a little further. 

I can now get chinese in gedit with a right-click, select the SCIM input method, then press Ctrl+Space and then just type.

But that method doesn't work for other programs, e.g. Firefox?

PS: &#20320;&#22909;

---

### Post by tiga2001 on 2008-06-24
Yea, it can be hard to get it to work in Firefox. My experience has been that scim is inconsistent there. Perhaps try another browser like Seamonkey or Konqueror? For me, Chinese input works only in KDE applications like Konqueror, but I guess it's because I'm using Kubuntu, so I can't really help you there. I guess you could try copy and pasting in from other applications that take chinese input.

---

