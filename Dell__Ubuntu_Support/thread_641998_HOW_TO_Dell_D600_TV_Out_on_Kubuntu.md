---
title: "HOW TO: Dell D600 TV Out on Kubuntu"
date: 2007-12-16
forum: Dell  Ubuntu Support
---

### Post by sigma_solutions on 2007-12-16
Hi All 

This is my first how-to but I saw alot of people battling on this subject and finally figured it out with the help of the guys at the Kubuntu IRC room.

Machines this has been tested on -
Dell D600 with ATI Mobility Radeon 9000

This How-To assumes that you are using Kubuntu 7.10 and have the opensource ati driver installed.

** Step 1: Edit the Xorg.conf DEVICE Section**

Add the following code to it -

Code:
Option "TVDACLoadDetect" "TRUE"

Ensure the "ati" driver is in use

**Step 2: Install Kommander**

Located in Ubuntu Repository 

**Step 3: Run the Following in Konsole**

Code:
xrandr --addmode S-video 800x600 

**Step 4: Use Dell TV Switch App (Attached in Zip file) to Enable S-Video**

In the App make sure you set both the LCD (LPMS) resolution and the svideo to 800x600 before clicking apply

Ensure that LCD is De-Activated after Switching - If you don't it won't play movies on the TV

The App is Self-Explanatory.

All credit for the app go to the developers of it from kde-apps.org

Use this at your own risk.

Let me know if it worked for you.

**NOTES:**
Cable must be connected to your TV prior to booting into Kubuntu.
You must have the TV on the AV channel prior to switching otherwise the display will become obscured
***** YOU MUST RUN THE LAST TWO STEPS EACH TIME YOU WANT TO ENABLE THE TV OUT, IF YOU DON'T IT WILL FAIL**

---

### Post by vussvillem on 2008-01-24
How can I "use  Use Dell TV Switch App"
What will I have to do?

---

### Post by vussvillem on 2008-01-24
Ok, I believe I've figured it out already. I had to run kommander and open this app with kommander and run this app. I did not see anywere a word LCD nor (LPMS). I saw two screens. I guessed that first screen is my laptops, I don't know if i was right on that. I was already on the way of guesses, so I tried if I set first screen LVDS and resolution 640X480 and the second screen svideo 640X480 and clicked your mentioned but not specified how to get there "apply". 

I got a picture on my TV screen. However, when I opened video with Totem or MPlayer, they put up an error message saying something like "cant find/execute video out -vo" or something like that and I could hear the audio from my tv and I saw a picture on both of my laprop and TV screen but there was no video seen on Totem nor MPlayer window. I have been searching for TV-out solution for about a week now, so I know there is some things that should be changed for MPlayer..... although I can't really understand why so simple thing such as TV-out that is so simple in Windows, for a REASON, is so frustratingly complicated in Ubuntu, making Ubuntu to fail against Windows big time.

However,** how can I change my screens resolution back with that app and kommander piece of software?!?!** I did a restart and I still have got 640X480 resolution right now when I'm typing!

---

### Post by vussvillem on 2008-01-24
Another addition to your "how-to". I figured out that this "app" had created another  xorg.conf file in /etc/X11 I just got my original resolution back by deleting the new xorg.conf and renaming backup xorg.conf~ to original xorg.conf.

So, my week of searching the solution for tv-out will continue because Windows still beats Ubuntu big time.

---

### Post by vussvillem on 2008-01-26
After trying this [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout) without success I find your way the way I ALMOST managed to TVout.

So, can you or someone else please explain me what exactly do you mean by open sourse drivers and can you please give me a simple how to install and configure or enable them?

I guess it's because I tried this how-to of wiki ( [http://wiki.cchtml.com/index.php/Tvou](http://wiki.cchtml.com/index.php/Tvou)) but now I get an error message:
vussvillem@vussvillem-laptop:~$ xrandr --addmode S-video 800x600 
xrandr: cannot find output "S-video"

---

### Post by vussvillem on 2008-02-10
I would like to apologize for being such a dumbass. Could some admin, please, erase my previous posts, they're just trash and can get other how-to readers disorientated or confused.

I've got it working on my Dell D600 with ATI Mobility Radeon 9000 exactly as sigma_solutions described after I've figured out how to "use app" and when I exactly followed the NOTES part of the how-to (this is important!)

By the way, I'm using Ubuntu, so this how-to works for Gnome desktop as equally well.

So, sigma:solutions thank you!

---

