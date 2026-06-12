---
title: "Configuring CUPS without GNOME nor KDE"
date: 2005-11-23
forum: Desktop Environments
---

### Post by jmpetit on 2005-11-23
Hello to every body,

I'm new at using Ubuntu (although not new at using Linux :-), and I'm stuck trying to configure CUPS.

I'm running Ubuntu 05.10, which I installed as a server, then I used:
apt-get install xubuntu-desktop
to get Xorg and Xfce4.

Now, how do I configure CUPS ? From the FAQs, HOWTOs, and other documentation, I should use the CUPS Web administration page. But this page says this feature has been disabled, and I should use the Menu System > Administration > Printing under GNOME, or something similar under KDE. I'm running neither of these, and I can't find anything similar in XFCE.

Please help.

Regards, Jean-Marc Petit

---

### Post by ubuntu_demon on 2005-11-24
I moved your thread. Please don't put any questions in the customization forum!

---

### Post by Xappe on 2005-11-24
hmm, if I remember correctly you can enable the web interface by editing  /etc/cups/cupsd.conf

---

### Post by Xian on 2005-11-24
[QUOTE=jmpetit]From the FAQs, HOWTOs, and other documentation, I should use the CUPS Web administration page. But this page says this feature has been disabled...[/QUOTE]
This is specific to Ubuntu for whatever reason.
You first have to set a root password.

$ sudo passwd root

Then goto [Linux Printing System](http://127.0.0.1:631/)

---

### Post by metoo on 2005-11-25
It's a PITA that they did that. You used to set a cups password but now it is even more difficult.

I had a hard time with it so the following is not a direct hit, but might get you going:

As mentioned in a previous post you have to edit /etc/cups/cupsd.conf:

1) Check the ServerName close to the top of the file. This must be your hostname, not cupsy.

2) If that's not doing the trick try setting (in same file):
<Location /admin>
#AuthType Basic
#AuthClass System
(This might disable admin authorization all together, your choice)

re-start cups:
sudo /etc/init.d/cupsys restart

---

