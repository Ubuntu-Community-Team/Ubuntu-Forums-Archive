---
title: "No icons or right click menu on xubuntu desktop"
date: 2006-06-30
forum: Desktop Environments
---

### Post by dafthamster on 2006-06-30
Hi,
I recently installed xubuntu desktop on my old desktop PC.  All was going well until I tried to install VLC media player yesterday.  After doing this the desktop functionality stopped working.
What I mean by this is that previously I could see icons on the desktop which represented files in my /home/desktop/ directory - now they are no longer visible.  Also, previously when I right clicked on the desktop the applications menu would pop up - now nothing happens.
I've tried the advice at [http://www.ubuntuforums.org/showthread.php?t=194680](http://www.ubuntuforums.org/showthread.php?t=194680) but it didn't help (and it would only have resolved the menu issue anyway.
Many thanks in advance ...

---

### Post by thingy on 2006-06-30
Hiya,

Sounds like the install of VLC broke your installation. It would be handy if you could attach a couple of files to your post to allow diagnosis.

~/.xsession-errors (<-- not sure of the spelling, it should be a .*error* file in your ~)

The apt-get/dpkg log file...can't remember what they are called but they should be in either /var/log in /var somewhere.

It could be the case that VLC installed/uninstalled something needed for XFCE to work.

regards

jin

---

### Post by dafthamster on 2006-06-30
Ok - files attached.

There does seem to be an error showing up in the .xsessions-errors one.

I've only included the most recent dpkg.log entries due to upload file size restrictions - I can post as a compressed file if you want the whole lot.  Unfortnately the entries are a bit of a muddle - did some uninstalling and reinstalling in an attempt to clear up the problem ...

Thanks

---

### Post by thingy on 2006-06-30
Hi

Thanks for the files...

The odd things are in the dpkg.log file.

For example, there are lines which say "half-installed":

2006-06-29 16:43:54 status half-installed xubuntu-desktop 1.32


That means, that there are packages which are being held back for whatever reason.

Need to find out what packages and what reasons:

umm i think you can look at this thread:

[http://ubuntuforums.org/showthread.php?t=189050&highlight=half-installed](http://ubuntuforums.org/showthread.php?t=189050&highlight=half-installed)

which says that doing a sudo apt-get -f install will install these half installed packages.

jin

---

### Post by dafthamster on 2006-06-30
Yeah ... I noticed the "half-installed app_name" and "half-configured app_name" entries too.

Looking at the whole dpkg.log file, they occur all the way back to when I first installed Ubuntu, and are always followed by an "installed app_name" line, so I'm not sure whether they are necessarily a problem ... ?

"apt-get -f install" fixes broken dependencies.  I used it when installing Opera yesterday and it worked very nicely.  You should be able to see that installation at the start of the file I uploaded.  However, if I run it now it doesn't bring up any problems.

---

### Post by thingy on 2006-06-30
Whats the output of this:

sudo apt-get -V dist-upgrade

---

### Post by dafthamster on 2006-06-30
[QUOTE=thingy]Whats the output of this:

sudo apt-get -V dist-upgrade[/QUOTE]

The standard "Reading package, Building dependency, Calculating upgrade ..."

Then "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded".

I like to keep things current  ;)

---

### Post by thingy on 2006-06-30
Ok. Well in that case I will have to assume your install is not broken and its XFCE which is not working correctly.

Can you launch a terminal in XFCE?

If so, then try typing in "xfdesktop4" to see if it brings back your desktop icons. If not then try running "startxfce4" to see if it starts up the modules or reports any problems when trying to start up XFCE's modules.

I think that a configuration setting is stopping XFCE working properly in which case, can you create a new user and try logging in as that user. Does this new user have the same problem? If they don't then you can fix your issue by removing the XFCe config files in you ~ and getting XFCE to re-create them when you launch it again.

Choose to save the session on logout.

---

### Post by dafthamster on 2006-06-30
The good news is that everything is working again.  However, I am a complete idiot (or, if you're feeling charitable, not familiar enough with Xfce).

There is a little setting under Applications -> Settings -> Desktop Settings where you tick to "Allow Xfce to manage the desktop".  Somehow this was turned off - don't ask me how - by some part of the installation procedure yesterday.  Turning it back on again bought back all the desktop functionality.

Huge apologies for wasting your time over this - and many thanks for your help.  On the bright side it has helped me poke around and learn a bit about the configuration in Xfce!

In case you're wondering how I got on with your last suggestions:-

[QUOTE=thingy]Can you launch a terminal in XFCE?[/QUOTE]

Yes

[QUOTE=thingy]try typing in "xfdesktop4"[/QUOTE]

"command not found"

[QUOTE=thingy]try running "startxfce4"[/QUOTE]

Reports that X server is already running, and that another session manager is already running (xscreensaver I think)

[QUOTE=thingy]create a new user and try logging in as that user. Does this new user have the same problem?[/QUOTE]

The new user doesn't have the same problem - the desktop works fine for them ...

[QUOTE=thingy]you can fix your issue by removing the XFCe config files in you ~ and getting XFCE to re-create them when you launch it again.[/QUOTE]

Ok - that didn't work either.

---

### Post by thingy on 2006-06-30
Ah well. At least the issue is resolved.

Best wishes

---

