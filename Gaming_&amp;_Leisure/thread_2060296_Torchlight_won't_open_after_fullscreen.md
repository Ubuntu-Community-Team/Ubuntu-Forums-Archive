---
title: "Torchlight won't open after fullscreen"
date: 2012-09-19
forum: Gaming &amp; Leisure
---

### Post by DoubleYouSee23 on 2012-09-19
I just downloaded TorchLight as a part of the humble bundle pack, played if for awhile on Ubuntu 12.04, everything worked fine at 800x600 (i think that was the default screen size), but when I restarted later I changed the setting to fullscreen causing the game to crash. when i try to restart all i get is a sliver of.......?something?   happening in the middle of my screen and sometimes my mouse pointer will turn into a gauntlet for smashing evil.... but no evil.
surfed around and couldn't find anyone with the same problem
then, feeling like a freaking genius (because i'm computer illiterate) i looked in my home folder, viewed hidden files, found the torchlight folder, found localsettings.txt opened that up, found the line that read fullscreen:1 (or something of the sort), changed that to fullscreen:0 (hey i just learned 1=yes and 2=no! wait, is that right?) and tried to open the program again. this time i get a splashscreen for the game, then the same ?thing? going on in the center of my screen, my mouse turns to a gauntlet for a second, and i stop feeling like a genius.
help?

---

### Post by Sealbhach on 2012-09-19
I think it's 0=No and 1=Yes


.

---

### Post by almightyboz on 2012-09-19
same issue after clicking the fullscreen box, it runs some sliver of a window and my resolution goes insane. help needed

---

### Post by thatguruguy on 2012-09-20
Open the localsettings.txt file again, and make sure that the values for RES_WIDTH and RES_HEIGHT match an available screen resolution for your computer.  You can find out the resolutions available for your display driver by opening a terminal and typing the following:
```
xrandr
```

---

### Post by cmyers2215 on 2012-09-20
This worked for me.  Thanks for the advice. > **thatguruguy said:**
> Open the localsettings.txt file again, and make sure that the values for RES_WIDTH and RES_HEIGHT match an available screen resolution for your computer.  You can find out the resolutions available for your display driver by opening a terminal and typing the following:
```
xrandr
```

---

### Post by peter07 on 2012-09-20
> **thatguruguy said:**
> Open the localsettings.txt file again, and make sure that the values for RES_WIDTH and RES_HEIGHT match an available screen resolution for your computer.  You can find out the resolutions available for your display driver by opening a terminal and typing the following:
```
xrandr
```

I have similar problem:
xrandr =  1366x768

In localsettings.txt:
FULLSCREEN :0
WINDOW_WIDTH :1366
WINDOW_HEIGHT :768
RES_WIDTH :1366
RES_HEIGHT :768

But torchlight is still opened in window.
Any ideas?

---

### Post by thatguruguy on 2012-09-20
EDIT: Fullscreen:0 is the correct setting for fullscreen, but see my post [here]("http://ubuntuforums.org/showpost.php?p=12251114&postcount=12").

---

### Post by peter07 on 2012-09-20
> **thatguruguy said:**
> Change FULLSCREEN:0 to FULLSCREEN:1

I've changed this value, but game still runs in window. Only effect is that I cant move mouse outside window :/

---

### Post by pnarciso on 2012-09-20
Ubuntu Unity and compiz are very problematic with games. I've tried Torchlight with Ubuntu 12.04 and indeed it can't go fullscreen.

The game use SDL 2.0, which have a new window behavior that can cause issues with compositors.

It runs flawlessly with Xubuntu.

---

### Post by cmyers2215 on 2012-09-20
I had the same problem, but realized full screen wasn't going to work at this point in time.  Also for some reason when I changed full screen in the .txt it didn't keep the changes.  I had to uncheck full screen in the game itself.  I then turned down the resolution slightly in order for the window to fill in my screen. 

> **peter07 said:**
> I've changed this value, but game still runs in window. Only effect is that I cant move mouse outside window :/

---

### Post by SierraStop on 2012-09-20
> **cmyers2215 said:**
> I had the same problem, but realized full screen wasn't going to work at this point in time.  Also for some reason when I changed full screen in the .txt it didn't keep the changes.  I had to uncheck full screen in the game itself.  I then turned down the resolution slightly in order for the window to fill in my screen.

Yep - exact same problem here too. Resigned that I won't be able to rectify this anytime soon and I've been playing it in a window mode without any significant troubles.

---

### Post by thatguruguy on 2012-09-20
I run my games through my media center computer, which runs Mythbuntu.  However, the following may get this to work in Ubuntu running Unity:

1. Install CompizConfig Settings Manager (ccsm), if it's not already installed.  You can find it in the Ubuntu Software Center, or install it from the command line by opening a terminal and typing:
```
sudo apt-get install compizconfig-settings-manager
```2. Open ccsm and go to the area marked "Utility." Make sure "Workarounds" is checked (See the first screenshot below), and then click on the word "Workarounds".

3. In the new menu that opens, make sure that Legacy Fullscreen Support is checked (See the second screenshot below).

4. You may need to reboot, or at least log out and back in to your Unity session, for the change to take effect.

5. Try to set the Fullscreen:0 in the Torchlight config file, as described in earlier posts.

EDIT: I just installed torchlight on my computer running Unity, and I can confirm that this works.

---

### Post by lilkidz on 2012-09-20
> **thatguruguy said:**
> I run my games through my media center computer, which runs Mythbuntu.  However, the following may get this to work in Ubuntu running Unity:

1. Install CompizConfig Settings Manager (ccsm), if it's not already installed.  You can find it in the Ubuntu Software Center, or install it from the command line by opening a terminal and typing:
```
sudo apt-get install compizconfig-settings-manager
```2. Open ccsm and go to the area marked "Utility." Make sure "Workarounds" is checked (See the first screenshot below), and then click on the word "Workarounds".

3. In the new menu that opens, make sure that Legacy Fullscreen Support is checked (See the second screenshot below).

4. You may need to reboot, or at least log out and back in to your Unity session, for the change to take effect.

5. Try to set the Fullscreen:0 in the Torchlight config file, as described in earlier posts.

EDIT: I just installed torchlight on my computer running Unity, and I can confirm that this works.

I can confirm that this works for me; running Ubuntu 12.04 on Unity. Using Gnome Shell also worked for me without this.

---

### Post by thatguruguy on 2012-09-20
> **lilkidz said:**
> I can confirm that this works for me; running Ubuntu 12.04 on Unity. Using Gnome Shell also worked for me without this.

Gnome Shell doesn't use Compiz.

---

### Post by jjst on 2012-09-21
> **thatguruguy said:**
> I run my games through my media center computer, which runs Mythbuntu.  However, the following may get this to work in Ubuntu running Unity:

1. Install CompizConfig Settings Manager (ccsm), if it's not already installed.  You can find it in the Ubuntu Software Center, or install it from the command line by opening a terminal and typing:
```
sudo apt-get install compizconfig-settings-manager
```2. Open ccsm and go to the area marked "Utility." Make sure "Workarounds" is checked (See the first screenshot below), and then click on the word "Workarounds".

3. In the new menu that opens, make sure that Legacy Fullscreen Support is checked (See the second screenshot below).

4. You may need to reboot, or at least log out and back in to your Unity session, for the change to take effect.

5. Try to set the Fullscreen:0 in the Torchlight config file, as described in earlier posts.

EDIT: I just installed torchlight on my computer running Unity, and I can confirm that this works.

I just registered on the forum to aknowledge that this indeed works. I was facing the same problem described in this thread and tried fiddling around with the local_settings.txt file to no avail (well, at least it allowed me to change the resolution to a correct one because the values in there were silly). I then googled for a solution and found this thread, and yours seems to work like a charm. So kudos to you! Now back to some gaming at last :)

---

### Post by Slav3k on 2012-09-21
I have a question - where is localsettings.txt? I can't find it in ,,home", neither /usr/local/games :( I am using Nautilus and nothing have happened :/

---

### Post by thatguruguy on 2012-09-21
> **Slav3k said:**
> I have a question - where is localsettings.txt? I can't find it in ,,home", neither /usr/local/games :( I am using Nautilus and nothing have happened :/

First, make sure you can view hidden files in Nautilus.  You can do so by changing the entry under the "View" menu, or by clicking the "Ctrl" and the "H" keys together.

The localsettings.txt file is in the .runicgames/Torchlight folder in your home directory. It won't exist unless you've tried to open the game at least once.

---

### Post by zsorzs on 2012-09-22
Hi All,

I can confirm that turning on "Legacy Full screen" support solved my issue
Thank you

---

### Post by chrisinspace on 2012-09-22
> **peter07 said:**
> I have similar problem:
xrandr =  1366x768

In localsettings.txt:
FULLSCREEN :0
WINDOW_WIDTH :1366
WINDOW_HEIGHT :768
RES_WIDTH :1366
RES_HEIGHT :768

But torchlight is still opened in window.
Any ideas?

Adjusting these settings, along with the compizconfig-settings-manager, took care of my problem.  When I checked the config file, the WINDOW_WIDTH and WINDOW_HEIGHT did not match the RES_WIDTH and RES_HEIGHT.  I synced those up, then enabled the legacy fullscreen work-around and I'm all set.  I'm running Ubuntu 12.04 with an nVidia GPU.

---

### Post by nll on 2012-09-23
I got a weird bug here. I have checked the mentioned option in CCSM so Torchlight starts in fullscreen correctly, but when I click fullscreen on its options, the game goes to windowed mode. Unchecking it and rechecking it makes no difference. When I quit and run it again, the game is back at fullscreen mode. While it's in fullscreen, I can still use compiz shortcuts like ctrl+alt+arrow to change workspaces.

---

### Post by homerhomer on 2012-09-23
Try this!
Open ccsm ( In the software center I think it's called compiz config system manager. )
Open Workarounds 
enable Legacy Full screen Support
log out and then back in


* Huh also try, minimize the Torchlight window ( pressing crappy windows key ) and then open it again by clicking on it in the unity icon. 


Good Luck

---

### Post by whatthefunk on 2012-09-25
Having the same problem, but compunded in Kubuntu.  When I first opened the game, the resolution was all messed up, so I followed the advice in the README file and set the following:

export SDL_VIDEO_X11_XINERAMA=0
export SDL_VIDEO_X11_XRANDR=0

Now the game wont load at all.  I set both variables back to 1 (I think thats default...) but still no good.  I tried purging the game and reinstalling but no luck.  Because the game wont start, there is no localsettings.txt file.  Anybody have any idea about this??

---

### Post by thatguruguy on 2012-09-25
> **whatthefunk said:**
> Having the same problem, but compunded in Kubuntu.  When I first opened the game, the resolution was all messed up, so I followed the advice in the README file and set the following:

export SDL_VIDEO_X11_XINERAMA=0
export SDL_VIDEO_X11_XRANDR=0

Now the game wont load at all.  I set both variables back to 1 (I think thats default...) but still no good.  I tried purging the game and reinstalling but no luck.  Because the game wont start, there is no localsettings.txt file.  Anybody have any idea about this??

Are you using the latest version of the game, which was updated yesterday on the humblebundle site? The revisions were meant to fix the full-screen problem, by making illegal resolutions impossible.

Also, the statements "When I first opened the game, the resolution was all messed up" and "Because the game wont start, there is no localsettings.txt file" are contradictory. It's impossible for both statements to be true.

---

### Post by thatguruguy on 2012-09-25
> **homerhomer said:**
> Try this!
Open ccsm ( In the software center I think it's called compiz config system manager. )
Open Workarounds 
enable Legacy Full screen Support
log out and then back in


* Huh also try, minimize the Torchlight window ( pressing crappy windows key ) and then open it again by clicking on it in the unity icon. 


Good Luck

Was there something wrong with the instructions given [here]("http://ubuntuforums.org/showpost.php?p=12251114&postcount=12"), which were virtually the same?

---

### Post by whatthefunk on 2012-09-25
> **thatguruguy said:**
> Are you using the latest version of the game, which was updated yesterday on the humblebundle site? The revisions were meant to fix the full-screen problem, by making illegal resolutions impossible.

Also, the statements "When I first opened the game, the resolution was all messed up" and "Because the game wont start, there is no localsettings.txt file" are contradictory. It's impossible for both statements to be true.

I purged all the associated files and then the game wouldnt work again so there was no localsettings file.  Anyway, the new version of the game works in full screen.  Thanks!  Now if only the players had faces....

---

### Post by JDShu on 2012-09-25
Has anybody been able to get past floor 19?

---

### Post by thatguruguy on 2012-09-25
> **JDShu said:**
> Has anybody been able to get past floor 19?

That's where I left off today. I'll let you know tomorrow.

---

### Post by thatguruguy on 2012-09-25
> **whatthefunk said:**
> I purged all the associated files and then the game wouldnt work again so there was no localsettings file.  Anyway, the new version of the game works in full screen.  Thanks!  Now if only the players had faces....

Good to know that they actually fixed the full-screen bug as promised. They also fixed the problem causing the music not to play. Hopefully, the invisible face thing will be knocked out soon.

---

### Post by oldrocker99 on 2012-09-26
I am SO impressed by the rapidity of the Torchlight fixes. Now I have the great music along with everything else. This game is so much fun that I bought the Windows version 3 years ago and played it under wine with no sound at all (at the time).

Gaming on Linux is getting better and better and better.

---

### Post by Simeo on 2012-09-26
> **oldrocker99 said:**
> I am SO impressed by the rapidity of the Torchlight fixes.

Am I missing something? I just purchased this game from Humble Bundle a moment ago and I have no face on two of the characters and no full screen....

---

### Post by Dana88 on 2012-09-26
> **thatguruguy said:**
> Open the localsettings.txt file again, and make sure that the values for RES_WIDTH and RES_HEIGHT match an available screen resolution for your computer.  You can find out the resolutions available for your display driver by opening a terminal and typing the following:
```
xrandr
```

It's a bit embarassing, but I cant find the localsettings.txt with any kind of search. Not even if I search with Terminal. Anyone could help me with that?

---

### Post by thatguruguy on 2012-09-26
> **Simeo said:**
> Am I missing something? I just purchased this game from Humble Bundle a moment ago and I have no face on two of the characters and no full screen....

You're missing the following:

1. This thread tells you how to get fullscreen going, if you can't otherwise figure it out.
2. The missing faces thing is a known bug (it's included in the Humble Bundle FAQ for H.B. 6), and it's being worked on.

---

### Post by thatguruguy on 2012-09-26
> **Dana88 said:**
> It's a bit embarassing, but I cant find the localsettings.txt with any kind of search. Not even if I search with Terminal. Anyone could help me with that?

I gave instructions [here]("http://ubuntuforums.org/showpost.php?p=12252473&postcount=17").

---

### Post by Simeo on 2012-09-26
> **thatguruguy said:**
> You're missing the following:

1. This thread tells you how to get fullscreen going, if you can't otherwise figure it out.
2. The missing faces thing is a known bug (it's included in the Humble Bundle FAQ for H.B. 6), and it's being worked on.

Oh ok it's being worked on. I thought they said it was fixed by now. How do I make updates to Torchlight after having installed it? I don't need to reinstall each time do I?

---

### Post by thatguruguy on 2012-09-26
> **Simeo said:**
> Oh ok it's being worked on. I thought they said it was fixed by now. How do I make updates to Torchlight after having installed it? I don't need to reinstall each time do I?

If you installed it through the Ubuntu Software Center, you'll receive updates shortly after they're released.  If not, you'll need to reinstall it, but the reinstallation won't overwrite your settings and game progress.

---

### Post by oldrocker99 on 2012-09-26
I cannot help but be impressed by the Torchlight Linux team at the speedy and frequent updates. I have (no foolin') gotten father and deeper playing Linux Torchlight than I ever did playing the Windows version, which I played a LOT.:)

---

