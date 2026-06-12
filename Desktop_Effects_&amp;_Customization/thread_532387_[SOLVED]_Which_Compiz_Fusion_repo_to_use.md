---
title: "[SOLVED] Which Compiz Fusion repo to use?"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-08-22
I used Trevino's repos and everything worked well. Then some update screwed everything up. So I used Amaranth's repos and found there were quite a few plugins missing.

Then someone suggested Vorian's repos. Can someone tell me which is stable and has all the plugins as of Aug 22 2007 ?

---

### Post by mysticmatrix on 2007-08-22
None :lolflag:

Either you can face breakups(IT IS STILL ALPHA SOFTWARE); or be stable.

You can't have your cake and eat it too.

EDIT: Vorian's repo is old and stable. Amaranth repo gives backward compatibility that would save you headaches when upgrading to Gutsy.

---

### Post by Rupertronco on 2007-08-22
I prefer Vorian's repo, it's a little old but it has working 3-d windows, atlantis, scale switcher etc.

---

### Post by reacocard on 2007-08-22
I like amaranth's. It's lost me my compiz settings once but it keeps working just fine.

---

### Post by umanzor on 2007-08-22
Cool now, any links to those repos?

---

### Post by FuturePilot on 2007-08-22
I like Trevino's. It runs much smoother than other repos I've tried.

---

### Post by Vorian on 2007-08-22
I just updated my repository and the CCSM has been fixed

[http://vorian.org/?p=122](http://vorian.org/?p=122)

---

### Post by GFree678 on 2007-08-22
I prefer Trevino's simply because I've been using his packages the longest, and when I switched to Vorian's a lot of the default config settings were different. I'm not sure why the two guys have chosen different default settings.

(eg. Vorian's had some kind of arrow graphic when switching sides of a workspace, Trev's doesn't. Probably a lot more subtle things, but I didn't bother to stick to check it out. Still waiting for the CCSM fix with Trev's repo though.)

---

### Post by gtrtx on 2007-08-22
I'm using the Trevino packages. Currently using the ones before everything broke. For me, these work the best.  Version 0.5.1.....

You can downgrade by using this guide:
[URL="http://forum.compiz-fusion.org/showthread.php?t=3432"]
http://forum.compiz-fusion.org/showthread.php?t=3432[/URL]

When installing the debs it's kinda trial and error as to which order to install them. You will get dependency errors if they are installed out of order, but it will tell you which package to install in order to satisfy the dependencies.

Also for some reason the get_compiz script leaves out libdecoration0_0.5.1+git20070622~3v1ubuntu3_i386.deb

but it's easy enough to download that from 
[ http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/]("http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/")

hope somebody finds this useful

I've tried all the different repositories and the above version is the one I've had the most luck with. I'll stick with this till the rest of this blows over. Hell, I may just keep using it until Gutsy final  is  released. 


smo

---

### Post by Inxsible on 2007-08-23
I uninstalled CF. then removed all the related folders from my /home. then used Trevino's repos to re-install. everything works now.

I also commented Trevino's repos from my sources.list. That way, it won't show in my updates. On the flip side, I would have to manually track if and when a stable update is released, then uncomment his repos and then update.  I think I can live with that :)

---

### Post by glupee on 2007-08-23
> **Inxsible said:**
> I uninstalled CF. then removed all the related folders from my /home. then used Trevino's repos to re-install. everything works now.

I also commented Trevino's repos from my sources.list. That way, it won't show in my updates. On the flip side, I would have to manually track if and when a stable update is released, then uncomment his repos and then update.  I think I can live with that :)

That's an awesome idea! Will be using that ;)

---

### Post by ricardoec on 2007-08-23
> **Inxsible said:**
> I uninstalled CF. then removed all the related folders from my /home. then used Trevino's repos to re-install. everything works now.

I also commented Trevino's repos from my sources.list. That way, it won't show in my updates. On the flip side, I would have to manually track if and when a stable update is released, then uncomment his repos and then update.  I think I can live with that :)

what are those RELEVANT folders to be removed?. I also have a mess of different installations and want to start everithing clean. I have two computers, one used to work just fine, the other I could never get it to run compiz.

After the latest upgrades of tha past few days, none of them work so, please if you could post a "clean - up" procedure, will appreciate.

Cheers

---

### Post by Inxsible on 2007-08-23
> **ricardoec said:**
> what are those RELEVANT folders to be removed?. I also have a mess of different installations and want to start everithing clean. I have two computers, one used to work just fine, the other I could never get it to run compiz.

After the latest upgrades of tha past few days, none of them work so, please if you could post a "clean - up" procedure, will appreciate.

CheersCheck this link 

[http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---

