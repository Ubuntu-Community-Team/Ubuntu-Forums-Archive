---
title: "Won't Install?"
date: 2009-04-08
forum: General Help
---

### Post by Chrismanquiz on 2009-04-08
Today, I tried to open a .avi video in Totem, and a message appeared, telling me that I did not have the right codec. It searched for the appropriate codec, then gave me the option to install the codec. I confirmed the install, and instantly I received this error message:

```
E: dpkg was interrupted, must manually run 'dpkg -- configure -a' to
correct the problem
E: _cache-> open() failed, please report.
```

So, I next tried to install an alternate video player. When I tried, I received a similar error message. I'm not that Linux savvy yet, I just recently made my switch from Windows to Ubuntu so if someone could _simply_ explain to me how to fix this, that would be great. :p 

Thanks in advanced, 
Chrismanquiz.

---

### Post by 3Miro on 2009-04-08
What is the other player that you tried. I have had some similar problems under KDE's Kaffeine, it looks for a codec, presumably installs it and then it doesn't play. I had to use MPlayer.

 The thing that is telling you to do is to go to Applications -> Accessories -> Terminal and enter:

```

sudo dpkg -- configure -a

```

This will try to reconfigure all the installed apps on you machine. It should be a safe command, however, it is probably wise to wait for a comment form someone more knowledgeable then me.

---

### Post by linux_lover69 on 2009-04-08
> **3Miro said:**
> What is the other player that you tried. I have had some similar problems under KDE's Kaffeine, it looks for a codec, presumably installs it and then it doesn't play. I had to use MPlayer.

 The thing that is telling you to do is to go to Applications -> Accessories -> Terminal and enter:

```

sudo dpkg -- configure -a

```

This will try to reconfigure all the installed apps on you machine. It should be a safe command, however, it is probably wise to wait for a comment form someone more knowledgeable then me.


Yeah use this command, It's not gonna hurt anything.

---

### Post by Chrismanquiz on 2009-04-08
Wow guys, thanks! That fixed the problem right up!

---

