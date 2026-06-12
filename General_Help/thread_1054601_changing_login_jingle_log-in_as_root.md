---
title: "changing login jingle/ log-in as root?"
date: 2009-01-29
forum: General Help
---

### Post by frankwakeman on 2009-01-29
I've managed to do this twice in the past, with Linux Mint 6 and Mandriva 2008.1 KDE, but am stumped with Ubuntu.  I have a clip from the start of a song that I want to use to overwrite the login jingle, which I've located easily enough.  I'm sure with Mint I logged in as root, but I don't seem to be able to do that.

With Mandriva KDE you do kdesu konqueror in the console - is there an equivalent, or an easier way to open the file system, or can you tell me how to log in as root.  (I have currently set a separate password for root, as I'd hoped to be able to login with it.)  I know it can get messy, but there is just this one task I want to do.

Thanks.

---

### Post by frankwakeman on 2009-01-29
B.t.w. the file is desktop-login.ogg (which is in usr.share/sounds/ubuntu/stereo), and what I've done is to name my clip the same, so that I can just paste it into the folder when I know how.  This is what worked before.

---

### Post by jerome1232 on 2009-01-29
Hit alt+f2 then type
```
gksu nautilus
```

and I think you should read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), has some good info in there.

---

### Post by sisco311 on 2009-01-30
You also can set the login sound in System -> Administration -> Login Window... Accessibility tab.

---

### Post by frankwakeman on 2009-02-01
Before Jerome1232 told me about gksudo I had gone into users and groups and entered a password for root.  Does that constitute enabling a root account?  And can I then undo this as it's not needed?  If I can and do now undo it and wanted to use gksudo would it prompt for my normal password (it's been a few days since my jingle episode, so I can't remember whether it was my normal or root password that was needed then).

Thanks.

---

