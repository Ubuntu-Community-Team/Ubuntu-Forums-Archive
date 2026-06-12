---
title: "Gnome-3 failed to start!"
date: 2011-05-25
forum: Desktop Environments
---

### Post by shafiee01 on 2011-05-25
Hi,
I had My Gnome-3 on 11.04 and i was happy with that till i update it and after restart during logging into gnome 3, i got this error: "Failed to load session 'gnome-fallback' ".
and i can login just by choosing "ubuntu" in the login panel.
I have attached list of all changes made by update manager, also.
Thanks

---

### Post by satanselbow on 2011-05-25
This is probably down to the most recent round of updates in the official repos and gnome3-team / ricotz ppas - there is loads of good "recovery info" in the existing gnome3 and gNatty threads.

No need to duplicate it all in a new thread ;)

---

### Post by shafiee01 on 2011-05-25
> **satanselbow said:**
> This is probably down to the most recent round of updates in the official repos and gnome3-team / ricotz ppas - there is loads of good "recovery info" in the existing gnome3 and gNatty threads.

No need to duplicate it all in a new thread ;)

Thanks satanselbow! :D
I solved my problem by modifying:
 /usr/share/xsessions/gnome.desktop file.

---

### Post by uMany on 2011-05-25
Hi,
Can you please post a link to the instruction to modify the gnome.desktop file or post the instructions? Thanks in advance.

---

### Post by macozz on 2011-05-25
I had the same problem, so I do a fresh install and after that I installed the UGR version for Gnome 3, but it fail to start too. Any suggestion?
I also appreciate if you post the modification you do in the gnome.desktop file

---

### Post by uMany on 2011-05-25
Hi,

I found it!

Change this:

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

to this:

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=gnome
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

that's all you need to do

---

### Post by NareZ on 2011-05-27
Kinda the same problem there. Was happy about G3 up until natty update a couple of days ago.. The only difference is that I got this 'surprise message':
[http://img15.imageshack.us/img15/9873/screenshotjph.png]("http://img15.imageshack.us/img15/9873/screenshotjph.png")

Any explanations, why this happened? How to fix it?

---

### Post by macozz on 2011-05-27
Not sure if it is the same problem I had, but the message was the same. Delete the content of ~home/.local/share/gnome-shell/extensions/ and reboot. This fix the problem for me.

---

### Post by NareZ on 2011-05-27
I'm pretty sure that 2 extensions, I have there, couldn't brake the system.
Anyway, I tried to move them somewhere else - didn't help.

---

### Post by Javad_Amiry on 2011-08-23
Hi. I'm new to forum :D and also to linux :D
I test all above issues and my problem not resolved! is there any suggestion to me?

---

