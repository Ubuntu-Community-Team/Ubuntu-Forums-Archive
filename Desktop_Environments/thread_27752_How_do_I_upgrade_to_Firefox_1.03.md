---
title: "How do I upgrade to Firefox 1.03"
date: 2005-04-17
forum: Desktop Environments
---

### Post by denzilla on 2005-04-17
Since Ubuntu comes with 1.02 will the Ubuntu auto updater prompt me to install 1.03? If not, how to I upgrade?

---

### Post by XDevHald on 2005-04-17
You can download it from [b][http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/)

[/b]If you come accross an "xpistub" error, reply back because I get that error.

---

### Post by denzilla on 2005-04-17
Should I remove the original FF installation first?

---

### Post by XDevHald on 2005-04-17
It shouldn't matter, but give it a shot and see what it does, I'll post my errors etc here if you need help with yours as well.


**Edit > $ **In fact don't remove FF 1.0.2 because it will remove, yelp with is th eabout Ubuntu guide, which you will want, also, mozilla-mplayer, httpheaders for mozilla and others, so don't remove it.

Just try to install the 1.0.3 because I am getting the same error as before.

---

### Post by denzilla on 2005-04-17
The part that confuses me is that it wants to install where ever the file is executed at. So if I clicked on the binarry from the desktop, then thats where it wants to be installed. It seems that if I install 1.03, then I'm going to have 1.02 and 1.03 installed.

---

### Post by Firetech on 2005-04-17
Just install it as root (sudo) in /usr/lib/mozilla-firefox and you will overwrite the apt-get'd version.
This will prevent shortcut problems. (It works fine, I did it with 1.0.2)

---

### Post by XDevHald on 2005-04-17
Exactly that doesn't make any sense to me as well, and to be honest, 1.0.2 won't be replaced by 1.0.3 in the Synaptic.

You can basically just remove 1.0.2 IF the 1.0.3 will install and be sure to check the dependencies that 1.0.2 is removing with it and go back and install those dependencies again because you will need those as default by mozilla firefox plugins.

---

### Post by denzilla on 2005-04-17
Thanks for the tip, Firetech.

I'm getting the same xpi error. Had to re-install Firefox 1.02 from ubuntu CD to get back on the net again.

---

### Post by denzilla on 2005-04-18
*bump*

---

### Post by wxlidar on 2005-04-18
[QUOTE=denzilla]*bump*[/QUOTE]
 Are there two .sh files? I seemt to remember this problem and I simply ran the other .sh install file. Perhaps the one without the 'bin' in it?

Of course, I may be insane. 

Give us an update,
Dave

---

### Post by WeberMax on 2005-04-18
Hmm, wont come a official update from ubuntu to 1.0.3?  :neutral:

---

### Post by IdoMcFly on 2005-04-18
[QUOTE=WeberMax]Hmm, wont come a official update from ubuntu to 1.0.3?  :neutral:[/QUOTE]
 it will : there are security fix, so there will be an official update

---

### Post by denzilla on 2005-04-18
Hmmm... an offical update would be nice, but I thought the Ubuntu team didn't release updates between OS releases? I'm a noob, so I'm prolly wrong.

BTW, How come they remove the Fox from the FF icon? Looks kinda stupid without it.

---

### Post by Bob D. on 2005-04-18
> BTW, How come they remove the Fox from the FF icon? Looks kinda stupid without it.
Actually, it is a completely different icon. IIRC, it was due to an issue Debian has with the artwork license Mozilla used for the Firefox artwork. Since Ubuntu is built off of Debian....well, there you go.

Bob

---

### Post by denzilla on 2005-04-18
[QUOTE=wxlidar]Are there two .sh files? I seemt to remember this problem and I simply ran the other .sh install file. Perhaps the one without the 'bin' in it?

Of course, I may be insane. 

Give us an update,
Dave[/QUOTE]

THAT WORKED!!!! Thanks man :)  Everyone use this file, select "run" and point it to the /usr/lib/mozilla-firefox directory. Let it delete the old FF files. Your themes and favs will remain intact.

---

### Post by nix4me on 2005-04-18
Pretty disappointing that it has taken this long to get an official ubuntu Firefox 1.0.3 package.  Its been out for 2 days.

nix

---

### Post by denzilla on 2005-04-18
Bah..just install it like I said above. Same difference :)

---

### Post by quickgun on 2005-04-18
Just a note: It'd be wise to back-up your plugins dir in /usr/lib/mozilla-firefox before upgrading to 1.03.  Might save you some trouble. :smile:

---

### Post by gmc on 2005-04-19
[QUOTE=Firetech]Just install it as root (sudo) in /usr/lib/mozilla-firefox and you will overwrite the apt-get'd version.
This will prevent shortcut problems. (It works fine, I did it with 1.0.2)[/QUOTE]

BAD Move. Doing the above broke firefox v1.0.2/ubuntu. I had to uninstall it, delete the /usr/lib/mozilla-firefox directory and then reinstall the current v1.0.2/ubuntu version.

I'd remove firefox v1.0.2/ubuntu version and install v1.0.3 into the /opt directory and use that but doing so breaks 'yelp'. So in the meantime, I've turned off Javascript and will wait for firefox v1.0.3/ubuntu. Thanks just the same.

Gord

TIP: If you don't mind having two copies of FF installed, you can do the following:

1. Install FF v1.0.3 into the /opt directory
2. mv /usr/lib/mozilla-firefox/firefox /usr/lib/mozilla/firefox-102.backup
3. (as root) create a file called firefox in the above directory, with the
     following:

[B]#!/bin/bash

# Temporary Script to bypass FF v1.0.2 in favour of FF v1.0.3
cd /opt/firefox-103
./firefox
cd -

exit 0
[/B]

4. chmod 755 /usr/lib/mozilla-firefox/firefox

It's an ugly kludge, but it works and doesn't break "yelp"

---

### Post by Deusiah on 2005-04-19
[QUOTE=Bob D.]Actually, it is a completely different icon. IIRC, it was due to an issue Debian has with the artwork license Mozilla used for the Firefox artwork. Since Ubuntu is built off of Debian....well, there you go.

Bob[/QUOTE]

Thanks for that info, I had always wondered who I have to thank for needing to replace the fake icon with the real icon everytime :( Same goes for Thunderbird which uses's the most ugliest icon I have seen lol.

Isn't it possible to use the etiquette icon's version of it without the license issue?

---

### Post by denzilla on 2005-04-19
Well, I did notice today that yelp was broken. Any ETA on the official package update?

---

### Post by derrick1985 on 2005-04-19
[http://www.ubuntuforums.org/showthread.php?t=27842&highlight=firefox+1.0.3](http://www.ubuntuforums.org/showthread.php?t=27842&highlight=firefox+1.0.3)

---

### Post by Firetech on 2005-04-25
[QUOTE=gmc]BAD Move. Doing the above broke firefox v1.0.2/ubuntu. I had to uninstall it, delete the /usr/lib/mozilla-firefox directory and then reinstall the current v1.0.2/ubuntu version.[/QUOTE]
 Strange, it works perfectly for me... I did some days ago with 1.0.3. Although, I'm using Kubuntu.  (I used gnome when I did it with 1.0.2)

---

### Post by denzilla on 2005-04-25
it worked fine for me too except for breaking yelp. Its a shame that FF is tied so closely with other packages in ubuntu :( I just don't think you should have to wait for a whole new distro release to get a better browser.

---

### Post by Staesys on 2005-04-28
Well... I broke Yelp. I uninstalled firefox 1.0.2 and it took out ubuntu-desktop and yelp too. I installed firefox 1.0.3 and then tried to reinstall yelp and ubuntu-desktop. Eventually I had to reinstall the whole bunch and then installed firefox 1.0.3 on top of it and replaced that awful icon.

Yelp complained that it couldn't find libgtkembedmoz.so anymore, so a quick look around my harddrive produced a copy in another directory. After copying that into the /usr/lib directory, it didn't give that error anymore, but now it has a new one...

**I/O warning : failed to load external entity "/root/.gnome2/yelp-bookmarks.xbel"** 

I'm going to go to my other ubuntu computer and see if I can find a copy of what it says it's missing.

Wish me luck!

-Paul

Edit: No dice. I upgraded firefox on that computer as well. I just compiled and installed yelp 2.6.4 and now help works in programs, but not the main desktop. Almost there!

---

### Post by denzilla on 2005-04-29
1.03 is in the backports repository now :)

---

### Post by sarimak on 2005-05-04
FF 1.03 package can be found in hoary-backports...

---

### Post by thebentfender on 2005-06-19
I tried doing that (Installing in usr/lib/mozilla-firefox) but I got an error saying that I don't have permission to install.  I made sure Firefox was closed and everything.

I made myself the root user in Terminal using [COLOR=Red]sudo -s -H[/COLOR].  How do I give myself permission to install in this directory?  I just installed Ubuntu yesterday so the solution is probably right in front of me.

---

