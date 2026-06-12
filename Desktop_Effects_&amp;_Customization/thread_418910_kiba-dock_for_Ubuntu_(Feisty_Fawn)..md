---
title: "kiba-dock for Ubuntu (Feisty Fawn)."
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by EverHardy on 2007-04-22
Hi EveryBuddy

I'm using Ubuntu (Feisty Fawn) + Beryl + AIGLX + Avant Window Manager. But I want to use kiba-dock instead.

I'm struggling to install kiba-dock on my system. I've tried to install .deb versions available online, but I don't see any windows minimized to kiba-dock. Is it because of avant present already ? I tried using kiba-dock  only, even then no luck.

Please help me install kiba-dock.

with regards
EverHardy

---

### Post by Muppeteer on 2007-04-26
This is how i installed it

(Taken from kiba-dock website)

   1.  Open a Terminal Window.
   2. Type the following:

```
sudo gedit /etc/apt/sources.list

   1. Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins
```

Then press Alt + F2 and type kiba-dock and it should work :)

---

### Post by russell.h on 2007-04-27
Is there a way to make that work in 64 bit? I can only seem to find like 3 packages in the 64 bit version of those repos.

---

### Post by EverHardy on 2007-04-28
I tried to follow the above mentioned instructions to install kiba-dock. This is what I get in terminal.
-----------------------------------
Upto sudo apt-get update, everything went fine, but,

sudo apt-get update  (shows following)

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2)  MD5Sum mismatch

and

sudo apt-get install kiba-doc  (shows following)

Package kiba-dock is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kiba-dock has no installation candidate

----------------------

Pleaes help me solve this problem.

with regards
EverHardy

---

### Post by kgriffin on 2007-04-28
whats the difference between kiba-dock and avant?

---

### Post by vectorslave on 2007-04-28
Same problem here!:( 


> Failed to fetch [http://download.tuxfamily.org/3v1deb...6/Packages.bz2](http://download.tuxfamily.org/3v1deb...6/Packages.bz2) MD5Sum mismatch

---

### Post by Muppeteer on 2007-04-28
I was on the kiba dock forums and requested a few bug fixes/changes...i think that may have something to do with it as i was able to update earlier this afternoon...:confused:

---

### Post by rustysail on 2007-05-01
When I try to run it a black bar just goes across the bottom of my screen.
```
rusty@rusty-desktop:~$ kiba-dock 

(kiba-dock:12443): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
** Message: cant load file /home/rusty/.kiba-dock/config into buffer notifications: Failed to open file '/home/rusty/.kiba-dock/config': No such file or directory

```

I suppose there is some kind of config file I need to get. Where can I get it?

So I made a blank file called config.
```
rusty@rusty-desktop:~$ kiba-dock 

(kiba-dock:12511): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",



```

Got any suggestions?

---

### Post by Fidelity on 2007-05-01
Im having all the same problems. This is rediculous. Why wont it work?

---

### Post by Muppeteer on 2007-05-01
I get the black bar accross the bottom if i don't have Beryl enabled as my window manager, but i think there's a way around it. Try looking on kiba-dock.org :)

---

### Post by scanez on 2007-05-01
If you are getting a black bar, try running gset-kiba first (it will give errors). Then run kiba-dock again.

---

### Post by huzzak on 2007-05-02
Thanks scanez, that did the trick.

---

### Post by mezcla on 2007-05-03
Hey guys, I am following instructions here and receiving the following in terminal after issuing the command:

> 
yason@yason-desktop:~$ sudo apt-get install kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock


any ideas or suggestions?

---

### Post by Muppeteer on 2007-05-03
Are you sure you have the repo's in your /etc/apt/sources.list? It should work ok if you do :confused:

---

### Post by kakarotossj4 on 2007-05-06
> **rustysail said:**
> When I try to run it a black bar just goes across the bottom of my screen.
...
I suppose there is some kind of config file I need to get. Where can I get it?

So I made a blank file called config.
```
rusty@rusty-desktop:~$ kiba-dock 

(kiba-dock:12511): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",



```

Got any suggestions?


Just installed kiba-dock, following instructions from kiba-dock website. First time I ran 'kiba-dock', the same black bar appeared. I tried 'killall kiba-dock', then retried it again and the dock bar appeared normally. Really dunno what happened first time I tried it, but it finally worked!

---

### Post by Cresho on 2007-05-14
i get a core dump and totalled my beryl.  the updates killed me.  not sure if it was intended for a 3200xp chip 32bit.

---

### Post by Izobalax on 2007-05-15
> **Muppeteer said:**
> This is how i installed it

(Taken from kiba-dock website)

   1.  Open a Terminal Window.
   2. Type the following:

```
sudo gedit /etc/apt/sources.list

   1. Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins
```

Then press Alt + F2 and type kiba-dock and it should work :)

I followed this method. When I run kiba-dock, the harddisk accesses for a moment and then nothing happens. Kiba-dock won't run for me. :(

I tried running it from the Terminal and got this:

```
izo@izo-desktop:~$ kiba-dock
Illegal instruction (core dumped)
```

What's going on, anyone know?

/izo

---

### Post by TheRingmaster on 2007-05-15
I am having this problem that I stated [here]("http://ubuntuforums.org/showpost.php?p=2660969&postcount=277"). Anyone know what the problem/solution is?

---

### Post by karlhm76 on 2007-05-18
I am having the same problem since I upgraded kiba to 1.1

I ran kiba-dock --verbose and found this:

```
karl@karlubuntu:~$ kiba-dock --verbose
Info Message (main.c @ line 141):
        Kiba was build with SVG support

Info Message (main.c @ line 149):
        Kiba was build without SDL support

Info Message (main.c @ line 155):
        Kiba was build without GLITZ support

Misc Message (main.c @ line 174):
        Initiall RSVG Library

Misc Message (kiba.c @ line 954):
        Initiall Akamaru Engine

Misc Message (kiba.c @ line 797):
        Creating the Window..

Misc Message (main.c @ line 191):
        Loading Plugins...

Misc Message (main.c @ line 72):
        Try to load Plugins from/usr/lib/kiba-dock

Misc Message (plugin.c @ line 738):
        Found Library at /usr/lib/kiba-dock/liblauncher.so

Misc Message (plugin.c @ line 665):
        launcher Plugin loaded

Misc Message (plugin.c @ line 738):
        Found Library at /usr/lib/kiba-dock/libtaskbar.so

Misc Message (plugin.c @ line 665):
        taskbar Plugin loaded

Misc Message (plugin.c @ line 738):
        Found Library at /usr/lib/kiba-dock/libwinlist.so

Misc Message (plugin.c @ line 738):
        Found Library at /usr/lib/kiba-dock/libclock.so

Misc Message (object.c @ line 624):
        Adding KibaObject 'clock'

Illegal instruction (core dumped)
```

Now, I may be barking up the wrong tree, but from this it looks as if the clock object is causing the problem

anyone got any other ideas?

---

### Post by hype on 2007-05-18
I'm getting the same error.
Either running gset-kiba or kiba-dock gives a "core dumped".

---

### Post by karlhm76 on 2007-05-22
I made some progress on this, albeit slight but it still doesn't work:

I reinstalled kiba-dock and gset-kiba. gset-kiba didn't work at first, but I ran kiba-dock and got the illegal instruction error, then after that gset-kiba worked (?!)

I disabled pretty much every option in gset-kiba and reran kiba-dock. It loaded, but all I get is a black bar at the bottom of the screen. The bar starts about 1.5 cm from the left of the screen and extends all the way across to the other side where it seems to slip off the edge, but I'm not certain.

I have beryl running, so I know its not that problem, although I am running beryl svn version.

I have posted over at the kiba-dock forum and I'll post here if I find any more information.

I am pretty close to abandoning this whole thing if I can't get the problems sorted out soon. Kiba seems far too buggy for me to bother with. The version I was running before this only had half as many options in gset-kiba (if that) and was also buggy as hell, but at least it worked most of the time.

---

### Post by IulianMoise on 2007-05-26
hi there everyone

i am using ubuntu feisty+beryl and recently i tried installing kiba dock. it-s installed and i see the icon for it ..in the installation there were no visible errors and still i don't see anything.nothing except my usual beryl..does anyone have any idea why ??

---

### Post by UNaruto1990 on 2007-05-26
HELP PEOPLE, I installed kiba-dock on my ubuntu 7.04, but not in your HOWTO way, anyways it worked perfectly but when I restarted it was horrible, everything disappeared but kiba-dock blue bar, and my desktop, most importantly my two (top and bottom) menus disappeared, I can't launch anything like Beryl and stuff, lucky me I could press Alt+F2 and run firefox from there, and also I couldn't uninstall kiba-dock from the package manager, oh and background of the kiba-dock  icons were black, in other words my ubuntu isn't working !!!! please I need a solution :(:(:(

---

### Post by diemos on 2007-07-09
So I tried installing this using the guide in the first reply. I haven't used linux in years, so I'm quite a bit rusty. Anyone lend a hand?

Once I tried apt'ing kiba-dock, I ran into trouble.


```

diemos@diemos-laptop:~$ sudo apt-get install kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kiba-dock: Depends: libakamaru0 but it is not going to be installed
             Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is to be installed
             Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
             Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is to be installed
             Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
             Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
             Depends: libgnome-keyring0 (>= 0.7.1) but 0.6.0-0ubuntu2 is to be installed
             Depends: libgnomeui-0 (>= 2.17.1) but 2.16.1-0ubuntu2 is to be installed
             Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.16.1-0ubuntu7 is to be installed
             Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is to be installed
             Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
             Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is to be installed
             Depends: kiba-plugins but it is not going to be installed
             Depends: gset-kiba
E: Broken packages

```

---

### Post by Ptero-4 on 2007-08-02
I installed Kiba-dock but I wanted to know one thing. How do I make kiba-dock capable of launching a launcher that points to a VFS URI? I ask b/c I added the network:/// and computer:/// locations to kiba-dock, the icons appear but clicking on them do nothing, they don´t launch at all. launchers that point to apps or locations like /home launch normally.

---

### Post by Ptero-4 on 2007-08-03
Do anyone know this? Do I have need permission (from M$) to get kiba-dock fixed?

---

### Post by Scapegoat427 on 2007-09-06
I followed the instructions posted earlier in the thread and it installed perfectly. My only issue now is that I can't add anything to the dock

---

### Post by anemptygun on 2007-09-11
> **Muppeteer said:**
> This is how i installed it

(Taken from kiba-dock website)

   1.  Open a Terminal Window.
   2. Type the following:

```
sudo gedit /etc/apt/sources.list

   1. Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins
```

Then press Alt + F2 and type kiba-dock and it should work :)

Thanks Muppeteer! this worked perfectly!

---

### Post by ralvynl on 2007-09-30
Mine is working fine except for the black bar . . .
Please, does any 1 know how I can get rid of the bar . . .Please, Help

Thanx in Advance

---

### Post by Spam Banjo on 2007-12-02
Works sweet in Ubuntu 7.04 Feisty Fawn on an old Dell Optiplex SX280 with onboard intel gfx following this guide. The Eye candy resource is a well known beast, there are loads of pretties to play with!

Kiba-dock runs better on this old peice o' shuugga than any of the machines I've tried it on. Although I'm yet to try it using an Nvidia card. Linux is making me hate ATI so bad.

---

