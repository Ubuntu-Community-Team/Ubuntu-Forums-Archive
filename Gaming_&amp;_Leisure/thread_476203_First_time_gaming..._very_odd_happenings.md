---
title: "First time gaming... very odd happenings"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by copcar on 2007-06-17
Hey guys I'm very new here but I've lurked for a long time.  Thanks to searching these forums I was able to make the switch from windows without too much heartache.  Now I'm getting into games...

Here's my problem, thanks to you guys I got UT04 to install.  Then I patched it and everything but something is horribly wrong with the game.  It starts up  but runs at around one frame every 5 seconds =/

I know this PC can run UT fine because it did when I ran windows.  I did many searches but no one else seems to have this problem.  I checked and all my drivers are up to date.  I have no idea what to do now so I'm asking you guys for help.  If anyone has any idea why this would happen please let me know.

Some info on my PC:
AMD 2000+
1gig ram
GeforceFX 5200

---

### Post by jasmuz on 2007-06-17
Is accelerated rendering on?
Check that with glxinfo

Did you try the Envy package, wich does the dirty work of installing proper drivers for Nvidia and ATI?

---

### Post by johnny4north on 2007-06-17
"Some info on my PC:
AMD 2000+
1gig ram
GeforceFX 5200"

my sys= P4 2000mhz 512mb ram Nvidia 4000mx 128mb plays ut2003 very well, you need to check your video card drivers, then take a look at this - [http://www.ataricommunity.com/forums/showthread.php?s=&threadid=357981](http://www.ataricommunity.com/forums/showthread.php?s=&threadid=357981) use this how-to get better fps.:)

---

### Post by Cappy on 2007-06-17
Goto (System-->Administration-->Restricted Drivers Manager) click the check box, let it work, reboot. Also make sure when you run UT you have any kind of Desktop CPU monitoring tools like gdesklets off or the game will lag. Same goes for Beryl/Compiz if you have enabled those.

---

### Post by slimdog360 on 2007-06-17
you may be interested in this [http://ubuntuforums.org/showthread.php?t=472743]("http://ubuntuforums.org/showthread.php?t=472743")

---

### Post by sloggerkhan on 2007-06-17
You might not have the fglrx driver setup correctly. Make sure your xorg.conf has:
```

Section "Extensions"
  Option "Composite" "Disable"
EndSection

```

---

