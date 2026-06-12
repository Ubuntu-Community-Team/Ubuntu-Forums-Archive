---
title: "Just how light weight is Fluxbox"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Gotou on 2006-09-02
Hi!  In terms of ram, how much lighter is Fluxbox than KDE and Gnome?  Are we talking 10 megabytes of savings or just 10 kilobytes?

After adding a bunch of eye candy, icons and other Fluxbox compatible extras does Fluxbox get just as heavy as KDE and Gnome?

Thanks!

---

### Post by JonahRowley on 2006-09-02
You'll be saving many, many megabytes.  Fluxbox is very small, and some would argue more workable than a full-blown DE.  Of course, some of these gains are lost as soon as you start running K* or G* apps.  Gnome apps are a bit more modular, but KDE apps need to load the entire KDE API and start a daemon, which take a bit of resources.  Still, the desktops themselves take a lot of resources, which you can save by running a lightweight wm like fluxbox.  To test, run your desktop of choice with all the apps you use open, then use the free -m command to see how much memory you're using.  Repeat with fluxbox.

---

### Post by key on 2006-09-02
I like fluxbox a lot- the startup is fast and it is one of the fastest window managers. However, its speed and low memory usage are without a panel, without a desktop/filemanager, without support for HAL and pluggable usb drives, and some other things that KDE/Gnome have. Thats how light weight it is. And you have to edit lots of text files to get it set up the way you want. I kind of like that in a masochistic sort of way - but it is time consuming. Like you mentioned above - once you put all the icons and stuff in there, get your usb working, you are right back where you started with KDE/Gnome. Nothing comes for free :). Unless you run [e17]("http://www.enlightenment.org/") maybe...

Give fluxbox a try and see what you think. I find that you can slim down your KDE/Gnome desktop and make it feel fast like fluxbox and retain little things like the Desktop and handy access to USB drives. KDE in particular is quite snappy and quick to start if you turn off all the flashy stuff. I think it is on par with or better than xfce4 actually. I have an older laptop with 8Mb of graphics memory so eye-candy is pretty much out of the question for me.

It would be nice if someone would build a KDE that is highly optimized for speed. Include only the fastest settings, minimal window decorations, etc. Leave the nice things that don't slow KDE down, and get rid of the things that do. What ever happened to [KDE-light? ]("http://shots.osdir.com/slideshows/slideshow.php?release=425&slide=1")

---

### Post by gThree on 2006-09-02
Consider Openbox too.  Be open to altering your habits a little so you can leave the icons, the panel, and the desktop behind.  I find it much easier to focus on a given task in Openbox.  A good set of keyboard shortcuts takes care of the rest.

The "box" window managers do require some configuration, but it's easy once you get the hang of it.  Helps if you approach it by doing a little at a time, instead of everything all at once.

You may find xfe and gmrun useful.  Sorry I can't contribute any numbers on memory consumption.

---

### Post by mindtrick on 2006-09-02
It exactly worths trying.

---

### Post by Gotou on 2006-09-02
Thanks for the input everyone!

Yup, I'm begining to see how time consuming setting up Fluxbox can be the more I learn about it.

For the moment it looks like I'll be sticking with Gnome for my everyday stuff on the desktop computer.  For the times when I need as much system resources as possible I'll have a very application-specific Fluxbox set up.

My ancient laptop computer buried in the closet will be resurrected with DSL.  I plan to study it to better learn Fluxbox.

Any good, step-by-step, non-linux guru, "Bubba, jes doit like dis", Fluxbox "HowTo" websites you would recommend?  I'm still a Linux newbie in a lot of areas.

Thanks!

---

### Post by key on 2006-09-03
First, I would nose around the [fluxbox]("http://fluxbox.sourceforge.net/") site, just to get started. There is some info here but you'll find much more over at the [gentoo fluxbox wiki]("http://gentoo-wiki.com/HOWTO_Fluxbox"). Just ignore all the gentoo specific stuff. There is also useful wiki at [http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki) .

The ubuntu fluxbox is usable out of the box - but it needs some fine tuning. The menus need to be edited - like the KDE and Gnome menus, the flux menu comes with every app under the sun in some near arbitrary structure. There is a program with a GUI to do this, but I find it much easier to get in there with a text editor and delete a bunch of that crap. Next, you may want to set up the pager (fbpager), and a few styles. You can get more styles from [freshmeat.org]("http://themes.freshmeat.net/browse/962/").  

If you want some eyecandy try out adesklets or conky. I also find the unfortunately named 'slit' in fluxbox very useful. You can dock all sorts of [dockapps]("http://dockapps.org/") in there. [Gkrellm]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") too. 

have fun!

---

### Post by Gotou on 2006-09-09
Thanks key for the links and suggestions!  The ablility to tweak Fluxbox to my whims is very appealing to me.

---

### Post by Feanor on 2006-09-09
Waiting for a full stable e17, I'm using the one from cvs... Eyecandy and fast, but in kde there're many many tools that I can't live without ^^

Hope in future upgrades :D

this is how it was my e17 desktop yesterday on my laptop 

[http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=](http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=)

---

### Post by key on 2006-09-11
You might also want to play with openbox3.
I recently installed it from the repos and I have to admit - I may not go back to flux. 

In the end, I think this is a matter of presonal taste as both are lightweight, super fast, and similar in function. Just like flux, there is some text file editing to configure everything in openbox, but it is really great once you get it set up. To be fair, there are some GUIs to do some of it, but it is usally faster to just get in there with vi. If you are running straight flux or openbox, chances are this is your preferred method anyway.  

Pair openbox with rox-filer, and everything is super fast. I use thunar from time to time as well - also pretty fast and it can mount my USB drives. 

Maybe I'll switch back and forth. But I won't be back in KDE or Gnome anytime soon :)  .

---

### Post by DJiNN on 2006-09-14
> **Feanor said:**
> Waiting for a full stable e17, I'm using the one from cvs... Eyecandy and fast, but in kde there're many many tools that I can't live without ^^

Hope in future upgrades :D

this is how it was my e17 desktop yesterday on my laptop 

[http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=](http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=)


Hey, that looks pretty neat. How difficult was it to set up e17 on Ubuntu? and where did you get it from? Is it in the repos?

---

### Post by moore.bryan on 2006-09-14
> **key said:**
> You might also want to play with openbox3.
I recently installed it from the repos and I have to admit - I may not go back to flux. 
*did the same and never went back...*

---

### Post by Gotou on 2006-09-15
Ok, I'll check Openbox out too.

e17, that's the Enlightenment windows manager, right?  If so, it was too much strain on my ancient laptop (which is the primary reason for looking into Fluxbox).  My desktop can handle it though.

All in all, the biggest bottleneck is the guy typing at the keyboard. :rolleyes:

---

### Post by treris on 2006-09-19
I've just installed Openbox and didn't even realise it had started yet at first, because it is so nice and plain. I'm trying it out now, but I'm thinking of using it on an old laptop (p-2 333Mhz, 160mb ram and 4,5Gb hdd) which I intend to use as a thin client and backup pc for my normal desktop pc.

I think Openbox is gonna do just fine!!

---

### Post by skymt on 2006-09-19
I'm torn. I love Openbox, but I can't give up Fluxbox-style tabbed windows. I might even wind up making a patch to fix my dilemma.

---

### Post by moore.bryan on 2006-09-20
[I]it's a freakin' openbox revolution, man!  ;-)
(i just couldn't resist)
[/I]

---

### Post by key on 2006-09-20
I totally agree about being torn - I am as well. I am basically using both openbox and fluxbox now. I just semi-randomly pick one when I log in. 

Openbox seems to play slightly better with rox-filer pinboards than flux. But I could easily give up rox pinboards. (The rox-filer is fantastic BTW). 

Some things seem a little more snappy in openbox than flux - like the opaque window moving and resizing - especially under full load. In fact, openbox is pretty hard to bog down. Fluxbox is too, if you turn off the opaque window moving. Obviously, each are still a world of difference from gnome/kde. 

Fluxbox has the really nice tabbed windows feature, and really cool transparency effects to satisfy my eye-candy desires. It seems to have more accesible configuration options and great themes. I am not sure if this is a good or a bad thing since it leads to me spending waaaay too much time playing and making themes.  

So - is there a deciding factor between the two?  Fluxbox's tabs?  They are both good, so how does one choose between the two?

---

### Post by Gotou on 2006-09-21
OK, I've fiddled with Openbox a little and have come up with a "usuability" question/situation.

Since my old laptop has a stubborn video card that seems only able to display 800x600, many apps intended for more modern resolutions don't fit well on the little screen.

When I was running Openbox I opened a couple OpenOffice files , a few pics in Gimp, a couple layouts in Xara in full screen.  I was seeing how much more the laptop could handle without the gui overhead.

Anyway all apps were in full screen.  The annoying problem I ran into was that I would have to reduce an app so I could right click on the desktop to start more apps or to move to another desktop.

Fluxbox has a taskbar that makes this easier but I like having as much screen space available as possible on the old laptop.

Are there keyboard shortcuts to maximize/minimize an app and switch to another desktop?

How do you folks get around in Openbox?

---

### Post by key on 2006-09-21
I use the alt-tab to get around, but I hear what your saying. My laptop also has precious screen real estate. I map all the apps I use frequently quick keys. I do the same in fluxbox. That way I don't have to reach for the mouse/trackpad as much. Now if I could only remember all those key maps :) 

You can program the keys to pop up the desktop menu, which may be superior to the current alt-tab function. There is a how to here. 
[http://ubuntuforums.org/showthread.php?t=75471](http://ubuntuforums.org/showthread.php?t=75471)

Also - you can run a panel at 95% width and use those little bits of screen in the corners to get to your menus. I do that sometimes too.

---

### Post by moore.bryan on 2006-09-21
*many of us ob users choose either fbpanel, fspanel, perlpanel, or pypanel as our "taskbar."  i use pypanel and love it; very customizable.  i found it useful to edit the rc.xml file for ob and put a keybinding on the windows key to have it open my right-click menu.  very useful.*

---

### Post by Gotou on 2006-09-24
Got another usabliltiy question.

How do you configure the screensaver and screen resolution?

I like the ablility to "lock" the desktop with a screen saver by using a mouse click without waiting for the idle time limit to pass.


The screen resolution matter:

I've been trying Fluxbox and Openbox on my desktop.  Problem I run into is when I move the mouse too far to the right the screen shifts to the left.  When I right click on side a context menu appears over on the opposite side.

Also when I click and drag a window it can go half way off screen.

What files do I edit and where are they?  The configuration files seem scattered.

Thanks!

---

### Post by az on 2006-09-24
Icewm is every bit as performant as any of the window managers mentioned here and is more intuitive to use.  It also plays really well with rox filer pinboards.

I find it better looking, too.

---

### Post by kerry_s on 2006-09-24
> **Gotou said:**
> Got another usabliltiy question.

How do you configure the screensaver and screen resolution?

I like the ablility to "lock" the desktop with a screen saver by using a mouse click without waiting for the idle time limit to pass.


The screen resolution matter:

I've been trying Fluxbox and Openbox on my desktop.  Problem I run into is when I move the mouse too far to the right the screen shifts to the left.  When I right click on side a context menu appears over on the opposite side.

Also when I click and drag a window it can go half way off screen.

What files do I edit and where are they?  The configuration files seem scattered.

Thanks!

"How do you configure the screensaver and screen resolution?"
Have you tried xscreensaver?

"I've been trying Fluxbox and Openbox on my desktop."
Which one are you trying to configure?

"What files do I edit and where are they?  The configuration files seem scattered."
The files are all in on place
Fluxbox= /.fluxbox/
openbox= /.config/openbox

---

### Post by key on 2006-09-25
Gotou-

I think your screen resolution problems can be fixed by editing your /etc/X11/x.org.conf file. Make sure you have the correct driver and set the screen resolution and if need be, the size. You can set the size using :
     DisplaySize    260 195
in the monitor section of xorg.conf .
The two numbers denote your screen size in mm. Don't use these numbers unless you have a pathetically small laptop screen like me :) .

You can lock your screen with xscreensaver. I think there is a command argument that you can use to lock the screen directly, check in the xscreensaver docs. You can bind this command to a key combination or mouse click, or put it in a menu.

For configuration, I the gentoo pages here are good:
[http://gentoo-wiki.com/HOWTO_Openbox](http://gentoo-wiki.com/HOWTO_Openbox)
[http://gentoo-wiki.com/HOWTO_Fluxbox](http://gentoo-wiki.com/HOWTO_Fluxbox)

---

### Post by WalmartSniperLX on 2006-09-25
duude I use like 90mb of ram on boot. Talk about insanely lightweight. I think openbox3 is even more lightweight tho, since it is built from the ground up, while fluxbox is based on blackbox

---

### Post by key on 2006-09-25
definitely. just check the binaries:

openbox:191k
fluxbox:1.2M

---

### Post by DJiNN on 2006-09-25
> **key said:**
> definitely. just check the binaries:

openbox:191k
fluxbox:1.2M

Wow!! That's quite a difference! But how do they "BOTH" compare against say "XFCE" or Gnome & KDE? Do you know>

I think i'm going to give OpenBox a try..... & IceWM for that matter! But i do love my Fluxbox. :)

---

### Post by skymt on 2006-09-25
> **DJiNN said:**
> Wow!! That's quite a difference! But how do they "BOTH" compare against say "XFCE" or Gnome & KDE? Do you know>

I think i'm going to give OpenBox a try..... & IceWM for that matter! But i do love my Fluxbox. :)

There's one big problem with Openbox: no panel. Fluxbox has the panel at the bottom, with a window list, system tray, workspaces, etc. Openbox doesn't have that. Personally, I use the XFCE panel with it, increasing the load slightly. Other popular choices include pypanel, perlpanel, fbpanel, gnome-panel and kicker.

Or, if you like, you can just do everything through menus and key commands.

---

### Post by Gotterdammerung on 2006-09-25
Fluxbox, Openbox, Blackbox are just window managers. It doesn't make any sense comparing them with KDE or Gnome, full desktops environments. If you wanna know how lightweight is a *Box window manager, compare it to Metacity and KWin, window managers of Gnome and KDE, respectively.

---

### Post by key on 2006-09-25
well... to be fair I am not sure you can just compare compiled binaries to each other *exactly*, but it is some indication. There are other factors, obviously. They use nearly the same amount of memory on my system.

Compared with gnome/kde/xfce4 both flux and openbox are super lean and fast. I like to use the xfce4 panel with openbox and use xfce-mcs-manager to keep my icons looking nice. You can use xfdesktop too and have a sort of super light xfce4. But then you lose your menu, so it is a trade off. 

Thunar is nice with openbox because it is hal-aware and mounts usb drives. Rox is better (IMHO) and faster, but not so good about mounting my external drives. you can configure it with pmount, but it seems like a real pain. I use rox when I don't have to mount anything.

You can try using openbox or fluxbox as the window manager in gnome or KDE too.

---

### Post by Gotterdammerung on 2006-09-25
> **key said:**
> well... to be fair I am not sure you can just compare compiled binaries to each other *exactly*, but it is some indication. There are other factors, obviously. They use nearly the same amount of memory on my system.

Compared with gnome/kde/xfce4 both flux and openbox are super lean and fast. I like to use the xfce4 panel with openbox and use xfce-mcs-manager to keep my icons looking nice. You can use xfdesktop too and have a sort of super light xfce4. But then you lose your menu, so it is a trade off. 

Thunar is nice with openbox because it is hal-aware and mounts usb drives. Rox is better (IMHO) and faster, but not so good about mounting my external drives. you can configure it with pmount, but it seems like a real pain. I use rox when I don't have to mount anything.

You can try using openbox or fluxbox as the window manager in gnome or KDE too.

Since you can use *Box as KDE or Gnome WMs, it is possible to compare *Box, KWin and Metacity concerning to memory allocation. 

Maybe using KDE as the base system, and just substitute KWin with each *Box and them with Metacity. This process will give a better idea of the amount of memory each WM consumes.

---

