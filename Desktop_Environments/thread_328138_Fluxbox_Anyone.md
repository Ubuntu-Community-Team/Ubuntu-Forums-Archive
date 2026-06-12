---
title: "Fluxbox Anyone?"
date: 2006-12-30
forum: Desktop Environments
---

### Post by teejay17 on 2006-12-30
Hello everyone, I'm just wondering if anyone has experience with Fluxbox on Ubuntu, and what they have to say about it? 
Currently I'm running Ubuntu 6.10 on an older IBM Thinkpad with a 4.5 gig hardrive and a Celeron processor, about 500 mb. And 92 Megs of RAM. It works great, although sluggish, but I can't complain--I understand my hardware limitations. 
I've tried Xubuntu, and although I liked it, I found it somewhat limited and that's why I switched back to straight Ubuntu. I also tried Kubuntu, and that was a disaster--talk about slow! Again, I'm back to straight Ubuntu;)
So now I'm researching Fluxbox, wondering if it's something I should try. I have 1.7 gigs left of free space on my hard drive; would it fit? Also, will it benefit?

---

### Post by taurus on 2006-12-30
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by teejay17 on 2006-12-30
> **taurus said:**
> [http://fluxbuntu.org/](http://fluxbuntu.org/)

Yes, I have visited this site; I'm looking forward to its release. However, I see that it is based on Feisty, so does that mean Fluxbox is not currently available for 6.10? Or even 6.06?
Is there something available in Synaptec?

---

### Post by taurus on 2006-12-30
```
sudo aptitude update
sudo aptitude install fluxbox
```

---

### Post by teejay17 on 2006-12-30
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install fluxbox
```

Thanks for that! I guess the only thing I have left to do now is to take the plunge and do the install, to see what Fluxbox is like. 
I wonder what the learning curve is like?

---

### Post by pharcyde on 2006-12-30
I use fluxbox exclusively.  I absolutely love it.  The one thing you will have to deal with is add/remove some items to your fluxbox menu directly since this does not happen automatically using apt sometimes.  Other than that it is absolutely fast and simple to use.

---

### Post by RevNomad on 2006-12-30
I tried installing Fluxbox on my laptop, runnning Edgy.  I get the workspace but no configuration options.  How do I set it up?

NTP](*,)

---

### Post by taurus on 2006-12-30
You need to add apps that you use all the time in ~/.fluxbox/menu.  Otherwise, install idesk and create some icons on your desktop so you can double-click them to run...

---

### Post by paparucino on 2006-12-30
> **pharcyde said:**
> I use fluxbox exclusively.  I absolutely love it.  The one thing you will have to deal with is add/remove some items to your fluxbox menu directly since this does not happen automatically using apt sometimes.  Other than that it is absolutely fast and simple to use.
I tried to use fluxbox, but I'm not able to set the wallpaper. (First I must install wallpaper then all other stuffs :-) ).

I tried to set fbsetbg in /.fluxbox/startup     nothing happens
I tried to set in /usr/local/share/fluxbox/init via session.screen0.rootCommand: fbsetbg -f /path/image.jpg    nothing
I tried to set in  /styles/Twice via  rootCommand bsetbg  /path/file.jpg     nothing

Can you tell me where that ... :evil: ... must be setted?

---

### Post by RevNomad on 2006-12-30
> **taurus said:**
> You need to add apps that you use all the time in ~/.fluxbox/menu.  Otherwise, install idesk and create some icons on your desktop so you can double-click them to run...

How do I run iDesk?
NTP:confused:

---

### Post by pharcyde on 2006-12-31
> **paparucino said:**
> I tried to use fluxbox, but I'm not able to set the wallpaper. (First I must install wallpaper then all other stuffs :-) ).

I tried to set fbsetbg in /.fluxbox/startup     nothing happens
I tried to set in /usr/local/share/fluxbox/init via session.screen0.rootCommand: fbsetbg -f /path/image.jpg    nothing
I tried to set in  /styles/Twice via  rootCommand bsetbg  /path/file.jpg     nothing

Can you tell me where that ... :evil: ... must be setted?

does running fbsetbg -f /path/file.jpg work in a terminal once fluxbox has loaded?

---

### Post by paparucino on 2006-12-31
> **pharcyde said:**
> does running fbsetbg -f /path/file.jpg work in a terminal once fluxbox has loaded?
Yes, it works. 
I've noticed a particular I didn't see before. After I login the wallpaper appears for one/two seconds then it's covered by the style.

---

### Post by Tux Aubrey on 2006-12-31
re: wallpaper

This can be set using the fbsetbg command in either the** init **or **startup** files (located in ~/.fluxbox directory.)

If you are using the Rox pinboard as a desktop (it comes setup with the default fluxbuntu install) you have to use a Rox folder icon (right click) to set your background.

If you can't work it out, post a copy of your startup file here for diagnosis.

re: menus

That first gray screen and an empty menu is a bit intimidating, isn't it?  

**fluxbox-generate_menu** should do it for you, but otherwise you should open or create the ** ~/.fluxbox/menu** file and start constructng it yourself.  The syntax is straight forward.  Eg.

> [begin] (Fluxbox)
      [exec] (Rox) {rox}
      [exec] (Eterm) {Eterm}
      [exec] (firefox) {firefox} </usr/share/pixmaps/mozilla-firefox.xpm>
 
[submenu] (wallpapers)
      [wallpapers] (~/.fluxbox/backgrounds/widescreen)
[end]
[submenu] (Terminals)
      [exec] (Eterm) {Eterm}
      [exec] (Aterm Transparent) {aterm -tr +sb -fg white -bg green &}
      [exec] (Gnome terminal) {gnome-terminal}
[end]

The wallpapers section is a cracker (but does not work if you are using Rox as a desktop)


Here's the "standard" fluxbox command menu sections that I use: 
> 
[submenu] (fluxbox menu)
      [config] (Configure)
[submenu] (System Styles) {Choose a style...}
      [stylesdir] (/usr/local/share/fluxbox/styles)
[end]
[submenu] (User Styles) {Choose a style...}
      [stylesdir] (~/.fluxbox/styles)
	[stylesdir] (~/.fluxbox/themes)
[end]
      [workspaces] (Workspace List)
[submenu] (Tools)
      [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center}
[end]
[submenu] (Window)
      [restart] (gnome) {gnome-session}
[end]
      [commanddialog] (Fluxbox Command)
      [reconfig] (Reload config)
      [restart] (Restart)
      [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center}
      [separator]
      [exit] (Exit)
	[separator][http://ubuntuforums.org/gallery/showphoto.php/photo/4349/ppuser/167727]("http://ubuntuforums.org/gallery/showphoto.php/photo/4349/ppuser/167727")
	[exec] (Reboot) {gksudo shutdown -r now}
	[exec] (Shutdown) {gksudo shutdown -h now}
[end]
[end]

Finally, here's my fluxbox desktop (built from "scatch", just as you are doing):

[http://ubuntuforums.org/gallery/showphoto.php/photo/4349/ppuser/167727](http://ubuntuforums.org/gallery/showphoto.php/photo/4349/ppuser/167727)

---

### Post by paparucino on 2006-12-31
> **Tux Aubrey said:**
> re: wallpaper

If you are using the Rox pinboard as a desktop (it comes setup with the default fluxbuntu install) you have to use a Rox folder icon (right click) to set your background.

If you can't work it out, post a copy of your startup file here for diagnosis.

It works now. I edited the wrong init file. :-(
Rox is not installed, for me, with fluxbuntu

> 
re: menus

That first gray screen and an empty menu is a bit intimidating, isn't it?  

No. Years ago I used blackbox (the granpa of the various openbox, fluxbox....) and I'm feeling confortable with menus.
I remeber that I had problems with slits.  I really hate them. :-)


Thank you and happy new year. You are already in 2007, isn't it

---

### Post by teejay17 on 2006-12-31
Awesome. There's been some good feedback on this thread. However, I haven't installed Fluxbox yet (mostly because I'm busy with New Year's preparations). 
What I still want to know, however, is Fluxbox performance. How does it compare to regular Ubuntu running Gnome? Currently I'm running Ubuntu on an older laptop, going on 7 years old tonight, so I'm wondering if there will be a marked improvement on this machine using Fluxbox?

---

### Post by mscclr3 on 2006-12-31
Not to complicate things but, I would suggest following this howto [http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox](http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox)

I noticed major differences in between the synaptic version and the compiled version

---

### Post by teejay17 on 2006-12-31
> **mscclr3 said:**
> Not to complicate things but, I would suggest following this howto [http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox](http://www.ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox)

I noticed major differences in between the synaptic version and the compiled version

Thanks! I'm looking at that now.

---

### Post by pharcyde on 2006-12-31
Edgy has a fairly up-to-date version of fluxbox (0.9.15.1+1.0rc2-1).   I believe this is the latest official build on the website.  Performance wise you can't get much more effecient in a window manager as fluxbox/blackbox/openbox.  It really depends on what you need v. what you want.  Most minimal window managers do not have integrated filemanagers (i.e. nautilus, konqueror) but you can still use them.  I like using shells to manage my files and am very comfortable doing so.  The biggest thing when deciding on a window manager is determining the tradeoffs applicable to you.  I've found that once you get used to minimal window managers you realize how much bloat other window managers contain and how useful most of it really is.  While this is my opinion I find that most people start off with gnome or kde and evolve to something past that once they are more familar with linux.

---

### Post by ppc_guy on 2006-12-31
Just as a side note. Thunar which is the file manger for XFCE works really well w/ Flux and is in the repos. I've used it w/ flux since way before Dapper w/ no issues.

nathan
hotel-tango-hotel

---

### Post by mscclr3 on 2006-12-31
Yea the version that I have is 1.0rc2... the only speed difference is that you disable soemthign during the ./configure ... I'm blanking on what but it says in the howto

---

### Post by RedSquirrel on 2007-01-04
I highly recommend Fluxbox for your situation. You will notice a significant improvement in performance.

I am running Fluxbox on a computer that is 6 years old: Duron 600 Mhz, 320 MB RAM, 15 GB HD, 32 MB video card (ATI XPERT 2000). It runs very well.

When I first installed Edgy, I started out with GNOME and found that it worked, but that it was a little sluggish. Everything runs smooth as silk with Fluxbox. (Aside: I also played around with WindowMaker and even sawfish, but didn't like them enough to keep using them.)

I found that Fluxbox didn't have much of a learning curve, but then it depends on the individual user. All the configuration for Fluxbox can be done by editing text files which were not too hard to follow. There are some GUI tools to help with configuration if you prefer that route.

Fluxbox doesn't have the eye candy that GNOME and KDE have when you first install it. Once you get the hang of it, you can install all sorts of eye candy if you want that (I personally like an uncluttered desktop, so I don't use the slit at all or anything to put icons on the desktop).

If you install the Fluxbox package, it simply becomes one of your session options when you login, so you can go back to using GNOME now and then if you want. Also, you can run GNOME applications in Fluxbox. I still use nautilus, gedit, etc. sometimes, though there are plenty of alternatives to GNOME applications, of course.

As you have no doubt discovered during your research, there is a great deal of information about Fluxbox out there, so it's usually not hard to find answers to problems and lots of suggestions of things to tweak (just for fun, today I put rounded corners on my windows).

Hope my reply wasn't too long...

---

### Post by teejay17 on 2007-01-04
> **RedSquirrel said:**
> I highly recommend Fluxbox for your situation. You will notice a significant improvement in performance.

I am running Fluxbox on a computer that is 6 years old: Duron 600 Mhz, 320 MB RAM, 15 GB HD, 32 MB video card (ATI XPERT 2000). It runs very well.

When I first installed Edgy, I started out with GNOME and found that it worked, but that it was a little sluggish. Everything runs smooth as silk with Fluxbox. (Aside: I also played around with WindowMaker and even sawfish, but didn't like them enough to keep using them.)

I found that Fluxbox didn't have much of a learning curve, but then it depends on the individual user. All the configuration for Fluxbox can be done by editing text files which were not too hard to follow. There are some GUI tools to help with configuration if you prefer that route.

Fluxbox doesn't have the eye candy that GNOME and KDE have when you first install it. Once you get the hang of it, you can install all sorts of eye candy if you want that (I personally like an uncluttered desktop, so I don't use the slit at all or anything to put icons on the desktop).

If you install the Fluxbox package, it simply becomes one of your session options when you login, so you can go back to using GNOME now and then if you want. Also, you can run GNOME applications in Fluxbox. I still use nautilus, gedit, etc. sometimes, though there are plenty of alternatives to GNOME applications, of course.

As you have no doubt discovered during your research, there is a great deal of information about Fluxbox out there, so it's usually not hard to find answers to problems and lots of suggestions of things to tweak (just for fun, today I put rounded corners on my windows).

Hope my reply wasn't too long...
Thanks a lot! No, your reply definitely wasn't too long; it was very informative. 
I think I will actually try Fluxbox this weekend, thanks to your post. 
Perhaps this comes across as being slightly apprehensive and fearful of Fluxbox, and perhaps I was a little, but I just want to make sure that there's enough room on my little drive. When I installed KDE on this little box, it was paralysing...I didn't know that it would install everything! I just thought, you know, the basics. 
I had to reinstall Ubuntu, which, because of this slow machine, takes about 3 hours (although that can be fun in its own right!)

---

### Post by RedSquirrel on 2007-01-04
> **teejay17 said:**
> Thanks a lot! No, your reply definitely wasn't too long; it was very informative. 
I think I will actually try Fluxbox this weekend, thanks to your post. 
Perhaps this comes across as being slightly apprehensive and fearful of Fluxbox, and perhaps I was a little, but I just want to make sure that there's enough room on my little drive. When I installed KDE on this little box, it was paralysing...I didn't know that it would install everything! I just thought, you know, the basics. 
I had to reinstall Ubuntu, which, because of this slow machine, takes about 3 hours (although that can be fun in its own right!)

Just wondering...

Did you know that there are ways of installing Ubuntu that make it extremely light weight (that is, ideal for older systems)?

I mean that you don't have to install GNOME at all, just stuff like xdm and Fluxbox. I haven't tried it myself, but I probably will someday when (if!) I have more free time.

There are some good HOWTOs for this, but I don't have the links handy and I have to leave soon. You can probably find them just by searching the Ubuntu forums.

Good luck!

---

### Post by Ozitraveller on 2007-01-04
Someone might find these useful:

Fluxbox
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Installation/LowMemorySystems
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

HOWTO: Fluxbox Basic Configuration
[http://forums.debian.net/viewtopic.php?t=5382&start=0&sid=69d236a1c9c37fad6e407829ac97485b](http://forums.debian.net/viewtopic.php?t=5382&start=0&sid=69d236a1c9c37fad6e407829ac97485b)

I know this isn't Fluxbox, but I think it's still worth a look:
HOWTO: IceWM Basic Configuration
[http://forums.debian.net/viewtopic.php?t=5450](http://forums.debian.net/viewtopic.php?t=5450)

---

### Post by johnnymac on 2007-01-05
I used fluxbox period.....I have for years....love it and wouldn't do anything other.  What's so great about it....I can do with it whatever I wan and it only uses 64MB of my 4GB available :)

---

### Post by teejay17 on 2007-01-05
> **Ozitraveller said:**
> Someone might find these useful:

Fluxbox
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Installation/LowMemorySystems
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

HOWTO: Fluxbox Basic Configuration
[http://forums.debian.net/viewtopic.php?t=5382&start=0&sid=69d236a1c9c37fad6e407829ac97485b](http://forums.debian.net/viewtopic.php?t=5382&start=0&sid=69d236a1c9c37fad6e407829ac97485b)

I know this isn't Fluxbox, but I think it's still worth a look:
HOWTO: IceWM Basic Configuration
[http://forums.debian.net/viewtopic.php?t=5450](http://forums.debian.net/viewtopic.php?t=5450)
Awesome. These are useful!

---

### Post by RevNomad on 2007-01-05
Thanks  for the links.  How does Fluxbox work on an old IMB Thinkpad?  I've heard there are some special files needed to use linux on one but don't know any details.
Thanks
NTP

---

### Post by tcrroadie on 2007-01-05
Teejay17,

You have gotten some great information so far on the installation and use of Fluxbox from this post.  I use Fluxbox for only a week or so for something new to try and learn and from my experience I would highly recommend Fluxbox for your old notebook pc.  As others have noted in this discussion, that Fluxbox is more of a hands on type of window manager in that you need to edit your menu and startup files manually.  Editing your menus can be a fun learning experience but can also be very time consuming.  

Since it sounds like you are on the search for a lighter weight working environment you may want to check out another window manager called Enlightenment.  Their are currently two versions of Enlightenment, E16 and E17.  E16 is an older version of Enlightenment but is very easy to install and easier to configure than Fluxbox.  E17 is currently in active development but is very stable at it's current state.  I use E17 everyday on my home pc.  E17 is not quite as light as Fluxbox but is much easier to configure that Fluxbox and is drop dead goergous.  E17 is very easy to install.  I created a new How-To on installing the latest development release of E17 on Edgy.  Here is a link to it.  Give it a try, you might like it.

[http://www.ubuntuforums.org/showthread.php?t=319336]("http://www.ubuntuforums.org/showthread.php?t=319336")

In my opinion Fluxbox is the king of window managers, and if you decide to give Fluxbox a try, be prepaired to spend a few hours learning how to edit the menu and other config files.  

As stated earier in this post you may want to try out Fluxbuntu.  Fluxbuntu will run from a live cd just like Ubuntu and most commonly used apps are allready installed and added to the menu.  I ran Fluxbuntu in Vmware for a while and really liked it.  

[http://fluxbuntu.org/]("http://fluxbuntu.org/")

Some other usefull links.

[http://fluxbox.sourceforge.net/docbook/en/html/]("http://fluxbox.sourceforge.net/docbook/en/html/")

[http://fluxbox-wiki.org/index.php/Fluxbox-wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki")

[http://www.boxwhore.org/modules/news/]("http://www.boxwhore.org/modules/news/")

[http://www1.get-e.org/]("http://www1.get-e.org/")

Kris

---

### Post by teejay17 on 2007-01-05
All this information is so fantastic. Thanks a lot for everything so far!
I haven't tried any of the approaches yet; I have to consider everything I have before me now and think about which avenue I'd like to pursue first. I'll let everyone know about the progress as I go along, of course. I'm hoping to start this little project this weekend, as I won't be at work and I'll have more time:D.
There's so much choice here, it's great. I'll probably end up trying all the choices...Fluxbox, Enlightenment, etc. 
Be back soon...

---

### Post by RedSquirrel on 2007-01-05
> **teejay17 said:**
> All this information is so fantastic. Thanks a lot for everything so far!
I haven't tried any of the approaches yet; I have to consider everything I have before me now and think about which avenue I'd like to pursue first. I'll let everyone know about the progress as I go along, of course. I'm hoping to start this little project this weekend, as I won't be at work and I'll have more time:D.
There's so much choice here, it's great. I'll probably end up trying all the choices...Fluxbox, Enlightenment, etc. 
Be back soon...


If you don't end up having much time this weekend, you might try the following to at least get a chance to experiment with Fluxbox a bit:

If you still have Ubuntu 6.10 installed (that is, GNOME and stuff) try just installing the Fluxbox package using synaptic. Then you just logout, and at the gdm login screen, choose Fluxbox instead of GNOME. That's probably the easiest way for you to see what Fluxbox feels like, since the download for the Fluxbox package itself is (according to synaptic) only 922 kB, and the installation is 2957 kB.

If you start to do some tweaking, you will find that pretty much all of your configuration files are kept in the ~/.fluxbox directory, so if you change the configuration significantly, you can easily back up those files if you decide to wipe out your existing Ubuntu to do a clean install with fluxbuntu  or something else later on.

---

### Post by teejay17 on 2007-01-06
> **RedSquirrel said:**
> If you don't end up having much time this weekend, you might try the following to at least get a chance to experiment with Fluxbox a bit:

If you still have Ubuntu 6.10 installed (that is, GNOME and stuff) try just installing the Fluxbox package using synaptic. Then you just logout, and at the gdm login screen, choose Fluxbox instead of GNOME. That's probably the easiest way for you to see what Fluxbox feels like, since the download for the Fluxbox package itself is (according to synaptic) only 922 kB, and the installation is 2957 kB.

If you start to do some tweaking, you will find that pretty much all of your configuration files are kept in the ~/.fluxbox directory, so if you change the configuration significantly, you can easily back up those files if you decide to wipe out your existing Ubuntu to do a clean install with fluxbuntu  or something else later on.
Awesome. I'm going to try this approach tomorrow; turns out my weekend is a little more hectic than originally planned. I've been beer connoisseur-ing with a buddy I haven't seen in ages (the real deal, like beer geek stuff!) But I'm putting aside some time tomorrow to just play and experiment, and this particular experiment is going to include Fluxbox. 
Cheers

---

### Post by Ozitraveller on 2007-01-06
Before we finish I thought I would add one last idea in, Ubuntulite

Ubuntu-Lite is geared towards Pentium I or newer systems with as little as 32 megs of ram...

Default window manager in Ubuntu Lite is IceWM with IcePref as control panel, IceME as menu editor and lots of themes

Ubuntulite
[http://www.ubuntulite.org/dokuwiki/doku.php](http://www.ubuntulite.org/dokuwiki/doku.php)

FAQ
[http://www.ubuntulite.org/dokuwiki/doku.php?id=faq](http://www.ubuntulite.org/dokuwiki/doku.php?id=faq)

How to install Ubuntu Lite on your computer
[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)

---

### Post by teejay17 on 2007-01-07
Thanks. I have heard about UbuntuLite, and actually considered downloading it mid-fall '06, but at this point it was still fairly early in development, around the first Alpha or so. I guess it's probably more developed now. I'm going to read into this, and consider it as an option too.
Oh, the choices!
> **Ozitraveller said:**
> Before we finish I thought I would add one last idea in, Ubuntulite

Ubuntu-Lite is geared towards Pentium I or newer systems with as little as 32 megs of ram...

Default window manager in Ubuntu Lite is IceWM with IcePref as control panel, IceME as menu editor and lots of themes

Ubuntulite
[http://www.ubuntulite.org/dokuwiki/doku.php](http://www.ubuntulite.org/dokuwiki/doku.php)

FAQ
[http://www.ubuntulite.org/dokuwiki/doku.php?id=faq](http://www.ubuntulite.org/dokuwiki/doku.php?id=faq)

How to install Ubuntu Lite on your computer
[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)

---

### Post by teejay17 on 2007-01-07
Whoa, look at the weird stuff on the "download" page for UbuntuLite: [http://www.ubuntulite.org/drupal/?q=node/21](http://www.ubuntulite.org/drupal/?q=node/21)
Someone should look into this; it can give Ubuntu a bad image.

---

### Post by paparucino on 2007-01-07
> **teejay17 said:**
> Whoa, look at the weird stuff on the "download" page for UbuntuLite: [http://www.ubuntulite.org/drupal/?q=node/21](http://www.ubuntulite.org/drupal/?q=node/21)
Someone should look into this; it can give Ubuntu a bad image.
You are right, but that page seems abandoned. last time the "admin" (?) wrote something it was
```

Submitted by admin on Sun, 2006-02-26 12:58.

Curently no download links are avalible

Sorry


```

---

### Post by teejay17 on 2007-01-07
> **paparucino said:**
> You are right, but that page seems abandoned. last time the "admin" (?) wrote something it was
```

Submitted by admin on Sun, 2006-02-26 12:58.

Curently no download links are avalible

Sorry


```
Is there a way that the weird x-rated stuff can be taken off the site? I'm not being a prude, but that stuff doesn't belong on anything that pertains to Ubuntu.
Perhaps I should start another thread about this?

---

### Post by MetalMusicAddict on 2007-01-07
> **teejay17 said:**
> Is there a way that the weird x-rated stuff can be taken off the site? I'm not being a prude, but that stuff doesn't belong on anything that pertains to Ubuntu.
Perhaps I should start another thread about this?

Not really. It happens. Only way to do it is to get the site admin do it. The host might be able also.

---

### Post by Ozitraveller on 2007-01-07
Sorry about that, I hadn't noticed that their siet was being so badly spammed! The only reason I posted Ubuntulite was because it uses IceWM.

That Debian guy's posts on Fluxbox and IceWM look like the best options to me.

I'd be interested to hear how you go too.

Cheers

Ozi

---

### Post by usererror on 2007-01-07
Anyone have any screenshots of their desktops using Fluxbox or Blackbox?  I used to use the blackbox port in Windows, haven't tried it with Ubuntu...  I think I got bored with not having a ton of styles to use.  Interested in seeing what some of you guys out there have!

---

### Post by RevNomad on 2007-01-07
I have enjoyed expermenting with differing windowmanagers and desktops, perhaps too much.  Now I need to clean up my system.  I how do I remove the options from the session menu?

I run Kubuntu on a Dell Latitude D505 the lighter managers certainly made it more responsive.  Unfortunately XFCE lost my wireless signal, Openbox was simply confusing.  Fluxbox and FVWM proved difficult to configure.  I liked Afterstep's approach but simply don't know enough Linux to comfortably configure it. 

Using Klick packages proved difficult in each of the alternative wm's.  

NTP

---

### Post by teejay17 on 2007-01-08
> **Ozitraveller said:**
> Sorry about that, I hadn't noticed that their siet was being so badly spammed! The only reason I posted Ubuntulite was because it uses IceWM.

That Debian guy's posts on Fluxbox and IceWM look like the best options to me.

I'd be interested to hear how you go too.

Cheers

Ozi
No worries. I'll keep you posted about my setup.

---

### Post by Ozitraveller on 2007-01-08
I saw this in Distrowatch:
[http://distrowatch.com/weekly.php?issue=20070108#news](http://distrowatch.com/weekly.php?issue=20070108#news)




I came across this on the forums some time back, I thought it might give some contacts, as there are others interested in the same idea.

xubuntu lighter design - help request ( closed)
[http://ubuntuforums.org/showthread.php?t=200316](http://ubuntuforums.org/showthread.php?t=200316)

---

### Post by teejay17 on 2007-01-08
> **Ozitraveller said:**
> I saw this in Distrowatch:
[http://distrowatch.com/weekly.php?issue=20070108#news](http://distrowatch.com/weekly.php?issue=20070108#news)




I came across this on the forums some time back, I thought it might give some contacts, as there are others interested in the same idea.

xubuntu lighter design - help request ( closed)
[http://ubuntuforums.org/showthread.php?t=200316](http://ubuntuforums.org/showthread.php?t=200316)
Thanks for these. I am interested in a lighter Xubuntu that could include Fluxbox and icewm (actually, this is the first I hear of icewm). 
I have tried Xubuntu and didn't find there was any major improvement over the way regular Ubuntu works; there was minor difference, of course, but not enough to warrant having such a limiting system. 
This other thread foreshadows something cool.

---

### Post by Ozitraveller on 2007-01-08
> **teejay17 said:**
> Thanks for these. I am interested in a lighter Xubuntu that could include Fluxbox and icewm (actually, this is the first I hear of icewm). 
I have tried Xubuntu and didn't find there was any major improvement over the way regular Ubuntu works; there was minor difference, of course, but not enough to warrant having such a limiting system. 
This other thread foreshadows something cool.

Hi teejay17

I mention IceWm earlier, if you have a look you find a link to a howto. :)

I thought the comments on DistroWatch were interesting too.


Installation/LowMemorySystems
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

HOWTO Ubuntu mini ram
[http://ubuntuforums.org/showthread.php?t=42873](http://ubuntuforums.org/showthread.php?t=42873)

Ubuntu Mini-RAM HOWTO 
[http://ubuntuforums.org/showthread.php?t=8338&page=10&pp=10](http://ubuntuforums.org/showthread.php?t=8338&page=10&pp=10)



I found this too!
==============================


Hi folks!

There's a lightweight Ubuntu variant: BeatrIX --- pleaase see:
[http://www.watsky.net/](http://www.watsky.net/)

My old laptop (Compaq Armada 7400; Pentium II-300Mhz with 128 MB RAM and 6 GB Harddrive) works better with BeatrIX 2005.1F (Rel. Jan. 29, 2005). 

This laptop was previously running on custom Ubuntu with iceWM; I've installed it via the "Ubuntu/Debian-Sarge Mini-RAM HOWTO" by Ingo LANTSCHNER (Thanks Ingo!!!).

BeatrIX runs faster than my previous installation (Ubuntu 4.10 custom-installed with iceWM) for a gnome-based distro (which is, SURPRISE! SURPRISE! -----derived from Ubuntu). 

Test drive a BeatrIX live CD, and see what I meant!

dfv3

---

### Post by heathen on 2007-01-08
here's a screenshot of my desktop...
[IMG]http://i19.photobucket.com/albums/b164/solenberg/january8.png[/IMG]
I just started playing with fluxbox (and conky, forgive the broken stuff in it.. i just copied someones .conkyrc)
I'm glad you started this thread, I've found a lot of usefull info here...

---

### Post by BLTicklemonster on 2007-01-09
My computer is plenty quick enough to run what I want, but I prefer to use fluxbox most of the time. I have gnome of course, and e17, icewm, xfce4, fvwm, fvwm-crystal, and for some dumb reason, I'm installing kubuntu-desktop right now... more out of curiosity than anything else. 

BUT, whenever I use anything else, it's just for a short while, then I come back here to fluxbox again.

I have tried rox and idesk, even running xfce panel, but I prefer gdesklets with the toolbar customized for quick launches, but I also have my menu edited like this so everything I use frequently is where I can get to it. 

```
# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)
#   [submenu] (My Apps) {}   
    [menu] {}
       [exec] (Gnome Terminal) {gnome-terminal}
       [exec] (Thunar) {thunar}
       [exec] (Nautilus) {nautilus --no-desktop --browser}
       [exec] (Gimp) {gimp}
       [exec] (Gaim) {gaim}
       [exec] (FireFox) {firefox}
       [exec] (UTGOTY) {/home/bill/ut/ut}
       [exec] (UT Cache Cleaner) {./utcleaner}
       [exec] (Windows XP Pro) {vmware}
       [exec] (IE6) {/home/bill/bin/ie6}
       [exec] (Amarok) {amarok}
       [exec] (Stream Tuner) {streamtuner}
       [exec] (Opera Browser) {opera}
       [exec] (gFTP) {gftp}
   [submenu] (____________) {} <>
     [end]
   [submenu] (Apps) {}
      [submenu] (Databases) {}
         [exec] (HSQLDB Database Manager) {/usr/bin/hsqldb-databasemanager} </usr/share/pixmaps/hsqldb.xpm>
(Editors) {}
```

The rest of course is your general fare. I just wanted to show how to put stuff up front where you want it. Took me a while of playing around to get it like that. I was extremely pleased to find that I could actually get away with it :mrgreen:

---

### Post by halw on 2007-01-09
I recently loaded Kubuntu from the alternate cd and then installed Fluxbox. After restarting X and selecting Fluxbox, I find no menu items.

Does anyone have an idea as to why fluxbox did not create menu entries for the apps accessable in KDE?

---

### Post by teejay17 on 2007-01-09
Looking at the last two entries, seems Fluxbox has been the choice, particularly [BLTicklemonster]("http://www.ubuntuforums.org/member.php?u=44485"), who keeps coming back to it again and again. That's a good indication that it's something to like, something that someone will feel comfortable with. 
heathen, your screenshot looks awesome! I can't wait to get my laptop looking like that!
>  I'm glad you started this thread, I've found a lot of usefull info here...No problem. I'm very glad I started it too; the info here is awesome!

---

### Post by heathen on 2007-01-09
I've had an on again/off again love afair with fluxbox...  I got into an eyecandy deal a while back and played with
Kubuntu for a while... then I decided that it wasnt worth the extra processing...   I just like simple over 

thru a lot of random web/forum searches I've dug up stuff to help me customize it to mostly the way I want it...  
I'd like to dump the gnome theme stuff, for whatever reason when I try to change my gnome theme to make it 
match my FB theme it never works... I'll get the window borders but never the interior stuf...


I've really enjoyed playing with fluxbox (ask my wife, She'll complain all about it...)  Hopefully I'll get everything 
the way I'd like it and not have to mess with it, just use it..

Edit to add:  I also ran Openbox for a while...  It's "almost" the same thing...  the biggest thing for me is that I wanted the toolbar to not be an "external" aplication... otherwise I really liked OB too..

---

### Post by RedSquirrel on 2007-01-09
> **halw said:**
> I recently loaded Kubuntu from the alternate cd and then installed Fluxbox. After restarting X and selecting Fluxbox, I find no menu items.

Does anyone have an idea as to why fluxbox did not create menu entries for the apps accessable in KDE?

I'm not 100% certain, but I think it has something to do with whether the 'menu' package was installed before the 'fluxbox' package. If it wasn't, you won't have a menu when you first start Fluxbox.

In any case, if you still don't have a menu, here is a link to help you get one:

See the section on Menu Customization in:

[https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox#head-b872ae8cd3c546e75b1eb2e30e55c2f6d06651fd")

and the Fluxbox Wiki has a section on editing the menu:

[http://fluxbox-wiki.org/index.php/Howto_edit_menu](http://fluxbox-wiki.org/index.php/Howto_edit_menu)

and post #13 of this thread discussed menus too.

---

### Post by teejay17 on 2007-01-09
A little off topic, but as I was reviewing all the information in this thread, getting up the nerve to install Fluxbox for the first time, I noticed something again: we ***_really_*** _***have***_ _***to***_ do something about all the spam that's on the ubuntulite page, particularly the download page, because that's where most people will go directly for: [http://www.ubuntulite.org/drupal/?q=node/21#comment-661](http://www.ubuntulite.org/drupal/?q=node/21#comment-661)
It's terrible; the Ubuntu name should not be seen on the same page as this stuff. There must be someone out there somewhere, partial and kind enough to the Ubuntu name and community to save it/us from being associated with this filth?

---

### Post by teejay17 on 2007-01-09
P.S. like can the site be taken down, or the project taken over if it's been abandoned?

---

### Post by BLTicklemonster on 2007-01-09
Wow, I just decided to try something, and with xmms running playing streaming audio, firefox open with 5 pages tabbed, and running conky to see what happened, I used scrot to get a screenshot and compared info.

Kubuntu
125 processes, 6 running. 
18% load on my cpu
26% ram usage (one gig)


Fluxbox
107 processes, 1 running
6% load
22% usage

Enlightenment E17
100 processes, 1 running
2% load
20% usage

Huh. You know, with all that bling, you'd think that E17 would be hogging the bed.

I'm going to have to test icewm and the others now, dang it.

---

### Post by teejay17 on 2007-01-11
Okay, I did it! I installed Fluxbox. I was very surprised to see how quickly it went.
It looks way cool. Now, however, I have some learning to do!
I'd send everyone a screenshot, but it's pretty generic right now. Also, I don't know how the heck to do that yet; I'm sure I'll figure it out. There's lots of information here in this thread that I'll go back to, thanks to everyone who participated. 
Now, however, I must retire.

---

### Post by tcrroadie on 2007-01-12
> **teejay17 said:**
> Okay, I did it! I installed Fluxbox. I was very surprised to see how quickly it went.
It looks way cool. Now, however, I have some learning to do!
I'd send everyone a screenshot, but it's pretty generic right now. Also, I don't know how the heck to do that yet; I'm sure I'll figure it out. There's lots of information here in this thread that I'll go back to, thanks to everyone who participated. 
Now, however, I must retire.

Glad to hear that your Fluxbox install went well for you and you are liking it.  For taking screenshots you can use a small terminal command line tool called scrot.  I believe it is not installed on Ubuntu by default so you may need to apt-get install scrot. 

Basic screen capture syntax is 

```
scrot -d 5 screenshot.png
```

Where -d is time delay of 5 seconds and of course you can name the output file to your liking.  Scrot is very easy to use. I use it all the time for my screencaptures.

See man scrot for more information

```
man scrot
```

---

### Post by teejay17 on 2007-01-12
> **tcrroadie said:**
> Glad to hear that your Fluxbox install went well for you and you are liking it.  For taking screenshots you can use a small terminal command line tool called scrot.  I believe it is not installed on Ubuntu by default so you may need to apt-get install scrot. 

Basic screen capture syntax is 

```
scrot -d 5 screenshot.png
```Where -d is time delay of 5 seconds and of course you can name the output file to your liking.  Scrot is very easy to use. I use it all the time for my screencaptures.

See man scrot for more information

```
man scrot
```
Okay, I'll give that a whirl. Thanks!

---

### Post by heathen on 2007-01-12
you can also do it with gimp...  (scrot is a lot easier though)

I finally got around to installing 6.10 and waiting impatiantly for the updates to finish so I can reinstall fluxbox...  I'm going to compile it myself this time instead of using the repo version... wish me luck...

I keep right clicking on the desktop to get my menu... it's a pain in the butt being used to one WM and suddenly being in another..

---

### Post by teejay17 on 2007-01-12
Okay, one thing that I need to know before making Fluxbox my default GUI: how does one log out? 
I saw that I can restart and shut down by right-clicking, but how does one log out, say if I wanted to log back in to Gnome?

---

### Post by tcrroadie on 2007-01-12
> **teejay17 said:**
> Okay, one thing that I need to know before making Fluxbox my default GUI: how does one log out? 
I saw that I can restart and shut down by right-clicking, but how does one log out, say if I wanted to log back in to Gnome?

To log out of Fluxbox you should only need to click Exit at the bottom of your Fluxbox menu. 

If exit is not working you may need to edit your ~/.fluxbox/menu file.  

Simply add this entry to the end of your menu file.

[exit] (Log Out)

An example menu file. 

```
 # Fluxbox menu file
       [begin] (Fluxbox)
         [exec] (rxvt) {rxvt -ls}
         [exec] (netscape) {netscape -install}
         [exec] (The GIMP) {gimp}
         [exec] (XV) {xv}
         [exec] (Vim) {rxvt -geometry 132x60 -name VIM -e screen vim}
         [exec] (Mutt) {rxvt -name mutt -e mutt}
         [submenu] (mozilla)
           [exec] (browser) {mozilla -browser}
           [exec] (news) {mozilla -news}
           [exec] (mail) {mozilla -mail}
           [exec] (edit) {mozilla -edit}
           [exec] (compose) {mozilla -compose}
         [end]
         [submenu] (Startup)
           [exec] (gkrellm) {gkrellm -w}
           [exec] (xmms) {xmms -p}
           [exec] (galeon) {galeon -s}
           [exec] (kdeinit) {kdeinit}
         [end]
		 [submenu] (user wallpapers)
		   [wallpapers] (~/.backgrounds) {fbsetbg -f}
		 [end]
         [submenu] (Window Manager)
           [exec] (Edit Menus) {nedit ~/.fluxbox/menu}
           [submenu] (Style) {Which Style?}
             [stylesdir] (~/.fluxbox/styles)
             [stylesmenu] (Fluxbox Styles) {/usr/local/share/fluxbox/styles}
           [end]
           [config] (Config Options)
           [reconfig] (Reconfigure)
           [restart] (Restart)
         [end]
         [exit] (Log Out)
       [end]
       # end of menu file
```

When I have time tonight, I'll post my menu file from my system at home that you can use for yourself or as another example file.  Sorry but I am at work at the moment.

---

### Post by paparucino on 2007-01-12
> **tcrroadie said:**
> 
When I have time tonight, I'll post my menu file from my system at home that you can use for yourself or as another example file.  Sorry but I am at work at the moment.
Can you tell me, pls, the way to change global fonts? I've modified those in my style (Twice) but it works only for the items liste in that file and not for global settings.

---

### Post by tcrroadie on 2007-01-12
> **paparucino said:**
> Can you tell me, pls, the way to change global fonts? I've modified those in my style (Twice) but it works only for the items liste in that file and not for global settings.

If you are referring to the fonts used in gtk apps such as Firfox, Abiword, Banshee,thuna, etc, you can use a tool called gtk-theme-switch.

You can use gtk-theme-switch to change the theme and fonts used for gtk applications.

```
sudo aptitude update
```

```
sudo aptitude install gtk-theme-switch
```

```
gtk-theme-switch2
```

---

### Post by tcrroadie on 2007-01-12
To be honest I haven't used Fluxbox in about 4 months.  I had Fluxbox installed on my Dapper system for use on a vnc server.  Anyhow reading this thread caught my curiosity again and I decided to install Fluxbox on my Edgy system along with Gnome and Enlightenment E17.  I forgot how light and fast Fluxbox is.  It is really a nice environment giving it is essentially just a window manager.  

Teejay17, one question for you.  Do you have the package "menu" installed on your system?  At least on my system it looks as if "menu" entered a menu entry for just about every application on my system and created an Exit entry at the end of the fluxbox menu.

I am attaching my fluxbox-menu file from my system.  You can do with it as you like. 

I am also posting a couple of screenshots I just took from my Edgy system that I hope will help keep you motivated.

---

### Post by teejay17 on 2007-01-12
> **tcrroadie said:**
> To be honest I haven't used Fluxbox in about 4 months.  I had Fluxbox installed on my Dapper system for use on a vnc server.  Anyhow reading this thread caught my curiosity again and I decided to install Fluxbox on my Edgy system along with Gnome and Enlightenment E17.  I forgot how light and fast Fluxbox is.  It is really a nice environment giving it is essentially just a window manager.  

Teejay17, one question for you.  Do you have the package "menu" installed on your system?  At least on my system it looks as if "menu" entered a menu entry for just about every application on my system and created an Exit entry at the end of the fluxbox menu.

I am attaching my fluxbox-menu file from my system.  You can do with it as you like. 

I am also posting a couple of screenshots I just took from my Edgy system that I hope will help keep you motivated.
Wow, those are real nice screenshots! I can't wait to make my system look like that. 
I'm just on my way home from work/errand running, so I'll log in and check to see if I have that menu installed.

---

### Post by RedSquirrel on 2007-01-12
> **tcrroadie said:**
> If you are referring to the fonts used in gtk apps such as Firfox, Abiword, Banshee,thuna, etc, you can use a tool called gtk-theme-switch.

You can use gtk-theme-switch to change the theme and fonts used for gtk applications.

```
sudo aptitude update
``````
sudo aptitude install gtk-theme-switch
``````
gtk-theme-switch2
```

Minor addition:

You can also run gtk-theme-switch with:

```
switch2
```(saves typing!) :)

---

### Post by Ozitraveller on 2007-01-12
> **tcrroadie said:**
> To be honest I haven't used Fluxbox in about 4 months.  I had Fluxbox installed on my Dapper system for use on a vnc server.  Anyhow reading this thread caught my curiosity again and I decided to install Fluxbox on my Edgy system along with Gnome and Enlightenment E17.  I forgot how light and fast Fluxbox is.  It is really a nice environment giving it is essentially just a window manager.  

Teejay17, one question for you.  Do you have the package "menu" installed on your system?  At least on my system it looks as if "menu" entered a menu entry for just about every application on my system and created an Exit entry at the end of the fluxbox menu.

I am attaching my fluxbox-menu file from my system.  You can do with it as you like. 

I am also posting a couple of screenshots I just took from my Edgy system that I hope will help keep you motivated.

Hi tcrroadie

I'm interested in Fluxbox as well. Just for my interest, could you tel' me what apps you have installed for fluxbox, and what theme(s) you are using.

How does fluxbox compare to E17, if you had a choice of only one which one would it be? and why? 

I have an old pc (PII/400), currently running ubuntu, it's ok for most things, and I have tried Fluxbox, and Xubuntu before. Xubuntu is not substantially quicker than Ubuntu, so that is out.

FYI: I'm currently using DSL on a work pc to write this! :)

---

### Post by RedSquirrel on 2007-01-12
> **teejay17 said:**
> Wow, those are real nice screenshots! I can't wait to make my system look like that. 
I'm just on my way home from work/errand running, so I'll log in and check to see if I have that menu installed.

I'm pretty sure you do have it installed. I recently found out that Fluxbox has menu as a dependency, so it should have been installed when you installed the fluxbox package.

---

### Post by teejay17 on 2007-01-12
> **tcrroadie said:**
> To be honest I haven't used Fluxbox in about 4 months.  I had Fluxbox installed on my Dapper system for use on a vnc server.  Anyhow reading this thread caught my curiosity again and I decided to install Fluxbox on my Edgy system along with Gnome and Enlightenment E17.  I forgot how light and fast Fluxbox is.  It is really a nice environment giving it is essentially just a window manager.  

Teejay17, one question for you.  Do you have the package "menu" installed on your system?  At least on my system it looks as if "menu" entered a menu entry for just about every application on my system and created an Exit entry at the end of the fluxbox menu.

I am attaching my fluxbox-menu file from my system.  You can do with it as you like. 

I am also posting a couple of screenshots I just took from my Edgy system that I hope will help keep you motivated.
Okay, I was able to log off using "exit" no problem. I guess I was getting confused somehow with what was happening; to turn off my machine in Fluxbox, I have to "exit" and then shut down at the login screen. 
Now I have other fish to fry. I'm wondering if Synaptec is still available in Fluxbox? And if it is, how to I access it?
I would like to install "esetroot" to get backgrounds available on my box. I just want to ask here first before I proceeed, for tips and advice.

---

### Post by heathen on 2007-01-12
in a terminal type sudo synaptic

edit to add
if you install Eterm you can use the fbsetbg command...

---

### Post by tcrroadie on 2007-01-12
> **Ozitraveller said:**
> Hi tcrroadie

I'm interested in Fluxbox as well. Just for my interest, could you tel' me what apps you have installed for fluxbox, and what theme(s) you are using.

How does fluxbox compare to E17, if you had a choice of only one which one would it be? and why? 

I have an old pc (PII/400), currently running ubuntu, it's ok for most things, and I have tried Fluxbox, and Xubuntu before. Xubuntu is not substantially quicker than Ubuntu, so that is out.

FYI: I'm currently using DSL on a work pc to write this! :)

Dude, sweet.  I have a live cd of Elive I like to use at work also.  I use it on an old PIII 1ghz machine at work to play with.  I can watch just about any media off of the internet with Elive on that machine.  It is great fun and looks sweet.  Give it a try it's really nice. 

[http://www.elivecd.org/]("http://www.elivecd.org/")

As far as installing Fluxbox on my Edgy system, I just installed it on a slightly moded Ubuntu Edgy install.  I have Beryl installed with the beta Nvidia driver and also have E17 installed.  Just did an "aptitude install fluxbox".  

As far as applications, I did install Thunar since launching Nautilus causes gnome-desktop or something to launch and messes up Fluxbox.  I did stumble across a work around for this but Thunar does the job just fine for me.  Also installed gtk-theme-switch so that I can easily change my gtk themes.  That is basically it.  

As for my thoughts on Fluxbox and Enlightenment E17, when it comes to just plain vanilla window managers, Fluxbox is king.  Fluxbox is light on RAM, fast, fairly easy to configure once you get the hang of it, and can look really nice with a little work.  E17 is also fairly light on resources, almost no configuration after install is needed (so it is much faster to get up and running compared to Fluxbox) and the obvious, it is GORGEOUS.  

I personally love to use E17 over Fluxbox because it is easy to use, gets the job done for me, takes far less time to get to a usable state, and is GORGEOUS.  If you keep the loaded modules in E17 to a minimum, E17 uses just about the same amount of memory as Fluxbox.  So really it all comes down to preference and what work best for you.

What I would recommend is to install both and see what works best for you.  E17 can easily be installed on Ubuntu.  I created an easy 'how to' that you can find here.

[http://www.ubuntuforums.org/showthread.php?t=319336]("http://www.ubuntuforums.org/showthread.php?t=319336")

As an added note.  Elive is a distribution that I have found uses much less ram than just about any distro I have found, next to Fluxbuntu and Zenwalk.  We are talking around 100-110mb of ram used after initial boot.  Elive is based on Debian Etch with E17 as the desktop environment.  You may want to have a look at both Elive and Fluxbuntu for your PII400. 

[http://fluxbuntu.org/]("http://fluxbuntu.org/")

As for my Fluxbox Style.  It is called darkmystic and can be found here.

[http://www.boxwhore.org/modules/wfdownloads/singlefile.php?cid=2&lid=311]("http://www.boxwhore.org/modules/wfdownloads/singlefile.php?cid=2&lid=311")

---

### Post by Ozitraveller on 2007-01-13
Hi tcrroadie, thanks for the quick reply! And lots of useful info too! I hadn't heard of Fluxbuntu before, but I thought there was a Fubuntu floating around, maybe the same?? 

I haven't tried Elive before, so I just dashed off to their site to have a look at the screenies. Very pretty!!!

I'm off to try your HowTo now..

Thanks very Enlightening! LOL!!

---

### Post by teejay17 on 2007-01-13
This isn't a negative comment, but I can already see what the benefit of Fluxbuntu will be when it is released. Having a system already preconfigured will go a long way to helping people understand Fluxbox and the way it works. 
I'm not saying I'm having difficulty; I'm actually having fun with Fluxbox on my system. Nonetheless, I can see how it will be far simpler for people to have installable media to get things going, and once the system boots, things are pretty much already set up.

---

### Post by heathen on 2007-01-13
while I was playing around I installed the (beta?) fluxbuntu cd...   It needs some work...  personally I'd rather just do it myself...

---

### Post by teejay17 on 2007-01-13
I considered downloading Fluxbuntu this morning. But, what I'd like to know first, is what the difference is between downloading "Fluxbuntu" and installing it, compared to what I've already done, which was install Fluxbox in the terminal and then log into the Fluxbox environment?
Also, what is the method that Fluxbuntu installs; is it a LiveCD, or is it a text based install? I can't install using Live CD method (machine too slow) so I'd need something text based.

---

### Post by kelean on 2007-01-13
> **teejay17 said:**
> I considered downloading Fluxbuntu this morning. But, what I'd like to know first, is what the difference is between downloading "Fluxbuntu" and installing it, compared to what I've already done, which was install Fluxbox in the terminal and then log into the Fluxbox environment?
Also, what is the method that Fluxbuntu installs; is it a LiveCD, or is it a text based install? I can't install using Live CD method (machine too slow) so I'd need something text based.

I have tried fluxbuntu and its very fast.  It is a live CD but I do knot know how it installs.  

Fluxbuntu is far less bloated that than  your install frum I have read.  I have an older computer I am going to install it on.  It is the fastest live CD i have used so far.

---

### Post by heathen on 2007-01-13
to install fluxbuntu from live cd open terminal and type 
```
sudo ubiquity
```

i looked around their site for a few minutes to figure that out...
fluxbuntu is liveCD only (as far as i know)


I think my biggest problem with fluxbuntu was rox... I just dont like it, no particular reason...

as for the fastest live cd.. try DamnSmallLinux-Not (DSL-N)  that was pretty spiffy... but it lacks alittle in hardware support out of the box..

---

### Post by kelean on 2007-01-13
> **heathen said:**
> to install fluxbuntu from live cd open terminal and type 
```
sudo ubiquity
```

i looked around their site for a few minutes to figure that out...
fluxbuntu is liveCD only (as far as i know)


I think my biggest problem with fluxbuntu was rox... I just dont like it, no particular reason...

as for the fastest live cd.. try DamnSmallLinux-Not (DSL-N)  that was pretty spiffy... but it lacks alittle in hardware support out of the box..

DSL did not like my computer for some reason.  It might have been the disk, not sure.

---

### Post by paparucino on 2007-01-13
> **teejay17 said:**
> I considered downloading Fluxbuntu this morning. But, what I'd like to know first, is what the difference is between downloading "Fluxbuntu" and installing it, 
I don't know the answer. What I can say is that whe I tried to install fluxbox from a CD I had some problems, when I installed it via apt-get I was smiling.
It works well, not what I'ld like but about 95% :-)

---

### Post by teejay17 on 2007-01-13
> **kelean said:**
> I have tried fluxbuntu and its very fast.  It is a live CD but I do knot know how it installs.  

Fluxbuntu is far less bloated that than  your install frum I have read.  I have an older computer I am going to install it on.  It is the fastest live CD i have used so far.
Good to know. I'm going to try and download Fluxbuntu, and see how that goes.
So you're telling me all I have to do is insert the CD and it should work half decent? 
I have only 96 megs of RAM.

---

### Post by paparucino on 2007-01-13
> **teejay17 said:**
> Good to know. I'm going to try and download Fluxbuntu, and see how that goes.
So you're telling me all I have to do is insert the CD and it should work half decent? 
I have only 96 megs of RAM.
Ahem.... I cannot believe it!!!! Are you joking?!?!?!??!?
Well....  think it should be better something like this 
```
apt-get install fluxbox
```
then edit 
/home/your home/.fluxbox/menu
/usr/local/share/fluxbox/styles/your preferred style
and be happy


;-)

---

### Post by teejay17 on 2007-01-13
> **paparucino said:**
> Ahem.... I cannot believe it!!!! Are you joking?!?!?!??!?
Well....  think it should be better something like this 
```
apt-get install fluxbox
```then edit 
/home/your home/.fluxbox/menu
/usr/local/share/fluxbox/styles/your preferred style
and be happy;-)
Yeah, okay, that's the sort of reaction I expected. :rolleyes:
I think I'm going to abandon trying to install from CD; I mean, I've already installed Fluxbox through apt-get, and it's working great. I just wanted to test Fluxbuntu out and see what that was like. 
Perhaps I'll wait for when (and if!) they release an "alternate" ISO for Fluxbuntu.

---

### Post by heathen on 2007-01-13
if you already have fluxbox running I'd stick with it until there is an official fluxbuntu release

---

### Post by kelean on 2007-01-13
> **teejay17 said:**
> Good to know. I'm going to try and download Fluxbuntu, and see how that goes.
So you're telling me all I have to do is insert the CD and it should work half decent? 
I have only 96 megs of RAM.


I have installed fluxbuntu and it is very fast!!.  I had no problems with the install.  I am still playing around with it but all in all I really like it.  I am not use to flux but that was part of the interest in tring fluxbuntu.  Now I need to get my hands dirty and learn how to flux.

As far as only having 96 megs of ram I would think it will be a bit slow from the livecd but I think you can get a feel for how it will work with your system.  Plus if you do install fluxbuntu it will so much faster once installed.

---

### Post by teejay17 on 2007-01-13
> **heathen said:**
> if you already have fluxbox running I'd stick with it until there is an official fluxbuntu release
Yeah, I think that's what I'm going to do. It's not that far away anyway, April '07. In the meantime I'll get used to the Flux environment, and if worse comes to worse, I'll just reinstall Ubuntu and try something else. 
I still have many avenues to go down, just using the information available in this thread--and that's awesome!

---

### Post by heathen on 2007-01-13
feisty is due out april? or fluxbunut??

god i need to read these forums more...

---

### Post by teejay17 on 2007-01-13
> **heathen said:**
> feisty is due out april? or fluxbunut??

god i need to read these forums more...
Well "Feisty" i.e. 7.04 translates into: release date April 2007...hence the 7 and the  04. That's how the release numbers work: year and month. :KS

---

### Post by RedSquirrel on 2007-01-13
> **tcrroadie said:**
> As far as applications, I did install Thunar since launching Nautilus causes gnome-desktop or something to launch and messes up Fluxbox.  I did stumble across a work around for this but Thunar does the job just fine for me.


Just thought I'd add that the fix to make Nautilus behave in Fluxbox is that you have to add some options like this when you run it:

```

nautilus --no-desktop --browser

```From the Nautilus man page:

--no-desktop
Do not manage the desktop — ignore the preference  set  in  the  preferences dialog.

--browser
Open a browser window.

---

### Post by RedSquirrel on 2007-01-13
> **heathen said:**
> in a terminal type sudo synaptic


I think this is safer:

```
gksudo synaptic
```
See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jesse121 on 2007-01-13
The Fluxbox files you are looking for are not in usr/share/local or even etc/X11/fluxbox, the files you need to change are in home/your_username/.fluxbox. Files and folders prefixed with a period are hidden by default. 
To set your background just open up the init file inside the home/your_username/.fluxbox folder and type:

session.screen0.rootCommand:	fbsetbg -l
Sets the last background used. Set a bg in terminal first: fbsetbg path/to/file
or
session.screen0.rootCommand:	fbsetbg -r /home/your_username/.fluxbox/backgrounds
This randomly chooses a background from the folder backgrounds.

---

### Post by Tux Aubrey on 2007-01-14
Congrats on getting fluxbox up and running.  Cool isn't it?

Here's a link to my desktop (in the gallery): [FluxBuddah]("http://ubuntuforums.org/gallery/showphoto.php/photo/4349/ppuser/167727")

Out of interest, has anyone been able to do either of the following:

1.  Get a menu listing of recently used documents; or

2. Change the look of the Rox filer window - I love Rox (so simple yet powerful) but it looks clutsy on a subtle desktop.

---

### Post by NeoLithium on 2007-01-16
Hmmm, April....I'm downloading the fluxbuntu disc right now; since I've completely fallen in love with Fluxbox now for a window manager, and wouldn't mind starting out from scratch there...suppose I'll decide later, so handy having the seperate /home and stuff; no loss for my important data.

Wonder how the net setup for it is....pppoeconf?  So tempted, I'm pretty quick with this fluxbox on my ubuntu install; but it'd probably scream super-fast with a bare install...

---

### Post by Pitbull11188 on 2007-01-18
Here's my favorite way of setting up an ubuntu system:

1.) server/CLI install
2.) sudo aptitude install x-window-system-core xserver-xorg
3.) sudo aptitude install fluxbox
4.) sudo aptitude install ivman
5.) sudo aptitude install thunar or pcmanfs or rox-filer
6.) sudo aptitude install xtrlock
7.) sudo aptitude install (preferred applications)
note: you'll need browser + editor + multimedia player + im + torrent + irc + pdf + image viewer  + anything else you use.

Then I just like to use startx,  but you can install gdm, xdm, or kdm if you wish.

Overall my system boots in 20 seconds and I can reach X in 25 seconds; and that's on a 1ghz p4 with 128mb of ram.

If you choose to do a similar setup and need help PM me and I'll see what I can do.

---

### Post by teejay17 on 2007-01-18
> **Pitbull11188 said:**
> Here's my favorite way of setting up an ubuntu system:

1.) server/CLI install
2.) sudo aptitude install x-window-system-core xserver-xorg
3.) sudo aptitude install fluxbox
4.) sudo aptitude install ivman
5.) sudo aptitude install thunar or pcmanfs or rox-filer
6.) sudo aptitude install xtrlock
7.) sudo aptitude install (preferred applications)
note: you'll need browser + editor + multimedia player + im + torrent + irc + pdf + image viewer  + anything else you use.

Then I just like to use startx,  but you can install gdm, xdm, or kdm if you wish.

Overall my system boots in 20 seconds and I can reach X in 25 seconds; and that's on a 1ghz p4 with 128mb of ram.

If you choose to do a similar setup and need help PM me and I'll see what I can do.
Seriously, that looks cool. I have never done anything like this before. I guess the first thing I should do is download the server ISO. I'll get on that.

---

### Post by teejay17 on 2007-01-18
P.S. I'm going to be honest and say that once the server edition finishes downloading, I'm going to be super new at it (like no experience at all!)

---

### Post by tcrroadie on 2007-01-18
> **teejay17 said:**
> P.S. I'm going to be honest and say that once the server edition finishes downloading, I'm going to be super new at it (like no experience at all!)

You can also use the Alternate Install cd.  One of the install options on the alternate install cd is "install command line system".  Basically the same as a server install but with less bloat (lamp sever packages).  

As I am writing this, I am installing E17 from "Command Line Install" using the alternate cd.  I am creating a virtual machine in Vmware.  So far it is going really well.  Currently I only have E17 installed and working, and ram usage is incredible small so far.  Maybe I'll write a little how-to thread on it.  We'll see.  

Anyhow, thought I would add.  Sounds like you are having a really good time. 

Linux=Fun :)

---

### Post by Dakaru on 2007-01-18
Of course. Fluxbox or nothing at all.

Here is how mine looks. 

[http://img207.imageshack.us/img207/1554/screenshot2007011818132rr8.jpg](http://img207.imageshack.us/img207/1554/screenshot2007011818132rr8.jpg)

---

### Post by paparucino on 2007-01-19
> **Dakaru said:**
> Of course. Fluxbox or nothing at all.

Here is how mine looks. 

[http://img207.imageshack.us/img207/1554/screenshot2007011818132rr8.jpg](http://img207.imageshack.us/img207/1554/screenshot2007011818132rr8.jpg)

A suggestion to have a better syste, use Midnight Commander instead of gnome commander.
The first is lighter and faster.

---

### Post by teejay17 on 2007-01-19
> **tcrroadie said:**
> You can also use the Alternate Install cd.  One of the install options on the alternate install cd is "install command line system".  Basically the same as a server install but with less bloat (lamp sever packages).  

As I am writing this, I am installing E17 from "Command Line Install" using the alternate cd.  I am creating a virtual machine in Vmware.  So far it is going really well.  Currently I only have E17 installed and working, and ram usage is incredible small so far.  Maybe I'll write a little how-to thread on it.  We'll see.  

Anyhow, thought I would add.  Sounds like you are having a really good time. 

Linux=Fun :)
Thanks. Maybe I'll check that out too.
I am having fun, lots of fun:-D I love tinkering, and I love experimenting and learning. I'm not afraid to learn something new.

---

### Post by BLTicklemonster on 2007-01-19
I found midnight commander in synaptic as mc and have installed it from synaptic. Now, how do I migrate over to it?

---

### Post by paparucino on 2007-01-19
> **BLTicklemonster said:**
> I found midnight commander in synaptic as mc and have installed it from synaptic. Now, how do I migrate over to it?
Two options:
```

Create an intro in Acessories via Ccontrol Center -> Main Menu Editor -> Accessories -> new Item: Name=mc Command=/usr/bin/mc   then add icon mc.xpm

```
```

Create alauncher of gnome-terminal on the panel, you can use the terminal you prefer, right click on the laucher and select Properties, modify Command in **/usr/bin/gnome-terminal -e mc**   select the icon as stated before

```

Now you can configure gnome-terminal and mc as you prefer.
Enjoy it. :-)

---

### Post by BLTicklemonster on 2007-01-19
Thanks. I may not totally understand what is going on here. I typed mc into terminal and saw a basic dos looking file browser. This is not exactly what mc is, right? What I will do if I follow your instructions is do away with nautilus in gnome, replace it with mc? And it'll be quicker?

---

### Post by paparucino on 2007-01-19
> **BLTicklemonster said:**
> Thanks. I may not totally understand what is going on here. I typed mc into terminal and saw a basic dos looking file browser. This is not exactly what mc is, right? What I will do if I follow your instructions is do away with nautilus in gnome, replace it with mc? And it'll be quicker?
MC is a clone of the DOS Norton Commander the famous two panel file manager befor the windows era.
If you follow my instructions you have another file manager on the panel. Stop
All other programs are alway available and they are where you aspect they are.
I use it mainly because it's faster than any other file manager and because I was born with Norton Commnader under the fingers :-)
It is fully configurable and via F9 -> Command -> Edit xxxxx you can do toast, also :-)

---

### Post by BLTicklemonster on 2007-01-19
Thanks!


wth? there's smilies over there I never noticed before... when did that happen?

---

### Post by johnnymac on 2007-01-19
Love the fluxbox - don't use anything else - here's my desktop

LOVE IT!!

---

### Post by paparucino on 2007-01-19
> **BLTicklemonster said:**
> Thanks!


wth? there's smilies over there I never noticed before... when did that happen?
Uhu?!?!?
Can you explain, pls?

---

### Post by Aspra on 2007-02-11
i dont know if i did something wrong but, all there is when i switch to the Fluxbox session is the bar. I right click but no submenues come up so im basicly stuck untill i hit ctrl alt backspace and reset it i guess. then i go back to the default ubuntu.I really like the way flux looks and would like to get it working and custimized.

---

### Post by RedSquirrel on 2007-02-12
> **Aspra said:**
> i dont know if i did something wrong but, all there is when i switch to the Fluxbox session is the bar. I right click but no submenues come up so im basicly stuck untill i hit ctrl alt backspace and reset it i guess. then i go back to the default ubuntu.I really like the way flux looks and would like to get it working and custimized.


The Fluxbox links in my signature will help you get everything working and customized. :)

---

### Post by Aspra on 2007-02-12
> **RedSquirrel said:**
> The Fluxbox links in my signature will help you get everything working and customized. :)

Yeah i fallowed the guide on installing flux from [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)  before and i dont know what to do know. to me it seems that its not working right.

---

### Post by RedSquirrel on 2007-02-13
> **Aspra said:**
> Yeah i fallowed the guide on installing flux from [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)  before and i dont know what to do know. to me it seems that its not working right.


Can you be more specific? What is not working?

Were you able to set up a menu using the guide above? 

**fluxbox-generate_menu** should work, but if it doesn't, you'll have to set up the menu yourself, as described in that guide under "Menu Customization" and in the links in my signature. [EDIT: see my post (#109) below]

Fluxbox requires a fair bit of "hands on" work to get things set up.

---

### Post by RedSquirrel on 2007-02-13
Well........

I was just looking at the section of the guide that deals with "Traditional Menu Generation" and some of the commands are missing "sudo" (they have # character in front which implies that root is running those commands, but that's not really the Ubuntu way).

So, if you still don't have a menu in Fluxbox, do the following (in a terminal):

```

cd /usr/share/doc/fluxbox

sudo gzip -d fluxbox-generate_menu.gz

sudo cp fluxbox-generate_menu /usr/bin

sudo chmod a+x /usr/bin/fluxbox-generate_menu
 
```Then go back to your home directory and run  fluxbox-generate_menu:

```

cd ~

fluxbox-generate_menu

```Let me know if that works for you.

---

### Post by jay019 on 2007-02-15
Good to see all the fluxbox love. Was about to install blackbox on my new ubuntu laptop but remembered about fluxbox. Found the forum while looking for info so hi all!

):P

---

### Post by RedSquirrel on 2007-02-15
> **jay019 said:**
> Good to see all the fluxbox love. Was about to install blackbox on my new ubuntu laptop but remembered about fluxbox. Found the forum while looking for info so hi all!

):P

Hi!

Yeah, Fluxbox is great. I have been tinkering with transparency levels. Fun & easy. :)

---

### Post by teejay17 on 2007-02-15
> **RedSquirrel said:**
> Hi!

Yeah, Fluxbox is great. I have been tinkering with transparency levels. Here's a screenshot. Not overly fancy, but I like it.

What's the difference between Fluxbox and Blackbox, anyway?

---

### Post by RedSquirrel on 2007-02-15
> **teejay17 said:**
> What's the difference between Fluxbox and Blackbox, anyway?

Here is a quotation from the home page: [http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

> 
What is FluxBox

Fluxbox is yet another windowmanager for X.

It's **based on the Blackbox 0.61.1** code. Fluxbox looks like blackbox and handles styles, colors, window placement and similar thing exactly like blackbox (100% theme/style compability).

See the website for more details and a feature list.

And here is Synaptic's description for *Fluxbox*:

> 
Highly configurable and low resource X11 Window manager
Fairly similar to blackbox, from which it is derived, but has been
extended with features such as pwm-style window tabs, configurable
key bindings, toolbar, and an iconbar. It also includes some cosmetic
fixes over blackbox.

I have never used Blackbox, but from what I understand, it has fewer features installed by default, and maybe fewer dependencies. Most of the fancy stuff comes in the form of 3rd party apps since Blackbox claims to put the emphasis on the window manager itself, not on the extras.

---

### Post by PARO on 2007-04-10
This was a great thread, it really helped me get a handle on flux, but a couple things still puzzle me.  

First off, I have an extra tab on all my windows, every theme displays these... at first I thought, "these are pretty pointless," but noone else has had screenshots with them, so I think that theres a problem.  I reinstalled fluxbox from the repos and had the same result. Does anyone know how to get rid of them? See [http://img130.imageshack.us/img130/51/94265236tk1.png]("http://img130.imageshack.us/img130/51/94265236tk1.png") if you're wondering what I'm talking about.

Also, is it possible to get transparency support for flux without compiling it yourself, i.e. can I somehow enable imlib2 and disable xmb or xpm or whatever it was in the repo version (I read that's why transparency doesn't work)?

EDIT: Also, anyone know how to change the double click on a window pane from shading the window to minimize (or "iconify")? Or how to change mouse gestures in general?

---

### Post by RedSquirrel on 2007-04-11
> **PARO said:**
> This was a great thread, it really helped me get a handle on flux, but a couple things still puzzle me.  

First off, I have an extra tab on all my windows, every theme displays these... at first I thought, "these are pretty pointless," but noone else has had screenshots with them, so I think that theres a problem.  I reinstalled fluxbox from the repos and had the same result. Does anyone know how to get rid of them? See [http://img130.imageshack.us/img130/51/94265236tk1.png](http://img130.imageshack.us/img130/51/94265236tk1.png) if you're wondering what I'm talking about.

Also, is it possible to get transparency support for flux without compiling it yourself, i.e. can I somehow enable imlib2 and disable xmb or xpm or whatever it was in the repo version (I read that's why transparency doesn't work)?

EDIT: Also, anyone know how to change the double click on a window pane from shading the window to minimize (or "iconify")? Or how to change mouse gestures in general?


[B]Fluxbox Menu -> Configuration -> Tab Options -> Tabs in Titlebar
[/B]
That toggles the tabs setting.

I'm just about to head out for a bit, so I'll have to address your other issues a little later... unless someone else takes care of them before I get back... ;)

---

### Post by RedSquirrel on 2007-04-11
OK...

Transparency in the repo version should work fine. I never had a problem with transparency using the version from the repos. I'm talking about transparency for the titlebar, the toolbar, the Fluxbox menu, and the slit. If you want to have imlib2 support, I think you would have to compile it in yourself, but for basic transparency features that shouldn't be necessary. 

Transparency worked well for me with no effort, but you might try the following:

Open up your ~/.fluxbox/init file and find this line:

```
session.forcePseudoTransparency:        false
```and change it to:

```
session.forcePseudoTransparency:        true
```For that to work, you also need a decent wallpaper setting program, such as feh or eterm. feh is nice because it's a small program with few dependencies and it's in the repos.

```
sudo apt-get install feh
```By the way, to apply your new alpha values for transparency, you have to restart Fluxbox (Fluxbox menu -> Restart).

*double click on titlebar to minimize:* I thought there was an easy way to do that, but I must have been thinking of another WM. [Here]("http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize") is a page that talks about adding something similar to the Fluxbox source code (!).

---

### Post by PARO on 2007-04-11
Ahhh... I don't know how I missed that tabs menu. I'm kinda embarrased about that... it was a long day I guess.  You're right, the transparency works, I tried it with the the taskbar before and it would get lighter and my background would dissapear, and I couldn't see anything through it (I guess that's why it's called "psuedo-transparency" without the background I couldn't even tell that it was working, I thought it was just destroying my background.  

I installed Feh, and it does a fine job keeping my background alive now :) .  Thanks for that!  I can't say the psuedo-transparency is at all attractive though since it grabs the background image through open windows, which makes it look like there's a hole somewhere, or a vortex to a parallel dimension even!

Thanks for the link about changing the double-click action to the titlebar, if I ever get the courage to compile this myself I'll do that. It seems simple enough... the next time I do a fresh install.

---

### Post by RedSquirrel on 2007-04-15
> **PARO said:**
> Ahhh... I don't know how I missed that tabs menu. I'm kinda embarrased about that... it was a long day I guess.  You're right, the transparency works, I tried it with the the taskbar before and it would get lighter and my background would dissapear, and I couldn't see anything through it (I guess that's why it's called "psuedo-transparency" without the background I couldn't even tell that it was working, I thought it was just destroying my background.  

I installed Feh, and it does a fine job keeping my background alive now :) .  Thanks for that!  I can't say the psuedo-transparency is at all attractive though since it grabs the background image through open windows, which makes it look like there's a hole somewhere, or a vortex to a parallel dimension even!

Thanks for the link about changing the double-click action to the titlebar, if I ever get the courage to compile this myself I'll do that. It seems simple enough... the next time I do a fresh install.


Yeah, that's just the way transparency works in Fluxbox. It's not all that attractive. At the moment, I only have my toolbar set to alpha=160 and the rest are at 255.

If you want full window transparency, you can play around with xcompmgr and transset. I have tried them but they're slow, especially on old hardware.

I don't really like transparency all that much. It *looks* impressive but it can destroy usability in a lot of cases. I do have a transparent terminal sometimes, but that's about it.

Compiling Fluxbox isn't all that hard. If you do some searches on these forums for "compile fluxbox" and "compiling fluxbox" you should get some good results. I'm using 1.0rc3 svn revision 4855 right now. :)

---

### Post by SBFC on 2007-04-16
> 
First off, I have an extra tab on all my windows, every theme displays these... at first I thought, "these are pretty pointless," but noone else has had screenshots with them, so I think that theres a problem. I reinstalled fluxbox from the repos and had the same result. Does anyone know how to get rid of them? See [http://img130.imageshack.us/img130/51/94265236tk1.png](http://img130.imageshack.us/img130/51/94265236tk1.png) if you're wondering what I'm talking about.

The nifty thing about tabs though...you can group like windows (or any window if you really want to). if you grab a tab with middle+click (or left + right mouse button click) and drag it onto another window it'll group them. Then just click on the tabs to switch between them. Nice if you have a lot of term windows open.

---

### Post by BLTicklemonster on 2007-04-16
Hey, if you want to spiff fluxbox up a little, get 

xdesktopwaves 

from the repositories and run it.

[http://xdesktopwaves.sourceforge.net/](http://xdesktopwaves.sourceforge.net/)

[http://xdesktopwaves.sourceforge.net/manual.html](http://xdesktopwaves.sourceforge.net/manual.html)

no 3d cubes or anything, but it's still neat. :guitar:

---

### Post by RedSquirrel on 2007-04-18
> **BLTicklemonster said:**
> Hey, if you want to spiff fluxbox up a little, get 

xdesktopwaves 

from the repositories and run it.

[http://xdesktopwaves.sourceforge.net/](http://xdesktopwaves.sourceforge.net/)

[http://xdesktopwaves.sourceforge.net/manual.html](http://xdesktopwaves.sourceforge.net/manual.html)

no 3d cubes or anything, but it's still neat. :guitar:


How does it affect performance? I have an old box, and I can picture something like that eating up a lot of resources. :)

Might still give it a try though...

---

### Post by BLTicklemonster on 2008-03-23
Oops. Um, I forget. Did you ever run it, and how did it effect performance?

Oh, and having been away for a while, using mainly gnome and icewm, I came back to flux. Trying to figure out how to get gdesklets loading my starterbar automatically. But I made a neat background to go with the flux aqua theme/style.

[[IMG]http://img403.imageshack.us/img403/1748/200803240041551600x1200yq5.th.jpg[/IMG]](http://img403.imageshack.us/my.php?image=200803240041551600x1200yq5.jpg)

---

### Post by RedSquirrel on 2008-03-28
> **BLTicklemonster said:**
> Did you ever run it, and how did it effect performance?

I never did run it with Fluxbox, but I decided to try it just now (for a few minutes) with Openbox. It's mildly amusing, but I have gotten away from the eye candy thing altogether. My Openbox look is very plain.

Anyway, there are some different quality settings for the xdesktopwaves, but it does use a fair bit of CPU. Don't think I'll be running it again anytime soon. :)

---

