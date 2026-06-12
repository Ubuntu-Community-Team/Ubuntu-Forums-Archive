---
title: "Slow performance and loss of configuration since upgrade"
date: 2008-12-20
forum: General Help
---

### Post by DetroitLibertyPenguin on 2008-12-20
In the past week I upgraded from 8.04 to 8.10 using the built in upgrade. Granted this is my first "upgrade" in Linux instead of just burning a new CD for fresh install. 

I have been quite disappointed in a few things. First of all, my overall performance seems much slower than before. If I have multiple programs running it seems to take much longer to stitch between or finish . particular processes. (For example that sentence was done being typed several seconds before it was shown on the display). 

Many websites I used to visit on a regular basis are now giving my script errors that they never did before. 

Least fun of all, I seem to have lost all of the specialized hardware configuration. I had set the volume knob on my HP Internet keyboard to actually adjust the volume with visual output, and my "scroll" button on my trackball to actually scroll, but these features are now gone. I tried to re-edit my xorg.conf to what I had previously, at least for the "marble mouse" trackball, and when I restarted X my video was all messed up. 

Originally I had it set to where I wouldn't have to enter my Password when loading, my old machine takes long enough to boot as it is, and I can't sit around and wait for it to ask me this in the morning, I gots emails to write and coffee to drink! However after the update even with auto log-in activated I am still being prompted for my password everything I restart.

Also, previously I had it set to start Pidgin when I started my PC, now instead of actually starting Pidgin it opens the pidgin folder in Thunar. 

Is there problems with 8.10? Did I set something wrong in my upgrade?

---

### Post by davarino on 2009-01-03
Sorry to hear that you ran into problems.

I avoid "upgrading" like the plague. I have had too many things blow up in my face, and the fixes are so numerous and often machine-specific that it seems that I never really clean up the pieces.

That being said, my own suggestion is to revert your machine to 8.04 and make whatever changes you need to restore your previous configuration.

Then, if you really need something that only 8.10 can give you, tarball in the application that you want to add. You'll have to keep an eye open for updates to any tarballed apps you put onto your machine, but it sure beats blowing up your machine.

My own piece of advice about upgrades: DON'T, unless you have no choice or if you're moving from one LTS to another.

And of course, whenever you upgrade it's a smart idea to have a complete backup of your /home directory somewhere in case you have to revert to the previous Ubuntu version.

---

