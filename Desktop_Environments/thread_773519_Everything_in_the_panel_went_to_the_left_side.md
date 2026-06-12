---
title: "Everything in the panel went to the left side"
date: 2008-04-28
forum: Desktop Environments
---

### Post by shokoup on 2008-04-28
Hello, i'm using the newest version of Kubuntu, kde4, suddenly, everything in the lower panel go to the left side beside the K button, i failed to drag and drop the icons, i attached pic,.
Thanks for help

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67883&stc=1&d=1209438436[/IMG]

---

### Post by Xiong Chiamiov on 2008-04-28
Is there an option to unlock the panels, or some such?

I tried KDE 4, really, but hated it absolutely.  I still have it installed for the libs and stuff (so I can get updated versions of things), but I'm using 3 still for everyday usage.  You'll notice that there are quite a few people who consider 4.0 to be a beta, and are waiting for 4.1; that's why the supported kubuntu release has 3.5.8.

---

### Post by shokoup on 2008-05-01
any help :(:(:(

---

### Post by T-Virus on 2008-05-01
I tried KDE 4 myself and I still think it's not in the state of being functional and customizable. I would suggest you stick around with KDE 3 little bit more. Like until KDE 4.2 or KDE 4.3 comes out.

---

### Post by caryb on 2008-05-01
I had the same problem, the fix is easy boot into a console delete the .kde4 file in your home directory then reboot & it will recreate it with default settings.


Cary

---

### Post by shokoup on 2008-05-05
> **caryb said:**
> I had the same problem, the fix is easy boot into a console delete the .kde4 file in your home directory then reboot & it will recreate it with default settings.


Cary

I'm sorry for this question, but really i started to hate Kubuntu, when i logged to delete .kde4 file by terminal, it asks for root password, i couldn't log as root, the beta version was better than this version, please help me with detailes of how to delete this file by commands.

I was using, Mandriva, Pclos, and finally beta version of this kubuntu, i didn't face all these bugs in this releases.

Thank you for help

---

### Post by Xiong Chiamiov on 2008-05-05
The reason you're having so many bugs is because you're using the **unsupported** version of Kubuntu Hardy - the supported one comes with KDE 3.5.9.  The other distros you used probably also used the KDE 3.5 branch, which is why they weren't buggy as hell.  Don't blame the Kubuntu devs - blame the KDE devs.

That said, *buntu uses a different version of sudo than you're probably used to.  Rather than having a separate root account, you only have one account: yours.  Whenever you need to do something as root, just put "sudo" in front of it, and enter your password when it asks.  For instance, to edit your fstab (please don't mess around with this!), you would do something like
```

sudo kwrite /etc/fstab

```
and then enter your password when it asks. (well, it would be better to use kdesudo, I know, but that's not the point of this illustration)

That said, since the .kde4 folder is in your home directory, you shouldn't have to be root to edit it.  Try this:
```

cd ~
mv .kde4 .kde4_old

```
and if, for some strange reason, you get a permission denied error on the 2nd command, do
```

sudo mv .kde4 .kde4_old

```
then log out and back in.  All of your old KDE settings will be in the .kde4_old folder in case you need them.

---

### Post by shokoup on 2008-05-07
Thank you for great help

---

