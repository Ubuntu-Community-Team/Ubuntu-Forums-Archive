---
title: "xfce removed, option still left in login screen"
date: 2005-04-24
forum: Desktop Environments
---

### Post by hashimoto on 2005-04-24
Hi guys,

I installed xfce just for testing and after playing with it for a while I decided to remove it. The problem is, in login screen I still have the possibility to select xfce session (though selecting it starts Gnnome). I was wondering how do I remove the option as it didn't get removed automatically.

Any hints appreciated.

---

### Post by Juippisi on 2005-04-24
Try removing the "xfce4.desktop" file located at "/usr/share/xsessions/"

---

### Post by hashimoto on 2005-04-24
[QUOTE=Juippisi]Try removing the "xfce4.desktop" file located at "/usr/share/xsessions/"[/QUOTE]
 Nope. Don't have that.

---

### Post by Juippisi on 2005-04-24
Try ls /usr/share/xsessions/ and look for xfce

---

### Post by hashimoto on 2005-04-24
[QUOTE=Juippisi]Try ls /usr/share/xsessions/ and look for xfce[/QUOTE]
 It's not there. All I have there is gnome.dekstop

---

### Post by Juippisi on 2005-04-24
Heh, this is getting to be interesting.

joonas@lokalhost:~ $ locate xfce4.desktop
/etc/dm/Sessions/xfce4.desktop
/usr/share/xsessions/xfce4.desktop


Look for there, I'm afraid that I can't help more :\.

---

### Post by hashimoto on 2005-04-25
All that I seem to find referring to xfce is:

/etc/menu-methods/xfce
/var/lib/dpkg/info/xfce.list
/var/lib/dpkg/info/xfce.postrm
/etc/gdm/Sessions/Xfce

Funny, since I removed using  --purge

/etc/gdm seems to be the most relevant regarding the option in login.
Which of these can I delete without problems?

---

### Post by tread on 2005-04-25
Well, just move the gdm to /tmp, and if you don't have any problems delete it :)

Edited to add: I mean the Xfce file in the gdm folder.

---

### Post by Juippisi on 2005-04-25
I would remove that /etc/gdm/Sessions/Xfce

But remember, if you can broke something, you can always fix that ;).

But if something really goes wrong, I bet that re-installing GDM would help to get the system back. I don't even have GDM, I run the X from TTY.

---

### Post by hashimoto on 2005-04-28
Tread, Juippisi,

Problem solved as poer your suggestions. Thanks for the input!

Vaasa kiittää!

---

