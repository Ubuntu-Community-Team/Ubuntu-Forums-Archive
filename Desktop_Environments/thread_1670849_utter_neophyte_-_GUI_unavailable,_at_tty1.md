---
title: "utter neophyte - GUI unavailable, at tty1"
date: 2011-01-19
forum: Desktop Environments
---

### Post by Jmob on 2011-01-19
Okay, so forgive me if this is posted; I'm new enough that I'm not even clear on the best keywords to use, and so far I've turned up nothing.

Here's where I am, figure I'll learn something here.

Completely new to Linux.  Used an Ubuntu (10.10) LiveCD on a Lenovo T500 to clone a harddrive onto a larger one.  Was intrigued, used Wubi, and installed on new hard drive.

Trying to get scrolling working, did a change on this page:

[http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html](http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html)

then told to restart X.  Little web searching turns up this:

[http://ubuntuforums.org/showthread.php?p=9854296](http://ubuntuforums.org/showthread.php?p=9854296)  (it's the beta, yes)

Anyway, GUI drops, goes to input screen w/o command line prompt.  Sits a bit, I kill the power, perhaps a bit prematurely.   Not sure.  

Now boots up to tty1, will log in, but gui nowhere to be found.  Tried a few things, but with no success--I'm old enough to be familiar with command line parsers and switches, but I don't know enough to really diagnose this or quite be aware of what I'm doing.

Tried "sudo gdm start" <-- returns that 
Tried "sudo service gdm start"  <--returns that gdm is already running

Tried "sudo X" <--returns a fatal error: no display
Tried "sudo X -configure" runs through process, but doesn't seem to make any meaningful changes

Would show actual text displayed if I could, but I'm cycling between ubuntu and my win7 boot, and don't know how to dump the text to a file.

I'm not just looking to have my hand held here; it would be great if someone could let me know what to do, but if I could be pointed somewhere to figure it out, that would be fine too.  Best thing would, of course, be a quick fix and then some direction, so I can stop being ignorant more quickly.

Thanks for your time.

---

### Post by Jmob on 2011-01-19
I did try and run X -config referencing the xorg.config.new file, which brings up a black screen.  I was only able to leave with the power button (not a hard kill, just pressed it).

---

### Post by Jmob on 2011-01-19
Okay, so now I'm thinking I had identified the incorrect thing as the problem.  I was able to restart X using the dialogue box in recovery mode--that got things going again.  I think it was some conflict with the video card (updating to the non-free AMD driver), as I had deleted the trackpoint configuration file for GNOME I'd made before.  Once the and then did the process over again with no issue.  

Just in case someone wants to still help me learn--how would I have restarted X without the dialogue?

---

