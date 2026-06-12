---
title: "compiz fusion 3d windows in Gutsy script"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by ArielTM on 2007-10-21
Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

---

### Post by Khuezy on 2007-10-21
When it asks to [Y/n]
I type Y and it aborts

---

### Post by celticbhoy on 2007-10-21
Works great for me - how about giving the screensaver plugin a go ????

---

### Post by Dropknee on 2007-10-21
Ok is this plug-in is updated, I run this scrip again and thats it??

---

### Post by sdowney717 on 2007-10-21
thanks, working fine.

lets get  the snow plugin working.

 run all those commands in terminal
then the 3d windows plugin will show up in ccsm

---

### Post by ArielTM on 2007-10-22
> **celticbhoy said:**
> Works great for me - how about giving the screensaver plugin a go ????

I don't know which snapshot of the screensaver plugin works in gutsy

---

### Post by tomak on 2007-10-22
> **Khuezy said:**
> When it asks to [Y/n]
I type Y and it aborts
it also happened to me....help guys

---

### Post by ArielTM on 2007-10-22
> **Khuezy said:**
> When it asks to [Y/n]
I type Y and it aborts

> **tomak said:**
> it also happened to me....help guys

Try to run the commands one by one and see what it tells you

---

### Post by cybersaicho on 2007-10-24
-For me the instalation worked and the icon apears in manager but after enabeled it doesnt do nothing ,ánd there are no freatures for it or in other words the plugin parameters dont show at all but im sure its from my machine  any one have any ideas ???:confused:
thanks anyway in advanced :)

---

### Post by jimmy the saint on 2007-10-24
Seems to want to install a whole lot of packages for a simple plugin.

---

### Post by emulation_fan on 2007-10-24
Wow. Thanks this works great. Yay!:popcorn:

---

### Post by Wangfu on 2007-10-24
username@username-desktop:~/fusion/plugins/3d$ sudo make install
install   : /home/username/.compiz/plugins/lib3d.so
install   : /home/username/.compiz/metadata/3d.xml
install   : build/compiz-3d.schemabuild/compiz-3d.schema:1: parser error : Document is empty

^
build/compiz-3d.schema:1: parser error : Start tag expected, '<' not found

^
install   : build/compiz-3d.schema
username@username-desktop:~/fusion/plugins/3d$ 

everything works until i do make install than i get whats above

Anyone know whats up?

EDIT: I got it to work by deleting the fusion folder and extracting the tar again. AWESOME THANKS! :D

---

### Post by AlienTech on 2007-10-25
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main compiz-bcop 0.5.2-0ubuntu1 [8686B] 
Fetched 10.8MB in 14m9s (12.7kB/s)                                             
Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `linux-libc-dev':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)



anyone...anyone.... beuller.... beuller

---

### Post by joshuachad on 2007-10-25
all ill say is they took the 3d plugin out of Gutsy for a reason. Personally im waiting till the compiz dev guys fully re-write it. But hey the Linux croud isnt known for its patience.

---

### Post by w116tjb on 2007-10-25
The script ran great. Plugin seems to work fine too. Except for the fact that I can't change the amount of space the windows lift off of the desktop... A bummer, but it'll be fixed eventually... Also, when a window is maximized, the side of the window gets a little glitchy on rotation. It's really smooth otherwise.

---

### Post by w116tjb on 2007-10-25
Found the problem. After installing the plugin, right-click on the fusion-icon (if you have it) and reload the window manager. The modified 3D plugin settings will take effect.

---

### Post by TadH on 2007-10-25
This worked fine for me excellent job. Could you please explain to me how to edit how far off of the cube the windows come? Thanks again works awesome

---

### Post by Toffeeapple on 2007-10-25
Thanx for this **ArielTM**.. works a charm.. ta!

**TadH**.. none of the settings would work for me till I'd rebooted.

---

### Post by NoVista on 2007-10-25
Thanks for stopping by over here.
I'm WartHog over at Compiz.
Thanks again, it all went very sweet !

---

### Post by the_nz_monkey on 2007-10-25
Works like it says on the box - good work on the script :)

Can't wait 'till this plugin's working like it did on Beryl...

---

### Post by BarBQ on 2007-10-26
ran the script and when i got to the last two lines i got this.

       make: *** No rule to make target `build/fusion/plugins/3d/3d.lo', needed by `c-build-objs'.  Stop.

   I dont really know much about any of this but have been following peoples directions with pretty good success rate. Is this normal or am i doing something wrong. I dont see the 3d windows plug in on the ccsm. This is my first post so i just want to say thanks to everyone for all there how to.

---

### Post by khanh_coltech on 2007-10-26
when a window stay at two workspaces:
[IMG]http://lh4.google.com/phantrongkhanh87/RyHwg5MD2QI/AAAAAAAABEk/hl6-FoKwSI8/s400/3d.jpg[/IMG]
how to solve this problem?

---

### Post by Derspankster on 2007-10-26
The script ran just fine but I have no icon in Compiz. I rebooted to make sure that Compiz was restarted.

---

### Post by idanbd on 2007-10-26
> **BarBQ said:**
> ran the script and when i got to the last two lines i got this.

       make: *** No rule to make target `build/fusion/plugins/3d/3d.lo', needed by `c-build-objs'.  Stop.

   I dont really know much about any of this but have been following peoples directions with pretty good success rate. Is this normal or am i doing something wrong. I dont see the 3d windows plug in on the ccsm. This is my first post so i just want to say thanks to everyone for all there how to.

I'm having the same issue and am too a newbie.

---

### Post by Derspankster on 2007-10-27
> **sdowney717 said:**
> thanks, working fine.

lets get  the snow plugin working.

 run all those commands in terminal
then the 3d windows plugin will show up in ccsm

The plugin doesn't show up for me and the script ran OK.

---

### Post by peddy on 2007-10-27
> **BarBQ said:**
> ran the script and when i got to the last two lines i got this.

       make: *** No rule to make target `build/fusion/plugins/3d/3d.lo', needed by `c-build-objs'.  Stop.

   I dont really know much about any of this but have been following peoples directions with pretty good success rate. Is this normal or am i doing something wrong. I dont see the 3d windows plug in on the ccsm. This is my first post so i just want to say thanks to everyone for all there how to.

Happens to me too... Anyone know how to fix?

---

### Post by NoVista on 2007-10-27
The 'make', and 'sudo make install' command need to be run from the 3d folder.

---

### Post by anmiv on 2007-10-27
i am sorry guys this is a really stupid question but i think i have the script up and running now how do i do the 3d cube thing? i tried "windows key"+ tab and atl+tab but did not work

ps this is the first time i am using linux

---

### Post by Caffeine_Junky on 2007-10-27
> **anmiv said:**
> i am sorry guys this is a really stupid question but i think i have the script up and running now how do i do the 3d cube thing? i tried "windows key"+ tab and atl+tab but did not work

ps this is the first time i am using linux

Hey there, ...try **Ctrl + Alt ** <direction arrows>  or  Left-mouse click-and-hold  and drag on Desktop\  or mousewheel on desktop  and you can also rotate cube by left-click on the 4 boxes (work spaces  bottom bar  right-hand side) individually, ..any and all of these actions will rotate the cube.

PS:  there are no stupid questions ;)

welcome to Ubuntu Forums

---

### Post by khanh_coltech on 2007-10-28
when a window stay at two workspaces:
[IMG]http://lh4.google.com/phantrongkhanh87/RyHwg5MD2QI/AAAAAAAABEk/hl6-FoKwSI8/s400/3d.jpg[/IMG]
how to solve this problem?

---

### Post by flamepanther on 2007-10-28
> **BarBQ said:**
> ran the script and when i got to the last two lines i got this.

       make: *** No rule to make target `build/fusion/plugins/3d/3d.lo', needed by `c-build-objs'.  Stop.

   I dont really know much about any of this but have been following peoples directions with pretty good success rate. Is this normal or am i doing something wrong. I dont see the 3d windows plug in on the ccsm. This is my first post so i just want to say thanks to everyone for all there how to.Same here.  It does the same when I run "make" from inside the 3d folder as well.  I"m on the 64-bit version, if that might make a difference.

---

### Post by ArielTM on 2007-10-28
Hi
Fixed the script

Hope that it'll work for you all now

---

### Post by tikal808 on 2007-10-28
The script ran fine for me too, but no 3d windows icon in the ccsm? Any ideas on how to fix? I'm running Gutsy 64bit.  Other than getting 3D Windows to work, Compiz-Fusion works fine for me.

---

### Post by Derspankster on 2007-10-28
This is not going well. I ran the updated script and it completed. I now have a 3d windows icon in ccsm....But, I cannot enable it by checking it.  IN FACT.. I cannot enable or disable anything in ccsm now. Compiz is still running OK, however but I've lost the ability to make any changes at all.

---

### Post by ANtrah on 2007-10-28
100% to 100 :guitar:

---

### Post by Derspankster on 2007-10-28
> **ANtrah said:**
> 100% to 100 :guitar:

OK, you got me on that one.

---

### Post by khanh_coltech on 2007-10-29
Thanks, very good, but I still have an error when i put a window stay at two workspaces.
Plz fix this.

---

### Post by ariel.darkserver on 2007-10-29
:guitar: WORKS!!! Looks great again!!! now my friend gonna be jealous!!! XD 
i KILL THEM WITH My ubuntu 7.10 compiz fuzion, now I gonna destroy their "vista" world with all the plugins working fine and only using 2% of my cpu with an average PC, XD

---

### Post by Derspankster on 2007-10-29
I'm not sure what i did wrong. Like I said in my earlier post. The 3d applet is now present but all my check boxes are grayed out and I cannot enable the 3d nor can I change any other settings. Since I ran the downloaded script from my desktop perhaps the plugin that was made isn't in the correct location. I simply don't know. Hope Compiz is not broken although it still runs OK.

---

### Post by mc4man on 2007-10-29
Works fine here - good job
@Derspankster - make sure auto.. plugin sorting is checked  (ccsm>preferences>plugins)

---

### Post by andyanderso on 2007-10-29
I extracted the file to my home directory /home/andy.
I ran it in terminal. It seemed to run fine,  but I do not have the 3d option in ccsm.  Did I do something wrong?  Did I extract it in the wrong location?  Is there an easy way to remove everything the script installs in case I can't get it working?

andy

---

### Post by Derspankster on 2007-10-29
> **mc4man said:**
> Works fine here - good job
@Derspankster - make sure auto.. plugin sorting is checked  (ccsm>preferences>plugins)

Thank you so much - that did the trick!

---

### Post by flamepanther on 2007-10-30
> **ArielTM said:**
> Hi
Fixed the script

Hope that it'll work for you all nowIt works flawlessly for me now.  Many thanks for the effort :)

---

### Post by cedenburn on 2007-11-02
I have had no problem with install or effects works very well. Hardware is Dual Core AMD 64,4 gigs ram, Nvidia 8600GT 512mg, Samsung 22" display and looks AWESOME:)

Thanks been waiting for this one

Chuck

---

### Post by frograven on 2007-11-02
ArielTM, awesome job. Worked flawless! You say this is your first script uh, well two thumbs up buddy. Thank you for the contribution!

~~~~~~~~
(marty0577)
          **... are you kidding me, starcraft can run on a godd---n toaster.**

---

### Post by kshane on 2007-11-02
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

**Absolutely *AWESOME!*  Worked right off the bat!  Thank you very much!!!**

Kevin

---

### Post by phillipjennings5 on 2007-11-03
sweeeeett thanks:)

---

### Post by Jose Catre-Vandis on 2007-11-03
Downloading and running the attached script worked. Copying the lines one by one to terminal from the first post didn't. Good work :)

---

### Post by PaulRay on 2007-11-03
Try running the script a few times, this worked for me. It seems to run in bits. 
Anyway, I now have 3-D windows again! Thanks!

---

### Post by nikoPSK on 2007-11-07
I love you!

---

### Post by AcademyKP03 on 2007-11-07
Do I just copy and Paste the following into my terminal?

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

??

---

### Post by camarojones on 2007-11-07
I ran the script, and it downloaded a bunch of stuff. I found that it only downladed the first apt-get install items.

I had to basically go one line at a time from there to get it to work, however...

The MAKE line gives this and i cannot continue:

**make: *** No rule to make target `build/3d.lo', needed by `c-build-objs'.  Stop.**

What do i do from here?

---

### Post by BoneyOne on 2007-11-08
Nice, it worked perfectly the first try. Thanks!!

One question, is there a way to change the thickness of the windows? With Compiz on Fiesty it was with no thickness when pulled up, I kind of prefer it like that.

---

### Post by Jacktoga on 2007-11-11
I have been looking a long time for this, thank you so much ,  great work! 

Copy and pasteing of the script didn't work for me though, running the script from the attached package did. 

After a reboot 3D windows worked nicely :)

---

### Post by brunoskrebs on 2007-11-11
OK it didn't work for me, how do I undo this changes? Because it did a bad stuff actually... Now its everything disabled, I mean I cannot change the setting because the square box that you click is not enabled anymore...

And it didn't show the 3d option on the manager for me...

So please how do I undo those changes??

---

### Post by digitalbenji on 2007-11-12
I entered each line (minus the first which defines the script) into a terminal, since its pretty evident what it does.  It worked flawlessly.  Thanks!

---

### Post by Mr-BuntYou on 2007-11-15
Thank you for this nice script. With this one i get it installed!

just copy it to your home directory and run it and .... it works!


PS: i'm new here in this forum, but i'm not an ubuntu newb ... and i'm german so sry for my bad english :lolflag:

---

### Post by cibao5923 on 2007-11-17
I installed the script and received no errors.  The only issue is that the icon shows up on the settings but i can't enable it.  I can't also disable or enable anything else.  Did I do something wrong?  :confused:

---

### Post by SethJT on 2007-11-18
Wow! nice work.  Download, run in terminal & Wala, works like a charm.   Wish i new how to do that.  Thanks

---

### Post by Martje_001 on 2007-11-20
> **Khuezy said:**
> When it asks to [Y/n]
I type Y and it aborts
Typ it yourself (dont copy + paste).

---

### Post by kfealz on 2007-11-26
downloaded and ran the script.  worked perfectly.  thanks so much!

---

### Post by nikoPSK on 2007-11-26
the script wouln't let me set window distance. I just git'd it.

---

### Post by BujarM on 2007-11-26
the script works
but i dont see a cube
only a 2x2 rectangle
and with the ctr+alt+arrow i can change the workplaces
help anyone?

---

### Post by adza on 2007-11-30
BujarM, try right clicking the window switcher in the taskbar and checking preferences, have you got the option 'columns' set to 4? (or more than 2 anyways)

---

### Post by nikoPSK on 2007-11-30
gereral options, desktop size, set the first slider to 4:popcorn:

---

### Post by Chris5369 on 2007-12-09
Awesome script bro works awesome for me. (I did the install to home directory)

**Also make sure you restart or you cant change the 3D options with compiz

:)

---

### Post by vincentvee on 2007-12-15
had the same problem, what i ended up doing was running the script as sudo, I.E.  sudo /home/john/gutsy3d
every other time i kept getting an abort
anyway, was an excellent script
thanx heaps to the author

> **PaulRay said:**
> Try running the script a few times, this worked for me. It seems to run in bits. 
Anyway, I now have 3-D windows again! Thanks!

---

### Post by mcki0154 on 2007-12-16
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

------------------------------------------------------------

For all of us who have been getting the abort response (as I was), take the second route.

Download the attachment and extract in your home directory

1) Move it off your desktop and put into home folder Places>Home Folder

2) Right Click, hit extract

3) Double click on icon that says "gutsy 3d"

4) Select "Run in terminal"

5) watch the terminal do its job n wait

6) revel in the cool 3Dness

:)

P.S. make sure to have a fast Internet connection, as a dial-up will have you waiting for quite some time.  Also, be sure to have your Ubuntu 7.10 install cd or dvd handy, I don't have the best memory but I'm sure it asked for it.

---

### Post by lordawesome on 2007-12-19
For all of you who can't  get this to work..... Sorry about your luck. I don't see any reason why it should not. Thank you VERY much for this script. This is one of the few reasons I even installed compiz in the first place.

---

### Post by Victormd on 2007-12-20
Perfect script!!!

Thanks, love the effects this thing outputs!!!

---

### Post by jryprt on 2007-12-21
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated


It works Great had to run commands one at a time.

---

### Post by nononanette on 2007-12-24
down loaded pkg and ran. i got 3d options in ccsm and clicked to activate. i restarted and checked that 3d was still selected but i get no window stand off. i then went into ccsm again and set the  page separation to a higher number but still no separation. any ideas??:(

---

### Post by TravDelB on 2007-12-26
Works fine until it asks to put Ubuntu install disk into drive /cdrom/ and press enter.  I do, and it continues to pop up with same request.  Any ideas?

---

### Post by nononanette on 2007-12-26
did not ask me to put cd into the drive, so i can offer u no answer.i'm still trying to figure out why i can not get windows to stand off the cube.

---

### Post by nononanette on 2007-12-26
however i made the install by using the tar rather than by typing the script in one command at a time.

---

### Post by Martje_001 on 2007-12-26
> **TravDelB said:**
> Works fine until it asks to put Ubuntu install disk into drive /cdrom/ and press enter.  I do, and it continues to pop up with same request.  Any ideas?
Of cource ;). Typ in the terminal: [B]sudo nano /etc/apt/sources.list
[/B].

Remove the line(s) which holds 'cdrom://' and press CTRL + O, followed by CTRL + X. Now typ [B]sudo apt-get update
[/B]. Now do what you wanted to do.

---

### Post by TravDelB on 2007-12-26
Ah! Worked great, thanks.  But now the 3d option showed up in the Advanced Desktop Effects Settings, but everything is greyed out and I can't change any settings.  Is it because the plugin was placed in the wrong spot?

---

### Post by TravDelB on 2007-12-26
> **cibao5923 said:**
> I installed the script and received no errors.  The only issue is that the icon shows up on the settings but i can't enable it.  I can't also disable or enable anything else.  Did I do something wrong?  :confused:

I had same problem and (for some reason) I went into preferences in the Advanced Desktop Effects Settings window and hit the second tab "Plugin List" and enabled "Automatic plugin sorting".  And then it worked fine.

---

### Post by Victormd on 2007-12-27
Thanks, I had to run it line by line but in the end, worked like a charm!

---

### Post by Tha_Guru on 2007-12-28
Hi everybody, I've run the script in my home folder, a 3d.tar.gz appeared after installation, I enabled 3d windows in my ccsm and then rebooted but nothing seems to change. I can change face but I have no 3d effect. It's like I had a cube but I can see only one face and if I use ctrl-alt-arrows or mouse I see another face but no 3d stuff. Anybody can help me? Thanks

---

### Post by LinuxIsInnovation on 2007-12-28
For all plugins, check this:
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

### Post by rune0077 on 2007-12-28
This worked great for me, thanks a bunch.

---

### Post by nononanette on 2007-12-28
try this.  open ccsm. go to general options>desktopsize. set 'numberof desktops' to 4. see if that gives u a cube. check to see if your open windows stand off from the desk top if they do let me know. tks.

---

### Post by Tha_Guru on 2007-12-28
I've already set "number of desktops" to four.. I have a cube but I don't see it 3d like I've seen in some screen shots that were posted in this thread. I have a cube only because I can move from one face to another scrolling with mouse but each face is plane and covers all the screen. Plus the windows are not elevated but stand on the desktop. Dunno if there is something missing in my settings or in my tools.. I followed all the instructions correctly I think..
Thanks for the answer anyway!

---

### Post by nononanette on 2007-12-28
i can get the cube effect by depressing the scrool button on the mouse when the arrow is on the desk top or  by pressing cntl +alt and the left mouse button no matter where the arrow is, the in either move the mouse to roll the cube. the windows will only stand off when you do this.

---

### Post by Tha_Guru on 2007-12-28
when I scroll it just goes to another face I can't move around the cube I don't even see the cube.. I can just barely see it while it passes from a face to another..and while scrolling the windows stand on the desktop.. dunno why.

---

### Post by 5735guy on 2007-12-29
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

Many thanks 'AWESOME'

---

### Post by 5735guy on 2007-12-29
Many thanks it works great.

One question, how do you alter how far the windows are elevated from the cube ?

Cheers !

---

### Post by lightstream on 2007-12-29
> **Tha_Guru said:**
> when I scroll it just goes to another face I can't move around the cube I don't even see the cube.. I can just barely see it while it passes from a face to another..and while scrolling the windows stand on the desktop.. dunno why.

It's normal - on a faster machine it can be pretty quick at spinning from one face to another!

Try clicking and holding the mouse wheel on a blank bit of desktop, then move the mouse with wheel still held down. You should see the cube then!

You can slow the spin down in System > Preferences > Advanced Desktop Effects Settings. Click the Rotate Cube icon there, then reduce the speed a bit.

You can also adjust how far away the cube appears when you click and hold the wheel by adjusting the Zoom slider.

---

### Post by 5735guy on 2007-12-29
:) Once again many thanks for this, just need to know how to adjust the window elevation from the cube.

---

### Post by Tha_Guru on 2007-12-29
> **lightstream said:**
> It's normal - on a faster machine it can be pretty quick at spinning from one face to another!

Try clicking and holding the mouse wheel on a blank bit of desktop, then move the mouse with wheel still held down. You should see the cube then!

You can slow the spin down in System > Preferences > Advanced Desktop Effects Settings. Click the Rotate Cube icon there, then reduce the speed a bit.

You can also adjust how far away the cube appears when you click and hold the wheel by adjusting the Zoom slider.

wow now I can see the cube and the windows elevated but just when I hold the wheel.. If I don't hold the wheel after reducing the speed and increasing the zoom I can see the cube 3d but the windows still stand on the face. Is it normal?
Sorry I'm a newbie.
Thanks a lot for your help:D

---

### Post by 5735guy on 2007-12-29
I've sorted the window elevation settings.

Heres how :

Open CompizConfig settings

Double click 3Deffects

Click on Misc. Options tab

There is a Window Space option

Slide to your preferred setting.:):)

---

### Post by nononanette on 2007-12-30
> **nononanette said:**
> down loaded pkg and ran. i got 3d options in ccsm and clicked to activate. i restarted and checked that 3d was still selected but i get no window stand off. i then went into ccsm again and set the  page separation to a higher number but still no separation. any ideas??:(

ok i finally got the 3d standoff to work. i pasted in each line as was first recommened and ran them one at a time. everything works great. not sure what is wrong with the tar but that did not work even though i tried it a couple of times. any way have enjoyed reading all the post. just installed awn and that works great also.:biggrin:

---

### Post by mmm2010 on 2008-01-01
> **w116tjb said:**
> Found the problem. After installing the plugin, right-click on the fusion-icon (if you have it) and reload the window manager. The modified 3D plugin settings will take effect.

I'm having the same problem.  (When I adjust the space between the windows, nothing changes.)  What icon are you/ is he referring to?


EDIT:  Nevermind....   Anyone who has this problem probably just needs to reboot-it worked for me.

---

### Post by 5735guy on 2008-01-01
I had the same problem with the elevation not changing, so I rebooted and it worked fine.:):)

---

### Post by 5735guy on 2008-01-03
Hi, I was wondering if this would work on Compiz installed on Feisty ? :confused:

---

### Post by 5735guy on 2008-01-06
How could I get this to work on xubuntu 7.10 please ?

---

### Post by Nickedynick on 2008-01-11
Great work, but one small hitch - when you drag windows to the edge of a screen and rotate the cube they are broken in the animation. Any ideas how to fix this?

---

### Post by nikoPSK on 2008-01-11
oops I thanked you rather than quoting you... well, it could be your GPU not up to snuff....:confused:

---

### Post by 5735guy on 2008-01-12
Many thanks, works on Mint 4.0 as well !!!:):):)

---

### Post by octesian on 2008-01-21
Didnt work for me :(  Am I missing something?  When it tries to "make" I get this and it quits;

convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema    : build/3d.xml -> build/compiz-3d.schema
compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Error 1

---

### Post by strik9 on 2008-01-22
im running gutsy and i followed the script in your order exactly (via copy/paste) and everything worked perfectly! great thread keep up the good work.

---

### Post by Sctt on 2008-01-25
After installation (which ran smoothly), I am unable to edit ANY of the options in Compiz. All of the effects seem to be unchecked, but they're all functioning properly. Any suggestions?

---

### Post by SanskritFritz on 2008-01-26
> **Sctt said:**
> After installation (which ran smoothly), I am unable to edit ANY of the options in Compiz. All of the effects seem to be unchecked, but they're all functioning properly. Any suggestions?[http://ubuntuforums.org/showpost.php?p=3928703&postcount=6](http://ubuntuforums.org/showpost.php?p=3928703&postcount=6)

---

### Post by big dizzle on 2008-01-26
downloaded the script and it worked perfect!!!

---

### Post by kilo66 on 2008-01-28
Problems here also but my issue is at "Make" time...  I get an error of "make: *** No rule to make target `build/3d.lo', needed by `c-build-objs'.  Stop."  When at the make command.

Any idea?
New to Ubuntu

---

### Post by bcrom on 2008-01-31
It worked fine for me.  I had to log out and back in, but then the controls worked.  The flicker is annoying, but I just set window width to 0 and it disappeared.

---

### Post by 5735guy on 2008-02-01
Hi there, Is there a way to make this work on Ubuntu 7.04 please.

These are the Compiz Fusion sources I am using for Fiesty :

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

The 3D windows plugin is there, but non responsive. I have tried installing this solution with no joy, Is there a workaround so this will install on Fiesty ?

---

### Post by chlee on 2008-02-13
frackin awesome!

took a little bit, so this is how i did it:
copy/paste script=aborted
then followed this:

> **mcki0154 said:**
> ------------------------------------------------------------

For all of us who have been getting the abort response (as I was), take the second route.

Download the attachment and extract in your home directory

1) Move it off your desktop and put into home folder Places>Home Folder

2) Right Click, hit extract

3) Double click on icon that says "gutsy 3d"

4) Select "Run in terminal"

5) watch the terminal do its job n wait

6) revel in the cool 3Dness

:)

P.S. make sure to have a fast Internet connection, as a dial-up will have you waiting for quite some time.  Also, be sure to have your Ubuntu 7.10 install cd or dvd handy, I don't have the best memory but I'm sure it asked for it.



but, during the process in terminal it asked for my dvd. i didnt have that.. so i noticed that it would only ask for the dvd if it was still down loading.. weird. so i would wait a bit and hit enter again and that worked til around get:64.. 

so then i just canceled. went to system>admin>software sources and unchecked the dvd as a source. i had to cancel the terminal so that i could make this change without errors.. refreshed the sources and it downloaded the list and that was all good.

then i went back and opened the downloaded file again in terminal. making sure to type an uppercase 'Y' (i think that was the problem with just copy/pasting the script?) and off it went. worked like a charm.. and fast too..  perhaps because it got so far before.. duno. anyway it compiled and that was that.

check out the advanced prefs and sure enough 3d windows was there. made some adjustments and then restarted. looks awesome! i noticed a compressed version of the script where one wasnt before (in the home folder) .. so i just deleted it along with the script and calling it done.

:lolflag: made my day! thanks a ton!

---

### Post by emshains on 2008-02-23
I did everything like you guys or i did everything like i think you did, but i always get just the inside of the cube and i cant change it in compiz conf.

Will you help me?


Ok i got that sorted, but i see in the pic that the desktop cube is like further away so you can see like more of the sky and a smaller cube

---

### Post by Mcnrgnrg on 2008-02-23
hi this is a nooob and i wanted to know if you needed teh internet to make this work. i dowloaded the attatchment please help

---

### Post by gilang on 2008-02-24
well...your attachment work for me...the window raise successfully...
but i got problem when i put window between 2 desktop....
the window get cut in the middle of the cube's edge and doesnt integrate to each other...

can u help me fix this????

---

### Post by gilang on 2008-02-25
here's the capture.....

[img]http://pic16.picturetrail.com/VOL635/2414786/4766701/305777102.jpg[/img]

---

### Post by SanskritFritz on 2008-02-25
I dont think this will be fixed. the reason: the window is raised only on the z axis from the desktop. In order to have the window connected at the edge of the cube, the window has to be moved towards the edge on both desktops, according to the amount it was raised from the desktop. That is a whole new transformation, i dont think it is built into the plugin.

---

### Post by MaindotC on 2008-02-25
> **kilo66 said:**
> Problems here also but my issue is at "Make" time...  I get an error of "make: *** No rule to make target `build/3d.lo', needed by `c-build-objs'.  Stop."  When at the make command.

Any idea?
New to Ubuntu

This has still not been addressed.

---

### Post by lewisskinner on 2008-02-25
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

Hey.  This hasn't worked for me.

I type the code into the terminal line-by-line, and got this:

```
lewis@Lewis-Jen:~$ sudo apt-get install compiz-bcop compiz-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tk8.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libgl1-mesa-dev libice-dev libpng12-dev libsm-dev
  libstartup-notification0-dev libx11-dev libxau-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxinerama-dev libxrandr-dev libxrender-dev linux-libc-dev mesa-common-dev
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
  zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed
  compiz-bcop compiz-dev libc6-dev libgl1-mesa-dev libice-dev libpng12-dev
  libsm-dev libstartup-notification0-dev libx11-dev libxau-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxinerama-dev libxrandr-dev libxrender-dev linux-libc-dev
  mesa-common-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
  zlib1g-dev
0 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
lewis@Lewis-Jen:~$ #!/bin/bash
lewis@Lewis-Jen:~$ sudo apt-get install compiz-bcop compiz-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tk8.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libgl1-mesa-dev libice-dev libpng12-dev libsm-dev
  libstartup-notification0-dev libx11-dev libxau-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxinerama-dev libxrandr-dev libxrender-dev linux-libc-dev mesa-common-dev
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
  zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed
  compiz-bcop compiz-dev libc6-dev libgl1-mesa-dev libice-dev libpng12-dev
  libsm-dev libstartup-notification0-dev libx11-dev libxau-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxinerama-dev libxrandr-dev libxrender-dev linux-libc-dev
  mesa-common-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
  zlib1g-dev
0 upgraded, 33 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
lewis@Lewis-Jen:~$ 

```

Any ideas?

---

### Post by SanskritFritz on 2008-02-25
You are running Synaptic or similar in the background.

---

### Post by MaindotC on 2008-02-25
Yeah it's some sort of permissions issue - if not via using sudo then perhaps on the sources list or repository directory.

---

### Post by johnn1949 on 2008-03-01
3d worked perfectly for me,thanks.   I ran the scripts one at a time starting with sudo....... I accidently forgot to run the make command before the sudo make install, but it worked .

---

### Post by johnn1949 on 2008-03-01
here's screenshot

---

### Post by Job_314 on 2008-03-01
I had it working for a little while, then an update screwed my Compiz. When I had it working it looked great unless it was on a corner, the windows didn't wrap around... they just cut off.

But now when I install the depos to required get this working, those screw my Comzpiz too. Bah.

---

### Post by MaindotC on 2008-03-01
Any chance you are updating from unsupported or "test" repos that I think are referred to as "backports"?  I have a Fedora box and I made the mistake of enabling the test repos, and it downloaded FC9 which I found out is in beta for a reason...

---

### Post by dondolo on 2008-03-01
hi guys i got a problem. after installing, i stay locked on my desktop. i can't move to the other faces it's like my cube does not exist anymore. any idea?? please help

---

### Post by MaindotC on 2008-03-01
Ok, first of all, do you have 4 workspaces enabled?  In the lower right hand corner where the workspaces are an icon, right click and open properties.  It should tell you in there.

---

### Post by SanskritFritz on 2008-03-01
> **dondolo said:**
> hi guys i got a problem. after installing, i stay locked on my desktop. i can't move to the other faces it's like my cube does not exist anymore. any idea?? please helpRight click on the desktop, select Change Desktop Background and see at the last tab (Visual Effects) if you are using Custom.

---

### Post by Warprunner on 2008-03-07
> **strAlan said:**
> Ok, first of all, do you have 4 workspaces enabled?  In the lower right hand corner where the workspaces are an icon, right click and open properties.  It should tell you in there.

HAHAHAH Installtion worked GREAT and smooth as SILK!!
I don't have 4 Windows...I HAVE 6 and it works flawlessly!!!

:lolflag:      :guitar:      ):P

---

### Post by BooBooNTZU on 2008-03-07
The script worked , but there is something wrong with the ATI drivers or the xorg configuration. When i run a game like Chromium with Compiz Effects enabled the window doesn't get updated properly. If i move the Chromium window on the screen , only the frame is moving ...  the rest of the rendering is not following the frame. Any ideas ?

---

### Post by BooBooNTZU on 2008-03-07
> **Job_314 said:**
> I had it working for a little while, then an update screwed my Compiz. When I had it working it looked great unless it was on a corner, the windows didn't wrap around... they just cut off.

But now when I install the depos to required get this working, those screw my Comzpiz too. Bah.



After the update you have to reconfigure your video card again , then re-enable the restricted drivers and then reboot. To reconfigure your video card use :

sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --initial -f 

If you have and Nvidia card , you probably have to use other commands to do it.

---

### Post by UBU-Razer on 2008-03-12
Thank you very much!!! This worked great for me, and now I'm havin' 3d Windows in cubeeee weee! :D

---

### Post by szandor on 2008-03-12
after installing the 3d windows plugin, the windows would not elevate off the cube. not sure if this has been brought up in the last 13 pages but if your 3d effects do not work, make sure you have the cube reflection plugin enable. if you see a giant *** cube, it is not enabled. if you see a smaller cube and a reflection of the cube under it, then the plugin is enabled.

edit: maybe some clarification on what other plugins need to be enabled for other effects to work should be included on the first page. for example, if i disable cubereflex, the 3d effects do not work, if i enable cubeflex, 3d works. maybe it's just me but i was stumped until looking at a picture of the 3d effects and noticed the smaller cube and reflection.

---

### Post by UltraAnders on 2008-03-15
Thanks OP. This worked a treat. Quick reset needed to get Window Space changes working (as mentioned by others in thread). \\:D/

---

### Post by saguinus on 2008-03-16
Worked like charm.

Cheers !!

---

### Post by m4443 on 2008-03-20
Didn't work :( ;

```

drwxrwxr-x root/root         0 2007-08-06 17:48 3d/
-rw-rw-r-- root/root     26793 2007-08-06 17:48 3d/3d.c
-rw-rw-r-- root/root      3296 2007-08-06 17:48 3d/3d.xml.in
-rw-rw-r-- root/root     16338 2007-08-06 17:48 3d/Makefile
-rw-rw-r-- root/root        34 2007-08-06 17:48 3d/plugin.info
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema    : build/3d.xml -> build/compiz-3d.schema
compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Virhe 1
compiling : 3d.c -> build/3d.loIn file included from 3d.c:47:
build/3d_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
3d.c:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
3d.c: In function 'tdPreparePaintScreen':
3d.c:216: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c:216: error: (Each undeclared identifier is reported only once
3d.c:216: error: for each function it appears in.)
3d.c: In function 'tdPaintWindow':
3d.c:294: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdAddWindow':
3d.c:570: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintTransformedOutput':
3d.c:591: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdPaintOutput':
3d.c:669: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdDonePaintScreen':
3d.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintTop':
3d.c:739: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdCubePaintBottom':
3d.c:759: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkFirst':
3d.c:775: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkLast':
3d.c:782: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkNext':
3d.c:789: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdWalkPrev':
3d.c:796: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindowWalker':
3d.c:803: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForDisplay':
3d.c:824: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForDisplay':
3d.c:880: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitPluginForScreen':
3d.c:907: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniPluginForScreen':
3d.c:929: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitDisplay':
3d.c:959: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniDisplay':
3d.c:969: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitScreen':
3d.c:981: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniScreen':
3d.c:1027: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInitWindow':
3d.c:1044: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFiniWindow':
3d.c:1063: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdInit':
3d.c:1070: error: 'displayPrivateIndex' undeclared (first use in this function)
3d.c: In function 'tdFini':
3d.c:1079: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/3d.lo] Virhe 1

```

---

### Post by timmo_5 on 2008-03-20
Many thanks ArielTM from a linux noob, got the plugin to actually show up in compiz manager.

First, I was able to install by going to Applications>Accessories>Terminal and running each line in your post one at a time, being sure to type everything in correctly.

After installing, the effect was really subtle as the windows hardly stood off the cube. Then tried adjusting some of the settings in the plugin, which didn't affect anything. I reboot my system after reading some of the other posts about having to do so before settings changes are allowed. After rebooting, compiz wouldn't start at all, couldn't enable desktop effects.

Wellll... I remembered that before I had rebooted, I had also downloaded a restricted video driver for my ATI 9600 (argh! stinkin' closed source software). I looked up the ATI driver in Synaptic Package Manager and uninstalled it. Rebooted again. Enabled desktop effects, and, ta-da! Gorgeous 3D windows adorned my desktop cube! Everything running normal now... but in 3D ;)

The lesson of this is, trust your open source community friends, and don't rely on closed source drivers *unless* you *know* they work.

Thanks again ArielTM

Cheers!

---

### Post by 5h4rk on 2008-03-30
> **UltraAnders said:**
> Thanks OP. This worked a treat. Quick reset needed to get Window Space changes working (as mentioned by others in thread). \\:D/

How do you ¨quick reset¨ CF?

---

### Post by CC_machine on 2008-04-10
You NEED to type "y" not "Y"
anything apart from "y" makes it abort.
Linux is case sensitive, remember!!

---

### Post by djscribe on 2008-04-13
ArielTM, you are on the money - this worked like a charm the 1st time around. Some workarounds take a bit'a tweakin; this is **not** one of those times.

 Thanx 4 that.

DJScribe
:cool:

---

### Post by teseracto on 2008-04-18
> **ArielTM said:**
> Hi
Saw that many want to install the 3d windows plugin on gutsy so i've made this script
hope this will work for you all
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

Or you can exract the attachment to your home dir and run it in terminal

[[IMG]http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.th.png[/IMG]](http://img153.imageshack.us/img153/6265/gutsy3dwindowsfn5.png)[[IMG]http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.th.png[/IMG]](http://img153.imageshack.us/img153/3222/gutsy3dwindows2lh8.png)

Good luck
Ariel

P.S
This is my first script so feedbacks will be appreciated

This worked great, thanks man, I had been looking for this all day!

---

### Post by szandor on 2008-04-18
> **mc4man said:**
> Works fine here - good job
@Derspankster - make sure auto.. plugin sorting is checked  (ccsm>preferences>plugins)

i reinstalled compiz and 3d plugin and forgot to do this. took forever to figure it out. so, don't forget to have reflection and 'plugin sorted' checked if your windows do not elevate and compiling/adding plugin was successful.

---

### Post by abhister on 2008-05-01
works gr8...thx...you need to run the commands one at a time...

---

### Post by goldenglow21 on 2008-05-04
I'm still somewhat new to linux. But I just updated to Hardy and now all the compiz desktop effects work great. So I was wanting to get the 3D windows. But for some reason it doesnt work even though its enabled. Not sure if i need to edit some setting to get it showing as in this thread. Or should i just follow those commands to get it working?

---

### Post by gilang on 2008-05-27
i got problem with 3d windows on gutsy, like this
[img]http://pic16.picturetrail.com/VOL635/2414786/4766701/305777102.jpg[/img]

after i did clean install of hardy, everything just worked fine. no cut window again like pict above...thnks to hardy!

---

### Post by gilang on 2008-05-27
i think you should do fresh install to hardy
, easier way i think...

---

