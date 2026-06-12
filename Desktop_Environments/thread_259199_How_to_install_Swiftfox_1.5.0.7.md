---
title: "How to install Swiftfox 1.5.0.7"
date: 2006-09-17
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-09-17
Hi,

I have downloaded Swiftfox 1.5.0.7 and would like to install it.  The trouble is, I can't get permission to copy to the directory where the current swiftfox folder in located.  /opt    (I installed it originally using automatix).

Does anyone have the knowledge of how to upgrade Swiftfox while keeping my curent settings intact? and, how does one take control of the opt folder?

---

### Post by pay on 2006-09-17
You can open nautilus as the root by typing
```
gksudo nautilus
```
into the terminal

---

### Post by The Pinny Parlour on 2006-09-17
Thank you pay, that worked a treat.

For others:
I downloaded Swiftfox 1.5.0.7.  Then extracted to my desktop.  Opened nautilus by coding:
```
gksudo nautilus
```
I then copyed and paste, my Swiftfox 1.5.0.7 into the /opt directory, overwriting the existing.  It keeps your profiles intact. (eg, bookmarks,etc).

Happy  O:)

---

### Post by akak8ty on 2006-09-20
I got the message:
(nautilus:14738): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
:-x 
I want xampp, been using it for a long time- I realize it converts to Lampp along the way.

I really like the ubuntu, but I really like access to my files pronto- no commands, no permission. I am the administrator of my network- why must I always ask myself to grant myself permission?
That's a real pain in the a**.

---

### Post by Cable on 2006-09-20
> **akak8ty said:**
> I really like the ubuntu, but I really like access to my files pronto- no commands, no permission. I am the administrator of my network- why must I always ask myself to grant myself permission?
That's a real pain in the a**.

It's just how Ubuntu works.  Having access to such important files *shouldn't* be as easy as it is in Windows.  The Ubuntu way is much more secure.  You'll get used to it and learn to appreciate it.

---

### Post by akak8ty on 2006-09-21
Files are files, and I know what files not to mess with just as I knew which registry keys not to fool with. I am aware not everyone shares that ability, because when they screw up their machine, I am the one who has to fix it.
But to now take 6 hours trying everything I have found written to install a file to /opt and I still don't have the correct permissions is a bit infuriating. I've resolved error messages, and all sorts of other fun things since 5:00 pm est
I have had no trouble during this six hour plight installing anything else, except to opt.
Maybe the German version will be more helpful, since nothing else has worked.
I am happy about what I did accomplish, tweak and fix- but annoyed that I can not get "the right" permission- those words, yet my picassa seems to be sitting in there just fine and I didn't intentionally put it there.
I had to manually configure this particular file in windows as well-in dos, and it was much easier.
I didn't need sudo voodoo magic words to make it happen.



> **Cable said:**
> It's just how Ubuntu works.  Having access to such important files *shouldn't* be as easy as it is in Windows.  The Ubuntu way is much more secure.  You'll get used to it and learn to appreciate it.

---

### Post by puppy on 2006-09-21
It's good that your approach worked but I think that there's a much simpler way to do this  ;) 

You will find that if you enable "view hidden files" in Nautilus you can see a little folder in your home directory called (I think - not in front of my ubuntu box at the moment) .mozilla  <<< this is the folder where all your configured settings are stored i.e. extensions, themes, bookmarks etc etc

I periodically copy this folder in its entirety and store it somewhere safe in case of emergencies. If you're reinstalling firefox/swiftfox you'll find that it will install a fresh copy of this folder in your home directory, so to get all your stuff back to the way it was before just delete the folder that the new installation has put in there and paste back in the one you have stored for a rainy day - hey presto, everythings back the way it was before with near zero effort   :D

---

### Post by akak8ty on 2006-09-21
> **puppy said:**
> It's good that your approach worked but I think that there's a much simpler way to do this  ;) 

You will find that if you enable "view hidden files" in Nautilus you can see a little folder in your home directory called (I think - not in front of my ubuntu box at the moment) .mozilla  <<< this is the folder where all your configured settings are stored i.e. extensions, themes, bookmarks etc etc

I periodically copy this folder in its entirety and store it somewhere safe in case of emergencies. If you're reinstalling firefox/swiftfox you'll find that it will install a fresh copy of this folder in your home directory, so to get all your stuff back to the way it was before just delete the folder that the new installation has put in there and paste back in the one you have stored for a rainy day - hey presto, everythings back the way it was before with near zero effort   :D

Well today something is askew in the land of Oz. I went to reboot because I couldn't open my terminal, now it won't open at all, and I have 4 admin files, add remove programs are gone as is synaptic package manager. 
To be quite frank, the issues began after I switched over to nautilus. 
I wasn't the one inquiring about installing firefox, but am happy the info was provided- 
I was trying to install xampp -> {lampp}
Me thinks I will reboot again. :-&

---

