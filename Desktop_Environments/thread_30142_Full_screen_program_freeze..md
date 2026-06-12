---
title: "Full screen program freeze."
date: 2005-04-27
forum: Desktop Environments
---

### Post by blaine00 on 2005-04-27
Sorry if this is a stupid question... but I have a problem with Totem, (and sometimes other programs) going full screen and freezing (blank black screen). I'm wondering if their is a key combination or something I could press to kill the frozen program so I can get back to the desktop without having to reboot. 

Thanks a lot!

---

### Post by wulf on 2005-04-27
Three questions:

1) How often?

2) Does the keyboard still appear to be working (eg. can you turn the CAPS LOCK light on and off)?

3) I'm a bit confused by your description - if the apps are automatically maximising, how do you know the background is going black?

Wulf

---

### Post by heimo on 2005-04-27
If ESC doesn't work, you can try to switch to console ctrl+alt+F1, log in and type
 ```
killall totem
```  That should kill totem and you can type  *exit* or simply press ctrl+d and go back to X using ctrl+alt+F7.

If this method doesn't work, you can try to kill X using ctrl+alt+backspace.

Oh. I'm not sure, but when the program has freezed, you can try alt+tab to switch to another window. (Hmm.. just tried it. I had vlc running, playing video fullscreen, I did alt+tab and everything went crazy, had to go to console to kill... )

If you don't know the name of the program, you can run *top *in console, press P to sort processes according to CPU usage, press k to start killing and type in the PID.

Hopefully this helps.

PS. Of course you should get the root of the problem fixed. Maybe a bad graphics driver. (BTW, try vlc someday)

---

### Post by davegahan on 2005-04-27
I had exactly the same problem with totem. Totem itself showed a blue screen, and the whole ubuntu system froze. Removing and reinstalling totem did not help.
I decided to use xine instead.  I posted an earlier l&#305;nk about the issue and some friendly people of the development team asked me to report it in bugzilla. However, next day upon reboot GNOME would not load. It got stuck somewhere loading windows metacity manager.... 
So it seems there is NO solution yet for that problem, and it seems to be a nasty bug within totem. Go to my earlier post [http://ubuntuforums.org/showthread.php?t=26460](http://ubuntuforums.org/showthread.php?t=26460) 
and report the issue in Bugzilla.

Good luck, after I got that crash in Totem my whole system went crashing down and now considering a reinstall.... see my other posts.

---

### Post by blaine00 on 2005-04-27
To Wulf:
1)Recently, it's been happening fairly often.
2)I didn't check to see if the caps lock light would turn on and off... next time I have the problem I'll check.
3)Well, it isn't the background going black, it is the entire screen.

The reason I am asking about key combinations and stuff is because in the past, I had full screen programs(Tux Racer) freeze up because of video issues and I had no idea how to get out of it (I'm no good at navigating through an invisible gui). I don't have the problem with Tux Racer anymore (new distro and new computer since then), but I was wondering for future reference.

heimo:
Okay, I'll try all that to see if it helps. I did try alt+tab, no luck. I do plan on trying a different video player... like Mplayer or something.

Thanks for all the help everyone! I'll be sure to let you know how it worked. The more things I am able to do without booting to Windows the happier I am!

---

### Post by wulf on 2005-04-28
1) There's a good chance that you'll get a chance to test any ideas out soon then! ;)

2) If you know the keyboard is working, then key combinations might help (as per Heimo's post); if not, then the computer probably won't even know you typed them and a physical reset is the only option.

3) The whole screen going black sounds like a problem with the video system. Log files might help, although I've not been using Hoary long enough to figure out where X.Org keeps its records.

Wulf

---

### Post by blaine00 on 2005-04-28
Now, for the most part, that problem is gone... though my brother said he recently got on and meet with this "black screen of oblivion"... the only problem I have now is videos running a bit choppy... hopefully getting a different video player will fix that.

It's always a bit scary when problems... fix theirself over time... for some reason Ubuntu has been acting a bit random at times. One example of a random event would be my mounted partitions appearing on my desktop. I have a FAT32 Windows XP partition and a FAT32 general storage partition and every now and then they appear on my desktop and every now and then they don't... of course this isn't a problem at all... I don't mind going to /media to get to the partitions, I just think it's a bit funny.  :grin:

---

### Post by blaine00 on 2005-04-28
Okay, it happened again just now... and no, the keyboard was not responding. I pressed the capslock key and nothing happened. I guess the whole system crashes... which would make key combinations kinda useless...

---

### Post by wulf on 2005-04-29
That means you have to escalate to the next stage of troubleshooting - looking through the log files for evidence of problems - */var/log/Xorg.0.log* and perhaps some of the other files in that directory. Unfortunately, I can't help much more than that but there might be someone else who can tell you how to proceed.

Wulf

---

### Post by heimo on 2005-04-29
blaine: If you have anything overclocked on that computer, undo it. And check the logs, as was suggested. /var/log/messages is one of those. Or you could for example run the player from terminal and redirect output to file,

IIRC:
 ```
nohup totem & exit
``` 
will put output to nohup.txt. Then you can crash the program, reboot and go back to terminal and *less nohup.txt *for at least some information. To go further, you could run some deeper debugging, trace perhaps (but I'm not correct person to give advice on that - it's easy to run and less easy to analyze).

---

