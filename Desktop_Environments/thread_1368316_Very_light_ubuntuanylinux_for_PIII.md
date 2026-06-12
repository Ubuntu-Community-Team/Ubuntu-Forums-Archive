---
title: "Very light ubuntu/anylinux for PIII"
date: 2009-12-30
forum: Desktop Environments
---

### Post by jbond007m3 on 2009-12-30
My dad is setting my mom up with an old pIII laptop with 128 ram.  He put xp on it and it runs like poop.  I am toying with puppy, dsl, a bunch of other distros so it will run like a half way decent box.  

Since it for my mother to check her email and such i need it to look like xp.  Gnome is the easiest to setup to resemble start menu, rightclick fo options.... all the normal xp stuff.
But gnome eats up too much ram for that little laptop.

There are so many linux distros out there.  Anyone running something very light that resembles xp a little in function and more in looks.

I dont want to scare my mom with something new.

I found some cool gnome mods that work, all i really need is a gnome linux that is light on the ram.  Or maybe a lighter GUI that it will be easy to mod to look like xp.

---

### Post by michaelzap on 2009-12-30
My favorite light distro for old machines is Dreamlinux XFCE:
[http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

You're right on the edge of their system requirements, but I've installed it on similar machines and it's worked very well.

It's based on Debian Lenny and is really fast yet full-featured. You'll want to keep Compiz off and probably turn off the Engage dock in Autostart Applications if you want it to look more like XP. XFCE menus are trickier to edit than Gnome's, but once you learn how it's not such a big deal. I just set up my sister-in-law's laptop with DL yesterday and deleting the various menu items that I thought might be confusing took me longer than anything else I did.

Puppy is also an OK option, but I much prefer a Debian distro on any machine that can handle one (which is practically any machine still worth using).

---

### Post by schmolch on 2009-12-30
128MB RAM?
If you care about the relationship between your Mom and your Dad you should upgrade that to at least 512MB !!!
Or get her a Netbook. They are shiny, women like that.

---

### Post by jbond007m3 on 2009-12-30
I agree, im gonna try and find some ebay ram to get it up to at least 256.  She has a quick desktop, she just wants something for sitting on the porch to check email, maybe stream music.  I told my dad about my netbook he just doesnt want to spend money on something that may get used once every few weeks or so.  If she uses it alot he will probably hook her up with a atom dell or something. 
I know even if i put karmic it will use less resources than xp.

---

### Post by Project PWNED on 2009-12-30
Debian netinstall with IceWM as the Window Manager.

---

### Post by schmolch on 2009-12-30
XFCE and a light Webbrowser (Chrome/Midori/Epiphany) will work fine on 256MB RAM.
Tell her to keep the webbrowser running so it does not need to be started every time and with a little luck Suspend-to-RAM will work and reduce waiting-time a'lot.
Also make sure there is no crap hugging resources that she wont need like Ubuntu-One, Tracker or whatever needless services.
Also a pink theme might be favorable for you.
Oh wait, we are talking about your mom, nevermind ;)

---

### Post by jbond007m3 on 2009-12-30
Im diggin the pink idea, girls like pretty things.

---

### Post by vnstudy on 2009-12-30
You have only 128 MB RAM right now? Oh my gold, it seemly becomes too old! Update your Pc harware and live with either Ubuntu or Kubuntu.

---

### Post by 3Miro on 2009-12-30
I got a nice computer back in 2001 that had 128MB of RAM. Windows 2000 worked well as well as Mandrake Linux 7, however, Xp requires minimum 256MB (and for anything pass SP1 even that is no enough). You are looking for a very small version of Linux (or alternatively an obsolete one).

For me, on my laptop, Firefox regularly takes over 100MB of RAM. I don't think you will be able to use that (unless you go with the old Mozilla browser, modern browsers wouldn't run). Flash is out of the question, this thing takes CPU time like nuts. Most of Hotmail/Yahoo have clogged their web-pages with adds and JavaScript that clog the CPU and RAM. Maybe if you use pine and/or lynx you will have no trouble, but I don't think this is a good idea.

Find better hardware, I am afraid this may be the only feasible solution.

---

### Post by MooPi on 2009-12-30
If your up for it download the Ubuntu minimal CD [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)
Use the Cd to create a minimal install then from command line add some essentials. 
```
sudo apt-get install gnome-core humanity-icon-theme network-manager firefox
```From this point you have a fairly simple gnome desktop, with the need to only add plugins and whatever strikes your fancy. It should be on the light side because it is not the full gnome desktop.
I'd like to add that if you really feel adventurous, maybe a frugal Openbox desktop would be fun. I have an Atom based ITX mini computer that boots to 45 mb. There isn't any panel or menu or dock, just an open file manager with program icons to choose from. Like I said it's lite and you won't even need to upgrade that ram. [http://s559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/](http://s559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/)

---

### Post by XubuRoxMySox on 2009-12-31
The minimal Ubuntu CD (it just installs the minimal Ubuntu system) with [LXDE]("lxde.org") is light and fast and familiar-looking for a user coming from Windows. It has been a little buggy on my system, and a lot of people have to un-mute the sound on startup, but if that's the only bug, it's a very small price to pay for such speed and ease.

The best implementation of minimal Ubuntu+LXDE I know of is called [Masonux]("http://sites.google.com/site/masonux/"), and I bet it would run fine on your momn's 'puter despite it's low resources. Earthpigg has done an awesome job with it.

LXDE is the most lightweight GUI desktop there is, and it's superb simplicity and "famailiar-looking" interface sounds like just the ticket.

-Robin

---

### Post by adam814 on 2009-12-31
I think your best bet is doing a minimal install then adding only what you need.  I recently set up a Debian machine that way using LXDE as a desktop environment and slim instead of gdm as a login manager.  When up and running conky showed less than 64MB of RAM in use (I want to say as low as 39MB, but I'm not entirely sure).  Just make sure you have an adequate swap partition, it will be needed.

---

### Post by kevinatkins on 2009-12-31
> **Project PWNED said:**
> Debian netinstall with IceWM as the Window Manager.
+1

It should run OK in 128MB but if you can, do try and up the RAM - you might find that memory for the old warhorse is a bit more expensive than that for modern machines but even if you only pop another 128MB in, it should make a big difference for relatively little outlay.

I had an old PIII 733MHz desktop machine with 384MB RAM running Ubuntu 8.04 quite happily a year or so back - even YouTube / Flash worked acceptably well!

---

### Post by Syndri on 2009-12-31
I had windows xp home edition sp3 on my PIII 733mhz, 128mb ram, 20gb hd
Anyway try these listed below:

*[http://www.planetwatt.com/](http://www.planetwatt.com/) *[I]
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://puppylinux.org/](http://puppylinux.org/)[/I][I]
[http://www.slitaz.org/](http://www.slitaz.org/) 
[http://www.simplicitylinux.org.uk/](http://www.simplicitylinux.org.uk/) 
[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/) 
[http://tinymelinux.com/doku.php](http://tinymelinux.com/doku.php) 			
[/I]*[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/) *

---

### Post by chris1379 on 2009-12-31
What speed is your laptop and how much RAM can it take? I have a PIII 700 w/256MB that runs Hardy OK but it's not snappy. It's using around 160MB at the desktop, so definitely not light. Let me know what you come up with.
 
Chris

---

### Post by Project PWNED on 2010-01-06
Celeron 400Mhz
256mb RAM
8gb hard drive

I installed IceWM on it and it was perfectly fine for a server. I didn't run Firefox on it, because all I needed was just something easier than going through all the virtual terminals and I didn't feel like using screen. With your P3, you will have better results.

I was using IceWM on systems like that back in the mid-late 90s and it still works solid like it does today.

In other words, IceWM FTW. (for the win)

---

### Post by virgilx on 2010-01-10
I would recommend upgrading your ram.  I have a couple of PIII running well with above 256 ram. The first is a server (hardy) without a gui running several services using approx 160mb of 384mb ram and doesn't use the swap hardly at all.  The second is a desktop  using 190mb of 512mb ram and works well with browsing, playing streaming music and flash video.  Google chrome uses half the resources as firefox and seems stable even for beta.  So PIII should get her by for most tasks with a little more ram even with a modern distribution.

---

### Post by Leppie on 2010-01-10
if you don't mind setting everything up yourself, i used to have a minimal debian lenny with e17.
after boot, with e17 running memory footprint was around 40mb (obviously also depends on which daemons you start).

---

### Post by t1nm@n on 2010-01-11
check these OS
austrumi and slitaz

also if u are looking for a low resourse DE try openbox or fvwm-crystal
:P:P

---

### Post by Telecaster72 on 2010-01-19
My vote goes to minimal + LXDE or why not a nicely set up Crunchbang with her programs easy accessible? I also agree with the large swap!! :-)

---

### Post by ms.deidre on 2010-01-21
> **schmolch said:**
> They are shiny, women like that.


we also like a respectable performance grrrr....

---

