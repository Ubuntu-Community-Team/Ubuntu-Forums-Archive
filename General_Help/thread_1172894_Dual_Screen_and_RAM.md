---
title: "Dual Screen and RAM"
date: 2009-05-29
forum: General Help
---

### Post by xelasha on 2009-05-29
Hi All.
Recently have been getting into Linux, I have tried a few distros and I think I have settled on Ubuntu. Been learning a bit here and there as I have been using it as my main OS and Vista as my gaming OS.

I currently have the following setup:
C2Q Q9550 @ 2.8ghz
6GB 800mhz RAM
EP45-DS3R Gigabyte motherboard
ATi Radeon HD4870 1GB
And 2 17" Samsung Syncmaster monitors (Syncmaster 171S & Syncmaster 740N)

I want to have a dual screen setup, Now my defualt both monitors are showing the same thing.
How do you make it so it is an Extended monitor?

And my second problem is why is Ubuntu only reading 3.2GB of my RAM?

Sorry if these are noob questions, But I am pretty newbish with Linux at the moment.

---

### Post by zeker446 on 2009-05-29
you should install ubuntu x64 to get use of more than ttheoretically 4GB, but due to system restrictions you only get using about 3.xx gb, só install x64 and theres no problem

---

### Post by xelasha on 2009-05-29
Is there a separate x64 version that I have to download, or are both implemented in the Live CD?

Also, Thanks for the quick reply lol.
Now all I have is my dual screen problem.

Also , I will install the x64 version. But is there any way to bring over a few features that I have installed? Because I just got Compiz and a few other plugin's just the way i wanted :P.

-xel.

---

### Post by xelasha on 2009-05-29
*bump*

---

### Post by Ansraliant on 2009-05-29
You need to enable dual-screen support on your ati.
For that write in terminal:

```

sudo aticonfig --xinerama=on

```

I think it was like that, I do not remember clearly right now. If it didn't work, write in terminal:

```

aticonfig --help

```

And search for xinerama.
Good Luck!. If you couldn't solve your problem, just post again.

---

### Post by xelasha on 2009-05-29
Ok so i KINDA have it working.

In the Display Manager I have both monitors set as Single (Independent display) , I only have that option and an "unknown" option which clones the screens.

Now I can set ONE of the screens to the preferred resolution, But the other screen is stuck around 800x600 and I can't find a way to change it.

EDIT: Nevermind fixed it.

How: 
I turned xinerama back off, Had both monitors set to "Single (Independent display)" and was able to change the resolution of both in the ATi control panal. Then i turned xinerma back on and both monitors stayed at the same resolution but xinerama was working.

Thanks for the help guys. Too bad there isn't a rep system.

---

