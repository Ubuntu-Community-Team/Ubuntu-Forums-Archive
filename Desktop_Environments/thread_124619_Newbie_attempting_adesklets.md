---
title: "Newbie attempting adesklets"
date: 2006-02-01
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-02-01
I have been having a great time learning ubuntu.  I cant believe how much reading I have had to do lately this last month.  LOL....

I have been using gdesklets, pretty simple to install and use.

But I really like the looks of some of the adesklets.  I am kinda confused....can adesklets be used in gnome on ubuntu or is it for KDE only?

I have installed the .48 version via Synaptic, but I am now lost.

I downloaded the system monitor, extracted it...and then put it in my directory I created called desklets...then inside there it is in its own folder.

so I go to that directory via a terminal session....and yes here is where I know I sound really stupid...I get this error and I have no clue what it means.

There is not much information for a noob like myself on how to install this stuff and use it....

I am pasting what I got for output below.  Can anyone please explain adesklets in more noob terms, or point me to a post or website somewhere because I cant find one.  The adesklets site isnt real comprehensive, or I am just a dunce....

anyway....here is my output I got...

papawiskas@tmslaptop:~$ cd desklets
papawiskas@tmslaptop:~/desklets$ cd Sys*
papawiskas@tmslaptop:~/desklets/SystemMonitor-0.1.3$ dir
config.txt   COPYING               images  SystemMonitor.py
config.txt~  example_theme.tar.gz  README
papawiskas@tmslaptop:~/desklets/SystemMonitor-0.1.3$ ./SystemMonitor
bash: ./SystemMonitor: No such file or directory
papawiskas@tmslaptop:~/desklets/SystemMonitor-0.1.3$ ./SystemMonitor.py
Traceback (most recent call last):
  File "./SystemMonitor.py", line 43, in ?
    import statgrab
ImportError: No module named statgrab
papawiskas@tmslaptop:~/desklets/SystemMonitor-0.1.3$

---

### Post by PapaWiskas on 2006-02-02
I went back to their website and I still cant figure out what I did wrong.  I have uninstalled and reinstalled adesklets via synaptic twice now.

If anyone could explain this to me I would be very appreciative.  Anyway, I am going to go get another cup of coffee and see if I can figure out what I am doing wrong.

---

### Post by taurus on 2006-02-02
I don't know exactly what SystemMonitor does but apparently, it looks for something from your system that you don't have running, statgrab.  So, you can either look at the python script for SystemMonitor.py (line 43) to figure out what it calls or you can also go wth gdesklets.  It has far more applets available for you from its website at [http://gdesklets.gnomedesktop.org](http://gdesklets.gnomedesktop.org) and you can install gdesklets with apt-get.  I use it in Gnome right now.

---

### Post by PapaWiskas on 2006-02-02
I use gdesklets now, but i wanted to learn more and try out my choices.

The documentation for adesklets is not really for noobs like myself, and I dont want to give up, I really want to learn this stuff.

I really am thankful there are alot of patient people around here....

---

### Post by andlinux21 on 2006-02-05
i installed adesklets and tried to run it from xterm **adesklets** nothing happened so I take it this is not like gdesklets and starts some type of application??:confused:

---

### Post by PapaWiskas on 2006-02-05
[QUOTE=andlinux21]i installed adesklets and tried to run it from xterm **adesklets** nothing happened so I take it this is not like gdesklets and starts some type of application??:confused:[/QUOTE]


Its supposed to be like gdesklets, but I cant figure out how to get it to work.

The documentation is not geared to Linux idiots like me.  I will figure it out eventually, when I get more time.  Right now I am busy learning other stuff than to concern myself to much with it.

---

### Post by taurus on 2006-02-05
You're supposed to run the python script of whatever applet you plan to use first.  Then the next time you run adesklets, adesklets will start that applet for you automatically...

---

### Post by syfou on 2006-02-06
[quote="me, on top of the desklets download page"]
To use a given desklet, download and extract it, **see the README** and follow the instructions
[/quote]
All the dependencies for a given desklets are given in the README. Yours,

__
Sylvain

P.-S. At the time of writing, adesklets 0.4.8 is almost height months old... There are other .debs [floatting around](http://louis-nichols.uv.ro/adesklets_0.5.0-1_i386.deb) for Breezy that are much more up to date...

---

### Post by raul_ on 2006-10-09
You were trying to use the SystemMonitor without the dependencies installed...just open synaptic, search for statgrab and install them all :P

U can't just start adesklets with the command "adesklets". I'll assume u're on gnome so try "adesklets --nautilus" , and u must have ur desklets registered (test won't work, just to check for errors)

---

### Post by Gio2k on 2006-10-10
Something weird is happening to me. I always get some kind of command prompt when i try to  start  adesklets. Aynone knows how to fix this?

```

sergio@sergio-laptop:~/desknotes-0.0.1$ adesklets --nautilus
adesklets 0.6.1 (Wed Oct 4 22:39:23 CEST 2006), on Linux 2.6.15-27-686
[gcc 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
Press TAB for hints.
0 >>>

```

---

### Post by raul_ on 2006-10-10
do u have any desklets installed? just curious...

---

### Post by raul_ on 2006-10-10
i used to get this error when i tried to run "adesklets -i" and my version didn't support it...so i'll have to guess that u're using a window manager that's not nautilus, but that's a little odd...i can't think of anything else.
Are u using Gnome?

---

### Post by NeoLithium on 2006-10-11
Check [here]("http://packages.debian.org/unstable/source/adesklets") for a list of required headers; search for them through apt or synaptic (DON'T install them from that site though); remove the config files from adesklets install, then recompile and make it.

I ended up double checking; and had a few headers missing that didn't allow everything to work perfectly. Now it's all nice and easy.

Hope it helps.

---

### Post by AlesUbu123 on 2007-09-02
To make SystemMonitor adesklet work in ubuntu, please install python-statgrab from synaptic. This worked for me.

---

