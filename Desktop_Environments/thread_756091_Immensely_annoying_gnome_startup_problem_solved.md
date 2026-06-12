---
title: "Immensely annoying gnome startup problem solved"
date: 2008-04-15
forum: Desktop Environments
---

### Post by ceratophyllum on 2008-04-15
About 4 weeks ago, I decided to upgrade my old laptop to hardy from gutsy. Gutsy had always had sleep problems and 3D stuff was flakey on my macbook 2nd gen, so I figured I'd give Hardy a shot.

I replaced every instance of gutsy with hardy in /etc/apt/sources.list( :%s/gutsy/hardy/ in vi)  and did 

sudo apt-get dist-upgrade

Well, I rebooted, gdm started as usual and logged into gnome. The desktop appeared, but the panel buttons would not work.  So I crtl-alt-backspaced and started kde, which didn't work either, but just hung on a black screen.

I decided to rm -rf .gn* and .kde* in my home directory. Still couldn't log into kde or gnome.

I was able to log into a failsafe terminal and tried starting gnome/kde apps from the command line. Running eog, evince, plasma, etc. just resulted in a blank window or nothing at all. No error to stdout to stderr, nothing in system logs, xorg logs.

I gave up for a while, but kept apt-getting every week to make sure my system was at the bleeding edge and hoped that some change would clobber whatever was broken.
Still the same for 4 weeks.

I have some free time today, so I finally decided to start hunting around the forums and discovered the following:

 gconftool-2 --set --type=bool /desktop/gnome/sound/enable_esd false

After running this command, everything works again, except that there is, unsurprisingly, no sound.  I wonder how something wrong with esd can BREAK ALMOST EVERY GNOME APP W/O ANY ERROR MESSAGES.

Also, I wonder how the first person to post this solution figured it out. :?

---

