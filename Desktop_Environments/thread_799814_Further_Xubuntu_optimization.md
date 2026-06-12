---
title: "Further Xubuntu optimization?"
date: 2008-05-19
forum: Desktop Environments
---

### Post by gyzer on 2008-05-19
I just installed Xubuntu 8.04 on an old Dell Latitude CPI-A Laptop with these specs:
P2 366Mhz, 128MB of RAM, 6.4GB hard drive

It seems to be working fairly well, but I was wondering if there is anything else I can do to further optimize this system for it to run more smoothly?

This computer is going to primarily be used for just surfing the web, web based email, and chatting on AIM and yahoo messenger.

---

### Post by eriqjaffe on 2008-05-19
> **gyzer said:**
> I just installed Xubuntu 8.04 on an old Dell Latitude CPI-A Laptop with these specs:
P2 366Mhz, 128MB of RAM, 6.4GB hard drive

It seems to be working fairly well, but I was wondering if there is anything else I can do to further optimize this system for it to run more smoothly?

This computer is going to primarily be used for just surfing the web, web based email, and chatting on AIM and yahoo messenger.Probably the best thing to do on a system that low (my laptop has similar specs) is to do a command-line installation and then put a minimalistic window manager on it.  **Far** easier to build a system up than to break it down.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

No matter how minimalistic you go, though, Flash will absolutely bring that system to its knees.

---

### Post by kerry_s on 2008-05-19
i agree, custom or mini distro is the best option.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by gyzer on 2008-05-19
Thanks for the info!

I'm pretty new to linux, been using 8.04 since a bit before it hit full release.

I tried DSL for about two weeks, and with the limited support, I decided to give up for now and maybe try again when I'm more familiar with Linux in general.

I understand that its easier to build up a distro instead of taking one apart. I noticed that on the psychocats website that they say you need a stable internet connection, preferably wired, and sadly this laptop has no wired ethernet, I currently have a 802.11G wireless card in it right now, and that even gives me some probs.

Any help or suggestions on some things to strip out would be greatly appreciated, especially how to strip those things out.

Thanks for the help

---

### Post by kerry_s on 2008-05-19
the problem is the *ubuntus tie everything together, could lead to upgrade problems down the line. best thing to do is just leave the programs, but use lighter alternatives.

for the im, instead of pidgin, you could try ayttm
abiword for docs
epdfview for pdf
gpicview for images

using a lighter window manager, will help alot.

other wise just open synaptic, click status> installed and just mark for complete removal what ever you don't think you'll use.

just to let you know though, if it's not running it's not using resources, it's only taking up space, you'll get little to no performance gain from removing things.

---

### Post by BlackDragonBE on 2008-05-19
Check all things that start when your system logs in here:
System -> Preferences -> Sessions
Uncheck everything you don't need, e.g. Bluetooth etc.
I would suggest using IceWM as your window manager, it's very light weight.

Cheers

---

### Post by ugm6hr on 2008-05-19
Xubuntu starts a lot of gnome dependencies at startup.

Somewhere in the settings, you should be able to unselect this (sorry, I've moved to Gnome on my main laptop).

Network Manager is another thing you should try and replace.  Maybe try Wicd, or even command line wifi setup.

XFCE is relatively quick, but there are lighter options.

Preconfigured Ubuntu-based lightweight options do exist too...  but they are still Gutsy based (so far).

Although Ubuntulite is getting close [http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

---

### Post by gyzer on 2008-05-19
Sound like some really good ideas. I think I'm going to first tackle shutting down things I don't need and see if the performance is more to my liking. After that if I don't like it I'll try out this IceWM.

Is it possible to install IceWM with Xubuntu already installed? If so how do you do that and how do you switch IceWM to be the default window manager instead of XFCE?

Thanks

---

### Post by ugm6hr on 2008-05-20
> **gyzer said:**
> Is it possible to install IceWM with Xubuntu already installed? If so how do you do that and how do you switch IceWM to be the default window manager instead of XFCE?

Yes.

Enable all the repos (see link below).

Then read this: [https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)

---

### Post by gyzer on 2008-05-21
I've looked on that link and on the ICEWM FAQ on how to load ICWM after install and to make it my default window manager, but I have no idea where the  X start-up scriptis in Xubuntu, and I can't seem to find any search tool to search for them in the file system.

Any help would be very appreciated.

---

### Post by gyzer on 2008-05-21
Alright, of course after posting that last message I figured out how to get into ICEWM and all, but I've got more questions.

How do I add more programs to ICEWM? Is there another package manager or do I need to edit a specific file? If I need to edit a file, how do I do searches in the file system for Xubuntu and for ICEWM?

Thanks

---

### Post by ugm6hr on 2008-05-21
Adding Programs - use Synaptic Package Manager (it should be in the menu already).

Searching in Xubuntu / IceWM is not a standard feature (I know - stupid).  Thunar is the File Manager - and the easiest way to add searching is to install the program *catfish* - just use Synaptic Package Manager to find and install it.

---

### Post by gyzer on 2008-05-21
So Synaptic Package Manager should be accessable in the menu in ICEWM? If it is I can't find it because I looked through all the menues in ICEWM and didn't see it.
 
Or do I use Synaptic Package Manager in Xubuntu and some how add those installed programs to ICEWM? From what I saw ICEWM had very few programs in its menues.
 
Also is there a way to get ICEWM to show your wireless network connection status like next to that cpu utilization icon or something?

---

### Post by eriqjaffe on 2008-05-21
You should be able to just type "synaptic" in a terminal.

Or you can type "synaptic &" in a terminal, which won't kill synaptic if you close the terminal.  ;)

You can also just use apt in the terminal...some examples:

To search the repos for "catfish":

```
sudo apt-cache search catfish
```

To filter your searches, you can pipe that through grep.  To return packages named "catfish" but only see the ones with "dev" in the package name:

```
sudo apt-cache search catfish | grep dev
```

And then to install packages:

```
sudo apt-get install catfish
```

You can install multiple pacakges (picking a few random packages here):

```
sudo apt-get install catfish audacious abiword
```

To remove them, just replace "install" with "remove".  I find Synaptic to be a beast on my old laptop.  I've gotten so used to using apt that I don't use Synaptic on my desktop, even though it's more than capable of running it acceptably.

---

### Post by gyzer on 2008-05-21
So then when I'm using synaptic in ICEWM all the programs I download and install will be available in ICEWM?

---

### Post by ugm6hr on 2008-05-21
This will launch Synaptic (From Alt+F2)
```
gksu /usr/sbin/synaptic
```

You can edit IceWM menus manually, but from memory, when I experimented with it, the *menu* package should pre-configure it for you.

If you install programs in either XFCE or IceWM, they will be available in both.  You just need to find them in IceWM if they don't automatically get a menu launcher.

---

### Post by gyzer on 2008-05-21
So the menu package isn't downloaded automaticly when you download and install ICEWM? Is it just in the same repository as ICEWM?
 
Where is the file that I can edit the ICEWM menus?
 
How do I find then the individual files to run the programs I want to put into the ICEWM menus?
 
How can I access a file manager inside ICEWM?
 
Thank you guys for all your help!

---

### Post by joninkrakow on 2008-05-21
I just did a "sudo apt-get install icemc" and it installed the menu editor. It's running as I type. :-)

-Jon

---

### Post by ugm6hr on 2008-05-21
> **gyzer said:**
> So the menu package isn't downloaded automaticly when you download and install ICEWM? Is it just in the same repository as ICEWM?
 
Where is the file that I can edit the ICEWM menus?
 
How do I find then the individual files to run the programs I want to put into the ICEWM menus?
 
How can I access a file manager inside ICEWM?

1. No.  I think it needs to be installed separately (you can use apt-get install menu).

2. [http://www.icewm.org/manual/icewm-8.html](http://www.icewm.org/manual/icewm-8.html) (/lib/programs)

3. They are probably in /usr/bin.  But the easiest way is to install *menu* to see if it will find them automatically.  Otherwise, boot back into XFCE (Xubuntu), and find the Properties of all the menu entries from there (I think appfinder allows you to find them all and get their location).  You should also be able to launch appfinder from IceWM, but I can't remember what the command is (something like Alt+F2; xfce4-appfinder)

4. Alt+F2: thunar

---

### Post by joninkrakow on 2008-05-21
> **gyzer said:**
> So the menu package isn't downloaded automaticly when you download and install ICEWM? Is it just in the same repository as ICEWM?
 
Where is the file that I can edit the ICEWM menus?
 
How do I find then the individual files to run the programs I want to put into the ICEWM menus?
 
How can I access a file manager inside ICEWM?
 
Thank you guys for all your help!

Oops, I missed the file manager question the first time around.

I'm going through this at the same time as you, and I'm discovering some interesting stuff as I go. One of them is an interesting file manager. It's called xfe.

I installed it with a simple "sudo apt-get install xfe". It's much faster than thunar, and quite powerful. 

Also, I wasn't very clear in my first post, but the app for modifying menus is called icemc, which I got by doing a "sudo apt-get install icemc". It is a bit confusing getting it to work, so here's what I did.

First, using icemc (launched from the terminal), I opened the menu file located in /usr/share/icewm. I next saved it in ~/.icewm (my home folder). If you don't already have a .icewm folder, you will need to create it. Don't forget the dot at the beginning of the name. :-)

Once I saved the file there, I added an application, and named it "xfe" with the execution of "xfe", and now it's in my menu. What's cooler is that I found an icon file for xfe inside "/usr/share/pixmaps" that I added.

Next, I copied the file "/usr/share/icewm/toolbar" to "~/.icewm".
I added at the bottom:
"prog xfe xfe xfe"

And now it's on my toolbar. I lost my Firefox, so I have had to add that back in by adding 
prog firefox firefox firefox

Unfortunately, I then discover that I don't have an icon for Firefox, whereupon I discover a png in the /usr/share/pixmaps folder. I simply opened that up in Gimp, and resave it as an xpm. Unfortunately, getting that into the /usr/share/pixmaps folder requires some footwork with sudo. But I eventually got a firefox.xpm file into the right location, and I have firefox back. :-)

In any case, I hope this rambling helps you get this going too.

-Jon

I opened that, and at the bottom,

---

### Post by gyzer on 2008-05-21
Thank you guys so much!!!
 
I will be trying that stuff out when I get home tonight and I'll let you know how it goes.

---

### Post by gyzer on 2008-05-22
Ok, I think I'm starting to get the hang of this stuff now with icewm.

One thing though that I don't know how to do, how can I get my wireless network status to show up next to my time in the toolbar, similarly as in XFICE? Also how can I get the similar "automatic" update icon that I get in XFICE in icewm?

I do really like xfe, but I noticed it doesn't have a search feature. Are there any you would recommend?

Also I noticed that the contents of my desktop folder don't get displayed on icewm's desktop. How can I fix this?

---

### Post by ugm6hr on 2008-05-22
> One thing though that I don't know how to do, how can I get my wireless network status to show up next to my time in the toolbar, similarly as in XFICE? 

You can use Network Manager (NM in Xubuntu / Gnome), but that is quite a "heavy" Gnome application to have running in IceWM; if you want it, just add *nm-applet --sm-disable* to the startup apps list.  A lighter option is Wicd (see link in sig) - you will have to remove NM (network-manager and network-manager-gnome) to install it though.  If you are wifi only - be aware that uninstalling NM will lose wifi - so make sure you are ethernet plugged in when you do it, or download Wicd before uninstalling. 

> Also how can I get the similar "automatic" update icon that I get in XFICE in icewm?
Again - a question of resources - the more you have running, the slower things get.  Again - add to startup apps list as *update-notifier*

> I do really like xfe, but I noticed it doesn't have a search feature. Are there any you would recommend?
I would actually stick with thunar (same as Xubuntu), and just install *catfish* to search (if it isn't default).  Other benefit of thunar - you can also have thunar-volman automount USB devices etc (albeit at more processor use).

> Also I noticed that the contents of my desktop folder don't get displayed on icewm's desktop. How can I fix this?
IceWM doesn't have a default Desktop Manager.  There are a number of options.  The easiest is to use a File Manager with dual function (e.g. thunar, ROX-filer).  If you want to stick with xfe, then I think there is an app called *fbdesk* that is a standalone lightweight desktop manager.

---

### Post by joninkrakow on 2008-05-22
> **gyzer said:**
> Ok, I think I'm starting to get the hang of this stuff now with icewm.

One thing though that I don't know how to do, how can I get my wireless network status to show up next to my time in the toolbar, similarly as in XFICE? Also how can I get the similar "automatic" update icon that I get in XFICE in icewm?


Unfortunately, icewm is not a desktop environment as is xfce, so some things are more complicated. I've been discovering this as I have been on my own journey to move from xfce to icewm. I like xfce, but it is so much slower on my ancient PII 366 laptop, so I'm forcing myself to try to get icewm going for me. Hopefully, my own journey will help you. :-)

As to the network monitor. Theoretically, icewm is supposed to have something--it's in the preferences file, but turning it on didn't help. Maybe it's my hardware.

In any case, it can't hurt you to turn it on. Besides, you will probably _want_ to modify the preferences file anyway. 

Here's what you can do.

in the terminal, type "sudo cp /usr/share/icewm/preferences ~/.icewm/" That will copy the generic preferences file to your user folder's icewm folder.

Next, you can open the new, copied file in mousepad or some other text editor. Mousepad works for me. It has good enough search facilities. I scrolled through the document, looking at everything, but you probably don't want to waste your time with that (at least not yet), so hit <control>-F to invoke the Find, and type the word "network". The first item that pops up should be, "Show network status on task bar">. The next line begins with a #. Remove that, and change the text, "TaskBarShowNetStatus=0 # 0/1" to "TaskBarShowNetStatus=1 #0/1". You've just switched that 0 to a 1, and now, it's turned on, supposedly. Like I said, it didn't work on my Dell laptop. 

One other thing to try. Look for the line "TaskBarDoubleHeight=0" and change that 0 to a 1. Now, when you relaunch icewm, you will have a task bar that is twice as tall, but next to the launcher icons is a field you can type into to launch applications. Worth the extra desktop space, IMO. :-)

> 
I do really like xfe, but I noticed it doesn't have a search feature. Are there any you would recommend?


Still looking! I have one from KDE, but it keeps crashing on me--besides, who wants to keep loading all the kde libraries? I know that there's something for Gnome, but I haven't found it on my hard drive. Beagle? I need to keep looking. Maybe somebody else?

> Also I noticed that the contents of my desktop folder don't get displayed on icewm's desktop. How can I fix this?

Oh, man, I did a search on this, and discovered a wonderful trick that pcman does. If you don't know it, pcman is a file browser, like xfe. It's not as flexible, but it useful most of the time. It's quite fast also. you can do a "sudo apt-get install pcmanfm" do install it. Once it's installed, you need to make a minor change to icewm's preferences.

What you need to do is create a new file, called "startup" You can do it from mousepad or nano, or any text editor. 

Once it's open, add the following text to it:

```

pcmanfm &
#nm-applet --sm-disable &

```

I commented out the nm-applet part, because I haven't mentioned it yet. But, if your modification to the icewm preferences doesn't give you a monitor, this, at least, will give you something. It's from gnome/xfce, but it shows up in the panel at the bottom. Just uncomment it to turn it on. :-)

Now, when you are done with editing the file, and save it, go to the terminal, and type the following commands:
```

cd ~/.icewm
chmod +x startup

```

That will make the file executable, so that it will actually work. 

Now, you can sign out of icewm, and log back in, and see if everything is working.

If it is, launch pcmanfm, and go to the Edit menu, and open the preferences. Inside that window, is a tab, named "Desktop"
Choose that, and check "Show file icons on desktop" You can also use it to show a desktop picture. I discovered some nice cosmic ones inside /usr/share/pixmaps that can be used. :-)

There are some other oddball things I had to figure out along the way. For instance, where all the icons are located that icewm uses (/usr/share/pixmaps), and that the file for Firefox doesn't work, because it's a png. A quick trip to GIMP fixed that, but I couldn't save it in that location, and had to sudo cp  it later. Also, it seems that pcman doesn't have an icon either. :-(

If I think of anything else, I'll add it, but this has been an interesting ride for me so far, and I'm glad I'm not alone. :-)

-Jon

---

### Post by joninkrakow on 2008-05-22
Forgot one important point. I discovered a nice faq/guide to icewm. It's right here:
[http://socrates.if.usp.br/doc/icewm-common/FAQ/IceWM-FAQ.html#toc4](http://socrates.if.usp.br/doc/icewm-common/FAQ/IceWM-FAQ.html#toc4)

-Jon

---

### Post by gyzer on 2008-05-22
Thank you guys so much!!
 
I'm going to try pcman, and possibly start to use it for every-day browsing instead of xfe, with just using xfe for more intensive tasks.
 
I am going to try Wicd and see if I can get some graphical representation on the task bar for what my connection strength is.
 
Also where is the file that contains the startup program list? Would it be that startup file joninkrakow talked about making in the ~/.icewm directory?
 
joninkrakow- Are maybe some of the problems you are encountering, like with showing a network status icon in the task tray have something to do with Icewm not being currently updated to work with 8.04?
 
This has indeed been a learning experience. I had no idea that there was a separation between window managers, file managers, and desktop managers. Windows really makes you really take things for granted lol.
 
If I have anymore questions or if I run into anymore problems I will defiantly post again.
 
Thank you guys again so much, this has been a great experience.

---

### Post by joninkrakow on 2008-05-22
> **gyzer said:**
> Thank you guys so much!!
 
I'm going to try pcman, and possibly start to use it for every-day browsing instead of xfe, with just using xfe for more intensive tasks.
 
I am going to try Wicd and see if I can get some graphical representation on the task bar for what my connection strength is.
 
Also where is the file that contains the startup program list? Would it be that startup file joninkrakow talked about making in the ~/.icewm directory?
 
joninkrakow- Are maybe some of the problems you are encountering, like with showing a network status icon in the task tray have something to do with Icewm not being currently updated to work with 8.04?
 


Yeah, the startup file needs to be inside the ~/.icewm directory. It also has to be made executable (chmod -x ~/.icewm/startup) to work properly. I found that out the hard way. :-)

You know, I hadn't thought about icewm not being 100% compat. with Hardy. I wonder, also, now that you say that, if it could be the new kernel, as well? Need to look into that. Thanks for the thought!

-Jon

---

### Post by gyzer on 2008-05-22
Look into using Wicd for your network manager. I was looking at their faq, and they have some directions on how to get the tray icon to appear specifically in icewm.
 
Also I noticed that in the menu there are several folders that aren't represented in icewm menu file. Do you know if there is a way to place things in these folders or a way to delete these folders outright, seeing as I've already made several custom folders with most of the applications that I want to use anyways?

---

### Post by Inxsible on 2008-05-22
Say gyzer, did you install IceWM in a separate install or did you do it over Xubuntu itself and then chose which WM to choose at startup ?

---

### Post by eriqjaffe on 2008-05-22
> **gyzer said:**
> I am going to try Wicd and see if I can get some graphical representation on the task bar for what my connection strength is.Wicd's tray icon won't show you your connection strength, it'll just show you that you're connected.

---

### Post by ugm6hr on 2008-05-22
> **eriqjaffe said:**
> Wicd's tray icon won't show you your connection strength, it'll just show you that you're connected.

I haven't used it since Gutsy - but it used to give a 4 bar representation before.  Can't see why they would have removed that function.

---

### Post by gyzer on 2008-05-22
I installed Xubuntu first, then installed Icewm. I launch Icewm via the Xubuntu login menu with choosing my sessions.

---

### Post by NightwishFan on 2008-05-22
It is is slow, try Puppy Linux. It can run in 32mb of ram.
[http://puppylinux.org/](http://puppylinux.org/)

---

### Post by gyzer on 2008-05-22
I'm running Xubuntu with Icewm on 128mb of ram and it runs quite well. I can't multitask 20 things at once, but its work alot better then it did while using XFCE. 
 
Someone already mentioned in this thread to try puppylinux. I might try it one day, but as of now I'm very happy with what I'm using.

---

### Post by eriqjaffe on 2008-05-22
> **ugm6hr said:**
> I haven't used it since Gutsy - but it used to give a 4 bar representation before.  Can't see why they would have removed that function.You know what, you're right.  I just wasn't looking at it closely enough.

---

### Post by gyzer on 2008-05-22
Ok, something horrible has happened. I've installed Wicd, and I got it to appear on the task bar in icewm, but it runs 50x slower then Network Manager. In XFCE it runs like 100x slower. And it is also very unresponsive, where the prefrences window opens but doesn't load everything.

Is there something I can do to fix this? How can I change back to network manager?

---

### Post by ugm6hr on 2008-05-23
Uninstall wicd from Synaptic, and re-install network-manager-gnome.

Put *nm-applet --sm-disable* back into the startup apps, and remove wicd.

I haven't used Wicd for almost 12 months (computer & Xubuntu upgrade), but your statement suggests it has gone somewhat backwards in that time...

---

### Post by gyzer on 2008-05-23
k thanks. Yeah network manager is working so much better now.

small problem that I've encountered after installing pcman:

When ever it opens for the first time I get this large error window which says this:

"GTK+ icon theme is not properly set
This usually means you don't have an XSETTINGS MANAGER RUNNING. desktop ENVIRONMENTS like gnome or xfce AUTOMACTILLY execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0."

I did this and it hasn't changed anything. How can I fix this so this message doesn't come up in icewm?

Thanks

---

### Post by joninkrakow on 2008-05-23
Unfortunately, I just read yesterday somewhere (probably the wicd web site) that once you remove wicd, you won't have network access. However, I don't know if you can reinstall network manager without first uninstalling wicd. I believe the page I read suggested downloading the packages for network manager before the uninstall, and then installing these from your hard drive. In any case, I guess I'll stick with nm for now. :-)

-Jon

---

### Post by joninkrakow on 2008-05-23
> **gyzer said:**
> k thanks. Yeah network manager is working so much better now.

small problem that I've encountered after installing pcman:

When ever it opens for the first time I get this large error window which says this:

"GTK+ icon theme is not properly set
This usually means you don't have an XSETTINGS MANAGER RUNNING. desktop ENVIRONMENTS like gnome or xfce AUTOMACTILLY execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0."

I did this and it hasn't changed anything. How can I fix this so this message doesn't come up in icewm?

Thanks

If you created the .gtrc-2.0 file, and added the text, it should work. Are you sure you put a return after the text? I once had a config file not work properly because I didn't hit return after the last line. :-)

Second thought. It may be possible that you don't have the Tango theme icons installed.

Here's where you find the icons it's looking for. Go to /usr/share/icons and see what themes are installed. If Tango is there, and there are icons inside, then something is flakey with your .gtkrc-2.0 file. If there's not Tango, pick a theme that's there, and use that name. I've got a bunch that were installed with Xubuntu, so I'm betting you've got a bunch, also. BTW, oddly enough. Even though I changed my theme to another after first putting in the file what you wrote above, I _still_ get the Tango theme. Weird...

-Jon

---

### Post by firmit on 2008-05-23
I just want to shout out LXDE :)

It is a lightweight DE alternative. Uses much less resources than xfce. I know icewm might do the trick, but if you are looking for a lightweight DE (uses openbox as wm, pcmanfm), LXDE is a good choice: [http://ubuntuforums.org/showthread.php?t=738958](http://ubuntuforums.org/showthread.php?t=738958)

It also comes with a lightweight wireless network applet (lxnm). Have not tested lxnm myself, though.

---

### Post by gyzer on 2008-05-23
I'll try that joninkrakow.
 
Wicd does actually remove nm when it gets installed, but I found a great way to get nm back installed easier then a download. Do a sudo apt-get install nm(I forget the full name of the application) and then place the original Xubuntu CD that you originally installed from in, and it'll search for it and install it.
 
A hell of allot easier to deal with then downloading it.
 
I'll try out the icon thing tonight.
 
I also had some keyring problems, they might be fixed now, but I was wondering if there was a way to disable the keyring, or where I can find a keyring manager? I've looked in add/remove programs and in synaptic and haven't found any keyring managers.
 
Its so cool to have gotten this far, I'm so close to being done with exactly the type of environment that I want.
 
Oh one last thing, I'm using ayttm as my AIM/yahoo client, and it works pretty well, but oddly some of the people on my buddy list, their name shows up as something like "w::". Anyone have any ideas on what might be causing this problem? I'd really like to not have to use pidgen on here.

---

### Post by |Eric| on 2008-05-26
install slackware 
& run fvwm as a window manager 
startx to start Xwindows (grafic interface)

---

