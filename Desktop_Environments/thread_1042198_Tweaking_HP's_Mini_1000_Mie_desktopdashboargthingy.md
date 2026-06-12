---
title: "Tweaking HP's Mini 1000 Mie desktop/dashboarg/thingy"
date: 2009-01-17
forum: Desktop Environments
---

### Post by Bailywolf on 2009-01-17
I ended up an early adopter of HP's Mini with their MIE ('mobile internet experience') sort of by accident.  I really bought this netbook instead of the XP edition because of the 'powered by ubuntu' adcopy.

Anyhow, I like it, but...

HP's desktop/dashboard thing is pretty cool, and has some useful features- one being how good it looks on the screen.  Its well designed for the machine's form factor.  There are also two hotkeys on the keyboard that tie into it.  One takes you back to the dash from where ever you are, the other brings up a scroll of the programs currently running. After playing with it, I can flip between aps as fast or faster then with an XP taskbar.  I like these features.

My main issues with it is I'm stumped on how to customize it.  The dash is divided into three main panels.  The left is for email (via Thunderbird), the middle for internet (via Firefox), and the right is for media (defaulting to pictures and music). 

Fine, but I don't use a local email client- and so a full third of my desktop is wasted. 

I'd like to be able to customize what shows up on my desktop, but have no idea where the config for this stuff is hiding, or how to find it.  

Second issue, HP hasn't provided a way to add applications to the machine except via their add/remove programs (which is like a cut down Synaptic).  Funny thing, with ALT-f2 you can key 'gnome-terminal' and have a proper command line from which you can access the full blown Synaptic PM.  Lovely, but stuff installed this way doesn't seem to show up on HP's menus.  Worse, if I just grab a package and do a cl install, I can't access it except through the cl, and honestly for most of the things I want to install, this is a pain in the ***.  I just want to click the petty picture and have my app run, but there's no way to add items or cl shortcuts to these things that I can find, and again, I have no idea where the files storing this config are located.


Since this thing just came out, I suppose this stuff is to be expected.  This thing is aimed at people who'll use HP's interface as HP intended, and not try and install aps from other source lists or via direct downlod.  The linux is almost entirely hidden (which is a good thing for the future of linux, but irritating sometimes).  

So, I'm hoping some folks around here with more linux/ubuntu kung-fu and/or one of these genuinely sweet little machines might have some insight, tips, and tricks.  

-B

---

### Post by Bailywolf on 2009-01-17
A little more info-  it looks like the program nav stuff is a heavily tweaked version of gnome-panel.  I started looking at a process list, and trying to ID which processes lead to which elements of the dashboard, and when I killed gnome-panel, what died was the program list elements of the gui.  That makes perfect sense, given what gnome-panel is... and bodes well for my eventually running down what process and config are responsible for the rest of the desktop look/feel.

-B

---

### Post by Bailywolf on 2009-01-17
More info.

You can customize the Settings menus and add a bunch of stuff that's not shown by default, including a root terminal, logging, and a bunch of settings and config tools.  You can even add new items to this menu- providing the cli script for the clicky icon.  BUT I still can't see how to do that on the applications menus where stuff like Open Office and Firefox live.  

-B

---

### Post by Bailywolf on 2009-01-17
Woops!

I deleted the contents of my package source file (all of HP's sources).

Now I need to find these again somehow... perhaps adding the standard Heron sources.  

-B

---

### Post by Jeff Johnston on 2009-01-17
What kind of battery life do you get? I'll have to run for a few hours straight to see exactly what I get but it doesn't feel like 3 hours...

Thanks for the tip on the key to flip between the running programs!

I agree with you about the dashboard. I don't care about any of the local programs as everything I do requires a browser. I am thinking it would be cool to get vpn working on here so I can get onto my work network though :).

-Jeff

---

### Post by Jeff Johnston on 2009-01-17
One thing I have figured out is running the browser in full screen mode and just using the shortcut keys gives you more than enough real estate!

---

### Post by Bailywolf on 2009-01-17
I decided to see what I could do with the Ubuntu-behind-the-scenes, and just installed Wine and Wine Door (a GUI for Wine) successfully.  I'm going to see if I can get *World of Goo* running.

-B

---

### Post by Bailywolf on 2009-01-17
> **Jeff Johnston said:**
> One thing I have figured out is running the browser in full screen mode and just using the shortcut keys gives you more than enough real estate!

I figured that out too- especially for working inside one site (like google docs) it's a pretty painless experience.  When I put the googlebar up where I like to have it, the browser window starts to feel sort of cramped, but F11 takes care of that!

Any other good hotkey tricks you've got in your arsenal?


I'me getting about three hours of wen surfing or poking around in the file system.  I haven't done a hard-burn yet, running half a dozen aps, music, and movies yet.  I think it'll give 2 hours and change even with heavy use.  It's like paradise for me- I'm used to a laptop with like 9 minutes of battery time.  2+ hours feels like ages.

-B

---

### Post by mikewhatever on 2009-01-18
If that's the netbook with disabled Terminal, have you found any way to re-enable it? You are both welcome to upload some pictures to imageshack or the like and post the links, there isn't much info about the interface on the web yet.

---

### Post by Bailywolf on 2009-01-18
> **mikewhatever said:**
> If that's the netbook with disabled Terminal, have you found any way to re-enable it? You are both welcome to upload some pictures to imageshack or the like and post the links, there isn't much info about the interface on the web yet.

I don't really have any idea why they claimed to have disabled anything- all they really did was hide a link to it in the GUI (which you can restore anyhow by customizing the look of the settings gui list).  

If you hit alr-F2 you get run application popup, and can key 'gnome-terminal'.  It'll even autocomplete the command for you!


I used it to install Wine and Wine Doors successfully, and was playing World of Goo with almost no fiddling.  I had to run down some dependencies for Wine, but the actual effort to install it on this machine was pretty negligible.  I added all the Heron repositories to the sources list, and had no problem with them in Synaptic.  

I still haven't cracked how to add to the program launcher menus yet, or the grail of this thing, how to customize the desktop.  

Will post when I get some more insight on this thing.

-B

---

### Post by Bailywolf on 2009-01-18
Here's some screen caps:

[IMG]http://farm4.static.flickr.com/3376/3207132273_e1d6512589.jpg[/IMG]
The basic desktop.  See on the left?  All that space I'd like to do something else with since I don't use local email clients.

[IMG]http://farm4.static.flickr.com/3457/3207132277_9a7f559ed3.jpg[/IMG]
ALT-F2 gets you this lovely little dialog box.

[IMG]http://farm4.static.flickr.com/3492/3207132287_0b36a72e17.jpg[/IMG]
Key 'gnome-terminal' (minus the quotes) and you get a proper cli.

[IMG]http://farm4.static.flickr.com/3300/3207132295_661f2b1911.jpg[/IMG]
Here's my advanced settings- you can see I've added some things.  From here you select the 'custom settings' icon, and get this...

[IMG]http://farm4.static.flickr.com/3305/3207132299_ea59591615.jpg[/IMG]
From here you can select 'root terminal' to have that added to the settings menu.  


When you're in the command line terminal, you can do anything you want.  straight up Ubuntu in every way I've yet tried.  


There's nothing disabled at all.  


-B

---

### Post by mikewhatever on 2009-01-19
That looks good, and I am really not sure what all these articles talked about.:confused: Guess people like to get over exited.
[http://laptoping.com/hp-mini-mi.html](http://laptoping.com/hp-mini-mi.html)
[http://arstechnica.com/journals/linux.ars/2009/01/08/hp-introduces-command-line-free-linux-netbook](http://arstechnica.com/journals/linux.ars/2009/01/08/hp-introduces-command-line-free-linux-netbook)
[http://digg.com/linux_unix/Linux_based_HP_Mini_Mi_ships_with_command_line_disabled](http://digg.com/linux_unix/Linux_based_HP_Mini_Mi_ships_with_command_line_disabled)
[http://www.linuxtoday.com/news_story.php3?ltsn=2009-01-09-008-35-NW-HW](http://www.linuxtoday.com/news_story.php3?ltsn=2009-01-09-008-35-NW-HW)

---

### Post by Bailywolf on 2009-01-20
Some of HP's adcopy included a line about this version shipping with the command line being disabled.  Best I can tell, all they did was remove any obvious link to it.  

I played with it all weekend, and can now completely recommend this little machine.  I found the config files which point the program launcher at the Eliza-based media manager, so I think I'm fairly close to gutting the MIE desktop and filling it with tasty cornbread stuffing.

-B

---

### Post by Ubuntu Joe on 2009-01-20
Not sure if this was mentioned but:

The Mini holds it's own restore on the hard drive . . . To access it, and restore the factory default OS, simply shut down, reboot, and keep pressing ESC . . . you will get a menu giving you the option of Restoring or booting from the hard drive . . .

---

### Post by Bailywolf on 2009-01-20
> **Ubuntu Joe said:**
> Not sure if this was mentioned but:

The Mini holds it's own restore on the hard drive . . . To access it, and restore the factory default OS, simply shut down, reboot, and keep pressing ESC . . . you will get a menu giving you the option of Restoring or booting from the hard drive . . .

I noticed that in the docs- it gave me more confidence in my kicking of the OS knowing I could get an easy do-over.

-B

---

### Post by Jeff Johnston on 2009-01-20
I will have to say that I love the touchpad on this device. Its not really advertised how nice the touchpad is. You can do a single and double-click with just the slightest tap. The scrollbar on the touchpad works decent too. Its not perfect, but I for sure appreciate having it be there. 

The quality of the monitor has totally exceeded my expectations as well.

---

### Post by Bailywolf on 2009-01-21
Could one of you kind and wise human beings in possession of an HP Mini Mie please please post the contents of your sources.list file?

It occurred to me that while I can update Ubuntu and its packages with the Heron repositories I replaced them with, I can't update Hp's Mie stuff, and I imagine there's going to be a fair bit of updating going on in the next couple of months.

I goofed it with Ubuntu Tweak, and wiped out Hp's repositories rather than appending to the list.  

-B

---

### Post by Ubuntu Joe on 2009-01-21
> **Bailywolf said:**
> Could one of you kind and wise human beings in possession of an HP Mini Mie please please post the contents of your sources.list file?

It occurred to me that while I can update Ubuntu and its packages with the Heron repositories I replaced them with, I can't update Hp's Mie stuff, and I imagine there's going to be a fair bit of updating going on in the next couple of months.

I goofed it with Ubuntu Tweak, and wiped out Hp's repositories rather than appending to the list.  

-B

I sent mine back, so I can't tell you the pre-installed repositories, but I kinda posted that restore tip for you, so you can go back to the way it once was . . . then redo your other modifications . . . but I'm sure someone else can give you the repositories if you don't want to redo your other efforts . . .

---

### Post by Bailywolf on 2009-01-21
> **Ubuntu Joe said:**
> I sent mine back, so I can't tell you the pre-installed repositories, but I kinda posted that restore tip for you, so you can go back to the way it once was . . . then redo your other modifications . . . but I'm sure someone else can give you the repositories if you don't want to redo your other efforts . . .

Yeah, at this point it would be hours of fiddling to get things back to the way they are now.  Hmmm... I wonder if I can crack into the restore partition and find the archived copy of the file?

-B

---

### Post by Ubuntu Joe on 2009-01-21
> **Bailywolf said:**
> Yeah, at this point it would be hours of fiddling to get things back to the way they are now.  Hmmm... I wonder if I can crack into the restore partition and find the archived copy of the file?

-B

Now, **that **sounds like fun . . . I love freeing up that locked down space for my own purposes . . . sort of poetic don't you think?

---

### Post by Tomy on 2009-01-21
> **Bailywolf said:**
> Could one of you kind and wise human beings in possession of an HP Mini Mie please please post the contents of your sources.list file?

It occurred to me that while I can update Ubuntu and its packages with the Heron repositories I replaced them with, I can't update Hp's Mie stuff, and I imagine there's going to be a fair bit of updating going on in the next couple of months.

I goofed it with Ubuntu Tweak, and wiped out Hp's repositories rather than appending to the list.  

-B

sources.list
```
deb http://hpmini.archive.canonical.com/mie/ hardy main universe multiverse restricted
deb-src http://hpmini.archive.canonical.com/mie/ hardy main universe multiverse restricted

deb http://hpmini.archive.canonical.com/mie/ hardy-updates main universe multiverse restricted
deb-src http://hpmini.archive.canonical.com/mie/ hardy-updates main universe multiverse restricted

deb http://hpmini.archive.canonical.com/mie/ hardy-security main universe multiverse restricted
deb-src http://hpmini.archive.canonical.com/mie/ hardy-security main universe multiverse restricted

deb http://hpmini.archive.canonical.com/mie/ hardy-hpmini main universe multiverse restricted
deb-src http://hpmini.archive.canonical.com/mie/ hardy-hpmini main universe multiverse restricted

```

I unboxed my MI about two hours ago. I like it.

---

### Post by Bailywolf on 2009-01-22
You saved my ***!

-B

---

### Post by jip88 on 2009-01-22
I just got my Mini 1000 Mi Wednesday, and as a Linux neophyte, do not plan on a lot of wholesale changes or customization.  I do have an issue however that I thought you might be able to help on.  I am trying to configure the system to enable use of a Verizon UM 150 cellular broadband modem.  HP was no help, but I found a solution on another Linux board that requires creating two configuration files in the /etc/ppp/peers directory.  Unfortunately, write permission in this directory (and others) is locked by HP to the root user.  So far, HP has not been forthcoming with a password.  Can I circumvent this by booting from an IBEX USB drive or is there another easy way around the permissions issue?

---

### Post by prickly on 2009-01-23
Sorry that this is way off topic but do any of you find that your fan inside your mini mie is running most of the time when you are using your mie?

The fan on mine is loud enough to be annoying - I think I will call HP which is disappointing as I just unboxed it earlier this evening ...

I am insterested in customizing the interface though - sounds like you are getting close to cracking it?

---

### Post by Bailywolf on 2009-01-23
I haven't had the chance to dig too deeply yet, but the look/feel stuff is called harbour-launcher and its config files are xml.  I really don't know if I'm qualified to fiddle with that too much... I hope somebody is though.

If you need to access the root functionality, go to 'Settings' and then to the customize settings app (I posted a pic to it above).  Here you can access the root terminal (or rather, enable it so it shows up on the advanced settings menu).  I ran into that file ownership thing myself (ANNOYING AS HELL) but found I could do what I needed to do from the root terminal. gedit will work like a charm for you here.

-B

---

### Post by jip88 on 2009-01-23
Thanks.  That worked, although I still haven't gotten the configuration quite right on the UM150.

---

### Post by Bailywolf on 2009-01-23
> **jip88 said:**
> Thanks.  That worked, although I still haven't gotten the configuration quite right on the UM150.

I don't know if this will help, but try adding the standard Hardy Heron repositories to you sources.list file so they'll show up when you use the Synaptic package Manager (accessed from the cli with 'sudo synaptic' or via the advanced settings section). 

There might be something there that'll help with your config.

-B

---

### Post by gtt on 2009-01-27
> **Jeff Johnston said:**
> What kind of battery life do you get? I'll have to run for a few hours straight to see exactly what I get but it doesn't feel like 3 hours...

Thanks for the tip on the key to flip between the running programs!

I agree with you about the dashboard. I don't care about any of the local programs as everything I do requires a browser. I am thinking it would be cool to get vpn working on here so I can get onto my work network though :).

-Jeff

I was able to get this to work using this process from a root terminal:

[INDENT]```
apt-get install network-manager-openvpn nscd
```[/INDENT]

Then I used the standard network-manager VPN setup stuff from the network icon at the bottom of the screen.  Warning:  The dialog box for setting up a VPN extends past the bottom of the screen, so figuring out the right number of tabs to press to get to the "Apply" button was a certain amount of guesswork.

---

### Post by ProfessorZen on 2009-02-01
I've been doing some theming but whenever I try to sudo nautilus I get a segmentation fault
.  Is anyone else having the same problem or know what's going on?  As just a quick fix, I installed konqueror and it loads as root without any problems.

---

### Post by ProfessorZen on 2009-02-02
To add an application to a tab you need to create a desktop configuration file and save it to /usr/share/applications.  I'll use the program Celtx as my example.

I prefer to do things graphically when I can so I type Alt-F2, kdesu konqueror, and my password when promoted.  From here on I can do everything graphically as a root user.

I just open any one of the current desktop files with gedit, replace their contents with mine, and SAVE AS celtx.desktop.  For celtx, the contents would be something similar to the below:

```
[Desktop Entry]
Type=Application
Name=Celtx
GenericName=Media Pre-production
Exec=/home/yourname/.celtx/celtx
Terminal=false
Icon=/home/yourname/.celtx/icons/mozicon128.png
Categories=Office;WordProcessor;
StartupNotify=false
```

To change just the icon of an application that loads itself into a tab you can always just swap out the icon which is almost always located in /usr/share/pixmaps.

To change theme icons go to /usr/share/icons/GlassyBleu and /usr/share/icons/Human. For emblems, after you've changed them you'll still need to update the icon cache with gtk-update-icon-cache [path].

As far as adding or modifying tabs go, here is where I pass the buck (for now).

---

### Post by ArKay on 2009-02-02
I hate to point at things elsewhere but...

There is a discussion that just started up here : 
[http://myhpmini.com/forum/viewtopic.php?f=10&t=455](http://myhpmini.com/forum/viewtopic.php?f=10&t=455)

about how to mess with the interface, virtual desktops, etc.

might be a place to get a better idea or at least fish for some pointers... being focused on just HP minis - it might be a resource as well.

---

### Post by mcintire319 on 2009-02-04
I haven't yet figured out how to add tabs myself, but by downloading/installing some programs online (not through the root terminal/synaptic), they added tabs themselves. For example, wine has its own tab. Limewire, while it doesn't have its own tab, pops up on my internet tab. Some of my synaptic programs also have icons on the HP's menu.

Additionally, I was able to get directx working on my machine (helped by winetricks).


But my questions is this: is there a way to alter the screen resolution on the HP MIE? It's currently set to 1024x600, and I need it to be 1024x768 to run a program.

---

### Post by doorknob60 on 2009-02-04
^ 1024x600 is probably the max res, meaning it's impossible (or wouldn't work if it let you try) to get it into 1024x768.

---

### Post by ProfessorZen on 2009-02-04
You can't run 1024x768 in hardware but you can do it in software as a virtual *display* which is not to be confused with a virtual desktop.  I've only done this on Windows Mobile so I can't tell you what application to use or even if one exists for Linux.

---

### Post by mcintire319 on 2009-02-04
I found some code earlier that let me switch to 1024x768 by reconfiguring the graphics card... or something. I wouldn't recommend it. Bad things happened.

As far as getting new tabs, I retract part of what I said earlier. I downloaded bit torrent in the package manager, and I can't find it now.

---

### Post by netsyd on 2009-02-05
Has anybody figured out how to disable the harbour-launcher completely so I can get a normal desktop?

---

### Post by ChrisBuchholz on 2009-02-11
> **netsyd said:**
> Has anybody figured out how to disable the harbour-launcher completely so I can get a normal desktop?


Yeah, I'm quite interested in that too, even though I would much rather like to just change things in the harbour-desktop thingy, like placing a rss reader or something instead of the mail column and so on.


**UPDATE**
You can kill the harbour-launcher by going to Settings > Advanced -> Sessions Preferences > Current Session. Then you find the harbour-launcher and change it's style to *normal* followed by <Alt>F2 and run *killall harbour-launcher*. I doubt it will stick for the next time you turn on your PC, but it's a start.

I still would love to hear anybody's thoughts about customizing the harbour thingy...

---

### Post by blackstripes on 2009-02-27
Bump, any news on this front?

---

### Post by mudboy on 2009-03-04
Mail/Music/Photos are all wasted space, and I long for an actual desktop.  it seems that the have hacked up gnome-panel a bit to not allow you to add items to it.  Very frustrating, as now everything is a couple of clicks away, rather than 1. 

If anyone else can get rid of Harbor, and get gnome-panel to its usual top/bottom orientation, let us know.  This sucks.

---

### Post by aspergerian on 2009-03-10
On my Mini 1000 Mi I'd very much like to have a Ubuntu desktop like that on my Asus 901. Will the above instructions enable me to have that desktop? Eg:

[http://www.pbase.com/image/110077671](http://www.pbase.com/image/110077671)

I won't have to use my Mini 1000 Mi for work since my Asus 901 with Hardy Heron is available. Might I get the desktop I want by eliminating HP's version of "Ubuntu" and by loading Hardy Heron, Ibex, or ??? (Of course, after creating an HP restore USB)

---

### Post by aspergerian on 2009-03-10
My anticipated strategy is to wipe the HP "Ubuntu" and its desktop and install Hardy Heron or Intrepid Ibex. Once that's done, I'll see how many functions don't work (if any). A friend just loaded Intrepid Ibex onto a larger HP with Windows (dual boot). He was amazed at how well Intrepid works in his HP. If these maneuvers fail for me, I'll restore the original OS and keep trying to bypass what HP provided
- - - -
On my Mini 1000 Mi I'd very much like to have a Ubuntu desktop like that on my Asus 901. eg [http://www.pbase.com/image/110077671](http://www.pbase.com/image/110077671)

---

### Post by blackstripes on 2009-03-10
> **aspergerian said:**
> My anticipated strategy is to wipe the HP "Ubuntu" and its desktop and install Hardy Heron or Intrepid Ibex. Once that's done, I'll see how many functions don't work (if any). A friend just loaded Intrepid Ibex onto a larger HP with Windows (dual boot). He was amazed at how well Intrepid works in his HP. If these maneuvers fail for me, I'll restore the original OS and keep trying to bypass what HP provided
- - - -
On my Mini 1000 Mi I'd very much like to have a Ubuntu desktop like that on my Asus 901. eg [http://www.pbase.com/image/110077671](http://www.pbase.com/image/110077671)

I bought Mi edition 1000 a few weeks ago and had hoped to find some info on the Mi environment.  After not finding much information about it I decided to install 8.10, which I might add works perfectly.  Everything worked out of the box with the exception of the mic.  I was able to get it working with the help of this forum and now all is well.  8.10 is MUCH better than the HP flavored version of ubuntu.  Good luck.

---

### Post by aspergerian on 2009-03-11
> **blackstripes said:**
> I bought Mi edition 1000 a few weeks ago and had hoped to find some info on the Mi environment.  After not finding much information about it I decided to install 8.10, which I might add works perfectly.  Everything worked out of the box with the exception of the mic.  I was able to get it working with the help of this forum and now all is well.  8.10 is MUCH better than the HP flavored version of ubuntu.  Good luck.

Installing 8.04 had a glitch that was "soon" solved. A USB loaded with 8.04 Hardy Heron wiped the HP "Ubuntu" and Hardy Heron was installed. At first, wifi didn't work, so I hooked up via ethernet, which worked fine. Then ~250 update-packages were downloaded and installed. Wifi still didn't work, so Admin > System > Network led to tweaking away from WPA and to a 64-bit Hex something or other. All of a sudden, the various wifi sources (passworded and open) were being found and reported by my Mini 1000 Mi now running Ubuntu Hardy Heron. Wireless connection followed appropriately. Mail has been sent and received. I loaded newest Flash Player and latest Adobe Reader and now have  the desktop and tools I need... Also, sound works via speaker and via combined jack. All in all, doing these tasks took appx 4 hours. Now I like and can use my HP Mini 1000 Mi.

---

### Post by kevindubrow on 2009-04-21
Is there any chance that someone can get an online guide going on how to customize the Mini 1000 Mie? Mine is in the mail and I can't wait to get everything working on it.

---

### Post by ProfessorZen on 2009-04-22
For an online guide on how to customize the MIE (just the MIE), check out the thread _Customizing the MIE_ in the Linux forum on myhpmini.com.  For the moment, the URL is: [http://myhpmini.com/forum/customizing-the-mie-t837.html]("http://myhpmini.com/forum/customizing-the-mie-t837.html").  The Linux forum also has many other interesting threads on various aspects of the device.

---

### Post by xsunxspotsx on 2009-06-04
Did you ever get to customize the panels?  Or even figure out how to add anything to panels? Tbh, I'd like to remove all the crap on the home screen, and make it remotely useable beyond just "Web Browser" aka Firefox. 

Probably going to install a different Ubuntu over this.  I can barely stand it.  I would really like to actually be able to do some homework/programming (same thing for me) on this thing.

---

