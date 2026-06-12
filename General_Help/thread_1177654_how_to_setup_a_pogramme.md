---
title: "how to setup a pogramme"
date: 2009-06-03
forum: General Help
---

### Post by moham3d on 2009-06-03
[B][SIZE=6][COLOR=Red]hi 
i want to install some important programmes like unrar. filezilla.realplayer...
can you please tell how to realaze it using only by using " terminal " 
 [/COLOR][/SIZE][/B]

---

### Post by celticbhoy on 2009-06-03
The first step would be to use apt-get, ie -

sudo apt-get unrar

---

### Post by lisati on 2009-06-03
Wow! that's loud!

But seriosuly, apt-get and aptitude would probably be two tools to check out for installing stuff from the command line.

---

### Post by scratman on 2009-06-03
I would also suggest typing things correctly.  Spelling mistakes can make for an interesting time if you insist on using the terminal.  Synaptic Package Manager and Add/Remove would probably be better for you.

---

### Post by John.Michael.Kane on 2009-06-03
First make sure all the proper repositories are enabled.
[Adding Repositories in Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Next you would search though synaptic for the software you want, or install via the terminal.

```
sudo aptitude install unrar filezilla filezilla-common
```

For realpalyer there is a deb file you can use.
```
wget http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb

```

There is also the below repository.
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by moham3d on 2009-06-04
[SIZE=6]Thank you for your responses[/SIZE]

---

