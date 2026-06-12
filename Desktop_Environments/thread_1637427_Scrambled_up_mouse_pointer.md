---
title: "Scrambled up mouse pointer"
date: 2010-12-04
forum: Desktop Environments
---

### Post by bjtuna on 2010-12-04
I upgraded from 10.04 to 10.10 a little while back and something weird is going on with my mouse pointer. I'll explain:

Usually the pointer is just an arrow, styled according to your chosen "theme" (System -> Preferences -> Appearance -> Customize -> Pointer). Sometimes it changes, depending on the element you're hovering over. For example, if you hover over a text input box, it'll become the I-shaped "cursor".  If you hover over a hyperlink, you get the "hand".

On my system, in many cases where the pointer has to change, it's not properly showing the alternate pointer.  In particular, it seems to be having problems with the "magnifying glass". This is what it looks like:

[IMG]http://imgur.com/a62vV.jpg[/IMG]

It's also happening 100% of the time, even for the normal pointer, when I'm inside VMWare Workstation in an XP guest:

[IMG]http://imgur.com/rhld0.jpg[/IMG]

I created another account on my system and logged into GNOME using that account, and the problem does not exist. So, something is messed up in my personal settings, somewhere. I'd prefer to not have to wipe all my config directories just to solve this one issue, which is why I'm hoping someone here might know what specifically I could do to fix this.

Thanks!

---

### Post by frankski on 2010-12-04
I had the exact same problem this week. I rebooted and it solved it for me.

---

### Post by bjtuna on 2010-12-04
> **frankski said:**
> I had the exact same problem this week. I rebooted and it solved it for me.

That is not the solution for me, unfortunately. This has been going on for a couple months now, across many reboots.

---

### Post by cfreak2399 on 2011-04-04
Same problem here. I'm using Gnome but it seems to happen in specific applications. It happens any time the cursor turns to an "I" in Audacity and it happens when I'm looking at a picture in Firefox and the zoom magnifier should appear.

I read a few past threads where people had this issue and changing the cursor theme fixed it but that has not worked for me.

---

### Post by bjtuna on 2011-04-04
I was able to fix the problem some months back by switching from fglrx to the open source ATI drvier.

Hope this helps.

---

