---
title: "Ubuntu Compwiz problems - i think"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by klain on 2007-12-11
My normal expeirence is with windows as a good majority of the population

however for various reasons i have decided to move to linux but have found the following problems baring in mind i new to everything here.

Ubuntu (64-bit) doesn't seem to work with my graphics card as it won't enable effects it goes out and attempts it then goes back in.

I then thought graphics drivers, i have a 7600gs nvidia sli card and honestly couldn't get as far as installing them so i still don't know if thats the problem.

All i wan't is that compwiz cube effect working!

I expect this may all be a silly post and easily fixed and i'm just being a dumbass.

Every time i try to "fix" everything i mess up the x- server (and i don't know how to restore it).

I have run out of all ideas.

If anyone could help it would be greatly appreiated.:)

---

### Post by sowelie on 2007-12-11
It sounds like you don't have the right driver installed.  The easiest way to get a good driver installed for 3d support is to execute the following command:
```
sudo apt-get install nvidia-glx-new
```
After that you should be able to use desktop effects.

---

### Post by klain on 2007-12-12
Sorry, I didn't mention,

But my X-server? has messed up i think i gave it the wrong driver now i have weird symbols all over the place, later i get to the console.

i tried what you said but the download just timed out

how can i repair my x - server and get the driver re-installed?

I have only used windows in the past, i'm only moving to linux so i can have the best of both worlds.

But so far i'm not impressed this seems so dificult to just install a driver and install the correct software its really frustrating.

---

### Post by sowelie on 2007-12-12
Don't let this one experience ruin the whole thing for you. The operating system is very well built and generally behaves well.  However, with advanced features like compiz, there are complications.

What you want to do is get your x server back up.  You'll want to get to the console and edit the xorg.conf.  Paste what you have in that file here and I can help you from there.

```
sudo pico /etc/X11/xorg.conf
```

---

### Post by klain on 2007-12-16
Hi,

Thanks for your help,

this is all i get though:

[http://img520.imageshack.us/img520/6351/29919997ih0.jpg](http://img520.imageshack.us/img520/6351/29919997ih0.jpg)

---

