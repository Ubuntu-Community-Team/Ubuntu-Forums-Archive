---
title: "New problem with rhythmbox and amarok (but xmms is fine)"
date: 2006-03-17
forum: Desktop Environments
---

### Post by Dullin on 2006-03-17
It's seems that something went wrong with those 2 applications.

First of all, I am a great fan of amarok and usually use it as my main music player. Unfortunatly, since a couple of days (wich coincided with the gnome 2.14 update and my installing of xgl/compiz) I cannot play music in amarok.

The program starts fine, the database is fine but when I click on a song it just passes to the next without giving me any error message. Even if I start it from console, the program lauches another and closes the terminal session so I can't see what kind of error it gives me.

I then decided to use rhythmbox for a while thinking that amarok might fix itself in a couple of days (dev release after all). But this program also has it's share of problem, it crashes at random moments.

I now need to fall back on xmms wich works without flaw (well, it doesn't handle flac but that's another problem).

Anybody faced those problem here and can give me a little insight on what is going wrong on my system?

---

### Post by nrwilk on 2006-05-23
I have the exact same problem.

Each song goes straight through to the next song.  After they finish the OSD gives the message "Playlist Finished."

Kaffeine plays music with no problem.

I am running the latest Dapper, and also Xgl/Compiz.

---

### Post by MBro on 2006-05-23
What engine are you using in amaroK?  If it's gstreamer try switching to xine, if xine works that means you're gstreamer install is messed up because that's what both rhythmbox and amaroK were using.

---

### Post by nrwilk on 2006-05-23
[QUOTE=MBro]What engine are you using in amaroK?  If it's gstreamer try switching to xine, if xine works that means you're gstreamer install is messed up because that's what both rhythmbox and amaroK were using.[/QUOTE]

I'm using xine.

---

### Post by MBro on 2006-05-23
hmmm, then I don't know what to tell  you.

---

### Post by voidmain on 2006-05-24
I have the same issue and I don't even have a choice of chaning the engine for Amarok from Xine to GStreamer. Additionally, my Rhythmbox works fine, but doesn't play AAC files. I can't find the gstreamer 0.10 plugin for them although I haven't tried install 0.08 which did have a plugin for it.

I'm wondering what is happening with Xine. I also install gxine to test if it was an Amarok problem and it isn't. gxine also has the same behavior so it must be a Xine issue. Perhaps an incapability with gstream 0.10 or something of that nature?

Anyone having luck fixing this?

---

### Post by nalthien on 2006-05-24
Installing gstreamer 0.8 won't have any effect as the version of rhythmbox we have is not linked against the 0.8 libraries; it's linked against the 0.10 libraries 

As to the problem; I'm not sure what could be causing it as I don't use Xine.

---

### Post by Bartekc7 on 2006-05-24
sudo apt-get install libxine-extracodecs

---

### Post by feffe5274 on 2006-05-30
Same problem: under amarok engines section I have only XINE.
And xine doesn't work

Only XMMS is working.

I've tried "sudo apt-get install libxine-extracodecs" but this is the answer:

federico@Ath2500:~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another pack                                                                                                   age.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

What does it mean ? Pheraps a wrong repository ? Very strange...

Any idea ?

---

### Post by groggyboy on 2006-05-30
what versions of rhythmbox and amarok are you using?

I was having problems with rhythmbox until I updated.  rhythmbox is up to 0.9.4.1 (as opposed to 0.9.3 in the repos).  Check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=173543").

Make sure you have the latest version of amaroK as well (1.4).  Also, they have removed support for gstreamer in v1.4 because they claim it is inferior to xine.

feffe5274 - do you have the Penguin Liberation Front repos in your sources list?> ## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

---

### Post by Tachyon60 on 2006-06-19
I was having the same problem with amarok, and following the instructions on amarok's website:[http://amarok.kde.org/amarokwiki/index.php/MP3_on_Kubuntu_6.06](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Kubuntu_6.06) along with making sure I had installed "amarok-enignes" with apt-get fixed my problem. Hope this helps!

---

### Post by scuba_steve on 2006-09-04
The amarok/rhythmbox/etc. problem is actually a problem with xine.  If you run these applications as root (eg. sudo amarok from terminal) there will be no problems.

Now I'm pretty new to linux, so I have no idea how i could configure xine to be accessed by other users, but this would likely fix the problem so any help here?

---

### Post by scuba_steve on 2006-09-05
ok, so i fixed my amarok problem, turns out its just a line in the amarok config file, deleting the file fixes it.  You will have to redo the original amaroK setup.  It is possible simply to remove the problem lines from the file if you want to do some more research about this file.

anyway, 
sudo rm ~/.kde/share/config/amarokrc
in a terminal should fix it

see the string 'amarok-xine issues loading MP3 files' for a better discussion of the problem

---

