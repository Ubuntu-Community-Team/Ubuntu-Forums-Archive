---
title: "Black screen blinking randomly"
date: 2009-01-19
forum: General Help
---

### Post by onlineapps on 2009-01-19
This is a really bizarre thing. Randomly today, the screen (a brand new Acer LCD) just started blinking. As in, it would blank out for five seconds at a time, just showing blackness. Nothing like this happened in Vista. I tried a Ctrl-Alt-Backspace, a reboot, and nothing worked. I disabled Compiz Fusion, closed Firefox, uninstalled Flash, reinstalled my Firefox profile... nothing fixes it. Dropping to a tty seems to work, but I can't be 100% sure since it's intermittent. And it's randomly intermittent. Like, a minute ago, it blinked three times in 30 seconds. Now, it's not blinking at all. Never mind, I just maximized the window and it started again. Oh yeah, that's the other thing... it seems to happen more often when the focused window is maximized, but that's not ALWAYS the case (it just did it again, unmaximized!).

Things I've tried (will be updated)

[LIST]
[*]Ctrl-Alt-Backspace
[*]Reboot
[*]Disabled Compiz Fusion
[*]Uninstalled Flash
[*]Reinstalled Firefox + Profile
[*]Used Epiphany instead
[*]Used a new kernel
[*]Used Vista
[*]Alt-tabbing out of window (seems to temporarily fix the problem)
[/LIST]

I've had Ubuntu on this machine for two weeks now, and it hasn't ever acted like this. I haven't noticed it in Vista, so I don't think it's a monitor issue (though if someone could point me to a monitor calibration tool, that would be great).

You can keep typing while it's blanked, but I'm not certain about the mouse. I DO know that my Workrave timer pauses when it blinks, and unpauses when it goes back.

I'm using a brand new Nvidia GeForce 9800GT with restricted drivers. The monitor is an Acer, 20" widescreen, at 1680x1050.

---

### Post by onlineapps on 2009-01-19
Yeah, I can confirm Vista doesn't have this.

Never mind, it happened on Vista :(

---

### Post by hubie on 2009-01-20
Did you do just install a bunch of updates?  I had this problem a while ago, except that mine would only black-out for about a half-second.  It gets very annoying.  It seems to happen whenever something is happening graphically on the screen, such as a web page loading, or the mouse moving around.  When nothing is happening on the screen, there doesn't seem to be an issue.

Anyway, I was having this problem, then I applied some updates and the issue went away.  Today I applied a bunch of updates and the problem is back.  My xorg.conf file does not appear to have changed.  It is almost as if the wrong monitor settings (such as refresh) have been changed or overwritten, but I cannot seem to see what might have changed.

---

### Post by onlineapps on 2009-01-20
I dunno... I basically install updates every day :/

---

### Post by onlineapps on 2009-01-20
OK, now it just happened twice in Vista. Hasn't happened since or again (much less common than on Ubuntu). Anyone have a good monitor checking tool (Linux or Windows)?

---

### Post by onlineapps on 2009-01-20
Now I'm not even sure what it is. I booted into another kernel, and it still happens. It seems to happen the most while I'm in Firefox (on some pages more than others), and alt-tabbing out of the window seemed to fix it, so I thought it was a software issue. But now it happened on Vista!

EDIT: It hasn't happened in a day on Vista, though...

---

### Post by hubie on 2009-01-21
Darn, that doesn't sound like my problem.  Many things were updated recently for me, most notably a lot of xorg stuff.  My screen seems like it is just on the verge of losing vertical sync, and it flickers black.  It seems like it is related to any changes on the screen because the flickering dies down if I'm not doing anything.

I guess I'll have to start a new thread.

Good luck with your problem (maybe your cables aren't screwed in tight?).

---

### Post by onlineapps on 2009-01-21
Actually... don't start a new one yet, because that sounds like mine. Except maybe the vertical sync.

---

### Post by hubie on 2009-01-21
I think I just fixed it.  It was one of those things I should have thought of first, but didn't think to do until I saw it while Google-ing around.

I did a 
```
sudo dpkg-reconfigure xserver-xorg
```
and I took all the defaults.  I then went into ctrl-alt-F1 and restarted gdm and now I don't have any flickering.

I'll wait to declare success after about an hour or so, but it looks good for now.

---

### Post by onlineapps on 2009-01-21
Oh gosh. Why did I not think of that?

*reboots into Linux to test it out*

---

### Post by onlineapps on 2009-01-21
Used it for like fifteen minutes... no black screen!

Guess I'm gonna have to tell NewEgg I won't be using that RMA they just emailed me... :p

**Edit:** Darn. I just opened OpenOffice, and got the dreaded black screen. I think maybe it's tied to OO.o... :-/

---

### Post by onlineapps on 2009-01-21
OK, it's basically gone away, but it still comes back occasionally. Weird...

---

### Post by onlineapps on 2009-01-21
Here's something interesting. When visiting a site like [http://www.nwc.navy.mil/](http://www.nwc.navy.mil/), most of the time when I hit the next button in the slideshow (or when it cycles to the next one), it gives the black screen. It's not  a Flash problem (I uninstalled it and no fix, remember?), but it's an interesting symptom.

---

### Post by onlineapps on 2009-01-21
I feel stupid. I jiggled the monitor cord, and I haven't had the problem in half an hour. *sigh*

---

### Post by hubie on 2009-01-21
I'm glad it worked out for you and it was an easy fix.

I'm also glad you started this thread because it helped kick me in gear to finally figure out how to fix my own problem.

---

