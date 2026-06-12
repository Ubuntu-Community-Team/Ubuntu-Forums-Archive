---
title: "A bit lost and lonely in GNOME-land"
date: 2005-04-20
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-20
KDE's eyecandy was frying my brain and burning out my retinas.  KDE 3.4 is quite a desktop environment, which I lovingly updated regularly.  amaroK was incredible.  Lots of apps dock themselves into the system tray.  Nice.  But it was just too much.

I installed Ubuntu 5.04, just to try it out.  GRUB recgonized my PClinuxOS KDE installation, but it failed upon reboot (Error 21.)  Leaving me unable to get into my system.  I had everything backed up anyway, so I just reinstalled Ubuntu, wiped the drive clean, and used LILO to boot.  Worked fine.  

So, I'm fresh off the boat, and WHOA!!  Everything's . . . brown, earthy, soft.  Alright, nice touch.  It all seems alot simpler around here in GNOME land.  Glaring eyecandy is replaced by smooth visuals that stay out of the way.  System/preferences configuration is easy.  No digging needed.  Menus are logical, organized, brief.

But, I'm still a bit lost and apprehensive about this whole thing.  No more amaroK.  No more Kaffeine or kPlayer,  Still, everything seems to a be a bit tighter and more well-integrated than KDE.

I hope some of my new friends around here will be kind enough to clear up a few things for me . . . . . . please forgive my GNOME-n00bness.  I'm a wizard when it comes to KDE, but in this new land I'm just a greenhorn.

1.)  I miss my kPPP.  I'm using "network settings" to connect to the net right now.  Can this be docked in the system tray?  Seems to forget my connection details when I close it.

2.)  I have dialup.  Not sure why, but my connection seems slower on Ubuntu.  The Repositories are SLOW . . . I mean, I should be getting at least 4000 bytes/second (like with PClinuxOS), but I'm gettting anywhere from 200 to 900.  Takes forever, and then some indexes fail to load fully, at 99%, lol.  Is this due to heavy traffic?  Also, since I'm using Synaptic, which repositories should I enable for the "Latest and Greatest" stuff for GNOME 2.10?  I need to upgrade OpenOffice and a few other things.  Any way to install KDE apps from the repositories?

3.)  Is Evolution dockable in the system tray?  Is that even a system tray that I have?  Nice thing about Kontact was that I could dock it, and have it check my mail automatically, every 5 minutes.  I have Evolution doing that, too.  But I can't seem to dock it.    

4.)  CD burning?  Wheres the CD burner application?  I had k3b in KDE.  What's out there for GNOME?  I hope it's something I can upgrade via Synaptic as well.

5.)  Where can I download applications for GNOME?  I had kde-apps.org for KDE.  Anything similar for GNOME?

6.)  Not much multimedia yet.  Totem can't play .wmv or .mpeg files.  No decoders.  Why aren't decoders pre-installed?  I suppose I canm just download them via Synaptic?

Well, my friends, I'm now wandering through GNOME-land, which reminds me of a nice, warm cup of coffee.  It needs a bit more sugar, though.  Any help?

Thanks.

---

### Post by Stormy Eyes on 2005-04-20
[QUOTE=GTKpower]1.)  I miss my kPPP.  I'm using "network settings" to connect to the net right now.  Can this be docked in the system tray?  Seems to forget my connection details when I close it.[/quote]

To my knowledge, the "network settings" app can't be docked. Speaking as somebody who used Linux on dialup for five years (I even installed Gentoo from *stage 1* on dialup), have you considered using wvdial? It's a commandline app, but it does a great job of handling dialup connections once you've set up the config file, and it does a good job of autodetecting modems, leaving you to hack the config file for a phone number, userid, and password.

[QUOTE=GTKpower]2.)  I have dialup.  Not sure why, but my connection seems slower on Ubuntu.  The Repositories are SLOW . . . I mean, I should be getting at least 4000 bytes/second (like with PClinuxOS), but I'm gettting anywhere from 200 to 900.  Takes forever, and then some indexes fail to load fully, at 99%, lol.  Is this due to heavy traffic?[/quote]

Probably. Do you have anything else using the connection while doing updates? I don't notice any problems, but I've got a good cable connection

[QUOTE=GTKpower]Also, since I'm using Synaptic, which repositories should I enable for the "Latest and Greatest" stuff for GNOME 2.10?  I need to upgrade OpenOffice and a few other things.  Any way to install KDE apps from the repositories?[/quote]

Since you installed Hoary, you've already got the up-to-date repositories. You *could* use Breezy, but that's experimental stuff for the next official release. I use it myself, but I'm crazy. :) You should be able to upgrade OpenOffice and install KDE from Synaptic.

[QUOTE=GTKpower]3.)  Is Evolution dockable in the system tray?  Is that even a system tray that I have?  Nice thing about Kontact was that I could dock it, and have it check my mail automatically, every 5 minutes.  I have Evolution doing that, too.  But I can't seem to dock it.[/quote]

It's not dockable. You probably don't have a system tray on your panel by default, but if you want one, just right-click on the panel, choose "Add to Panel", and then select "Notification Area".

[QUOTE=GTKpower]4.)  CD burning?  Wheres the CD burner application?  I had k3b in KDE.  What's out there for GNOME?  I hope it's something I can upgrade via Synaptic as well.[/quote]

Install **gnomebaker**. It becomes part of Nautilus for creamy drag 'n drop goodness.

[QUOTE=GTKpower]5.)  Where can I download applications for GNOME?  I had kde-apps.org for KDE.  Anything similar for GNOME?[/quote]

[http://www.gnomefiles.org](http://www.gnomefiles.org)

[QUOTE=GTKpower]6.)  Not much multimedia yet.  Totem can't play .wmv or .mpeg files.  No decoders.  Why aren't decoders pre-installed?  I suppose I canm just download them via Synaptic?[/quote]

Most of the decoders are proprietary (as in, not free software), so Ubuntu doesn't include them by default. Frankly, Totem is crappy enough to make Windows Media Player look good. I recommend that you install vlc (VideoLan Client) instead; you can do it through Synaptic. You'll have to fiddle with "Open With" in Nautilus if you want to doubleclick a media file in Nautilus and have it play in vlc. Also, read the [Restricted Formats](http://www.ubuntulinux.org/wiki/RestrictedFormats) page.

---

### Post by dabang on 2005-04-20
I just switched from KDE to Gnome myself. Used Gnome somtime ago and thought, I'll give it another shot - and I like it.
So. I'm not a Gnome-expert, but maybe I can help a bit.

> 3.) Is Evolution dockable in the system tray? Is that even a system tray that I have? Nice thing about Kontact was that I could dock it, and have it check my mail automatically, every 5 minutes. I have Evolution doing that, too. But I can't seem to dock it.
To my knowledge, Evolution is not dockable, but you can add an applet to the Gnomepanel. Go to synaptic, search for ["gnubiff"](http://gnubiff.sourceforge.net/) (you have to enable the "universe"-repository) and install it. After right-clicking on the panel, you can add gnubiff as an applet, which will tell if you got mail.

> 4.) CD burning? Wheres the CD burner application? I had k3b in KDE. What's out there for GNOME? I hope it's something I can upgrade via Synaptic as well.
Gnomebaker seems quite good, another one would be Graveman.
```
sudo apt-get install gnomebaker graveman
```
Until now, I didn't use any of them, so I can't tell how good they work. But to tell from the looking, they seem very nice.

> 6.) Not much multimedia yet. Totem can't play .wmv or .mpeg files. No decoders. Why aren't decoders pre-installed? I suppose I canm just download them via Synaptic?
Go to the [mplayer hompage](http://www1.mplayerhq.hu/homepage/design7/codecs.html) get the "all-codecs"-pack and unpack them to /usr/lib/win32. Then open synaptic an install "totem-xine" (will remove "totem-gstreamer" if installed) and you should be set! 
(You may have to look at the unpacked codecs: I think, there are three, wich are not readable by all. You should change that...)

---

### Post by rajaiskandarshah on 2005-04-30
go to mplayer homepage get the "essential-codecs" pack and unpack to /usr/lib/win32. then open synaptic and install "kaffeine" .........

---

### Post by calvinpriest on 2005-05-01
Your modem slowness issue sounds similar to a problem I have seen with external serial modems.  On a recommendation from someone else in the forum, I installed wvdial instead, and download speed has been great ever since.

---

