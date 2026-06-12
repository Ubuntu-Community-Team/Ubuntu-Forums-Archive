---
title: "Ubuntu-netbook installed but not on the list of log in options"
date: 2011-08-07
forum: Desktop Environments
---

### Post by jonnyboysmithy on 2011-08-07
Hi, I have installed the package ubuntu-netbook and have followed the instructions on [http://ubuntuforums.org/showthread.php?t=1569926](http://ubuntuforums.org/showthread.php?t=1569926) 
The trouble is when Im at the logging screen I cannot choose the option to log in as ubuntu netbook, its just not on the list.



This is what I have in terminal:

jotham@jotham-desktop:~$ sudo apt-get install ubuntu-netbook
[sudo] password for jotham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-netbook is already the newest version.
The following packages were automatically installed and are no longer required:
  wine1.3-gecko galculator linux-headers-2.6.38-8 xscreensaver libgarcon-1-0
  pcmanfm xfce-keyboard-shortcuts tango-icon-theme libgarcon-common libfm-gtk0
  giblib1 libtumbler-1-0 linux-headers-2.6.38-8-generic libfm0 thunar-data
  gtk2-engines-xfce scrot libimlib2 xfdesktop4-data libexo-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jotham@jotham-desktop:~$ 

I have reinstalled the package but it didnt make a difference.

---

### Post by jonnyboysmithy on 2011-08-07
Anyone??

---

### Post by SalHelder on 2011-08-07
I don't think you can use ubuntu-netbook anymore, it has be deprecated. If you want the new "netbook" interface you'll need Unity, or KDE's plasma netbook.

---

### Post by jonnyboysmithy on 2011-08-07
I'm currently using 11.04, does that mean I need to install a different package?

ah of course it does but what package....

---

### Post by SalHelder on 2011-08-07
I guess you are already using Unity then. Just to be sure, you tried to look at the list of window managers after selecting the username (and before entering the password), right?

---

### Post by jonnyboysmithy on 2011-08-07
> **SalHelder said:**
> I guess you are already using Unity then. Just to be sure, you tried to look at the list of window managers after selecting the username (and before entering the password), right?
Yup already tried that, its not on the list.

---

### Post by SalHelder on 2011-08-07
If you still want an netbook interface you can try KDE's, but it's likely to be quite heavy if you are using an actual netbook, anyway:

sudo apt-get install kde-plasma-netbook

And if you are just looking for something more simple (and a bit uglier) try Lxlauncher, you'll just need to run it under Unity:

1. sudo apt-get install lxlauncher
2. Alt + F2 and type: lxlauncher

---

### Post by jonnyboysmithy on 2011-08-07
Thanks for that.
I'll try the lxlauncher..

I saw the ubuntu netbook on a friends pc and decided i wanted to try that looks really nice..

Is there any other way I can try the ubuntu netbook edition other than having to do a reinstall?

---

### Post by jonnyboysmithy on 2011-08-07
I still much prefer netbook i think than lxlauncher to be honest

---

### Post by SalHelder on 2011-08-07
You can still use it but you'll need to revert the system back to 10.04, because since 10.10 it started to use Unity instead of the netbook interface.

---

### Post by XubuRoxMySox on 2011-08-07
Unity is the new version of the old netbook-remix desktop. The netbook-remix desktop is obselete in Natty.

But if you use the LTS version (10.04), it is downloadable from the repos and selectable as a session.

-Robin

---

### Post by jonnyboysmithy on 2011-08-07
> **SalHelder said:**
> You can still use it but you'll need to revert the system back to 10.04, because since 10.10 it started to use Unity instead of the netbook interface.
I'm confused. so your saying that you can't install netbook since they switched to unity?

---

### Post by SalHelder on 2011-08-07
It's more like it was upgraded, from now on there's Unity which is the replacement (upgrade), as we said you can try the 10.04 and use the old netbook interface.

---

### Post by jonnyboysmithy on 2011-08-07
sorry but I think I'm missing something, so whats the difference between ubuntu netbook and netbook-remix

---

### Post by SalHelder on 2011-08-07
Here are the answers you need: [http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition)

Anyway, answering your question ubuntu netbook remix and netbook edition are the same thing.

---

### Post by jonnyboysmithy on 2011-08-07
That answers my questions thanks!
@robin love your [How I Discovered Linux]("http://robinsrantsandraves.wordpress.com/2011/07/14/how-i-discovered-linux/")

---

### Post by XubuRoxMySox on 2011-08-07
> **jonnyboysmithy said:**
> That answers my questions thanks!

**[COLOR="Purple"]Yay![/COLOR]** Be sure to mark this thread as **SOLVED** so others with the same question can quickly follow it to the answer.

Find your first post and choose Edit, then Go Advanced, and change the Subject line, adding [SOLVED] to the front.

Thanks!

-Robin

---

