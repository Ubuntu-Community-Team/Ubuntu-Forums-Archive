---
title: "Wanted: Gnome Mac Osx Dock"
date: 2006-01-09
forum: Desktop Environments
---

### Post by AMCDeathKnight on 2006-01-09
I am looking for an easy to get apt MAC Dock for gnome. I am trying to get my Ubuntu looking like MAC as much as possible the dock is the last thing I need. I have tried to get engage but comes up with a whole lot of errors and I dislike gdesklets Starterbar. 

Please if someone knows where I can get it from do not hesitate to post. :D

---

### Post by art on 2006-01-09
Although I am having troubles understanding people who try to get their linux look like OSX, here is what I know. There is gdeskltes 
[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)


as well as adesklets with **yab** and **modubar** here

[http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html)

EDIT: Sorry didn't see you don't like gdesklets...

---

### Post by AMCDeathKnight on 2006-01-09
Got this error when tried to apt-get it:

 Couldn't stat source package list [http://j.portalier.free.fr](http://j.portalier.free.fr) testing/main Packages (/var/lib/apt/lists/j.portalier.free.fr_debian_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

I tried apt-get update but did not work still same error. adesklets was not installed.

---

### Post by codejunkie on 2006-01-09
[QUOTE=AMCDeathKnight]I am looking for an easy to get apt MAC Dock for gnome. I am trying to get my Ubuntu looking like MAC as much as possible the dock is the last thing I need. I have tried to get engage but comes up with a whole lot of errors and I dislike gdesklets Starterbar. 

Please if someone knows where I can get it from do not hesitate to post. :D[/QUOTE]
try kxdocker it works under gnome now [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php)

---

### Post by crispy_420 on 2006-01-09
Or kooldock.

[http://www.kde-look.org/content/show.php?content=12097]("http://www.kde-look.org/content/show.php?content=12097")

It's for kde but I think it works in gnome too.
Just a thought, I'm no pro but I don't see it would not work. I don't use one in ubuntu but I did in FC4 in the past.

---

### Post by AMCDeathKnight on 2006-01-09
How would I get Kooldock installed? Im sorta a Linux newbie

---

### Post by handy on 2006-01-09
If you search the forums, there is a thread that goes all the way through this to the very satisfactory end.

handy

---

### Post by codejunkie on 2006-01-09
[QUOTE=AMCDeathKnight]How would I get Kooldock installed? Im sorta a Linux newbie[/QUOTE]
kooldock dosn't work in ubuntu using gnome if you use kde it should be fine and you have to compile it just search the forums for "kooldock" without the quotes and there are instructions posted somewhere.

---

### Post by AMCDeathKnight on 2006-01-09
Any other alternatives then?

---

### Post by codejunkie on 2006-01-09
**kxdocker** but you'll still have to compile it because the version in synaptic dosen't support gnome that well but version 0.39+ does it's pretty easy to compile there's a guide floating around here on how to do it, and if i get the time i'll make a .deb package of the newer version and post it.

---

### Post by codejunkie on 2006-01-09
Here's the .deb package for kxdocker i mentioned earlier, it's seems to run fine for me but i make no guarantees, so you use it at you own risk.
to install it extract the package open a terminal and cd to the dir where you extracted the files and run ```
sudo dpkg -i *.deb
``` if it gives you any errors when installing please post them here and i'll try and help you figure it out.
[http://rapidshare.de/files/10702452/kxdocker0.39-deb.tar.gz.html](http://rapidshare.de/files/10702452/kxdocker0.39-deb.tar.gz.html)

---

### Post by jan-banan on 2006-01-09
i tried your package and it worked, but is there any way i can make it work for gnome without changing the commands? because only xmms is clickable, the others just jumps even though i have the program :confused:

---

### Post by linuxden on 2006-01-09
[QUOTE=AMCDeathKnight]I am looking for an easy to get apt MAC Dock for gnome. I am trying to get my Ubuntu looking like MAC as much as possible the dock is the last thing I need.[/QUOTE]

AMC,

Hi, I am not trying to start a war or anything... (disclaimer done)

I have been using linux for a while, and have always wondered why noobs want to make there desktop look like mac osx??? now you seem like a cool guy....

Do you have a reason to make it look like OSX or is it because you find OSX to be the most pleasing graphicaly or what ???

Simple curiosity...

I myself have never tried to emulate mac OSX ... I do use the gdesklets starterbar because its a useful thing to keep my starters neatly organized.... But not to emulate OSX....

Rememebr4 its not a dig at you or anyone for that matter....

---

### Post by codejunkie on 2006-01-09
[QUOTE=jan-banan]i tried your package and it worked, but is there any way i can make it work for gnome without changing the commands? because only xmms is clickable, the others just jumps even though i have the program :confused:[/QUOTE]
unfortunately you may have to edit commands manually, because this app was designed with kde in mind not gnome. and the developer just recently started trying to make work on other desktop enviorment's. it is themeable though so you might try checking out his website and maybe you'll find one made for gnome.
[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php)

---

### Post by leech on 2006-01-09
[QUOTE=ubuntulifestyle]AMC,

Hi, I am not trying to start a war or anything... (disclaimer done)

I have been using linux for a while, and have always wondered why noobs want to make there desktop look like mac osx??? now you seem like a cool guy....

Do you have a reason to make it look like OSX or is it because you find OSX to be the most pleasing graphicaly or what ???

Simple curiosity...

I myself have never tried to emulate mac OSX ... I do use the gdesklets starterbar because its a useful thing to keep my starters neatly organized.... But not to emulate OSX....

Rememebr4 its not a dig at you or anyone for that matter....[/QUOTE]

I don't know what his reasons are, but I tried the Mac OS X look alike because.... I can :D  The beauty of the Linux desktop is that you can configure it however you want.  It was more of a challenge thing than anything else.  Of course I don't run my computer as that, but I just wanted to see if it could be done.  I much prefer just the Gnome default to anything else.

Leech

---

### Post by art on 2006-01-09
Please don't think that i am trying to offend anyone, but the thing is that you **cannot** make linux look like OSX. Whatever one does looks like a cheap copy of it. And I think the effort spent by so many people on trying to make linux look like OSX could have been spent better if they tried to make linux desktop look unique (which many people actually do, big thanks to them) and subject of envy from OSX and others. OSX wasn't trying to copy anyone when created their desktop...

---

### Post by linuxden on 2006-01-09
[QUOTE=art]Please don't think that i am trying to offend anyone, but the thing is that you **cannot** make linux look like OSX. Whatever one does looks like a cheap copy of it. And I think the effort spent by so many people on trying to make linux look like OSX could have been spent better if they tried to make linux desktop look unique (which many people actually do, big thanks to them) and subject of envy from OSX and others. OSX wasn't trying to copy anyone when created their desktop...[/QUOTE]

;o)

---

### Post by leech on 2006-01-09
Actually you CAN make it look just like OSX (check out baghira for KDE) But it doesn't neccesarily ACT like OSX (no cool effect when minimizing windows like OS X, which personally I think is the best feature of the OS :D.  Well, that and boot times, but then I only ever played with it on an x86... ok I know that's not legal, per se, but it's not like I actually used it for anything just wanted to play with it, but it booted in about 5 seconds!)

Leech

---

### Post by linuxden on 2006-01-09
Leech,

I can understand to want to emulate OSX as a challenge... 

But for me when i decide what i want my desktop to look like i create something orignial and personal and that is a challenge in itself... (thats for me.....)

Anyways clearlooks is a pretty cool Gnome theme....

---

### Post by art on 2006-01-09
[QUOTE=leech]Actually you CAN make it look just like OSX (check out baghira for KDE) 
Leech[/QUOTE]
You wanna bet:) Even in baghira I can show you lots of things, the presence of a menu to start with (no menu per se in OSX) that are NOT OSX. And when I say look like I mean look  with all the graphical features, like the genie effect you are refereing to (actually I read recently that the genie effect might be in next GNOME versions). Sorry for making this thread into a discussion...

---

### Post by AMCDeathKnight on 2006-01-09
I want it to look like a MAC because my friend brought a MAC and I find it really good with the GUI and all. All im stuck with is Gnome so I am trying my best to make it look like MAC for my own pleasure.

---

### Post by tukster on 2006-01-09
ah mac this and mac that, i don't think highly of OSX looks and feels. i have an iMac at work with tiger, and its a os for kiddies lol, of course mac lovers, i mean't no offense :razz: 

really its just a couple of graphic tricks and gradients that people like so much. but if u dig in osx, its no better than any other current os. and i have no wish to  emulate it on my box. but thats just my 5 cents.

[QUOTE=art]... And I think the effort spent by so many people on trying to make linux look like OSX could have been spent better if they tried to make linux desktop look unique...[/QUOTE]
\\:D/ =D>

---

### Post by linuxden on 2006-01-10
Mimicking is the biggest form of flattery... Your friend must feel real proud of his mac!!! 

Why dont you inform him that your brand new linux OS is as stable if not more (this could get us all into a big discussion) than OSX....

Perhaps Human is not such a nice theme... but once you start playing around staying clear of mimicking OSX you can get great looking desktops under gnome....

Of course your free to do what ever you please...

Enjoy Gnome what ever you do with it....

---

### Post by AMCDeathKnight on 2006-01-10
Thank you for your opinions I have quit trying to make it look like MAC OSX. Too much complications and instead have made it into a more darker more suited theme for me. What do you guys think?

[http://img300.imageshack.us/my.php?image=screenshot1pb.png](http://img300.imageshack.us/my.php?image=screenshot1pb.png)

---

### Post by leech on 2006-01-10
[QUOTE=art]You wanna bet:) Even in baghira I can show you lots of things, the presence of a menu to start with (no menu per se in OSX) that are NOT OSX. And when I say look like I mean look  with all the graphical features, like the genie effect you are refereing to (actually I read recently that the genie effect might be in next GNOME versions). Sorry for making this thread into a discussion...[/QUOTE]

Yeah, I know about that, and apparently you don't know that KDE can also put a non-menu menu at the top... yeah, I know that doesn't make sense.... It has the option to take the menu from the application and put that up top, just like it is on the Mac.  In fact, it even lists that as the option "Current application's menu bar (Mac OS-style)"

But as I stated, it can LOOK like it (after all, what's in a screenshot, you can make a linux DE look like just about anything these days) but it doesn't really act much like it.  

The only thing I couldn't get working quite right with KDE making it look like a Mac was that menu bar, it just didn't work like it was supposed to, but I think that's because baghira hasn't been updated for a while and doesn't work quite right with KDE 3.5  But it was pretty close.

Then I went happily back to my gnome desktop :D  because I just like it better.

Leech

---

### Post by jeremyclarke on 2006-11-11
This thread is kind of old but I found it while looking for a dock replacement and thought I'd leave a bit of an explanation for the gnome fans who don't understand the premises of macifying linux. 

Both Gnome and KDE are based on the "window" metaphor invented by M$ in 95. Each instance of an application is one window and they are all listed at the bottom (or top/side) of the screen. Clicking on the button for that window brings it to the front and closing a window exits the application and makes the window and button dissapear. This is totally obvious to people who use windows or linux and has been the standard for a long time. 

HOWEVER, Mac has always had a different sense of how applications work and used a strict application rather than window metaphor, so that you can close all windows of an app but it stays open till you explicitly kill it. The "dock" in OSX is not just eye candy but a fundamentally different way to interact with your programs. It assumes that you can handle your different windows and would rather have a clean taskbar than a cluttered task manager. It effectively requires things like tabbed applications (browsers, IM clients, text editors) but IMHO tabbed apps are better anyway (we all agree about browsers right? why not everything?). 

So at least for me using Linux as it is right now is just like using windows, which is just like kissing my ugly aunt, I'd rather do something else. The good things about linux have nothing to do with the design and interface elements lifted from windoze in the nineties and assuming that the way tasks are now managed is somehow the "real linux way" is kind of backwards to me. 

I actually spent some time on my last install trying to macify it but found that all the solutions were half-assed at best, effectively doing exactly what you're describing, adding silly visual hints at OSX without actually reproducing the valuable usability elements that keep me buying apple computers. Mac to me is not a shiny blue glass bubble on my buttons, it's a more robust way of dealing with your apps and processes. 

Also, a final point. Having a universal application menu at the top of the screen may seem weird at first but the fact is that getting to a menu at the top of a screen is EXTREMELY fast, you don't have to aim, just push the mouse up and you'll get there. When an app menu is in the window you have to carefully target the button and click. The difference might be less than a second, but the seconds add up over time and I for one notice it LIKE CRAZY when I use an OS that doesn't have a universal menu. It also wastes screen space (and adds clutter) to have menus in every window when you usually have to click on the window once before you can use the menu anyway.

---

### Post by jackkerouac on 2006-11-11
Have you tried kiba-dock?

[[IMG]http://img20.imageshack.us/img20/9857/screenshotji6.th.png[/IMG]](http://img20.imageshack.us/my.php?image=screenshotji6.png)

---

### Post by dbbolton on 2006-11-12
gdesklets is pretty lame to me. i constantly have to kill the python process via task manager because it often freezes. its launcher leaves much to be desired in terms of aesthetics and functionality.

adesklets is a complete waste of time. i had to install so many loosely correlated packages that it ultimately was also a waste of storage.

my opinion is that docks basically give the following:
launchers
list of open windows
system monitors
maybe a clock or weather

and the default gnome panels have those capabilities already. after attempting to delve in to the dock world, i've settled (and much more happily, i might add) with the default gnome panels.

---

### Post by Nonno Bassotto on 2006-11-14
> **jeremyclarke said:**
> Both Gnome and KDE are based on the "window" metaphor invented by M$ in 95.

Of course not. The feature was already present at least in the macs and windows for dos and maybe before.

---

### Post by buzlink on 2006-11-14
> **Nonno Bassotto said:**
> Of course not. The feature was already present at least in the macs and windows for dos and maybe before.

](*,) 
Any Linux system that I have ever used or tried in the past 10yrs have all tried to emulate the Microsoft Windows feel in some form.  I imagine this is done to keep things familiar for people jumping over to Linux.

The thing about emulating or using OS X like dock in Linux for me is fining a way to access programs and documents easily.  Apple found a smart useful way in doing this, so naturally one would want to carry this idea over to systems that do not use it.  If Linux had a smart innovative way to access programs easily other than the terminal I'm sure people would want to emulate that method in other operating environments.

:-D

---

### Post by macewan on 2006-11-21
Kiba-dock is an option

---

### Post by Rodneyck on 2006-11-22
> **buzlink said:**
> ](*,) 

The thing about emulating or using OS X like dock in Linux for me is fining a way to access programs and documents easily.  Apple found a smart useful way in doing this, so naturally one would want to carry this idea over to systems that do not use it.  If Linux had a smart innovative way to access programs easily other than the terminal I'm sure people would want to emulate that method in other operating environments.

:-D

You do not need to emulate a mac to get quick access to your favorite functions. I customized the gnome (Ubuntu) bottom menu by making it transparent, resizing (unchecked “expand” option) and added my favorite apps/icons to it.  There, a task bar that is completely gnome/linux!

Sure it does not animate, wiggle or dance around, but do you really need that?  As I have learned, eye candy is bloat and usually taxes the systems resources which is probably why the new Windows Vista is "suggesting" at least 2 gig of ram for optimal performance.

---

### Post by Frem on 2006-11-30
Not all eye candy is bloat. I've seen the latest version of OS X running quite speedly on a 400MHz computer. You don't need 2 gigs of ram for the pretty.

---

### Post by Rodneyck on 2006-11-30
Yes, but I bet it would run faster without all those special effects.

---

### Post by Bob_Mendon on 2006-12-01
I find these comments for and against an OSX look or functionality nearly insulting. Do you comment on the merits of wearing one brand of shirt over another? How about driving one kind of car as opposed to another. Am I a Ferrari wannabe if I drive another type of less expensive sports car?

Linux is generic in and of itself. The desktop choices are a simple matter of choice since they offer the same functionality. The themes are a way of personalizing that functionality. It is ridiculous to criticize people for their own personal choice. 

If you want to make a statement regarding your preference of operating systems, do it in another thread where someone asks specifically about the topic. Hijacking a thread to advance your own prejudicial views doesn't seem right. I was interested in finding an OSX dock when I started reading this thread and all I really got was a bunch of proselytizing.

---

### Post by Rodneyck on 2006-12-01
> **Bob_Mendon said:**
> I find these comments for and against an OSX look or functionality nearly insulting. Do you comment on the merits of wearing one brand of shirt over another? How about driving one kind of car as opposed to another. Am I a Ferrari wannabe if I drive another type of less expensive sports car?

Linux is generic in and of itself. The desktop choices are a simple matter of choice since they offer the same functionality. The themes are a way of personalizing that functionality. It is ridiculous to criticize people for their own personal choice. 

If you want to make a statement regarding your preference of operating systems, do it in another thread where someone asks specifically about the topic. Hijacking a thread to advance your own prejudicial views doesn't seem right. I was interested in finding an OSX dock when I started reading this thread and all I really got was a bunch of proselytizing.

The opinions here are just that, opinions. You ARE on a linux forum.  I do weight products on appearance and other standards. Lighten up, mac user.  :o

---

### Post by Bob_Mendon on 2006-12-01
"The opinions here are just that, opinions. You ARE on a linux forum. I do weight products on appearance and other standards. Lighten up, mac user."

Of course I'm on a linux forum. Do you think I don't know where I am? How you weigh your products is your business. Like anything else there is a time and place to do that sort of thing. I was pointing out that it wasn't exactly appropriate for this thread. Apparently, you failed to "get" that from what I wrote.

I am not a mac user nor do I play one on TV. Would I own a mac? If I could afford it, yes. It does what it does very well. I guess you also failed to notice my signature block as well. Take another look, it refers to a well known linux distro. 

So....anybody have a suggestion for a good OSX style toolbar?

---

### Post by blackmh on 2006-12-02
kxdocker is what you want. It works excatly as dock on macs. Although is a bit*h to set it up as you want it but works like charm.

[http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download)
Download sources

Dependencies are "build-essential xlibs-dev libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev"

Also search this forums for howto for better understanding of setup after compilage :)

Here is a guide

[http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

Edit: since this guide doesn't produce satisfactory results, I'll write guide later on as I spent couple of hours to sort things  correctly.

---

### Post by blackmh on 2006-12-02
[http://blackmh.googlepages.com/kxdocker](http://blackmh.googlepages.com/kxdocker)

---

### Post by Bob_Mendon on 2006-12-02
Thanks for your suggestions. I tried Kibadock and wasn't really impressed. Bouncy cute icons are not my thing. I just like the functionality that you get from the OSX doc. So, I looked around, did a little homework and decided to install Kbuntu. I added an OSX style theme and icons and now I have a well working, nice looking desktop.

[IMG]http://www.mosinnet.com/snapshot1.png[/IMG]

---

### Post by ramjet_1953 on 2006-12-03
Hi, there!

Kooldock works fine for me in Gnome.
It also hides and pops up when you move the mouse curser outside of the bottom border.

Regards,
Roger 8)

---

### Post by hamzamusa on 2007-03-24
> **art said:**
> Although I am having troubles understanding people who try to get their linux look like OSX, here is what I know. There is gdeskltes 
[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)


as well as adesklets with **yab** and **modubar** here

[http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html)

EDIT: Sorry didn't see you don't like gdesklets...

dear art : Thanx alot for the alternative solution for gdesklets 
the aim of linux and opensource ( Open minded world ) is not to like or to hate it`s to try 
some people try to get their own Mac OSX alike docks stand alone application that`s all..

there is many alternatives indeed ...
    
* engage - provided by E17 ..and you can install it on your ubuntu - ( Tested On gnome and run on xfce as in dreamlinux ) ( Engage still more than good to list on top - at least it`s provided by E-17 and it`s My Favorite Desktop )
    * Udock is the working title for a new dock project for GTK+ environments, e.g. Gnome or XFCE
    * KXDocker is Mac OSX Dock alike for KDE
    * avant window navigator - Gnome Dock Fully Customized … ( simple install and use on ubuntu )
    * gnome Dock - an evolution of cairo dock .
    * cairo dock and update by the developer MacSlow 
    * starterbar provided by gDesklets and customized look by daniel christophis at gnome-look.org

[http://dr-hamza.net/linux-dock-like-mac-osx-how-to/](http://dr-hamza.net/linux-dock-like-mac-osx-how-to/)


but it`s all worth a try to see what`s the difference and what`s the new

---

