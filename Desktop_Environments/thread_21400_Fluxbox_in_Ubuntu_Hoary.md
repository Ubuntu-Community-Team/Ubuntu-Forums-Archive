---
title: "Fluxbox in Ubuntu Hoary"
date: 2005-03-22
forum: Desktop Environments
---

### Post by mario8723 on 2005-03-22
Anybody have Fluxbox in Hoary and, if so, how do I go about install it?

---

### Post by Heli0s on 2005-03-22
apt-get install fluxbox  8) 

( you have to enable univers in your /etc/apt/sources.list )

---

### Post by mthaddon on 2005-03-22
I'm assuming it's similarly easy for enlightenment?

---

### Post by bored2k on 2005-03-22
[QUOTE=mthaddon]I'm assuming it's similarly easy for enlightenment?[/QUOTE]
 For enlightenment you will need to get the latest apt repositories [d17 ones] . You can search in the forums for them [i think if you search for anyone enlightenment you will get it].

There is also a how to on this.

---

### Post by Carchidi on 2005-04-20
[QUOTE=Heli0s]apt-get install fluxbox  8) 

( you have to enable univers in your /etc/apt/sources.list )[/QUOTE]
 I've installed it using Synaptic, but then how do I invoke it in liu of Gnome?

---

### Post by Psquared on 2005-04-20
[QUOTE=Carchidi]I've installed it using Synaptic, but then how do I invoke it in liu of Gnome?[/QUOTE]

did you get E16 or E17? I think only E16 is in the repos unless you modify your sources.list. You can also download the tar.gz file and compile it.

I have not tried it yet, but E17 is supposed to be the best thing going - eye candy-wise. It has all new libraries.

Personally, I just prefer something that works so I stick with the DEs like Gnome, KDE and Xfce.

---

### Post by Psquared on 2005-04-20
Whoops, to invoke it you gotta log out (probably reboot so you restart X) and then select it as a session in GDM.

If it is not listed you will have to manually install the entry in ~/xsessions. Search for enlightenment on here and there is a thread that gives the exact instructions.

---

