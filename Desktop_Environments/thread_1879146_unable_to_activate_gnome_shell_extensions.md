---
title: "unable to activate gnome shell extensions"
date: 2011-11-11
forum: Desktop Environments
---

### Post by porosjp on 2011-11-11
Hi I'm using Gnome Shell on Ubuntu 11.10 and the Gnome tweak tool is unable to activate new extensions. there's a yellow danger triangle in front of the correspondant buttons and they don't work. 
Thank's for helping me

---

### Post by Bobhuber on 2011-11-11
> **porosjp said:**
> Hi I'm using Gnome Shell on Ubuntu 11.10 and the Gnome tweak tool is unable to activate new extensions. there's a yellow danger triangle in front of the correspondant buttons and they don't work. 
Thank's for helping me
Your probably getting your updates from the testing ppa (ricotz). They have had quite a few problems recently. Web8 has a PPA for the most recent stable version of gnome-tweak and the extensions (sorry I don't have it handy).Change the PPA and update the source  and it should solve your problems.

Edit - sudo add-apt-repository ppa:webupd8team/gnome3 (make sure you disable or remove the Ricotz PPA)

---

### Post by Frogs Hair on 2011-11-11
I have had success with Web Upd8  extensions  also . They can be installed one by one are all at once .
[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

---

### Post by porosjp on 2011-11-13
Thank you to help me
I removed the ricotz ppa and have the last official version of gnome tweak tool and extensions peovided by Webupd8
but it's still the same problem, the extensions are marked "disabled" (the yellow triangle) even there are installed or not.

---

### Post by BigCityCat on 2011-11-13
Yeh I'm using the webupd8 ppa and I have the same problem. I have had it working for a while and the extensions that are enabled are fine but as soon as I turn one off I can not re enable it. Luckily I have the ones I want working. This is a bug. Not sure whats causing it.

here is the picture.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-11-13143645.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-11-13143645.png)

---

### Post by BigCityCat on 2011-11-13
Took a look at synaptic under the webupd8 ppa and most of the extensions are missing. I guess the reason the ones I am using are still working is because they are active. There seems to be a problem with the webupd8 ppa.

---

### Post by Frogs Hair on 2011-11-13
Try moving the extensions to be used into the on position and logout and back in . I have only had to do this when adding a new extension though and don't know the cause of the problem .

---

### Post by porosjp on 2011-11-13
same problem, only the desktop picture is different !

---

### Post by BigCityCat on 2011-11-13
> **Frogs Hair said:**
> Try moving the extensions to be used into the on position and logout and back in . I have only had to do this when adding a new extension though and don't know the cause of the problem .

You can't click on them. They don't move. I tried re installing but it says the newest version is installed.

---

### Post by BigCityCat on 2011-11-13
Tried removing some that I'm not using and re installing. Nothing changed.

---

### Post by cbowman57 on 2011-11-13
What do you see for errors when you open up looking glass?

---

### Post by porosjp on 2011-11-13
> **cbowman57 said:**
> What do you see for errors when you open up looking glass?

I don't use looking glass

JP

---

### Post by cbowman57 on 2011-11-13
> **porosjp said:**
> I don't use looking glass

JP

Makes it pretty hard to troubleshoot extensions without it.

---

### Post by BigCityCat on 2011-11-13
> **cbowman57 said:**
> What do you see for errors when you open up looking glass?

There are several errors for extensions. Wish I could cut copy and paste sure would make this easier. Anyway I will give you the first they all say same thing.

debug t=2011-11-13T22:52:51Z Loaded Extension [email]weather@gnome-shell-extensions.gnome.org[/email]

That's pretty much it. There are several but they are all the same.

---

### Post by cbowman57 on 2011-11-13
> **BigCityCat said:**
> There are several errors for extensions. Wish I could cut copy and paste sure would make this easier. Anyway I will give you the first they all say same thing.

debug t=2011-11-13T22:52:51Z Loaded Extension [EMAIL="weather@gnome-shell-extensions.gnome.org"]weather@gnome-shell-extensions.gnome.org[/EMAIL]

That's pretty much it. There are several but they are all the same.

Ok, that's normal.  Puzzling why you can't enable/disable them.

---

### Post by BigCityCat on 2011-11-13
> **cbowman57 said:**
> Ok, that's normal.  Puzzling why you can't enable/disable them.

Yeh it is, but honestly I have the ones I want working. So far as long as I don't disable them I can use them. I am assuming that this is a bug and that there will be a solution eventually, but the OP may not be happy about that.

I would suggest that he go into Unity and remove Gnome shell. Re install it and the extensions along with it.

---

### Post by cbowman57 on 2011-11-13
I've been running gnome shell for awhile, have only encountered one that did that to me & it was an acknowledged bug, worked even though it didn't look like it should.

Might want to check the shell version & compare it to the version in the metadata.json of the offending extension(s).


I apologise if you already mentioned this earlier in the thread, but just to summarise,  you got your extensions from Webupd8 & you're running 11.10?

---

### Post by BigCityCat on 2011-11-13
Yes I am using the webupd8 PPA. I am using ubuntu 11.10 with gnome shell.  I have been using it for a while without issue. Extensions were working fine. Recently I noticed that the extensions I was not using could not be enabled with a little error triangle next to them. If I disabled an extension I could not re enable it. If I highlight the little triangle nest to the extension it says "unknown extension error".

---

### Post by BigCityCat on 2011-11-13
Did you see this?

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-11-13143645.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-11-13143645.png)

---

### Post by BigCityCat on 2011-11-13
here is the metadata.json file

> {
 "uuid": "alternative-status-menu@gnome-shell-extensions.gnome.org",
 "name": "Alternative Status Menu",
 "description": "Replaces GNOME Shell Status Menu with one showing Suspend/Hibernate and Power Off as separate items",
 "shell-version": [ "3.2.1" ],
 "localedir": "/usr/share/locale",
 "url": "http://git.gnome.org/gnome-shell-extensions"
}

---

### Post by cbowman57 on 2011-11-13
Ok, I know you're running shell version 3.2.1 but try replacing "shell-version" 3.2.1 with just 3.2

---

### Post by BigCityCat on 2011-11-13
> **cbowman57 said:**
> Ok, I know you're running shell version 3.2.1 but try replacing "shell-version" 3.2.1 with just 3.2

It didn't work. There are several others that aren't working and the version number on those is 3.2 so...

---

### Post by pacco1 on 2011-11-13
I had the same  almost the same PB  but  didnt find the SOL...
a friend of mine solved it so will try to ask em..

---

### Post by porosjp on 2011-11-17
The solution of my problem is there :
[http://ubuntuforums.org/showthread.php?t=1874010](http://ubuntuforums.org/showthread.php?t=1874010) 
;)

---

### Post by Bobhuber on 2011-11-17
> **porosjp said:**
> The solution of my problem is there :
[http://ubuntuforums.org/showthread.php?t=1874010](http://ubuntuforums.org/showthread.php?t=1874010) 
;)
That solution works if you are using the  ricotz development PPA. Had you disabled it and installed the stable version from web8 and updated the system (as suggested) all would have worked quite a while ago.
The two versions of gnome-extensions and gnome-tweak are not compatible.
Makes no difference as long as your happy and everything is working.

---

### Post by cbowman57 on 2011-11-17
> **Bobhuber said:**
> That solution works if you are using the  ricotz development PPA. Had you disabled it and installed the stable version from web8 and updated the system (as suggested) all would have worked quite a while ago.
The two versions of gnome-extensions and gnome-tweak are not compatible.
Makes no difference as long as your happy and everything is working.

+1

Even Rico mentioned a few months ago NOT to use his ppa because it is not stable & can break things.  It was good advice then, & it's still good advice.

---

### Post by porosjp on 2011-11-17
By the way, I used to disable rico's ppa and reinstalling gnome tweak tool, but nothing did'nt change. May be I did'nt find the right way to install it from web8. Which is the right way ?

Greetings from France

---

### Post by Bobhuber on 2011-11-17
> **porosjp said:**
> By the way, I used to disable rico's ppa and reinstalling gnome tweak tool, but nothing did'nt change. May be I did'nt find the right way to install it from web8. Which is the right way ?

Greetings from France
Easy Way
1. Install Synaptic package manager.
2. Disable rico's PPA or remove it.

3. Add the web8 PPA to the listing and hit reload on the package manager screen  or from a terminal
sudo add-apt-repository ppa:webupd8team/gnome3
 sudo apt-get update

Reboot the computer (this will clear everything)
All of the updated extensions and gnome tweak tool are now in the package manager.

---

### Post by porosjp on 2011-11-17
It works perfectly now
Thanks for all

---

### Post by ubudog on 2011-11-17
> **porosjp said:**
> It works perfectly now
Thanks for all

Great, will mark as solved.  ;)

---

