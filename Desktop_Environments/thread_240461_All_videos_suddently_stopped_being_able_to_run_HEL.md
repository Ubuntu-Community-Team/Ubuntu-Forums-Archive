---
title: "All videos suddently stopped being able to run HELP!"
date: 2006-08-20
forum: Desktop Environments
---

### Post by slugkilla on 2006-08-20
I had had all of my video problems resolved and had been able to run most file types, including WMV, but earlyer it all stopped working. I think the problem started after I uninstalled VLC because I did not need it anymore. I have tried to reinstall the codecs with automatix, but this has not worked :(
Can someone give me some advice to get everthing working again? By the way, AVI and WMV have stoped working and before they worked fine in XINE. Thank you!

EDIT: well I can play video in mplayer and VLC, but XINE still does not work! It is my favorit.

---

### Post by LKRaider on 2006-08-20
On a fresh install of Xubuntu (uses xine by default), all I needed to install was w32codecs and libxine-extracodecs to play avi's and wmv's.

---

### Post by slugkilla on 2006-08-20
Ok the extracodecs did not help. Thanks though. I don't know why xine would stop on me. I don't really want to switch to mplayer, but I will have to, I guess.

---

### Post by nalmeth on 2006-08-20
Make sure everything you need in [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) is installed. Also, try reinstalling some gstreamer plugins, perhaps it will do the trick. It's happened to me before. I know, not really definitive, but there you go.

apt-cache search gstreamer

---

### Post by slugkilla on 2006-08-20
None of this seems to be working, but thanks for trying. At least I still have 2 working movie players. Maybe Mplayer will work just as well as XINE use to.

---

### Post by myke on 2007-10-23
I have the exact same problem.  It has nothing to do with the codecs.  I've been using them all fine with Feisty and suddenly no video will work with Gutsy ... unless I log out and then log back in as root into Gnome then they all work fine.  Now explain that???   Makes no sense and I sure as hell can not figure out what the problem is with my normal user idea suddenly causing all videos to not work no matter what program I use.  Trust me, it's not the program.  I've tried kaffeine, totem, mplayer, etc. etc.  None work ... unless I log in as root.

---

### Post by LKRaider on 2007-10-23
Check if your user is in the 'video' group:

```
$ groups
lkraider adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin lastfm
```

Also, try creating a new user and check if it can play videos.

---

### Post by myke on 2007-10-24
That could be the problem ...  I checked the user groups and here's the only ones that appear:

 root adm dialout fax cdrom floppy tape audio dip plugdev scanner admin fuse

I do not know why the video group is totally missing.    I added a group  for video in the group settings but it doesn't seem to have helped.  I'll try restarting but if that doesn't work, is their something I'm supposed to do to get a 'video' group added in the user/group settings besides just adding the group there and then adding my user to it?

---

### Post by myke on 2007-10-24
OK ... I moved over to logging in via root and checked the groups the way you suggested from there.  This was the output:

root adm dialout fax cdrom floppy audio dip video plugdev scanner admin fuse myke


So that obviously must be the problem that my regular user is not part of that group.  And creating an extra user name didn't work either.  It's only letting the root now be assigned to the video group.  How do I fix this?  the group "video" doesn't even show up when I pull up the groups from the 'users & groups' control panel even with root login.  Can I add my primary user 'myke' to this group 'video' by a terminal command?

IF so, can someone please tell me how.  It's late here on the east coast of the US so I gotta head to bed. I hope in the morning I'll have some good news about how to fix this.  At least I seem to know why it's not working.  A group issue.  Now if I can just get 'myke' into the 'video' group I should be fine.   Everything else is working.  At least the upgrade didn't kick me out of the audio group too.

I appreciate any of the help.

---

### Post by lsutiger on 2007-10-24
try:
sudo usermod -Gvideo *username*
where username is your username

---

### Post by myke on 2007-10-24
Well, I got myself added to the user group 'video' and I still can't open any video whether I'm using a kde program like kaffeine or a gtk based one like totem.  Totem opens but freezes.  Kaffeine won't even open and I then have to go to the system monitor to terminate both from taking up system resources.  I even tried doing a system restart but no go.   Yet ... I tried the root login again and sure enough ... good old root can get to anything.   Funny thing is, I never had this problem under Feisty.  And I didn't immediately have it after upgrading to Gutsy.  AFter my first restart the next morning all of a sudden, no video clips of any type will work unless i log in as root.

Any more ideas about what this might cause.  I even did a clean install and no go.  Could this be a GTK problem.   Would it help to try it thru KDE or is it likely a underlying system issue not a desktop environment one.

ANY help would be greatly appreciated.  If I can't get this fixed, I will have no choice but to either a) use winxp (shudder) or find another distro that won't break every time I upgrade.  And take in mind, I'm a fairly long time user of ubuntu so I don't say this lightly.   I've been using since breezy and every single upgrade has been a nightmare for several weeks after doing so.

I'll hang on out of loyalty if I can just get this fixed.  If root login can open the videos surely it must be some setting some where that I'm missing that has gotten out of kilter since the upgrade as it's obviously not a software problem as the codecs are working fine ... just under root login.  And I did install them under my own username so I know that's not the problem either.

HELP HELP HELP!

---

### Post by myke on 2007-10-24
Thanks for the response.  I tried that but to no avail.  I did pull up the 'group' file from the 'etc' folder and discovered my user id was on none of the groups.   I added myself to all necessary groups and logged out, restarted my system.  Still nothing.   And I discovered all of my music files won't open either in my id.  Only in root.  Same as the videos, doesn't matter what program, it just freezes and has to be forced to shut off.

I'm to the point of wanting to do another clean install.  This really really is highly frustrating.  I've never had good upgrading experiences back to Breezy but this has been the worst one.

---

### Post by lsutiger on 2007-10-24
When you do a clean install, did you immediately copy over your home folder, or do you have your home folder on a different partition?

What I am getting at is that if you are dumping your home folder onto the drive right after installing, you may have some settings that may not be compatible with the 'upgrade', but that is just a hunch.

Here do this:
Do a clean install, and I mean clean...bo upgrade, no old home folder.

Then copy and paste this in terminal:

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg gstreamer0.8-lame gstreamer0.8-faac gstreamer0.8-faad libdvdread3  libk3b2-mp3

Then try to play a video or sound file

If you could,. please answer the questions about the home folder.
Thanx

---

