---
title: "Ubuntu system cleaning - like in Windows?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by jan on 2006-07-12
Hi,

my desktop seems to be a kind of cluttered and bloated after using it for a while doing some installs (Symaptic or Add/Remove... though) of stuff that did or dit not work that much. I've had Thunderbird and X-chat start with each session, though i removed them from "Startup programs" and they still launch... I don't want to do a clean re-install like with Windows (oh com' on, this was the "Windows way" :twisted: ) - but yet I do not see other way how to kind of clean the system.

Any suggestions? Deinstalling and re-installing programs??? I have no clue... :( :( :(

---

### Post by Dr. Nick on 2006-07-12
[http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

To get the stuff rom starting on default go to System - Prefrences - Session
and click the checkbox by "automatically save session" so its enabled, then close everything before shutting down.

---

### Post by cptnapalm on 2006-07-12
One thing which I have taken to doing, when things in gnome start going goofy, is to just wipe out the .g* in my home folder.  This sets everything back to default mode and thus I can start mucking around with things until I break something again :)

---

### Post by jan on 2006-07-19
> **cptnapalm said:**
> One thing which I have taken to doing, when things in gnome start going goofy, is to just wipe out the .g* in my home folder.  This sets everything back to default mode and thus I can start mucking around with things until I break something again :)
Well ive tried that lets see what comes out ;)))

---

### Post by snellgrove on 2006-07-26
Sorry to drag up an olde thread.

But while searching for cleaning things, in Ubuntu I found this wonderful guide.[Click Here](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+ubuntu)

Also, just to serve as a warning here for other people, with the below:

> is to just wipe out the .g* in my home folder.

be careful, as your not going to just wipe out .g*nome* your going to wipe out settings, and possibly data files for *any* program that begins with a G!!!!

so be careful, it might be safer to do your rm -R .gno* or if you have something called .gnom  type in something even more specific..  rm -R .gnome* 

overall a good tip, and a great way of 'fixing' gnome when things get a bit funny. 

hope this helps someone......

:edit:

just an example, typing in rm -R .g* would erase all of my:

.gaim
.gconf
.gconfd
.gimp-2.2
.gstreamer
.gtk-gnutella

as well as, all of the gnome stuff...

---

### Post by carontis on 2006-07-26
Well I usually use Gnome APT Software Manager, check for what I need to erase and proceed. It can be that some empty folder stays on the pc, but you can remove it later. Hope it helps

---

### Post by jan on 2006-07-28
> Gnome APT Software Manager
What the hell is that??? Did you mean Synaptic...

I did wipe out the .g* stuff... hmm, not very impressive - you loose all your toolbar icons and Epiphany bookmarks... grrr

---

### Post by LORD_PoLvO on 2006-07-28
GNOME APT is the apt command in terminal like so 


apt-get install (program)

or

apt-get remove (program)

apt-get update 

apt-cache search (program)

etc etc

---

### Post by jan on 2006-07-31
> **LORD_PoLvO said:**
> GNOME APT is the apt command in terminal like so 


apt-get install (program)

or

apt-get remove (program)

apt-get update 

apt-cache search (program)

etc etc
Sure,

but the problem is if you have hundreds of stuff installed this gets rather buggy. :-&

---

