---
title: "Feisty desktop frustratingly slow"
date: 2007-05-14
forum: Desktop Environments
---

### Post by tlau on 2007-05-14
I upgraded from Edgy to Feisty a few weeks ago and since then have been suffering from a frustratingly slow desktop experience.  When I move the mouse from one window to another (I use focus-follows-mouse) it often takes *seconds* for the focus to shift, and for the new window to gain input focus.  It used to be that I could start typing as soon as the mouse pointer entered the other window; now I have to wait for the titlebar to change color so that I know that my keystrokes will go into the desired window.

Firefox is also extremely sluggish.  Sometimes, when I type characters into the Location bar, it will be 5-6 seconds before they appear.  As another example, when I go to cnn.com, Firefox displays a banner at the top of the page saying that it prevented the site from opening a popup window.  This banner takes about 5 seconds to draw.  As I watch, that bar progressively comes into view, a few pixels at a time.  I can see it draw the pixels row by row.  Changing tabs in Firefox can often take a couple seconds, during which the entire browser is unresponsive.

When I deiconify Thunderbird, it takes three seconds to fully appear.  I run Thunderbird full-size in a 1600x1200 monitor.  The folder view appears first, followed shortly by the message list view, followed by the message preview pane.  Finally, after another little pause, the metacity titlebar is painted on the top of the window.

My graphics card is an nvidia:
01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro4 NVS AGP 8x] (rev a2)

I'm using Twinview to configure two monitors in a dual-head configuration side by side.  Each monitor is 1600x1200.  The same hardware was much more responsive in Edgy.  I tried backing up xorg.conf and regenerating it with "dpkg -reconfigure xserver-xorg", but that didn't help.  I also tried switching to the free "nv" driver, but that didn't help either.  I tried switching from metacity to fvwm (which I used for years), but it's even slow with fvwm.

The slowness seems to get worse over time.  After restarting the xserver, things are relatively zippy again (though they still feel slower than Edgy), but after a couple days, things degrade and become quite unusable.

This is driving me nuts.  And I don't know how to start searching for the root cause.  Any ideas?

---

### Post by mssever on 2007-05-14
> **tlau said:**
> I upgraded from Edgy to Feisty a few weeks ago and since then have been suffering from a frustratingly slow desktop experience.  When I move the mouse from one window to another (I use focus-follows-mouse) it often takes *seconds* for the focus to shift, and for the new window to gain input focus.  It used to be that I could start typing as soon as the mouse pointer entered the other window; now I have to wait for the titlebar to change color so that I know that my keystrokes will go into the desired window.

Firefox is also extremely sluggish.  Sometimes, when I type characters into the Location bar, it will be 5-6 seconds before they appear.  As another example, when I go to cnn.com, Firefox displays a banner at the top of the page saying that it prevented the site from opening a popup window.  This banner takes about 5 seconds to draw.  As I watch, that bar progressively comes into view, a few pixels at a time.  I can see it draw the pixels row by row.  Changing tabs in Firefox can often take a couple seconds, during which the entire browser is unresponsive.

When I deiconify Thunderbird, it takes three seconds to fully appear.  I run Thunderbird full-size in a 1600x1200 monitor.  The folder view appears first, followed shortly by the message list view, followed by the message preview pane.  Finally, after another little pause, the metacity titlebar is painted on the top of the window.

My graphics card is an nvidia:
01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro4 NVS AGP 8x] (rev a2)

I'm using Twinview to configure two monitors in a dual-head configuration side by side.  Each monitor is 1600x1200.  The same hardware was much more responsive in Edgy.  I tried backing up xorg.conf and regenerating it with "dpkg -reconfigure xserver-xorg", but that didn't help.  I also tried switching to the free "nv" driver, but that didn't help either.  I tried switching from metacity to fvwm (which I used for years), but it's even slow with fvwm.

The slowness seems to get worse over time.  After restarting the xserver, things are relatively zippy again (though they still feel slower than Edgy), but after a couple days, things degrade and become quite unusable.

This is driving me nuts.  And I don't know how to start searching for the root cause.  Any ideas?
It's entirely possible that the problem is with X or your video drivers, but those symptoms could also be the result of memory problems. Have you checked the status of your memory (both RAM and swap)?

---

### Post by tgalati4 on 2007-05-15
Try a Dapper Live CD and see if it works any better.

---

### Post by Visceral Monkey on 2007-05-15
This is interesting. I'm having similar problems with my system. I noticed it did not occur until after I installed the 3d drivers. My card is an Nvidia 8800. My problems are not as pronounced as yours, but I do notice similar things: slow downs, horrible browser performance, tearing, etc. I've tried some other distros and don't have this problem, nor did I have it before Feisty. Performance does seem to get worse after more time goes on as well.

---

### Post by tlau on 2007-05-15
Thanks for the responses.  This system has 3G RAM and a 4G swap partition (which is enabled).

I booted into a Dapper Live CD this morning and have been working with it all day.  Performance is more responsive than the Feisty install.  Switching window focus occurs almost instantaneously.  Typing into Firefox and scrolling web pages seems reasonable.

In Feisty, I tried creating a new user and logging in as that user (thereby starting with a fresh profile).  It gave me the same sluggish performance.

Any other ideas?

---

### Post by Takis on 2007-05-15
Not sure if mine's the same problem but I've definitely been sluggish since moving to Feisty. Nowhere near as bad as yours, but infinitely more pronounced as more windows are opened. If I have more than 2 or 3 Firefox windows open (I'm not a fan of tabs, I must admit) then it takes a good second while alt-tabbing between them, and even scrolling is laggy. Like you, though, I'm running Twinview and like Visceral Monkey I have an 8800. Plenty of RAM to spare, the CPU is quiet (i.e. not busy), and applications like UT2004 (at max settings) run full speed. (*iacknowledgethatthisisnotabenchmark*) GLXGears runs about 17,000 FPS. I don't even know what I should be looking at, but I'm guessing it's something to do with the window manager (KDE in my case).

---

### Post by walmartshopper67 on 2007-05-15
I'm having the same thing here - and it's getting old fast, no pun intended. I'm seeing a ton of posts around here with the same symptoms ( performance degrades over time, high cpu usage for small tasks, high xorg usage, etc.) but I haven't seen very many solutions. 

I realize this is Linux, it's community and volunteer supported, but the OS is almost unusable in this state. I switched to Linux to get away from the instability - and now i'm getting a performance degradation over time, the same kind of ethereal error nonsense I got with windows, and nobody has an answer.

Now, I love Linux, and I like Ubuntu - so over the next couple weeks (its finals week here at RIT so bear with me) I'll be installing some monitoring / performance logging stuff (probably cacti and sar , maybe some others I run across) which should show what exactly is happening. I'll pass along anything i find (if anything) on here, anywhere I else I should send it? 

If anyone has any other ideas, by all means, post them. This is ridiculous.

---

### Post by Visceral Monkey on 2007-05-15
Yea, at this point I'm just orbiting my Ubuntu partition in windows because it's too painful to use Ubuntu :( 

If anyone has the same problem or suggestions, please post here. I'm almost positive it's something to do with Ubuntu itself because none of the other linux distros I try out have the same issue.

---

### Post by Peacez on 2007-05-15
cannot solve this problem..it happen to me :(

---

### Post by BLTicklemonster on 2007-05-16
... but according to some people in this thread: 
[http://ubuntuforums.org/showthread.php?t=431325](http://ubuntuforums.org/showthread.php?t=431325)
ubuntu isn't slow at all!

(you might want to share over there. someone might be able to help. just point them to this thread instead of hijacking that thread, mkay?)

---

### Post by Visceral Monkey on 2007-05-16
I'm wondering if it's related to this thread:

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

The problems are similar, if not different in scope. Several people said reverting to a previous kernel fixed their problems with the freeze, maybe it would do the same in our situation? Anyone care to try? My Ubuntu partition is currently gone.

---

### Post by mills on 2007-05-16
> **Visceral Monkey said:**
> I'm wondering if it's related to this thread:

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

The problems are similar, if not different in scope. Several people said reverting to a previous kernel fixed their problems with the freeze, maybe it would do the same in our situation? Anyone care to try? My Ubuntu partition is currently gone.

seems like two different problems to me, that post your linking to is about sudden freezes and this is about slow performance degradation,

but i dont see any harm in trying a new kernel, you can easily revert if its not the solution

---

### Post by Takis on 2007-05-18
> **BLTicklemonster said:**
> ubuntu isn't slow at all!
It's not that Ubuntu's slow, it's something in X that's slow for me. Window decorations? I dunno. I'll think maybe it's that, as the applications tend to blitz themselves, but then again, something like simply scrolling in Firefox, which has nothing to do with decorations, is laggy.  :cry:

---

### Post by synthetic_fenix on 2007-05-23
I am having a lot of these same issues with Feisty installed on my laptop. Ran Great with Dapper but since I have switched it just degrades over time. The system has a 2.8Ghz P4-M with 1Gb of Memory and a 64Mb Intel Extreme Graphics 855 Chipset. The Video is natively supported by Linux and X and I have never had to load up drivers. When I ran Dapper, I was able to run a VM of Windows XP with 256Mb of ram set for it, have Gaim, GKrellm, Firefox, and Evolution up and running and everything would be responsive. But I do all that in Feisty and it becomes painfully slow and I dont even have any of the desktop enhancements turned on.

---

### Post by Takis on 2007-05-28
Hey Visceral Monkey, would you say your problem's like [this one]("http://www.nvnews.net/vbulletin/showthread.php?t=87865")? Any one else in this thread have an 8800?

---

### Post by tlau on 2007-06-06
I have an nvidia Quadro4 at work, and an nvidia GeForce 6200 at home (I see the problem with both desktops, both running Feisty).  I also think that the problem might be related to the X server.  I've seen X grow to 500MB virtual usage, at which point I generally have to kill it.

Another symptom of slowness is that clicking on links in Thunderbird, to open them in Firefox, takes longer over time.  Right after restarting X, it takes a second or two before the new tab comes up in Firefox.  After the system's been up for a few days, this can take up to several minutes; sometimes the link never shows up in Firefox.  If it doesn't show up after waiting for a few minutes, I have to manually copy and paste the link into the browser.

---

### Post by tlau on 2007-06-14
Following the advice in this bugreport ([https://bugs.beta.launchpad.net/ubuntu/+source/xorg/+bug/77606](https://bugs.beta.launchpad.net/ubuntu/+source/xorg/+bug/77606)), I disabled the flash plugin and desktop performance has improved drastically.  Does this work for anyone else too?

```
apt-get remove flashplugin-nonfree
```

The bug trackers seem to indicate that a fix has been checked in and uploaded to the feisty repository, but I'm confused by the package names.  I have xserver-xorg 7.2-0ubuntu11, but they're saying that the fix was checked in to package xorg-server 2:1.2.0-3ubuntu4.  That package doesn't seem to be available for installation on my system.

---

### Post by tlau on 2007-07-04
My desktop is still slow ... the flash plugin removal didn't really help anything.  Another symptom I've noticed is that eventually I'll get an error when starting new Mozilla applications:

The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was '169'.
  (Details: serial 771 error_code 169 request_code 3 minor_code 10)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I can't start firefox or thunderbird again until after I restart my X server.  Anyone else see this problem too?

---

### Post by fjgaude on 2007-07-04
> **tlau said:**
> My desktop is still slow ... the flash plugin removal didn't really help anything.  Another symptom I've noticed is that eventually I'll get an error when starting new Mozilla applications:

I can't start firefox or thunderbird again until after I restart my X server.  Anyone else see this problem too?

I've got three computers here running Feisty and do not have any trouble with speed or crashing, memory or what ever.

Could it be some programs installed that X doesn't like. The memory issue should be a tip. Try using top to see where all the memory is going. Either top or htop will show memory and cpu usage by application.

frank

---

### Post by truthsifter on 2008-03-31
try removing the package xserver-xgl.  When I upgraded to gutsy, I had the same issue.  Removing that package sped my system back up.

---

