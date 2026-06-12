---
title: "User session won't load"
date: 2006-10-18
forum: Desktop Environments
---

### Post by modafokaxx on 2006-10-18
Hi Everyone!
Seems everytime I have a problem, it's my desktop that refuses to load..

last time, I was stuck at the splash screen, and the computer would freeze after that. I was able to solve that by removing the contents of the /tmp folder.

This time, when I enter my username and password, the mouse cursor appears on a black background and just sits there. Nothing happens. I can move the mouse, I can switch to virtual terminals, I can restart the X server (I think that's what ctrl+alt+backspace does) but I can't load my GNOME session.
I can't load any users session, as I have tried with another test user.
The X server is working, otherwise I wouldn't have the GNOME login screen..

Also, I noticed that the /tmp folder was filled (and I mean packed) with files called "orbit-axx-********" (axx being my username and the stars are series of letters and numbers).
Tried deleting the contents of the /tmp folder (they are temporarey files after all) as that was the miracle solution last time, but it didn't solve anything this time.

I don't really get what's going on..
yesterday, my computer started messing up, as I was not able to open any new applications at some point.. this happenned after I had fought my way with the apt-get command line and after that with synaptic after a failed upgrade of amarok from 1.4.1 to 1.4.3 which left me in a state of broken packages, a state that "apt-get -f install" couldn't fix.
Finally, I got rid of the problem by removing the broken package (amarok-libengines) in Synaptic, but I get the feeling now that I messed a lot more things doing that.

If anyone has any clue on what's going on, it would be much appreciated..
I hope I was precise enough in my description!

cheers!

axel

---

### Post by modafokaxx on 2006-10-18
adding this: I forgot to say, I am running Ubuntu 6.06 Dapper Drake.
And I can log in completely in a graphical interface as Root using the recovery mode (at the grub menu).

Still no clue.. but at least I can run my computer in a proper fashion (no trolling or anything, but having to go back to win2k even for 30 min to post the previous message felt strange)

---

### Post by modafokaxx on 2006-10-19
Nope? no one has any idea?

From what I can see, the GDM is working, since I can log in to gnome through [this sort of window](http://www.gnome.org/projects/gdm/screenshots.html). It's only after that is fails to work..
The "Failsafe GNOME" session doesn't do any difference (appart from a message telling me that I'm running a failsafe GNOME after I login).

Starting in recovery mode and starting X as root works, but if I log out and try to login as a normal user afterwards, it fails.

I removed compiz/berryl in cas it was that, but no difference.
I removed Amarok 1.4.1 and installed 1.4.3 in it's place through synaptic, and that's working fine (using the root session).

So what I'm wondering, is what is different in GNOME's settings between a regular user session and a root one? what does it do differently?
because it works in one case and not in the other... :/

---

### Post by gregster on 2006-10-20
I'm sorry, but this isn't a solution.

I'm having the same problem, but I'm using Edgy and Gnome (I assume from your post that you're using KDE?). Here's my situation:

Everything was fine - I've been running Edgy since Knot2. Dual monitors, non-free nVidia drivers etc. Suddenly, one day the whole thing did just what you said. I get a usplash, then a greeter screen, then a cursor on a coloured background (but not my desktop image of choice) with nothing else. Like you I can ctrl+alt+f1 to another CLI session, and gdm is running etc.

I cleared literally everything from my home directory (.gnome, .gconf etc) with no effect. I logged in as a different user, with no effect.

I find NO logs that indicate a problem of any sort. In desperation I re-installed Edgy. Everything went fine and I was happy as can be. I did all of my updates and restarted to the same old problem.

Here's a wrinkle: I had the nomachine.com version of the NX server installed previously, and I was able to remotely log in to the machine via the NX client without problem. I got a complete Gnome session with all of my theme changes in place etc. It was a perfectly normal session - but I could only get it remotely!

I was able to get in to the old build (locally) using Fluxbox or XFCE, but not Gnome.

I'm installing KDE right now (just because it's handy to have around), and I'll try deleting stuff from /tmp and report back.

---

### Post by modafokaxx on 2006-10-22
Hey!
ok, someone on the french Ubuntu forums found the solution to my problem :)
and it explains why I could login as root:
I had a problem with the /tmp folder's permission.. they should be set to rwx for everyone (777) and they weren't. It could also have been a problem with some config files in /etc (but apparently it was not the cas here, as a ```
chmod -R 777 /tmp
``` as root solved my problem :)

I guess the permissions were mangled with by my failed install of amarok.. or maybe I just did something I shouldn't have.

Anyway, you should try that gregster, or at least check out your permissions!

---

### Post by gregster on 2006-10-23
Thanks for that, modafokaxx. Unfortunately it didn't solve my particular problem - I suspect that as similar as the two problems seemed, they weren't the same. I've decided to go back to Dapper as this machine is too important to be fiddling with all the time.
Thanks for the feedback, though.
Cheers.

---

