---
title: "Google Calendar on the desktop"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by Kourosism on 2007-11-15
Hello,

Firstly, I'm loving 7.10. It's the first release that has had WiFi working 'out of the box,' and, well, it's just so pretty. The desktop is frankly gorgeous and I love the effects brought through with Compiz, even if they can be a bit hicuppy.

What I would really like to do, though, is potentially really rather simple but I've not found a sensible way of doing it yet. I've seen gOS and I like the desktop links to gMail and Google Calendar - two apps I use quite a lot.

What is the easiest way to add these to the desktop - should I be using a launcher bar? I'd like to keep both existing taskbars if I can, as I find them both kinda useful.

Best recommendations?

---

### Post by Espreon on 2007-11-15
The best way to run Web apps as Desktop apps is to use Mozilla Prism. Right know its just runs web apps as a Firefox window with no location bar or any of that but Prism is going to be able to do many amazing things in the future.

I wil make a Prism installation script when I get home.

---

### Post by keithacole on 2007-11-15
this is great, i use google notebook, and have my gmail contacts setup nicely, so this will be a great addition to my setup

---

### Post by Espreon on 2007-11-15
But in the meantime heres how to install Prism:

To install Prism:

1. Enter this in the terminal:

```

sudo wget http://people.mozilla.com/~mfinkle/prism/prism-0.8-linux.tar.bz2 -O /opt/prism.tar.bz2

```

2. Run Nautilus in root mode by entering  .

```

sudo nautilus

```

3. Browser to /opt

4. Extract the file you downloaded

5. Close Nautilus and enter this in the terminal:

```

alacarte

```

6. Then make a new menu item (in whatever category you desire) and use whatever icon you desire the Prism icon is in either /usr/share/pixmaps or in /opt/prism/xulrunner (it looks like the FF logo with out the Firefox).

7.Enjoy

---

### Post by keithacole on 2007-11-15
i had to wget without the options then move it over to the /opt directory. but its working fine. thanks:guitar:

---

### Post by Espreon on 2007-11-15
Your welcome, I corrected the wget line though.

---

### Post by Kourosism on 2007-11-16
Wow. Thanks for this. I'm at work and on an XP amchine at the moment, but will give this a go this evening.

---

### Post by Kourosism on 2007-11-16
It works a treat, thank you.

---

### Post by Espreon on 2007-11-16
Your welcome

---

### Post by jnylen on 2007-11-16
Also worth mentioning is Rainlendar.  The free version doesn't support Google Calendar, but the Pro version does.  It's a little finicky on Linux, but you'll want to go get version 2.2 beta 48 (there are also beta 49 and 50 but I haven't tried them yet).

---

