---
title: "Jaunty Headless Does Not Start Session"
date: 2009-05-27
forum: General Help
---

### Post by threadhead on 2009-05-27
My Jaunty box is running great, with the screen attached. But I need to run it without a screen and keyboard. It is setup to automatically login a user at boot, then I can VNC into it to run apps as I need.

But, if I disconnect the monitor to run it headless, I can no longer VNC into it. I'm assuming that the login session is not starting properly. The only applicable error I can find is from /var/log/Xorg.0.log:

```
Fatal server error:
no screens found

```

How can I get this box to startup and run the automatic login session with no screen or keyboard attached?

---

### Post by timcredible on 2009-05-27
can you access it with xdmcp?  sounds like it's not loading vnc, but xdm would load before vnc, so maybe try that.  if you're using a linux or unix machine as your workstation, just choose to connect to another box at the login screen, or use xNest if you want to do it as a window.  if you're using windows, use xming.

---

### Post by Bender2k14 on 2009-05-27
Why not just ssh with the -X option instead of VNC?

---

### Post by threadhead on 2009-05-27
I really need to have a full user session established. I need to run a couple of vm apps that require that I see the vm windows (data monitoring tools). I tried VNC'ing into them, but they freeze every so often and need to be restarted (ain't xp grand). So those vm's need to start at session login.

I really like using just VNC because I have to VNC into other machines. One tool, multiple windows, easier to manage.

Plus, I just like having the ubuntu session. It makes some tasks much easier.

I have not tried XDMCP. But correct me if I'm wrong, but that will instantiate a new session at each login, and kill it on logout? I need the session to persist.

I know this can be done, because I have it working on my hardy (desktop) box. But the configuration for that has changed since jaunty (at least what I have read).

---

### Post by infinityPlusOne on 2009-06-07
I have the same problem.  I would like to run Jaunty DESKTOP headless, however booting up without a monitor attached prevents Ubuntu from presenting the normal login screen.  Instead after plugging the monitor back in you are presented with a "Running in low-graphics mode" message.

I found [this]("http://ubuntuforums.org/showthread.php?t=618965") thread and tried to follow what others suggested by entering:

```
sudo dpkg-reconfigure xserver-xorg
``` 

but was not prompted to auto-detect monitor or mouse... only keyboard.  I suspect that this might have worked on Feisty (which was what the poster in that link was running) but has since been changed with Jaunty.

The discouraging thing I found in many threads that have to do with this problem is that most people just reply saying "duh! You can't run Desktop headless, use Ubuntu SERVER!".

I'm a normally a Windows user but do enjoy using Ubuntu.  Hopefully I can get this working with some help.  Any takers?

---

### Post by arnoldus on 2009-08-07
Have any of you found a solution? Same situation.

---

### Post by infinityPlusOne on 2009-08-07
Actually, because I was in a hurry to get it implemented, I ended up trying Ubuntu Server and am currently running it headless.

I did however buy a VGA connector but never got around to buying the correct resistors in order to make a vga dummy connector as others have done.  

If you're still wanting to run ubuntu desktop headless, you might want to look into it a bit more.  Try something like [this]("http://forums.techpowerup.com/showthread.php?t=86507").

Good luck.

---

### Post by Vitani on 2009-08-25
Same problem here, I've installed Mythbuntu (backend only) and want to run it headless, but run into the same issue when no monitor is connected. Annoying to say the least!

---

### Post by slamhound on 2009-08-25
I've been following a few threads related to this, but I haven't seen a good solution.  I would have been willing to run without booting into a gdm, but suspend never worked correctly without it, so I gave up on that.  The solution I came up with is related to the use of resistors to fool the computer into thinking it's plugged into a monitor. I had an old video card lying around and I thought that perhaps if I plugged the video cable from my headless box into the video card (which is not attached to anything) it would serve the same purpose.  And it worked.  The computer boots up correctly, as it thinks that it is attached to a monitor that is turned off.

So if you have any old hardware with a vga connector (video card, desktop, broken monitor), I think it should work.

---

### Post by john_spiral on 2009-09-08
the only cr@ppy work around I've found is:

to boot the beast with the monitor/keyboard/mouse attached. Remove them, and VNC into the beast from say XP. 


Not the best solution, as it breaks when you shutdown the machine.

---

### Post by P4man on 2009-09-08
Have a look here:

[http://ubuntuforums.org/showthread.php?t=618965](http://ubuntuforums.org/showthread.php?t=618965)

---

