---
title: "MAME Games in 10.10 64-bit"
date: 2011-03-30
forum: Gaming &amp; Leisure
---

### Post by AndyCinDallas on 2011-03-30
I was confused by all the older threads and all the various versions of Mame and SDL and all sorts of stuff, so I decided to try it from scratch:

1. I went into the Ubuntu Software Center and found GMAMEUI (I didn't select any of the available add-ons) - I installed that program just fine.

2. On opening GMAMEUI, it complained that "No MAME executables have been chosen" - that's because GMAMEUI is not Mame itself, it's just the pretty GUI front-end for Mame. So close GMAMEUI and then....

3. Open a Terminal window and type **sudo apt-get install sdlmame** (and give your password when prompted) - this will download and install SDLMame.

4. Open GMAMEUI again and see the same complaint about the MAME executable, so click the "Add" button and browse to **/usr/games/mame** - then hit "Ok"

5. To store the ROMs themselves, make a folder somewhere - I just put mine in /home/andy/ROMs

[IMG]http://i52.tinypic.com/2e3rcpx.jpg[/IMG]

It does a check on the games and voila! (I went into options to play in window-mode instead of full-screen):

[IMG]http://i56.tinypic.com/2elth1l.jpg[/IMG]

Hope this helps someone

---

### Post by supergreatbirdman on 2011-06-09
Hello and thank you for being so clear for a linux newbie like me, i have been swimming in forums trying to understand all this stuff.
I followed your instructions exactly and, for the 1st time, got the huge list of roms to appear "available".  However, when i open a rom i get the following error:

**GMAMEUI Could Not Load the Rom**

The following ROMs were not found:
3006-13.1b NOT FOUND
3006-14.2b NOT FOUND
3006-15.3b NOT FOUND
3006-16.4b NOT FOUND
3006-17.5b NOT FOUND
3006-18.6b NOT FOUND
3006-19.7b NOT FOUND
3006-20.8b NOT FOUND
3006-21.9b NOT FOUND
3006-22.10b NOT FOUND
3006-23.11b NOT FOUND
3006-24.12b NOT FOUND
decoder.4 NOT FOUND
decoder.6 NOT FOUND
joust.snd NOT FOUND


This list is from Joust (White/Green Label), but i have tried many with same results.  
The problem, of course, is the roms folder i created, home/pat/ROMs/mame,  is empty.  I was under the impression that installing sdlmame through the terminal meant installing the roms themselves.  If i am mistaken, can they be installed through the terminal?  If not, where can i find them?  Thanks in advance for anyone who wants to state the obvious to this desperate gamer.

---

### Post by mips on 2011-06-10
> **supergreatbirdman said:**
> 
I followed your instructions exactly and, for the 1st time, got the huge list of roms to appear "available".  However, when i open a rom i get the following error:

GMAMEUI is problematic in my experience and there has been many people posting here having similar issue out of the blue.

See [http://ubuntuforums.org/showthread.php?t=1734918](http://ubuntuforums.org/showthread.php?t=1734918) on how to use QMC2

---

### Post by DoktorSeven on 2011-06-10
> **supergreatbirdman said:**
> 
The problem, of course, is the roms folder i created, home/pat/ROMs/mame,  is empty.  I was under the impression that installing sdlmame through the terminal meant installing the roms themselves.  If i am mistaken, can they be installed through the terminal?  If not, where can i find them?  Thanks in advance for anyone who wants to state the obvious to this desperate gamer.
The ROMs are NOT included with the emulator because they are copyrighted and can't be distributed without compensation to the copyright owners.  There are "methods" to get them illegally but since this is not legal, it should not be discussed here at all.  The only legal method (besides the free ones below) is to own the game or PCB and dump an image from the ROMs.

The only truly legal ROMs for MAME are those the copyright owners have allowed to be distributed for free, and you can find those on MAME's site here:

[http://mamedev.org/roms/](http://mamedev.org/roms/)

Download those to the directory you created for ROMs (save as ZIP, don't uncompress) and point to them with your MAME frontend.

---

### Post by supergreatbirdman on 2011-06-10
Hey i downloaded some legal free roms from the posted link and it seems to be working smooth, so far.  finally!  thanks for your help everybody.

---

### Post by desktorp on 2011-06-11
> **mips said:**
> GMAMEUI is problematic in my experience and there has been many people posting here having similar issue out of the blue.

See [http://ubuntuforums.org/showthread.php?t=1734918](http://ubuntuforums.org/showthread.php?t=1734918) on how to use QMC2
I do not mean to be rude, but that thread basically shows you repeating the same suggestion for a personal preference, when it had no real bearing on the problem(s).  I'm not saying GMAMEUI is really any better - I hate both of them, frankly.. but in my experience, using a Qt program in any environment but KDE tends to be a form of torture, unless the program in question is some sort of a masterpiece.  I'm sure in KDE/Qt, QMC2 could be the obvious choice, but GMAMEUI is the obvious choice for Gtk, despite any shortcomings, real or imagined.

---

### Post by mips on 2011-06-11
> **desktorp said:**
> I do not mean to be rude, but that thread basically shows you repeating the same suggestion for a personal preference, when it had no real bearing on the problem(s).  I'm not saying GMAMEUI is really any better - I hate both of them, frankly.. but in my experience, using a Qt program in any environment but KDE tends to be a form of torture, unless the program in question is some sort of a masterpiece.  I'm sure in KDE/Qt, QMC2 could be the obvious choice, but GMAMEUI is the obvious choice for Gtk, despite any shortcomings, real or imagined.

If you say so. I would rather pick the app that works better before worrying about gtk/qt purity.

---

### Post by desktorp on 2011-06-11
> **mips said:**
> If you say so. I would rather pick the app that works better before worrying about gtk/qt purity.:(  If I say so?  I just thought your personal preference might have some more beef to it other than "it's better" .. but whatever.

---

### Post by DoktorSeven on 2011-06-11
Or you can be like me and run it from a terminal directly

```
$ mame galaga
```

In the end, it doesn't matter what you use as long as it works and works well for you.  Arguing over frontends is as pointless as arguing vim vs. emacs.

Also, vim > emacs :)

---

### Post by desktorp on 2011-06-11
Yeah you're right and I wasn't meaning to argue with mips, who I think is a super guy.  Sorry mips.  :popcorn:

---

### Post by mips on 2011-06-11
> **desktorp said:**
> Yeah you're right and I wasn't meaning to argue with mips, who I think is a super guy.  Sorry mips.  :popcorn:

No problemo.

My reason for recommending QMC2 is that I have used GMAMEUI (still have it installed) and I've had issues with loading roms or the app not finding roms. Thing is it initially works fine and then out of the blue it starts it's nonsense. I have also seen this behaviour reported by other people so it's not something unique to my install. I have Gnome DM (& Openbox WM) but I'm not fussy about running Qt apps although I usually prefer to first go for a Gtk app but in this case it did not work out for me. It partiality stems from personal experience and that reported by other users.

Either way the final decision on what to use is up to the individual.

---

