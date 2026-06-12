---
title: "Rhythmbox wont do streaming and XMMS freezes"
date: 2005-04-29
forum: Desktop Environments
---

### Post by Campitor on 2005-04-29
I finnaly got sound working on Hoary.  But, now, I can't get Rhythmbox to play stream.  If I open a site with Rhythmbox, and choose realplayer format, it just gives me errors. IF I choose the windows asf format, it starts buffering, and after thirty minutes I still have no music.

I downloaded xmms, and beep-media-player, and they both freez as soon as I give them any type of file to play:  ogg, mp3, cd-rom, stream.  They just freezz, no error, nothing.  I have to kill the process everytime.  I am able to use totem a bit, but it is SOOOOOO memory intensive, that any click of the mouse makes the music skip.  I don't have problems playing mp3, ogg's and cd-s from rhythmbox, and since it doesn't use that much memory I'm fine (just have 128 RAM).

I have all the codecs (including w32codecs and gstreamer0.8) and rhythmbox 0.8.8.  Anybody have any suggestions?

camp
Do

---

### Post by sancho on 2005-04-29
hey.  its hard to troubleshoot without errors. 

try launching the players from terminal without an "&" if you haven't already.   Lots of times if you do this they will spit out debuging info to the terminal.  If not there are more advanced ways to run most programs verbosely,thats just a good start.  

also try "sudo tail /var/log/messages"  to see if any errors are logged there.  

If you find any errors post away. 

Also a few other things you can try is to install streamtuner  or  vlc.   Both of which handle shoutcasts streams fairly well.

---

### Post by Campitor on 2005-04-29
[QUOTE=sancho]hey.  its hard to troubleshoot without errors. 

try launching the players from terminal without an "&" if you haven't already.   Lots of times if you do this they will spit out debuging info to the terminal.  If not there are more advanced ways to run most programs verbosely,thats just a good start.  

also try "sudo tail /var/log/messages"  to see if any errors are logged there.  

If you find any errors post away. 

Also a few other things you can try is to install streamtuner  or  vlc.   Both of which handle shoutcasts streams fairly well.[/QUOTE]
 Ok:  With rhythmbox buffering...it's still buffering...no errors.

with beep-media player, I just got this error when it crashed...it doesn't freez anymore...jsut crashes:
@Campitor:~ $ beep-media-player

Received SIGSEGV

This could be a bug in BMP. If you don't know why this happened, send a mail to us at [email]beepmp-devel@lists.sourceforge.net[/email]

Aborted
...

When I checked my log...the only relevant thing was:
Apr 29 16:50:30 localhost kernel:   The failed "Read CD" packet command was:
Apr 29 16:50:30 localhost kernel:   "be 00 00 00 3b 6a 00 00 01 f8 00 00 00 00 00 00 "
Apr 29 17:20:03 localhost -- MARK --
Apr 29 17:40:09 localhost -- MARK --
But, I wasn't trying to access my CD, I just wanted some streaming.  I uninstalled xmms, about an hour ago.  I checked for vlc on synaptic and there are a bunch of packages...which one should I install?

thanks sancho

---

### Post by derrick1985 on 2005-04-29
I have the same problem. I'm using Totem to stream my music.

IF you got totem, this will make it easy. Get Steamtuner (use ubuntuguide.org) and goto edit Preferences

Default opens XMMS, XMMS freezes, XMMS=Not good for current situation.

Replace lines with xmms to totem, and enjoy streaming music through steamtuner!

---

### Post by doclivingston on 2005-04-29
GStreamer (which is what Rhythmbox uses) doesn support Real Audio, and WMA support is a bit flaky; personally, I've never gotten either  to work.

One thing that might help is Pitfdll ([http://ronald.bitfreak.net/pitfdll.php)](http://ronald.bitfreak.net/pitfdll.php)), which lets GStreamer use codecs from .dlls (i.e. w32codecs). I've haven't had a chance to test it yet (it's building as I type this), but it'll be great if it works.

---

### Post by gobeavs on 2005-04-30
Before playing sounds in XMMS, try typing "killall polypaudio" in the terminal. Thats what works for me...if I don't do that I can't play XMMS or use Cedega.

---

### Post by Campitor on 2005-04-30
Ok...I got it working on rhythmbox.  I installed streamtuner and changed the application preference to:  rhythmbox %q

and now I can hear all the stations provided by streamtuner.  I still haven't figure out how to include the radio stations that I want to hear into streamtuner, but I did find a lot of very promissing substitutes in SHOUT.  

I uninstalled XMMS...just couldn't get it to work...and started hating it really quickly.  Kept beep-mp, because it works with somethings, but I can't get it to play mp3's, or my CD; it just crashers giving a SIGSEV error.  Don't know why...keeps giving me errors.  I want to give VLC a try, but I really don't know how many packages I have to install.  Synaptic gives me like 10 different packages with the VLC search string...and some say that they are deprecated.  Does someone know which packages are the best onew to install, to get the thing working properly?

Thanks for all your help

---

### Post by derrick1985 on 2005-05-01
[QUOTE=Campitor]Ok...I got it working on rhythmbox.  I installed streamtuner and changed the application preference to:  rhythmbox %q

and now I can hear all the stations provided by streamtuner.  I still haven't figure out how to include the radio stations that I want to hear into streamtuner, but I did find a lot of very promissing substitutes in SHOUT.  

I uninstalled XMMS...just couldn't get it to work...and started hating it really quickly.  Kept beep-mp, because it works with somethings, but I can't get it to play mp3's, or my CD; it just crashers giving a SIGSEV error.  Don't know why...keeps giving me errors.  I want to give VLC a try, but I really don't know how many packages I have to install.  Synaptic gives me like 10 different packages with the VLC search string...and some say that they are deprecated.  Does someone know which packages are the best onew to install, to get the thing working properly?

Thanks for all your help[/QUOTE]


Personally, I just got the VLC-GTK and the VLC-GNOME packages (frontend for VLC) and it did the rest.

The version I think is up to the latest, 0.8.1

---

### Post by hanzj on 2005-05-22
[QUOTE=derrick1985]Personally, I just got the VLC-GTK and the VLC-GNOME packages 


Currently, the above mentioned vlc packages are not current. It is now wxvlc. \\:D/

---

### Post by hanzj on 2005-05-22
[QUOTE=derrick1985]Personally, I just got the VLC-GTK and the VLC-GNOME packages. [/QUOTE]

As of May 22, 2005,  the above mentioned vlc packages are not current. It is now wxvlc. \\:D/

---

### Post by dmccarney on 2005-05-22
I had the same problem with Beep Media Player and XMMS in regards to crashing when trying to play mp3s etc. My rythmbox was able to play all of my files but XMMS and Beep could not. However, I was able to fix beep and this is how I did it:

Open beep
Right click its interface
Goto Preferences
Click the plugins button on the right pane
Click the output tab on the top right of the plugins pane
Change the current output plugin to eSound Output Plugin

That worked for me but it might just be because of my hardware setup. I have an ASUS motherboard with onboard sound functionality.

Hope that helped :)

---

