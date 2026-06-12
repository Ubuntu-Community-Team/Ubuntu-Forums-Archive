---
title: "Electric Sheep Edgy"
date: 2006-10-23
forum: Desktop Environments
---

### Post by shoki on 2006-10-23
Looks like the latest version of Electric Sheep is available now. Anyway to get it to run after installation? I followed the How-To about disabling gnome screen saver and using xscreensaver but was wondering if there was a cleaner way to do this now that the latest version is available in the repositories.

Thank you,
--Shoki

---

### Post by doherty on 2006-11-13
Not the cleanest way, but cleaner than replacing gnome-screensaver with xscreensaver (at least in my opinion):

Open terminal

$ sudo cp /usr/share/gnome-screensaver/themes/electricsheep.desktop /usr/share/applications/screensavers/electricsheep.desktop 

$ sudo ln -s /usr/bin/electricsheep /usr/lib/xscreensaver/electricsheep

$ sudo ln -s /usr/bin/electricsheep-voter /usr/lib/xscreensaver/electricsheep-voter

$ sudo nano /usr/share/applications/screensavers/electricsheep.desktop

Change the line:

Exec=electricsheep --root 1

to

Exec=electricsheep --root 1 --zoom 1

That should do it.  It worked for me, but I only have my one system to test it on.  I'm not entirely sure how to get the voter to work, though.

---

### Post by shoki on 2006-11-15
Thanks I'll give it a try!

---

### Post by LexAevum on 2006-11-22
Hey, doherty
I used your method to get ES running, and now it runs, but it just keeps looping the first 10 seconds or so.
When I try to run it from a terminal I get:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  126
  Current serial number in output stream:  126
Terminated

Does that mean anything to you? Because it means nothing to me, lol. I'm a total newbuntu.
/But I'm lovin it

OMG DDD,
Ok, when I run it in a terminal with:
$ electricsheep --root 1

My cursor goes to the next line and the terminal hangs.

---

### Post by sciurus on 2006-11-23
The X errors are caused by the composite extension. Run electricsheep with the --mplayer 1 flag or disable composite.

FOr me, this gets it working at a terminal. You can use --zoom 1 when launching from a terminal to go full screen. I have not been able to use gnome-screensaver; the screen is always black. I've tried "--root 1 --zoom 1 --mplayer 1", "--root 1 --mplayer 1", "--zoom 1 --mplayer 1", and just "--mplayer 1" in the desktop file to no avail.

[http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg74028.html](http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg74028.html)

Doherty, any reason to copy the .desktop file instead of linking it?

---

### Post by LexAevum on 2006-11-24
When I run from a terminal with --mplayer 1 I just get:

Terminated
$

Hmm hmm. I really like this screensaver too.
I've got xscreensaver loading it, but it just runs the first ten seconds or so and then loops. After a few of those it goes "no signal".

---

### Post by LexAevum on 2006-11-24
Wait.. HAH! I got the bugger. My error was that I somehow still had the gnome screensaver trying to run at the same time and they were pissing each other off.

Now I just have a problem where xscreensaver daemon doesn't start when I boot and I have to xscreensaver-demo in a term to get it to start up. I'm sure this will be easy... just like everything else. *Cry*
I WILL learn to use and love ubuntu... I refuse to go back to windows!

---

### Post by waveslider on 2006-12-03
Does anyone know where the "sheep" are stored? I want to download some from the server.  

Thanks!

---

### Post by muguwmp67 on 2006-12-16
You can manually download sheep from the server at:

[http://sheepserver.net/v2d6/cgi/status.cgi]("http://sheepserver.net/v2d6/cgi/status.cgi")

The mpegs should be saved into your home/.sheep directory.

You can use bittorrent to download them significantly faster, as the server is apparently always backed up.  

Current torrents are here:  [http://sheepserver.net/v2d6/cgi/status.cgi?&detail=stats]("http://sheepserver.net/v2d6/cgi/status.cgi?&detail=stats")

An RSS feed for torrents is here: [http://sheepserver.net/v2d6/gen/rss.xml]("http://sheepserver.net/v2d6/gen/rss.xml")

This screensaver is absolutely amazing.

I'm new to ubuntu and linux, so messing around with this screensaver has been a great learning experience.  After getting the basics working, I managed to do the following:

- run electric sheep on the [desktop in the background]("http://www.ubuntuforums.org/showthread.php?t=162897&highlight=root+screensaver+HOWTO") (i.e on the root window)  Yeah, a waste of resources, but its pretty cool.

- Set up an RSS reader in Azureus to download all the current sheep.
  **Still need help here,** the torrents all come down in individual folders, and even if tell it to save in your ~/.sheep directory, they won't show up because it appears that electricsheep doesn't scan recursively.  So at this point  they must be moved manually.  Any ideas for automating this process would be appreciated.  All in all though, this isn't really that important because once you get a few sheep down manually, you are good to go.
<edit>
I have gotten this to work.  I'm not sure what I did differently, but it does scan recursively.  However, I recommend only using this for seeding your first sheep.  Once you hit your cache limit, the prog will start deleting the sheep, which will then be missing from the torrent, which will then start leeching again.  It is probably better to grab them and dump them into the directory manually.  Then you can continue seeding until you decide to reclaim the disk space.
<end edit>

- Trying to get the voting thing working:
No luck yet.  I did manage to download the source for the hacked xscreensaver prog (the one that passes keystrokes)  After a bunch of failed attempts, I finally got all the -dev libraries I needed to compile it.  (great sense of accomplishment)  I replaced the gnome-screensaver with the new xscreensaver following a guide here, but it didn't work (mild disappointment)  Even though the screensaver-demo window shows the pass keystrokes checkbox, electric sheep doesn't seem to be recieving it.  **So if anyone else has gotten this to work on ubuntu, please let me know!**

---

