---
title: "HOW TO: AWN Media Control Applet for Amarok, Rhythmbox, Banshee and Exaile"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by narehart on 2007-09-27
Hi, Everyone.  This is my first guide.  While surfing the AWN forum at planetblur I found a cool applet which allows you to control your media player from a button on AWN.  The applet will display album art and title as well as prev next pause and play buttons.

[IMG]https://launchpadlibrarian.net/9336809/Screenshot.png[/IMG]

Before I start I'm assuming you already have AWN.  If not follow this guide here: [http://ubuntuforums.org/showthread.php?t=385981&highlight=media+control+applet]("http://ubuntuforums.org/showthread.php?t=385981&highlight=media+control+applet")

Okay to get started downlaod the trunk tarball from here: [https://launchpad.net/awn-py-applets/trunk/0.2b/+download/trunk2b2.tar.gz]("https://launchpad.net/awn-py-applets/trunk/0.2b/+download/trunk2b2.tar.gz")

Open the tar with archive manager. Then open the folder MEDIA CONTRL APPLET. You should see another folder named media control applet and a file called media-control.desktop. Extract both of these to /home/.config/awn/applets. If the folder doesn't exist then just create it.

Finally restart AWN.  Go to AWN Settings Manager, add the applet and enjoy. 

Oh, If you plan on using this with Amarok you'll need to download python-dcop from Synaptic.

---

### Post by hyperair on 2007-09-27
Hey that looks pretty good. I'll try it when I get home from college today =P

---

### Post by patchoro on 2007-09-28
Very nice applet. Would like another icon tho... 
Never satisfied, sorry mate. Thnx for the exellent tut!

---

### Post by malegria on 2007-09-29
The link to the trunk tarball is dead.

Could you post another?

Thanks

---

### Post by randome on 2007-09-29
I found the .awn file here [https://launchpad.net/awn-py-applets/+download](https://launchpad.net/awn-py-applets/+download)
Just not shure what to do with it.

---

### Post by tehkain on 2007-09-29
Hello I am the developer. I suggest following my directions on this page:
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=895&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=895&page=1&isLive=true)
or the wiki here:
[http://wiki.awn-project.org/index.php?title=Avant_Python_Applets_Project](http://wiki.awn-project.org/index.php?title=Avant_Python_Applets_Project)
> 
[img]http://img227.imageshack.us/img227/2103/screenshotvh6.png[/img]
AWN applet packages: install via awn manager(click the + button and select the .awn)
__Battery Level__
[https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Battery-Level.awn](https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Battery-Level.awn)
__Gnome Quit__
[https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Quit-Applet.awn](https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Quit-Applet.awn)
__Media Icons__
[https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Media-Icons.awn](https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Media-Icons.awn)
__Media Control__
[https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Media-Control.awn](https://launchpad.net/awn-py-applets/trunk/0.2b/+download/Media-Control.awn)

[Wiki Page with installation instructions](http://wiki.awn-project.org/index.php?title=Avant_Python_Applets_Project)

# Battery Level Applet
 > Displays Battery level and time remaing
 > Displays charging stats
 > Changes icons according to level/charging
 > Uses the Oxygen Projects Battery icons(lgpl)
 > Detects AC/Power changes like unpluging

[img]http://img520.imageshack.us/img520/2228/54656111111111114546rc0.png[/img]
[img]https://launchpadlibrarian.net/9336809/Screenshot.png[/img]

Amarok support requires python-dcop

# Media Icons
 > Its the Media Control applets controls on your awn bar!
 > 100% independent of Media Control. Uses the same module tho(included in both applet packages).
 > Supports the same apps as Media Control
# Media Control Applet 
 > Amarok, Rhythmbox, Banshee and Exaile support. Listen support is partial
 > Auto detects players
 > Amarok support requires python-dcop

# Quit Applet
 > Calls gnome quit dialog


Latest and Greatest in trunk.


---

### Post by vav on 2008-02-11
This wiki has the same problems as almost ALL linux applications:
Installation is detailed very well with MULTIPLE options. But there's NO mention of how to actually RUN it or CONFIGURE it once it's installed!. I dont know how many apps I've seen where there are source files, .deb files, .rpm files, installation instructions for sparc and what not, but the core command to run the app is just simply... not mentioned! and is sometimes not the same as the package name... of course a lot of apps have multiple ways in which they can be used, at least mention a few!

In this case, it's configuration: it says the media buttons can control many players, but doesnt say how to set it to control a app... I need python-dcop to control amarok.. ok installed. But how do I select them to control amarok? what if I want to change to totem later?!

Sorry about the rant... but... how do I set this up to control amarok? I have a gnome ubuntu install and amarok isnt the default player, so clicking on the media buttons does nothing for me. There's no way to configure the launchers in awn-manager either :(

EDIT: And lo and behold... it starts controlling amarok on its own... after a few restarts... hope it keeps working. still dont know how I would switch it around for other players.

---

