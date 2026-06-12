---
title: "Dell Inspiron 1420 with Ubuntu - Does not Suspend/Resume"
date: 2008-04-01
forum: Dell  Ubuntu Support
---

### Post by aidave on 2008-04-01
Hi, I just got an Inspiron Dell 1420!  Im pretty happy with it but there are a couple issues, this being the biggest one.

When I got it, I went and ran System Update, and updated like 80+ packages.  I dont know if this caused the bug but...

Suspend/Resume doesnt work.  It either doesnt suspend (detect the laptop lid closing) or doesnt resume.  Ie every time I have to reboot.  I dunno but I have had this same problem with nonDell laptops running Ubuntu.  It is extremely frustrating and I thought by buying a laptop preinstalled with Ubuntu, it wouldnt have this problem!  Guess not.

Anyone know a solution?

---

### Post by aidave on 2008-04-02
Well I tried a Dell reinstall of the OS.  And now Suspend/Resume works.  So it must be one of the system updates that breaks the laptop functionality!

---

### Post by aidave on 2008-04-02
Ok I spoke too hastily.  Suspend/Resume is still broken, has some quirks:

Suspend/Resume
- Either Doesnt resume after 10+ minutes
- Or doesnt resume after power removed after suspend (need to test)
- Or just randomly doesnt work.
- Result: must hold down power button for 5 seconds to "turn off", then turn back on to boot

- If the laptop is closed and opened quickly (within a minute) it will take quite along time to restore, in addition, the power button pressed repeatedly has no effect

- Slow resume when it does work, around 30 seconds

---

### Post by fragos on 2008-04-02
> **aidave said:**
> Hi, I just got an Inspiron Dell 1420!  Im pretty happy with it but there are a couple issues, this being the biggest one.

When I got it, I went and ran System Update, and updated like 80+ packages.  I dont know if this caused the bug but...

You got 80+ because you got about 5 months worth.  Actualy, 7.10 has had fewer updates than I recall from prior releases. You have nothibg to worrry about in that regard.

---

### Post by aidave on 2008-04-02
Ive been selectively adding updates, avoiding anything that starts with "linux" because I suspect the suspend/resume breaks down there.

BTW I have found it is working better, I have to leave it closed for a while before opening again.  I was used to fast close/open of laptops with XP/Mac, kinda got spoiled I guess.

---

### Post by aidave on 2008-04-02
Nope, still crashes.  After 3 times working, the suspend/resume crashed again.  This is absurd, because I depend on a laptop to keep my programs running.  If I cant depend on that, the laptop becomes useless!!!

I dont know what to do, should I send the laptop back and get a refund?

---

### Post by sdennie on 2008-04-03
You could look at the advice from Dell here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

Specifically, towards the bottom of that page there are common problems and fixes for various Dell laptop models that might fix your problem.

---

### Post by aidave on 2008-04-03
> **vor said:**
> You could look at the advice from Dell here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

Specifically, towards the bottom of that page there are common problems and fixes for various Dell laptop models that might fix your problem.

Thanks ... I tried the Dell 1420 fix for Nvidia cards.  

Now it reboots randomly instead of resuming.

---

### Post by aidave on 2008-04-05
Anyone know a solution?

---

### Post by aidave on 2008-04-06
bump

---

### Post by aidave on 2008-04-07
I tried installing Ubuntu 8.04 Beta, and the suspend now works!

Only problem is, I didn't back up the NVIDIA "xorg.conf" or "menu.lst" files.  Does anyone have a copy of either?  I need the menu.lst file to get the Dell reinstall back.

---

### Post by aidave on 2008-04-07
Oops, spoke too soon AGAIN!  Well it works if I dont install the new nvidia driver via Envy.  Now that I've d one that (I get good screen resolution) it resumes to a white screen.  It seems like everything is working after resume except a white screen.  What gives

---

### Post by sdennie on 2008-04-08
I get the white screen on resume from Hardy as well.  It turns out that it's not actually fatal and that the gnome screensaver dialog box is actually up, you can type in your password, hit enter and it will bring the machine back.  The problem seems kind of similar to bugs from older versions of compiz related to unredirected fullscreen windows.  Disabling that in System->Preferences->Advanced Desktop Effects Settings->General Options might fix the problem but, I haven't tried that because the workaround (pretend it's not actually happening) is pretty straightforward.

---

### Post by aidave on 2008-04-08
Wow that is great!  I guess I never tried entering my password because I figured the screen would stay white anyways.  Doesnt hurt to try!  I thought something was fishy because hitting Ctrl-Alt-Backspace would restart gnome.

Thanks, the suspend/resume seems to be working great now... FINALLY!!!  :)

---

### Post by peddy on 2008-04-26
any fix for the white screen? Its slightly annoying. Btw, it only resumes to the normal unlock screen once per boot, after that it just goes to the white screen. But I can still login, by typing my password.

I am not using a Dell.

---

### Post by jdeslip on 2008-05-04
I also have the white screen problem on my new 1420n laptop with nvidia card in Hardy.  As mentioned above, as soon as I type my password, I am able to resume my session with no problems (so far).  

The whitescreen is still a bit annoying when I am trying to show ubuntu off to my friends.  I'd like to find a solution.  I am using the 169.12 nvidia driver from the ubuntu restricted drivers manager.  Has anyone tried the 173.08 beta driver?  The release notes advertise some improvements for laptops and power management.  Perhaps it fixes this issue?  

I also reported this problem on Dell's forum: [http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13742](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13742)

---

