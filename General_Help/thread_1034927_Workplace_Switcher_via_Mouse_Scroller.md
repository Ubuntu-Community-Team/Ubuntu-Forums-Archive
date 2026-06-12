---
title: "Workplace Switcher via Mouse Scroller"
date: 2009-01-09
forum: General Help
---

### Post by GJLenon on 2009-01-09
Hello,

      First let me state that I am relatively new to Ubuntu (about a week) and for that matter Linux.  After the ten thousandth time Windows crashed on me, I decided that I was done and installed 64-bit Ubuntu.  I have no plans to go back.

     One of the features that first intrigued me about Ubuntu was the Workplace Switcher; what an incredibly neat feature!  One of the really neat features was the ability to switch workplaces "on the fly."  To do this, I would move my mouse to the corner of the screen and move the scroller, switching windows at my whim.

     As I said, I'm very new to Ubuntu and as such am downloading/installing new patches/updates on a daily basis.  Some days as few as 9, others as many as 40.

     On one of those patches my scroller quit moving my workplace.  To clarify, I can still manually click it via the graphic at the bottom right corner, and I can still move my mouse to the graphic and scroll that way; however, I can no longer move my mouse to the side of the screen to do this.  

     My question, then, is how do I re-enable this feature?  If it was a bug, how do I duplicate it?  I've checked the following areas:

[INDENT]Workplace Switcher > Preferences
Workplace Switcher > Help
Applications > System Tools > Configuration Editor
[/INDENT]
     As well as searching the web, these forums, and asking some Linux Buddies.

Help, please!

-Biggie

---

### Post by binbash on 2009-01-09
if you are using compiz, open compizconfig settings manager and enable viewport switcher plugin

---

### Post by GJLenon on 2009-01-09
I'm using standard ubuntu 8.10 Intrepid, I believe.

---

### Post by Drubie on 2009-01-09
what binbash meant was CompizFusion, the Desktop Effects Manager.

Within Compiz there are several addons, if you will, that add little graphics to your gui like the desktop cube and wobbly windows.  One other such addon is the Viewport Switcher; if that is enabled, you can switch workspaces "on the fly" as you said.  

if you dont have CompizFusion, check it out - very nifty stuff

---

### Post by GJLenon on 2009-01-09
I feel retarded.  Sorry for wasting your time.  Evidently one of the updates disabled the Nvidia drivers I have.  When I re-enabled them, the feature started working again.

Again, sorry for wasting your time.

---

### Post by tiggsy on 2009-11-25
Lovely. But how about enlightening those of us who still have the problem as to how you fixed it... with code?

---

### Post by audiomick on 2009-11-25
Hi.

@tiggsy

> **GJLenon said:**
>  Evidently one of the updates disabled the Nvidia drivers I have.  When I re-enabled them, the feature started working again.




The doo dads don't work without 3D, and the 3D doesn't work without the nVidia driver. Simple as that...

---

