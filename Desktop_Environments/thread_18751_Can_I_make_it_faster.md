---
title: "Can I make it faster?"
date: 2005-03-08
forum: Desktop Environments
---

### Post by VancouverJim on 2005-03-08
I've just installed Ubuntu on an older machine (P3, 15GB drive, 64M RAM). It's unbelievably slow. I've read in a couple of places that it's Gnome that's making it so slow. Are there ways to speed the thing up?

---

### Post by bored2k on 2005-03-08
[QUOTE=VancouverJim]I've just installed Ubuntu on an older machine (P3, 15GB drive, 64M RAM). It's unbelievably slow. I've read in a couple of places that it's Gnome that's making it so slow. Are there ways to speed the thing up?[/QUOTE]
 Install xfce4, its basically gnome like but faster .

If that's not enough for you,  get blackbox, wich is incredibly light, but has a more or less big learning curve.

---

### Post by Qdlaty on 2005-03-08
1st of all, consider a SMALL memory extension (an extra 192 MB will make the thing).
Other way is to replace Gnome with less memory-consuming WM - FluxBox, BlackBox or (my favourite ;) Enlightenment.
Sorry, but 64MB is good for console system.

---

### Post by bored2k on 2005-03-08
[QUOTE=Qdlaty]1st of all, consider a SMALL memory extension (an extra 192 MB will make the thing).
Other way is to replace Gnome with less memory-consuming WM - FluxBox, BlackBox or (my favourite ;) Enlightenment.
Sorry, but 64MB is good for console system.[/QUOTE]
 Ouch

---

### Post by regeya on 2005-03-08
[QUOTE=VancouverJim]I've just installed Ubuntu on an older machine (P3, 15GB drive, 64M RAM). It's unbelievably slow. I've read in a couple of places that it's Gnome that's making it so slow. Are there ways to speed the thing up?[/QUOTE]

I hate to echo what others are saying, but I must:  Sorry, pal, but while WinXP can be fairly zippy in 128 MB of RAM, a standard GNOME desktop cannot (though there are rumors they're working on that.)

If buying new hardware is absolutely positively not an option, but you want a GNOMEish desktop, here's some things to consider:

[list]
[*]XFCE 4  (Fairly standard but lighter desktop)
[*]Dillo (light webbrowser, but nearly nonexistent css support...for now)
[*]AbiWord (Word processor)
[*]Gnumeric (Spreadsheet)
[*]Sylpheed (Light email client)
[/list] 

I've heard rumors that a GTKHTMLv2-based browser is on the horizon.  And I'm sure that other people can suggest various windowmanagers; it gets to be a holy war when people start talking fave windowmanagers.  If XDND support worked I'd probably be raving about Window Maker.  :D

---

### Post by silentstriker on 2005-03-08
I have to disagree with the notion that 64mb is for consoles only.  Though that is far from optimum, if you shut down all unnecessary services, you can manage.


Though not if you use GNOME.  I love GNOME, but it is definatly a resource-hog.  As others have stated, go with XFCE4.  It is basically GNOME-Lite, or Gnome without the fat.  I run a much better machine (1gb RAM), but still XFCE is best for me.  It has everything I need, and works almost like GNOME.

Goto [www.xfce.org](www.xfce.org).   They released a new version recently, and they have flash demo's online.  Looking through the flash demo's you will realize how nice it is.

To go directy to the flash demos, go here: [http://www.xfce.org/various/flash_demos.html](http://www.xfce.org/various/flash_demos.html)

---

### Post by az on 2005-03-08
To be honest, I never found XFCE to be that much faster than gnome.  Part of the problem is that fonts are rendered with GDK and this makes it slow.

[http://ubuntuforums.org/showthread.php?t=17213&highlight=pentium](http://ubuntuforums.org/showthread.php?t=17213&highlight=pentium)

You can disable antialiasing.  Do not use the panel, since this disables antialiasing, but you still end up using gdk.  The result is ugly and slow.  You must make the changes noted in the thread above.

So, here are my ten ways to make Ubuntu run faster on older hardware:

1-  Get more Ram.
2-  Use Icewm.  It is as fast as fluxbox, faster than XFCE and easy to use.  Right click on the desktop for the menu.
3-  Buy more ram on ebay.
4-  Disable font antialiasing
5-  Avoid bloated apps such as openoffice.  Use abiword.
6-  Double your ram.
7-  Find out what kind of screws hold the panel of your computer case.  You will need to know what screwdriver to use to open it to insert more ram.
8-  If you have another linux computer on your network, use the thin-client approach.  Basically, the programs run in the fast machine and the slow computer is just a graphical terminal.
9-  Use rox-filer or xfe as your file manger.  Use mc (midnight commander, if you do not mind the console).  Rox filer has a pinboard option that makes a great, responsive desktop.
10  Bump up your ram.

---

### Post by landotter on 2005-03-09
Gnome **will** run just fine with 128mb--I used it that way for a couple years. Of course, those panel applets can eat some major ram, and there are ways of reducing your ram usage within gnome.

XFCE4 isn't the lightest or my favourite light desktop--what it IS is rather newbie friendly--in the sense that you can just apt-get it and it's modular. Add all the stuff you want to the toolbar or not. Run the taskbar or don't. Everything's there to pick and choose. 

I'm running the newest Blackbox right now, and I while I don't recommend it to total noobs, fleshing it out with some extra schtuff makes it a lovely & pretty environment.

I made a script which adds these things to Blackbox:


xscreensaver --quiet & *unnecessary and fun.*
gnome-volume-manager & *automounts cdrs and cameras when you plug them*
fbpanel -p default & *light taskbar with pager, clock, tray, and launchers. 2mb suckage.*
wmnd -I ppp0 & *dockapp monitors modem*
wmweather -s kbna & *dockapp fetches weather info*
gnome-settings-daemon & *loads gnome/gtk settings, themes and such*
chbg -scenario .scenario & *clever program draws your wallpapers for you*
wmix $ *sound mixer dockapp*

I've also custom edited a short and concise right click desktop menu for launching apps with no cruft.

here's a screenie:

[img]http://photos5.flickr.com/6169234_4d4be49270_o.jpg[/img]
dockapps are auto-hidden

Yeah, that's a bit advanced--but shows how modular linux is. Build your own desktop environment if you don't like what's offered. I made what works for me. It happens to use 30 mb less ram than an average Gnome session, and 10mb more than a Fluxbox session, but the conveniences are worth those 10 mb to me.

;)

---

### Post by bored2k on 2005-03-09
That one looks good . How far behind is the apt-gettable blackbox? I might give this one a shot.

---

### Post by ctrlz on 2005-03-09
[QUOTE=landotter]

I made a script which adds these things to Blackbox:


xscreensaver --quiet & *unnecessary and fun.*
gnome-volume-manager & *automounts cdrs and cameras when you plug them*
fbpanel -p default & *light taskbar with pager, clock, tray, and launchers. 2mb suckage.*
wmnd -I ppp0 & *dockapp monitors modem*
wmweather -s kbna & *dockapp fetches weather info*
gnome-settings-daemon & *loads gnome/gtk settings, themes and such*
chbg -scenario .scenario & *clever program draws your wallpapers for you*
wmix $ *sound mixer dockapp*

[/QUOTE]

do you run this script in your .xinitrc?

---

### Post by landotter on 2005-03-09
[QUOTE=bored2k]That one looks good . How far behind is the apt-gettable blackbox? I might give this one a shot.[/QUOTE]
 There's the old one available in Universe, as is Fluxbox. Flux is more advanced in some ways--I just don't like the way it looks, and you can't turn off the panel like in Blackbox.

Blackbox is a breeze to compile, grab the 0.70 source from the website

Then in a console  "apt-get build-essential" gets you all your compiling doo-dads.

decompress your bb package with file-roller if you're a gui kind of guy, then:
 (in a console)
cd blackbox*
./configure
make
sudo make install

you can run it from a failsafe console, just type "blackbox" at the prompt, or add it to your gdm menu like I did here:
[http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox](http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox)

Configuring the fbpanel is a bit tricky, but if you read the website's instructions, it's actually straighforward.

I boot into a plain bb session and then use a script to start all of my additional programs, which takes about a second.

You can of course do this type of thing with Fluxbox or Openbox, which are available in Synaptic. ;)

I've still got full Gnome and KDE on my box for fun, but I most often boot Blackbox because it's soothing. :D

---

### Post by landotter on 2005-03-09
[QUOTE=ctrlz]do you run this script in your .xinitrc?[/QUOTE]
 No, since I don't want it to start with other window managers.

I saved it as .blackboxutils.sh in my home directory, and added it to my ~.blackboxmenu file.

I boot into a plain Blackbox session and then I can rightclick and start the script for a fancier session if I'm in the mood.

Maybe not the smartest way to do it, but it works for me. ;)

---

### Post by user_stu on 2005-03-09
[QUOTE=regeya]I hate to echo what others are saying, but I must:  Sorry, pal, but while WinXP can be fairly zippy in 128 MB of RAM, a standard GNOME desktop cannot (though there are rumors they're working on that.)

If buying new hardware is absolutely positively not an option, but you want a GNOMEish desktop, here's some things to consider:

[list]
[*]XFCE 4  (Fairly standard but lighter desktop)
[*]Dillo (light webbrowser, but nearly nonexistent css support...for now)
[*]AbiWord (Word processor)
[*]Gnumeric (Spreadsheet)
[*]Sylpheed (Light email client)
[/list] 

I've heard rumors that a GTKHTMLv2-based browser is on the horizon.  And I'm sure that other people can suggest various windowmanagers; it gets to be a holy war when people start talking fave windowmanagers.  If XDND support worked I'd probably be raving about Window Maker.  :D[/QUOTE]


Re Linux performance tips
Ubuntu live, Linux Mandrake, Suse etc. performance versus Windows XP:-

I have found Linux (including recent releases) to be slow as a desktop machine (compared to XP). The OS itself seems to take forever to boot, then the GUI takes forever to load (KDE or Gnome - and some of the other "lighter" window managers don't seem much better).  I just tried the live Ubuntu and chose the load into memory option and it ran MUCH MUCH faster than any previous (installed) Linux I have tried. It was then comparable to the Windows XP experience (even Open Office writer loaded almost as fast as Word 2003 does). I suppose ram is faster than disk, but the difference was phenomenal

Hardware P4 3Ghz 1Gb RAM; Athlon 600Mhz 512Mb ram

***** Can I get an installed version of Linux to be as quick (eg. Via optimisation or can it be told to load to RAM)?
Even the 600Mhz computer runs Windows XP and Office at a comfortable speed – for modest uses I don't feel the system is lagging at all. However, run Linux on that machine (and I have tried several distributions) and the thing grinds away slowly (eg. Approx 1min to load writer; approx 15sec to load Mozilla)

---

### Post by az on 2005-03-09
[QUOTE=user_stu]Re Linux performance tips
Ubuntu live, Linux Mandrake, Suse etc. performance versus Windows XP:-


***** Can I get an installed version of Linux to be as quick (eg. Via optimisation or can it be told to load to RAM)?
Even the 600Mhz computer runs Windows XP and Office at a comfortable speed – for modest uses I don't feel the system is lagging at all. However, run Linux on that machine (and I have tried several distributions) and the thing grinds away slowly (eg. Approx 1min to load writer; approx 15sec to load Mozilla)[/QUOTE]

Live cds cannot be compared to an installer version.  A live cd is like a freakshow.  Very uselful, but do ot compare it to the real deal.  Install Ubuntu.

Ubuntu and Debian run much faster than mandrake, Suse or redhat.  They use a simpler kernel and have less sh*t running to take up cpu power.



Insofar as the initrc scripts and blackbox, Icewm has a neat feature.  It runs a startup script at startup.  You can put whatever you want in it.

Like

gkrellm &
rox -p=1


The file is /home/yourusername/.icewm/startup
Make it executable and restart icewm (CTRL-ALT-Del)

---

### Post by VancouverJim on 2005-03-09
Thanks for the ideas everyone. Yeah, I was pretty sure that more RAM would fix it up. Luckily it ain't my machine - I wouldn't be caught dead with 64MB. I wouldn't be caught dead with under half a gig actually. Anyways, it was a friends old machine, I stuck Ubuntu on there to see what it would be like. Now I know. Sloooooooowwww. I'll try putting it on my second drive on my machine, see if it whips along.

---

### Post by ioliver on 2005-03-12
If you're after a ultra-light distro you could try Puppy Linux. There is a new version that runs from ram and saves changes back to extra CD-RW partitions when you shut down.
Ian

---

### Post by EddieX on 2005-04-15
[QUOTE=landotter]There's the old one available in Universe, as is Fluxbox. Flux is more advanced in some ways--I just don't like the way it looks, and you can't turn off the panel like in Blackbox.

Blackbox is a breeze to compile, grab the 0.70 source from the website

Then in a console  "apt-get build-essential" gets you all your compiling doo-dads.

decompress your bb package with file-roller if you're a gui kind of guy, then:
 (in a console)
cd blackbox*
./configure
make
sudo make install

you can run it from a failsafe console, just type "blackbox" at the prompt, or add it to your gdm menu like I did here:
[http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox](http://ubuntuforums.org/showthread.php?t=18626&highlight=blackbox)

Configuring the fbpanel is a bit tricky, but if you read the website's instructions, it's actually straighforward.

I boot into a plain bb session and then use a script to start all of my additional programs, which takes about a second.

You can of course do this type of thing with Fluxbox or Openbox, which are available in Synaptic. ;)

I've still got full Gnome and KDE on my box for fun, but I most often boot Blackbox because it's soothing. :D[/QUOTE]


I suggest you use checkinstall wich will replace the make install and also create a debian package wich will be installed. And also EASY to uninstall through apt, synaptic etc..

Check install way:
fetch source
./configure + options
make
sudo checkinstall -D

Thats it ;) 
It simply RULES

---

### Post by defkewl on 2005-08-04
Is xfce available in ubuntu repository?

---

### Post by DJ_Max on 2005-08-04
[QUOTE=defkewl]Is xfce available in ubuntu repository?[/QUOTE]
 Yes, apt-get install xfce4

---

### Post by fishfork on 2005-09-05
Lots of good tips here. I'll add mine:

If you use Firefox, uninstall the ubuntu version from synaptic, go to mozilla.org and download the binary from there. Dead easy, you get a nice user friendly installer as well. I recommend installing it to /opt/firefox or /usr/local/firefox so you know where it is.  I really found that version to be **much** faster and generally more responsive on my old machine (AMD K6, 450MHz).

---

### Post by whiterabbit on 2005-10-13
Digging an old thread up but I'm sort of in the same boat.

I'm running Ubuntu on my desktop, which is great.  Very stable, fast and I haven't touched my XP partition in a while.

I'm also running it on my Thinkpad T20 (PIII).  It's running a speed of 700mhz with 256mb RAM.  Takes forever to boot up but it's not all that bad when Gnome's up and running.  However, Win2k runs a whole lot better on this notebook yet I'd hate to have to go back to it.  I'll be picking up some more RAM soon so I'd love to hear if it has helped the original poster.  Please report back if you get the chance.

As for trying another desktop environment(xfce4), how easy is it to get up and running once installed?

---

### Post by landotter on 2005-10-13
[quote=whiterabbit]Digging an old thread up but I'm sort of in the same boat.

I'm running Ubuntu on my desktop, which is great.  Very stable, fast and I haven't touched my XP partition in a while.

I'm also running it on my Thinkpad T20 (PIII). It's running a speed of 700mhz with 256mb RAM. Takes forever to boot up but it's not all that bad when Gnome's up and running. However, Win2k runs a whole lot better on this notebook yet I'd hate to have to go back to it. I'll be picking up some more RAM soon so I'd love to hear if it has helped the original poster. Please report back if you get the chance.

As for trying another desktop environment(xfce4), how easy is it to get up and running once installed?[/quote]

Just open up synaptic and install xfce4-desktop or fluxbox or whatever you want to try, and you can choose such a session upon login. It's possible to have as many environments installed as you and your HDD fancy.

I do find XFCE faster than Gnome, but it depends on how many components of it that you choose.

BTW, the the XF filemanager is horrendous, do install "Rox" instead--it's what most of us do that use XFCE.

That said, I use Gnome 95% of the time, as it's very relaxing and logical, Runs like a champ here on 1.1ghz/256mb.

You can disable some services you don't use and watch out for too many panel applets, they can hinder performance.

---

### Post by az on 2005-10-13
Enable universe and install xfce4.

The tell GDM to pick the xfce session instead of the default gnome session.

---

### Post by whiterabbit on 2005-10-13
In XFCE now.  

sudo apt-get install xfce4 worked well.  Need to get used to the commands.

It is soooo much quicker than gnome so I'll see how it goes.  I can always switch back and forth I suppose.  

Yep.... loving Ubuntu very much.  

Cheers.

---

