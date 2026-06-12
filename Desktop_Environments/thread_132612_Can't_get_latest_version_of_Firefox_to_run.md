---
title: "Can't get latest version of Firefox to run"
date: 2006-02-18
forum: Desktop Environments
---

### Post by imwalrus on 2006-02-18
Hi. I'm a newbie. Just installed Breezy Badger, and everything is up and running smoothly, including getting my wireless USB adapter to work. 

I downloaded Firefox 1.5.0.1. I used the following command to install from terminal: tar -xzvf fireox-1.5.0.1.tar.gz. I didn't notice any error messages, and I now have a new Firefox folder in my home directory. I opened the folder, and double-clicked on the firefox.sh file to try to start Firefox. I was presented with 4 options - I chose Run. Nothing happened. So, I went to a terminal, entered the Firefox folder, and typed in ./firefox (There are 2 firefox files here - firefox (which is the .sh file), and firefox-bin. I get the following error message: ./firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.

To make matters more interesting, I tried to download and install Real Player, and I got the same error message when trying to run the Real Player .bin file. 

Any ideas??

Thanks!

---

### Post by cilynx on 2006-02-18
Since you're new to the game, you'd be safer to stick with the Ubuntu distributed versions of software until you're more comfortable with what you're doing.

To the best of my knowledge, Firefox is installed by default.  If you don't have it, go to Applications -> Add / Remove and you'll find Firefox under Internet.

As for realplayer, I'm not a fan so I don't have it installed and thus can't tell you how I did it.  However:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

That site was made for 5.04, but the information scales forward pretty easily.  Just substitute 'breezy' for 'hoary' and it generally works.  Use common sense.

To actually answer your question:

The error that you got is telling you that the version of Firefox that you downloaded was built to be run on a different set of Stardard C Libraries than the ones you have.  Again, this is well beyond the scope of the casual desktop user.

Good Luck

---

### Post by aysiu on 2006-02-18
I, too, would advise sticking with the native Ubuntu 1.0.7 until you get more comfortable with how Ubuntu specifically and Linux in general work.

However, a couple of things to know right away:

1. If you're going to install 1.5, use these directions: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

2. Once you've installed it properly, you can type ```
firefox
``` to launch it. You shouldn't need to type ```
./firefox
```

3. Part of those instructions are to install the libstdc++.so.5 you're missing.

---

### Post by Lord Illidan on 2006-02-18
[quote=cilynx]Since you're new to the game, you'd be safer to stick with the Ubuntu distributed versions of software until you're more comfortable with what you're doing.

To the best of my knowledge, Firefox is installed by default.  If you don't have it, go to Applications -> Add / Remove and you'll find Firefox under Internet.

As for realplayer, I'm not a fan so I don't have it installed and thus can't tell you how I did it.  However:

[http://ubuntuguide.org/]("http://ubuntuguide.org/")

That site was made for 5.04, but the information scales forward pretty easily.  Just substitute 'breezy' for 'hoary' and it generally works.  Use common sense.

To actually answer your question:

The error that you got is telling you that the version of Firefox that you downloaded was built to be run on a different set of Stardard C Libraries than the ones you have.  Again, this is well beyond the scope of the casual desktop user.

Good Luck[/quote]

The UbuntuGuide is out of date. Use this link : [UserDocumentation - Ubuntu Wiki]("https://wiki.ubuntu.com/UserDocumentation")

---

### Post by imwalrus on 2006-02-18
Thanks to everyone for their replies. One of the reasons I chose Ubuntu was for the active and helpful support community. I ended up doing the following: sudo apt-get install libstdc++5, to install the C Library that I needed. Now, Firefox 1.5 works, and I was able to install RealPlayer with no problems. I appreciate all of you helping me to learn more about Ubuntu/Linux...

---

### Post by s_h_a_d_o_w_s on 2006-02-18
If you want an easy way to install the newest firefox with all plug-ins, and more interesting programs with the click of a button, you should install automatix. You just press what you want and it automatically installs.thats it.

Here how: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

it's so simple

---

### Post by imwalrus on 2006-04-10
I know it's been almost two months since this post, but I wanted to let you know that I tried Automatix, and think it's incredible! Everything I could want, and more. And as easy as it gets. Thanks so much!

---

