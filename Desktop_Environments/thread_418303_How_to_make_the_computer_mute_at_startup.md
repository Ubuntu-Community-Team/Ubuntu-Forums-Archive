---
title: "How to make the computer mute at startup?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Kamber on 2007-04-22
On the otherwise happy occasion that upgrading to feisty made my sound work, I've run into a bit of a problem: The sound is playing! Since I have no external means of turning down the sound on my laptop, and since I often use the laptop in an environment where I *don't* want it to be making sounds, I want it to be muted until I tell it not to.


Now, the problem is two-fold:

- First, every time I start the computer, regardless of the sound settings before I turned it off, it plays that welcome-to-the-login-screen bongo sound. I don't want it to do that!

- When it starts up, it restores the sound settings it had before I shut it down. Forgetful as I am, I can't always remember to mute my computer before I shut it down. So I would like the sound to be muted by default no matter what the settings were before I shut it down.


I've been searching around the forums for solutions, but all the solutions I've been able to find either refer to sound settings that I can't find (older versions I assume), or simply don't work (Like turning down the sound in Alsamixer)

---

### Post by aidanr on 2007-04-22
i think adding something like "amixer set mute" to your startup items should do the trick, check the amixer man pages for the exact command and also the startup sound can be turned off in system -> preferences -> sound (or something like that, on windows at work right now so can't check)

---

### Post by heimo on 2007-04-22
I'd try editing /etc/init.d/alsa-utils. It'll run "start" during boot and "stop" when shutting down. If you store settings when muted, and restore settings when booting, (and prevent it to saving settings anymore), you'll have muted sound next time you boot. Shouldn't be too complicated to figure out how to do it.

---

### Post by Kamber on 2007-04-22
> **heimo said:**
> I'd try editing /etc/init.d/alsa-utils. It'll run "start" during boot and "stop" when shutting down. If you store settings when muted, and restore settings when booting, (and prevent it to saving settings anymore), you'll have muted sound next time you boot. Shouldn't be too complicated to figure out how to do it.

That seems to have done the trick. Thank you!


And for anyone with the same problem stopping by this thread, a little step-by-step:

- Restart once with the sound muted
- open alsa-utils with sudo (sudo nano /etc/init.d/alsa-utils)
- Near the bottom, below the place where it says "stop)", comment out (add a # to the start of the line) the lines starting with store_levels and mute_and_zero_levels.

---

### Post by jorgealfonso on 2008-05-10
[http://ubuntuforums.org/showthread.php?t=58731](http://ubuntuforums.org/showthread.php?t=58731)

Add:
[INDENT]amixer set 'Master' mute[/INDENT]

In:

System -> Preferences -> Sessions -> Startup programs tab

To disable the login sound (the only one that could play before the line above acts)

    System -> Preferences -> Audio -> Sounds tab

... and change the "login" sound, to "no sound"

---

### Post by _ja_bob_ on 2008-05-16
Apologies to the mods --> I know it's bad form to multi-post but it'd be handy if this were easy to find:

I just found out how to do this with my laptop, but it should work just fine for probably any computer.

First, you have to know if your mixer has any weird settings. For my laptop, audio output is actually run on three different mixers, one for headphones, one for the speakers, and another for the 'subwoofer.' This is the procedure I used to mute them on startup

-----------------------------------------------------
*open up a terminal and go to the directory where the script will be put:

cd /etc/init.d

*now you need to make the script itself... I use gnome and therefore
*Gedit, but you can use vi or whatever you're comfortable with

sudo gedit mute.sh

*When the editor opens up, type this out and then save it
*just remember that you need to add a line for every mixer
*that you need muted and ones that are multiple words need ""
*most people can probably get away with just the "Master" channel

#!/bin/sh
amixer -q sset Master mute
amixer -q sset Headphone mute
amixer -q sset "Master Mono" mute

*Save the file and exit Gedit and make the script executable by typing

sudo chmod +x mute.sh

*Now to put it in the major startup catagories

sudo update-rc.d mute.sh defaults
-----------------------------------------------------

It worked for me and I hope it works for you. I am a beginner too, so no promises.

---

### Post by Franko30 on 2008-05-23
Hi there,

I also have a system that keeps "forgetting" the sound settings after every reboot once I installed Hardy (8.04). It's full blast after every logout/login.

I didn't know how to disable the drumroll at the login screen (that was especially annoying at full volume).

In another thread ([http://ubuntuforums.org/showthread.php?t=789779](http://ubuntuforums.org/showthread.php?t=789779)) I found a different solution than is advertised here.

[B]Disable all system sounds and in the menu system->admin->login window->accessibility tab uncheck the sounds for "login screen ready".
[/B]

The source is post 7 in the thread mentioned above.

Cheers

Franko30

---

### Post by executive on 2008-06-10
thank you Franko30. the stupid login drumroll was driving me mad. now i can finally boot ubuntu in peace.

---

