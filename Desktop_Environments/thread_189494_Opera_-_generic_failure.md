---
title: "Opera - generic failure"
date: 2006-06-05
forum: Desktop Environments
---

### Post by rudyszympans on 2006-06-05
So... I'm trying to launch Opera in my Ubuntu Dapper 6.06.

I have a tiny problem here. I used Automatix to install Opera.

When I write "opera" in the console it shows:
"opera: Preference initialization failure. Generic failure (-1)"

I removed Opera from "add/remove programs" and added it the same way (add/remove)
It didn't work

so... I wrote in console:

wget [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb) 

sudo dpkg -i xlibs_6.8.2-77_all.deb

sudo gedit /etc/source.list 
(add deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) unstable non-free)

After that I update my system and downland the new opera beta.

In console:
"opera"

and again, that's what I get:
"opera: Preference initialization failure. Generic failure (-1)"

I need a little help with this. ](*,)

---

### Post by Blur-king on 2006-06-05
I had same similar problem with Automatix which promted me that it cannot retrieved the opera file. I just download from opera.com and install the deb file via a terminal and it it works fine for me..... After it is install you have go to apllication---internet and launch the opera from there. You can add the launcher to the panel by right clicking it..Hope it works for you.

---

### Post by Mike_N on 2006-06-05
Back on Breezy, i got Opera by downloading the .deb file from Opera.com and running it, it asked for some dependencies but Synaptic found them for me, i think...

---

### Post by rudyszympans on 2006-06-05
Hmm... you know, the problem is "opera: Preference initialization failure. Generic failure (-1)"

---

