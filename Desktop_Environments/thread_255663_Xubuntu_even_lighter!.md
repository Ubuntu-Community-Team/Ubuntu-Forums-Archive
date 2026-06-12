---
title: "Xubuntu even lighter???!"
date: 2006-09-11
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-09-11
I am trying to make a very light desktop environment. Free from apps and libraries that I do not need.

I have installed UbuntuServer, x-window-system-core, xfce4, xfce4-terminal, thunar, (& prelik + preload for the hell of it.)

But my system is not usable. No icons, no anything! It looks like crap!

What else is needed alon with it? I would like to make it look like the Xubuntu desktop minus the artwork (Ubuntu branding)

Do I need gtk? GDM? What about the Xfce version of synaptic file manager? Whenever I attept to download it it brings along 60mb of gnome libs.

---

### Post by orb9220 on 2006-09-11
Where is the desktop? You should have really installed from synaptic since you have a hit and miss of installed xfce componets.

Open term
sudo aptitude update
sudo aptitude install xubuntu-desktop

---

### Post by brucevangeorge on 2006-09-11
Yes, I know of that. But if I do it that way... I might as well install the Xubuntu CD instead.

Thing is that xubuntu comes with alot of crap. Services I do not need, firefox, tbird, gnomexcel (whatever its called). And I remove them anyway. But they leave alot of libraries and other dependencies that I will never use.


So I figure: Install the base then add whatever I need on top and nothing more.

---

### Post by kerry_s on 2006-09-11
> **brucevangeorge said:**
> I am trying to make a very light desktop environment. Free from apps and libraries that I do not need.

I have installed UbuntuServer, x-window-system-core, xfce4, xfce4-terminal, thunar, (& prelik + preload for the hell of it.)

But my system is not usable. No icons, no anything! It looks like crap!

What else is needed alon with it? I would like to make it look like the Xubuntu desktop minus the artwork (Ubuntu branding)

Do I need gtk? GDM? What about the Xfce version of synaptic file manager? Whenever I attept to download it it brings along 60mb of gnome libs.

Alot of that xfce stuff is tide together so it's pretty big to start. Gdm is a good login manager and can be set to auto log you in to xfce. if you don't want to use synaptic you can learn to use apt-get in stead of the gui. Did you trim down further after you installed? For example: you installed x-window-system-core so it will install all the x stuff, but you can uninstall all those other drivers you don't need. I'll usally  use synaptic>status>installed scroll down and uninstall everything i don't need, like the laptop stuff,wireless stuff, the xserver-xorg-video-? (i only keep vesa as a fall back,but i use nvidia) i don't think i will ever need all those drivers. Then you can also delete everything in /usr/shre/doc and /usr/share/man if you don't use it, i usally use the ones on line through my browser. I love running a light system too but i use fluxbox. Here's the way i usally do mine.

Install the server> log in after install and reboot>
sudo su  <to become root
nano /etc/apt/sources.list   <comment(#) out the cd and uncomment the other repos.
ctrl and x and y and enter  <to svae the changes
apt-get update
apt-get install x-window-system-core fluxbox gdm xterm synaptic
reboot
change session to fluxbox and login
first i go to gdm setup(apps>system>gdm setup) and set that up to auto log me in(security tab)
then i open synaptic and start uninstalling things i don't use, after that i reboot to make sure i still have a functioning system.
then i open synaptic and start installing just the basic stuff i want to use,firefox,gaim,w32codecs,mplayer,xmms,rox-filer,leafpad....
everything else i wait till i need them then i install as needed. 
Right now my whole system is only 634mb and i got most of the stuff installed, i just installed this setup yesterday(edgy server install) so i can play with edgy eft. :wink:  have fun

---

### Post by IYY on 2006-09-11
I like IceWM. It's as light as Fluxbox, but acts a lot like Gnome (or Windows, KDE, XFCE) and is more comfortable to use without a mouse.

---

### Post by brucevangeorge on 2006-09-11
Thanks.

What about you guys that use XFCE? Are there any addons that I need to add with it? Like icon packs? (I am a fan of the gnome icons.) Or color themes?

I find that XFCE is a great blend of performance & speed. I am not switching to flux or IceWM on my desktop. (Its overclocked athlon xp 1800+ 512ram, & geforce ti4600 ). Switching to an  even lighter gui doesnt seem like its worth the effort. It can easily handle what I throw at it.

Soooo...

What else need to be included with XFCE?

---

### Post by kerry_s on 2006-09-12
You can put what ever you want, it supports both kde and gnome apps as well. Just add the apps you want. To keep the size down you don't have to use only xfce apps you can try lighter apps that do the same thing.

mousepad=leafpad  <mousepad is based on leafpad and they both look the same,but leafpad is smaller.
xfce4-terminal=xterm(you have to have for failsafe terminal to work) and eterm  <eterm is smaller and faster with less libs but all the same uses.
xfce4 plugin monitors=conky  <one app that does all those monitoring jobs.

lets break it down->
xfce4= 61.0mb right off the back, it installs the base, filemanager(thunar), standard icons themes , and a backgroud setter.
With that in place you can start selecting smaller apps.
leafpad= 500kb
xtem=1016kb
conky=385kb
firefox=28.7mb
gaim=3711kb

if you do some of the other tricks i told you like uninstalling what you don't need and deleting the doc and man files(i usally get around 250mb back).
Other than that you just got to spend some time setting up what you have installed so it feels comfortable and looks good to you.  You really should get synaptic it may be big but it's so much easier to actually see everything. It shows you right on the bottom how much space it's going to use and how many apps you have installed(mine is 474 installed). I do alot of marking and unmarking just to compare the size. ;)  and install what i need when i need it instead of installing all up front.

---

### Post by brucevangeorge on 2006-09-12
Thank You kerry.

---

### Post by brucevangeorge on 2006-09-12
> **kerry_s said:**
> You can put what ever you want, it supports both kde and gnome apps as well. Just add the apps you want. To keep the size down you don't have to use only xfce apps you can try lighter apps that do the same thing.

mousepad=leafpad  <mousepad is based on leafpad and they both look the same,but leafpad is smaller.
xfce4-terminal=xterm(you have to have for failsafe terminal to work) and eterm  <eterm is smaller and faster with less libs but all the same uses.
xfce4 plugin monitors=conky  <one app that does all those monitoring jobs.

lets break it down->
xfce4= 61.0mb right off the back, it installs the base, filemanager(thunar), standard icons themes , and a backgroud setter.
With that in place you can start selecting smaller apps.
leafpad= 500kb
xtem=1016kb
conky=385kb
firefox=28.7mb
gaim=3711kb

if you do some of the other tricks i told you like uninstalling what you don't need and deleting the doc and man files(i usally get around 250mb back).
Other than that you just got to spend some time setting up what you have installed so it feels comfortable and looks good to you.  You really should get synaptic it may be big but it's so much easier to actually see everything. It shows you right on the bottom how much space it's going to use and how many apps you have installed(mine is 474 installed). I do alot of marking and unmarking just to compare the size. ;)  and install what i need when i need it instead of installing all up front.

Have you tried swiftfox instead of firefox? It loads in about 1/2 the time.

Also, is there a way to figure out what apps have not been used in the system? Let's say that you have been using it for a couple of months, and you have some applications like "telnet" that you never used. Is there some way to get the system to find files and libraries that have never been accessed in the past month, or whatever time period.

---

### Post by kerry_s on 2006-09-12
Yes, i use to use swiftfox, but now it doesn't get along with some of my plugins, i'm currently using the firefox 2 beta2, it's just as fast.

I wish there was. I usally just look up what it does on the web. I always get rid of telnet,ssh client,.. and the rest of that remote access stuff, i don't connect remotely and don't want any one else doing it. ;)  I've done installs a few times so i know basicly what i want or can get rid of, It takes a little trial and error sometimes but i'm sure you'll get the hang of it real quick. Just start by removing apps that don't remove anything else but itself. The description really helps so turn that on in the preferences in synaptic.

---

### Post by brucevangeorge on 2006-09-12
Is acpi needed for anything?

My computer does not have a controllable power supply...its a desktop. Should I remove it or do other applications depend on it?

---

