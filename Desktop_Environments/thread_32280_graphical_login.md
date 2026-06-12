---
title: "graphical login"
date: 2005-05-06
forum: Desktop Environments
---

### Post by Dave88 on 2005-05-06
This might sound like a really stupid question (and i'm sure it is), but a while ago I really messed up gnome and had use apt-get from the command line to re-install it. After that everything worked great only i lost my graphical login screen I use the command line now but I'd like to get a gui back. Any one how, I can do it with other distro's with gnome so i think i might have removed some package. can some one help??

thanks.

---

### Post by nad on 2005-05-06
sudo dpkg-reconfigure gdm . Or if you removed the gnome display manager or a file used by it, reinstall the gdm package.

---

### Post by Dave88 on 2005-05-06
Thanks alot nad, it was gdm that was broken.

---

### Post by crazybill on 2005-05-07
You might consider giving KDE desktop a try with the kbuntu flavor of ubuntu while you are changing things

---

### Post by Dave88 on 2005-05-07
I'ev used kde with suse and slackware and i liked it for a short time but i always get drawn back to gnome!

Anyway how do you go about kde for ubuntu, do I need to download kubuntu or can i use apt-get?

---

### Post by Ptero-4 on 2005-05-07
[QUOTE=Dave88]I'ev used kde with suse and slackware and i liked it for a short time but i always get drawn back to gnome!

Anyway how do you go about kde for ubuntu, do I need to download kubuntu or can i use apt-get?[/QUOTE]
 use apt-get install kubuntu-desktop.

P.D: Make sure you got Broadband. That package downloads the whole KDE (+100MB).

---

### Post by Dave88 on 2005-05-08
thanks, I'll give KDE ago.

---

