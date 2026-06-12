---
title: "Dungeon Defenders Freezes"
date: 2012-12-21
forum: Gaming &amp; Leisure
---

### Post by rudeboyskunk on 2012-12-21
I got Dungeon Defenders through the Humble Indie Bundle 7, but when I start the game (from terminal ./DungeonDefenders), it shows the splash screen, then goes to the splash animation for the production companies/engines (Instinct and Unreal), but during the splash animations it freezes.  I've started it several times and the furthest it managed to get is partway through the Unreal animation.  I checked their system requirements on their wiki and I should be fine (granted the hardware listed was okay under Windows, they didn't list Linux requirements).

Ubuntu 12.04.1 64-bit
AMD Athlon II Dual-Core M300 x2
4GB RAM
ATI Mobility Radeon 4200

Any ideas?  Workarounds?  A way to skip the splash intros?

EDIT: Ok, I decided to just sit and wait and after about 1 1/2 minutes it got through the splash screens and into the game.  However, it was really choppy (just at the menu), and when I set it to full screen, it made a full black screen with the top left-hand corner being the game, and I couldn't move the mouse down to the "exit" button.  Ugh.

---

### Post by 10robinho on 2012-12-21
same here! not fair as we paid for non-working game...

---

### Post by Thunder God on 2012-12-22
Mine doesn't freeze although when I change to full-screen I get the same issue as you (3/4 of game screen is blacked out), and now can't change back to windowed mode!
Any suggestions?


specs:
core i5 3.4GHz
8GB ram
radeon hd 7770
120gb ssd
*Ubuntu 12.10 64-bit
*beta amd drivers 12.11

---

### Post by oldrocker99 on 2012-12-22
I only got one freeze, when I tried from the main menu to change resolution to a full-screen 1900x1200. The screen went black, the music continued, and I have to ctrl-F1 my way out. 

Since then, I've played in a 1600x900 window, and it seems to play OK. I have gotten my character to build 3 Magic Missile towers, and am trying out how to trigger the invasion I have to defend against.

At least(for me) it runs.

AMD 965 4-core, 3400 MHz (stock)
nVidia 520 graphics (cheapo), latest xorg-edgers drivers.

---

### Post by oldrocker99 on 2012-12-22
> **10robinho said:**
> same here! not fair as we paid for non-working game...

Don't be too indignant; in Humble Bundle 6, Torchlight crashed repeatedly, and was upgraded twice to the (nearly) perfect version I now avidly play. Keep checking the Humble Bundle site; Dungeon Defenders is a Big Farking Game, too large for updates to be delivered from the Ubuntu Software Center, as all the games in HB 6 can be upgraded. If there's an upgrade, the Humble Bundle site from which you downloaded (you did save your email with the link, right?), and that site only will be where updates will be posted.

---

### Post by thatguruguy on 2012-12-22
The guy who made this particular port, [Ryan C. Gordon]("http://en.wikipedia.org/wiki/Ryan_C._Gordon") (aka [icculus]("https://twitter.com/icculus")), maintains his own bugzilla. I'd suggest going [there]("https://bugzilla.icculus.org/buglist.cgi?product=Dungeon%20Defenders&component=everything&resolution=---") and looking to see if any of your issues have already been addressed, or if proposed fixes/work-arounds have been suggested.

For example, there is a workaround for the crash-upon-loading bug.  You can find it [here]("https://bugzilla.icculus.org/show_bug.cgi?id=5820#c10").

---

### Post by CrusaderAD on 2012-12-23
I've tried 2 different machines with this one... running > sudo ./DungeonDefenders only gets some "installed in" dialog in terminal, a splash screen for a quick second, and then exit... no other info. Any ideas?

---

### Post by rudeboyskunk on 2012-12-24
> **CrusaderAD said:**
> I've tried 2 different machines with this one... running  only gets some "installed in" dialog in terminal, a splash screen for a quick second, and then exit... no other info. Any ideas?

Why are you running it as root?  That's not an install script, that's the game.

---

### Post by CrusaderAD on 2012-12-24
> **rudeboyskunk said:**
> Why are you running it as root?  That's not an install script, that's the game.

It was a recommendation on their website. Either way, it doesn't work.

---

### Post by rudeboyskunk on 2012-12-25
> **CrusaderAD said:**
> It was a recommendation on their website. Either way, it doesn't work.

Really?  Strange... Did it say why?  Seems completely unnecessary to me.

---

### Post by CrusaderAD on 2012-12-25
> **rudeboyskunk said:**
> Really?  Strange... Did it say why?  Seems completely unnecessary to me.

Tried a few things. It says segmentation fault. Doesn't seem like a very solid port job. Tried on multiple machines.

---

### Post by thatguruguy on 2012-12-26
> **CrusaderAD said:**
> Tried a few things. It says segmentation fault. Doesn't seem like a very solid port job. Tried on multiple machines.

Is there some reason you completely ignored my post [here]("http://ubuntuforums.org/showpost.php?p=12417216&postcount=6"), which probably addresses your problem?

---

### Post by CrusaderAD on 2012-12-26
> **thatguruguy said:**
> Is there some reason you completely ignored my post [here]("http://ubuntuforums.org/showpost.php?p=12417216&postcount=6"), which probably addresses your problem?

I did have a look. There was one promising thread [here]("https://bugzilla.icculus.org/show_bug.cgi?id=5823"), but no fix has been deployed. Or even a solid work around for that matter. I'm sure they'll fix it at some point. Just gotta be patient.

---

### Post by CrusaderAD on 2012-12-27
Fyi They released 3 more games! Thanks devs!

---

### Post by zim2dive on 2012-12-28
I can't even get that far.. I get ```
./DungeonDefenders-x86: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

According to the SW center, I have libstdc++6-4.6-dev installed. (12.04)

EDIT: as someone else mentioned.. installing snapshot via SW center, gets me further.. now DD is saying it can't find any mice to control.  Off to spend more time investigating how to play the games I bought.
EDIT2: Installing the Isaac game fixed that.. and now DD launches... but is totally unresponsive to any mouse/keyboard input.  runnig with sudo seems to fix that.. but my TRS80 has a higher frame-rate...

---

### Post by Gaygerbil on 2013-01-01
This is what I get in the terminal when I run the game:

```
Dungeon Defenders: Installed in '/home/bewbman/Downloads/DungeonDefenders'.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 150 requests (150 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 18 requests (18 known processed) with 0 events remaining.

```

When I run it out of terminal it just flashes the screen and goes back to the login screen for some reason, weird. There'll be an update soon, but it sucks cuz this game is 5 Gigs big I hate having to keep downloading such a huge file over and over.

---

### Post by oldrocker99 on 2013-01-01
FWIW, I just played a session of Dungeon Defenders until it got too hard;), and all I had to do was ALT-TAB away from its window and back; the game ran perfectly.

For what it's worth.

---

### Post by Another Monkey on 2013-01-21
Has anyone got this to work?

Whenever I try full-screen, I get stuck with a black screen and have to kill the process.

Icculus's bugzilla for Dungeon Defenders seems to be down.

---

### Post by CrusaderAD on 2013-01-21
Not me. I've tried it on 3 machines with both installers. All I ever get is a segmentation fault.

---

### Post by Gaygerbil on 2013-01-25
For people still having a problem with launching this game pertaining to my error, I figured out it has something to do with a Gnome-screensaver dependency and if you don't have Gnome you are kinda screwed until this is addressed in a patch. 

However there is somewhat of a work around that allows the game to launch ATM:

```
 sudo ln -s /bin/true /usr/bin/gnome-screensaver-command 
```

It won't allow full screen but you can set it to your resolution and undercorate the title bar to make it look like full screen which is what I do and it runs pretty well still.

---

