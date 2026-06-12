---
title: "How to install Firefox in Debian"
date: 2008-11-08
forum: Debian
---

### Post by frank.zappa on 2008-11-08
I just installed Debian in a virtual machine to test it out and I noticed that instead of Firefox, it uses Iceweasel. I've tried some things on blog sites that tell me how to install it but I could not understand.

Could someone tell me how to install Firefox 3?

---

### Post by benerivo on 2008-11-08
Well iceweasel is pretty much identical. The only difference i've noticed is the name of the program. See [here]("http://en.wikipedia.org/wiki/Iceweasel"). If you want it to say firefox, then just [download the package from mozilla]("http://www.mozilla.com/en-US/firefox/"), extract it and put the extracted firefox folder in your home folder. Inside this folder is a file called firefox, which opens firefox when you run it.

---

### Post by frank.zappa on 2008-11-08
But I also want it to show up in the menu - shouldn't it be installed somewhere in /usr/bin? Also, will this make it the default internet browser?

---

### Post by lukjad on 2008-11-08
Just a question, can't you do everything you can with Firefox with Iceweasel?

---

### Post by benerivo on 2008-11-08
You can add it to the menu yourself by editing the menu (right click on it). To make it the default browser just include it in System > Prefs > Preferred  Applications (a menu entry alone won't make it the default).

---

### Post by frank.zappa on 2008-11-08
I can, but in Iceweasel, there's a wierd 'bug' in which when I scroll all the to the top or bottom of a page, it'll take me to the previous or next page. I just find it annoying and prefer Firefox.

Edit: So where should I unextract it? (as in preferred location for applications in Linux) ex. In windows, when a program is just packaged as a .zip, I'll extract it to C:\Program Files\'Program Name'\ and create the necessary shortcuts in the start menu.

---

### Post by lukjad on 2008-11-08
Ah, okay. I was just wondering.

---

### Post by benerivo on 2008-11-08
> **frank.zappa said:**
> So where should I unextract it? (as in preferred location for applications in Linux) ex. In windows, when a program is just packaged as a .zip, I'll extract it to C:\Program Files\'Program Name'\ and create the necessary shortcuts in the start menu.It doesn't matter, as you'll not be installing it. I would put the extracted folder in your home directory. (you may as well apt-get purge iceweasel if you are not going to use it).

---

### Post by frank.zappa on 2008-11-08
I'm guessing apt-get purge will remove iceweasel?

Just wondering, is the default location for program installations /usr/bin ?

---

### Post by benerivo on 2008-11-08
> **frank.zappa said:**
> Just wondering, is the default location for program installations /usr/bin ?

Yes, most things get installed there.

---

### Post by lukjad on 2008-11-08
It might, but I would wait a bit. I always found that using Firefox in a folder to be very annoying. First you need to go to the /home folder and find the /firefox folder, then find the correct file to double click and then choose Run. It's a hassle. Keep iceweasle for a while to see if you want it back.

---

### Post by frank.zappa on 2008-11-08
Yeah, I'll keep iceweasel until I'm sure I don't want it. If I make a shorcut of Firefox in the main menu and make it the default web browser, will it still ask me to "run, display, etc" when I select the shortcut?

And I noticed the fie is named "Firefox.sh" is this the '.exe' for Linux?

---

### Post by benerivo on 2008-11-08
You don't need to go through the questions to launch it. Just use the shortcut```
/home/bobby/firefox/firefox
```when making a menu item or icon.

---

### Post by lukjad on 2008-11-08
I had some trouble making a short cut, but maybe that was just me.

---

