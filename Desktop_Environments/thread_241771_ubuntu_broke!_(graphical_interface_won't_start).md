---
title: "ubuntu broke! (graphical interface won't start)"
date: 2006-08-22
forum: Desktop Environments
---

### Post by JohnJSal on 2006-08-22
Hi everyone. Big problem here. I restarted my computer just now and after Ubuntu finished booting up, it went to a blue/grey screen (very old school DOS looking) and said something about not being able to start up the X server (graphical interface). After choosing "Yes" to see the error info (which I couldn't really read), it took me to one of the first six terminals (i.e. non-GUI). Luckily ctrl-alt-del reset even in the terminal, so I'm back in Windows wondering what's going on.

Hope someone can help!

---

### Post by Bubbles on 2006-08-22
Same here.  Yesterday some Xorg updates came through the update notifier.  I downloaded and installed, but didn't restart until just now.  The X server no longer starts up.  The error it gives is "Cannot find device."

---

### Post by sisooktom on 2006-08-22
Guys honestly I don't normally post responses like this, but there are already several very large threads on this same problem.  Save yourself and everyone else some time and look before you post ;)

---

### Post by diablozx9 on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)


worked for me........

---

### Post by Toxicity999 on 2006-08-22
Indeed, keep an eye out on the main Forum page near the top there's a box with important announcments pointing you to a thread to take care of this...

---

### Post by JohnJSal on 2006-08-22
Thanks guys, and sorry for not checking first. But I'm a little confused by the sticky post. It says to type the following code, and it has this line twice:

```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb

```

Then it has this line after it, but I don't understand if I'm supposed to type this as well:

```
sudo dpkg -i xserver-xorg-core*.deb
```

---

### Post by sefs on 2006-08-22
> **JohnJSal said:**
> Thanks guys, and sorry for not checking first. But I'm a little confused by the sticky post. It says to type the following code, and it has this line twice:

```
wget -c http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb

```

Then it has this line after it, but I don't understand if I'm supposed to type this as well:

```
sudo dpkg -i xserver-xorg-core*.deb
```


If you check carefully i believe what you think is the same line twice are actually two diffent lines but the diffrence is very subtle...one says xserver-xorg-core and the other says xserver-xorg-dev or something like that if my mind serves me correctly from looking at them this morning.

---

### Post by JohnJSal on 2006-08-22
So does that mean I have to run all three lines?

---

### Post by sisooktom on 2006-08-22
A new version of the broken package was released today. You should just be able to apt-get update and apt-get upgrade to fix it.

---

### Post by K.Mandla on 2006-08-22
I updated about two hours ago and got the 10.4 (or whatever) version, which was corrected. I think 10.3 (or whatever) is the faulty one.

If it's still acting broken, you might try *sudo aptitude remove --purge xserver-xorg-core*. You'll get the option to downgrade to 10.2 (or whatever), and that was the earlier, stable version.

---

### Post by Bubbles on 2006-08-23
> **Toxicity999 said:**
> Indeed, keep an eye out on the main Forum page near the top there's a box with important announcments pointing you to a thread to take care of this...

I did a search straight from the Dapper Drake subforum page and therefore saw no "sticky threads" as they are not posted in search results.  This is the thread I ended up on as a result of the search.  Really, I missed nothing.  Starting point here:  [http://www.ubuntuforums.org/forumdisplay.php?f=130](http://www.ubuntuforums.org/forumdisplay.php?f=130) (from my URL location bar history cache) and I subsequently landed on this thread.

Maybe the alert should've been on *every* page.

---

