---
title: "nuatilus-sendto missing evolution email option"
date: 2011-04-05
forum: Desktop Environments
---

### Post by dre12b on 2011-04-05
I'm running a fully updated version of natty beta 11.04.

The nautilus sendto dialog avaiable from the right-click menu is working normally, but doesn't include the evolution "send to email" option.  I have evolution installed and it's working normally.

Anyone else experiencing this or have any ideas as to how to pursue a fix?

---

### Post by anishman on 2011-04-05
I'm running in Gnome classic mode under Natty beta1 and I'm having the same issue here with the missing Evolution.  
Only BlueTooth and Empathy** sendto** options are
available,_ even though the Nautilus sendto plug-in is definitely installed_.   (??)

---

### Post by makro on 2011-04-28
same issue here Natty amd64

---

### Post by johanPO on 2011-04-30
Me too, also in classic mode

---

### Post by ububot on 2011-05-01
Looks like nautilus-sendto is trying to use older versions of libraries. Running the following fixed it for me:

sudo ln -s /usr/lib/libebook-1.2.so.10 /usr/lib/libebook-1.2.so.9

sudo ln -s /usr/lib/libedataserver-1.2.so.14 /usr/lib/libedataserver-1.2.so.13

---

### Post by johanPO on 2011-05-02
Perfect, thanks!

---

### Post by jfabrizio on 2011-05-03
Great, it works rightly!

---

### Post by bhohe on 2011-05-04
yeah thanks and it also works with thunderbird

---

### Post by B Crowther on 2011-05-07
Once again I am stunned by somebody else's brilliance! Thank you for this fix, Ububot.

---

### Post by ziccho on 2011-05-10
It totally works, I don't know how to thank. You are great.

---

### Post by JDailey on 2011-05-12
But how do I add Skype to those options?

---

### Post by NJC on 2011-05-12
> **ububot said:**
> Running the following fixed it for me:

sudo ln -s /usr/lib/libebook-1.2.so.10 /usr/lib/libebook-1.2.so.9

sudo ln -s /usr/lib/libedataserver-1.2.so.14 /usr/lib/libedataserver-1.2.so.13
Thanks very much - indeed this worked too for Thunderbird. Why is this option omitted though in Ubuntu 11.04?

---

### Post by ctijacob on 2011-06-16
I've tried this and it's not working for me. I'm running Gnome 3, is there something else needed, perhaps?

---

### Post by aeklabunde on 2011-07-30
I have the option for "send to..." "email" but it does nothing.  My evolution window tab (I use Ubuntu classic instead of unity) becomes bold, but no other action is performed.  I guess I am used to the functionality of Picasa for sending pictures via email, and will probably have to switch back.  I was just really hoping to get away from using too much non-linux stuff on this clean install of Natty.

If anybody has a fix for this, or can recommend a linux photo manger with an all-around better email option, please let me know!

---

