---
title: "How do I take a screenshot?"
date: 2006-01-23
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-23
I have used many distros and am currently running Ubuntu 5.10. I have created some new GDM login screen themes and wish to make a screenshot to include in my new themes. In the past, I have used the following at tty1 to get a screenshot of the gdm login screen:

```

chvt 7; sleep 5; XAUTHORITY=/var/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/gdm-shot.png

```

this works on most othe distros but that does not work in Ubuntu. How do I take a screenshot of the gdm login screen on Ubuntu 5.10? What is the proper syntax?

---

### Post by manicka on 2006-01-23
[http://doc.gwos.org/index.php/GDM](http://doc.gwos.org/index.php/GDM)

About half way down the page is what you need

---

### Post by manicka on 2006-01-23
[http://doc.gwos.org/index.php/GDM](http://doc.gwos.org/index.php/GDM)

about half way down the page is what you need

---

### Post by GeneralZod on 2006-01-23
I don't know the "correct" way to do this, but I use this to dump a png to standard output:

```

xwd -root | xwdtopnm | convert  -  png:-

```

---

### Post by ardchoille on 2006-01-23
[QUOTE=GeneralZod]I don't know the "correct" way to do this, but I use this to dump a png to standard output:

```

xwd -root | xwdtopnm | convert  -  png:-

```[/QUOTE]
and that works from tty1 to get a screenshot of the gdm login screen on tty7 ?

---

### Post by GeneralZod on 2006-01-23
Ah, whoops - I didn't read that part of your post.  Sorry!

---

### Post by aysiu on 2006-01-23
[QUOTE=manicka][http://doc.gwos.org/index.php/GDM](http://doc.gwos.org/index.php/GDM)

About half way down the page is what you need[/QUOTE] That's awesome! I'm bookmarking that. Thanks, Manicka.

---

### Post by ardchoille on 2006-01-23
[QUOTE=manicka][http://doc.gwos.org/index.php/GDM](http://doc.gwos.org/index.php/GDM)

About half way down the page is what you need[/QUOTE]
manicka, thank you very much. The problem was that I was using "XAUTHORITY=/var/gdm/" in my command instead of "XAUTHORITY=/var/lib/gdm/", at least I think that was the problem. I had the path wrong. But that link you posted worked great :)

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=ardchoille]I have used many distros and am currently running Ubuntu 5.10. I have created some new GDM login screen themes and wish to make a screenshot to include in my new themes. In the past, I have used the following at tty1 to get a screenshot of the gdm login screen:

```

chvt 7; sleep 5; XAUTHORITY=/var/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/gdm-shot.png

```

this works on most othe distros but that does not work in Ubuntu. How do I take a screenshot of the gdm login screen on Ubuntu 5.10? What is the proper syntax?[/QUOTE]

Have you tried using the "-display" switch on the import command instead of manually tring to set the variable?

---

