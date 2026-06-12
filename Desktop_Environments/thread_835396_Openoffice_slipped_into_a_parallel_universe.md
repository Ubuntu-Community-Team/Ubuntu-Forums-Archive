---
title: "Openoffice slipped into a parallel universe"
date: 2008-06-20
forum: Desktop Environments
---

### Post by jesaisrien on 2008-06-20
Hi People,

Yesterday my openoffice stopped working. I can click on the icons on the desktop or in the menus but none of the parts open up - not the word processor, not the spreadsheet, not the database, etc.

I can't think of what it might be. I downloaded updates yesterday for everything, which I do about once a week.

The only thing odd I did was to download some google toolbar thingees through the new firefox 3 browser ( don't even remember what ). What is odd is that I never download anything into this computer except from the ubuntu download sites.

Haven't had any other problems. Everything else seems to work fine, to the extent that I've checked.

I have been using Hardy since it came out, and have been using Ubuntu since version 5.0 - awhile. But I'm nobodies guru for sure.

I use a 500 GB USB external hard drive for my OS, and just plug
into another computer that is on the web to upgrade and download. 

Except for the oddity mentioned earlier, this is what I have been doing for awhile with no problems before now. My hardware is all pretty vanilla, middle of the road stuff. Using DSL to get on the web.

Any thoughts? Thanks in advance for any help.

In the meantime I think I'll get back online, delete the present Ooo suite (2.4.1 by the way) and download again - reinstall. See if that works. Weird.

---

### Post by mike2357 on 2008-06-20
Gee whiz.  A puzzlement to be sure.

If re-installing doesn't work (that would be my strategy, too), I think you're going to have to go into heavy-duty diagnosis mode.

I'd want to know if the problem is the icons or if the programs really aren't there.  So I'd open up a command window (with ALT-F3) and run commands to invoke OpenOffice.

This command should start the word processor
ooffice -writer

This command should start the spreadsheet software
ooffice -calc

If the commands work OK, then it's the icons that are the problem.  You can right-click on them, click on properties and see if you see any problems.

---

### Post by jesaisrien on 2008-06-21
Reinstalled. The commands you suggested didn't work any better then the icons or the command line stuff ( e.g., " cd /etc/.../openoffice/8.3/program ", then, " ./soffice.bin.

All the many dozens of files seem to be there but I have to say I wouldn't know if one or two were missing. Insterestingly, " ./spadmin.bin " runs ok.

What is happening when I attempt to run soffice.bin or oofice -calc or use one of the icons, is that sometimes nothing happens, but sometimes the border appears, and one or two of the top toolbars, but all the area in the middle remains blank,, and the whole thing just is locked up and has to be killed.

So let me ask a really ignorant question: isn't there a log somewhere that lists exactly what happened? I think there is but I'm embarassed to say that after all these years I have never used it so I don't know where it is.

Thanks for you help!

---

### Post by Tomatz on 2008-06-21
Open a terminal and run the following command:


```
ooffice -writer %U
```


Then post the output ;)

---

### Post by jesaisrien on 2008-06-21
Right after this reply I am going to go try your suggestion and see what happens, but in the meantime I found a fix of sorts, in an interesting way.

Went to the open office community forums, under setup and troubleshooting under linux. The second post had to do with a problem similar to mine. The fix:
       sudo apt-get remove openoffice.org-gtk

I tried this and it works. Don't know why. I will have to look into this more to see what it is I'm now missing, but at least I have my open office back. Yay!

The irony was that fix was from the following link:
  [http://ubuntuforums.org/showthread.php?t=832849&highlight=openoffice](http://ubuntuforums.org/showthread.php?t=832849&highlight=openoffice)

Right back here! Ha!

---

### Post by jesaisrien on 2008-06-21
Hi Tomatz,

I ran the command:

ooffice -writer %U

as you suggested and this is what happened; Openoffice would start to open and then there would be an error message stating that %U did not exist in my home directory. That's it.

However, "ooffice -writer" and "ooffice -calc" now work fine, and the icons work also. Must be a gtk thing.

---

### Post by jesaisrien on 2008-06-21
Thanks again for the help Tomatz. It is greatly appreciated.

---

### Post by jesaisrien on 2008-06-21
And mike2357! Thank you so much! Sorry - thought you people were one.

---

### Post by Tomatz on 2008-06-22
> **jesaisrien said:**
> Hi Tomatz,

I ran the command:

ooffice -writer %U

as you suggested and this is what happened; Openoffice would start to open and then there would be an error message stating that %U did not exist in my home directory. That's it.

However, "ooffice -writer" and "ooffice -calc" now work fine, and the icons work also. Must be a gtk thing.

Hmm strange.

Oh well at least you fixed it :)

---

