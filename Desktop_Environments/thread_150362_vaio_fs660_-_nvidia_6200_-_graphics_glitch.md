---
title: "vaio fs660 - nvidia 6200 - graphics glitch"
date: 2006-03-25
forum: Desktop Environments
---

### Post by funkymonkey on 2006-03-25
Hello,
I've been having some graphical trouble with Ubuntu on my Vaio FS660.  Whenever I try surfing to a graphics-heavy site, such as The Onion AV Club or Newgrounds, my display becomes a weird, colorful hodgepodge of static and image artifacts.  If I roll my cursor over elements on the page, that element will appear correctly while my mouse is on it.

The only way I've discovered to get around this is to switch consoles using ctrl+alt+f1.  I have to wait a few seconds, then if I ctrl+alt+f7 to get back to X, the graphics problems seem to go away for a little while, until I access one of the problem sites again.

Additionally, I get graphical errors in OpenOffice Writer, such as the cursor lagging, leaving behind artifacts, and random black boxes.  That's the real problem, as I'm an author and I've been trying to edit a book, and those problems are very frustrating!

I'm using the NV driver right now.  I switched to VESA, but then I can't get the native LCD resolution of 1280x800 and its very blurry.  I've tried installing nvidia drivers according to this thread ([http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)) but I've gotten errors.

Again, I'm using a Vaio FS660 with a Nvidia Go 6200.

---

### Post by tsmets on 2006-03-26
Exactly the same problem ... with a VAIO FS-315M (similar graphical card as you do have on the FS660 : NVIDIA GeForce Go 64000 with turbo cache supporting 128 MB/Mo)

I noticed it the first time when I came back from a w-e in the country side & left the laptop "on" while away. AMOF, I do have the matter after heavily working for 2-3 hours :(

Any help from a senior is welcome.
AMOF booting the kubuntu DVD gives a similar problem strainght away !

\T,

---

### Post by funkymonkey on 2006-03-26
Okay, I've gotten the nvidia drivers working...the only problem I'm still having is the resolution.  The native resolution for the laptop is 1280x800, and the nvidia drivers don't support that by default.

But what I did was use EasyUbuntu and install the official nvidia drivers.  After a bit of difficultly, I followed tseliot's excellent advice here: [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074).  A few tense moments later, when I restarted the computer, the nvidia splash screen showed up and lo, glxinfo revealed that the nvidia driver works!  hooray!

---

### Post by tsmets on 2006-05-07
I noticed in my case (VAIO FS-315M with the NVIDIA GeForce Go 6400) that the problems comes faster when I have not plugged the electric cable (working on the battery).

\T,

---

### Post by Kidge on 2007-06-03
yeah why does that happen why does it run better on battery

its kinda annohying cuz everytimei wanna watch a video i have to hope i have enough battery life

videos run slightly choppy just enough to piss me off

does anyone know of a fix ive been searching for liek 2 weeks

---

