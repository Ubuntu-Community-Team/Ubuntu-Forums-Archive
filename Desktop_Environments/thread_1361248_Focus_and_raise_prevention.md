---
title: "Focus and raise prevention"
date: 2009-12-21
forum: Desktop Environments
---

### Post by teambob on 2009-12-21
Hi,

I am trying to prevent windows from gaining focus and raising themselves. I have installed compiz and I have been successful in preventing applications from stealing focus.

The problem is that a number of applications (particularly Java applications) can still raise themselves on top of everything else.

I am using Karmic Koala. The compiz settings I have are:
Click to focus: enabled
Raise on click: enabled
Auto-raise: disabled
Auto-raise delay: 1000
Focus prevention level: high
Focus prevention windows: !(class=Polkit-gnome-authentication-agent-1)

The regex plugin is installed. I have tried both the gconf and flat file backends. I have also tried removing the .compiz directory.

Does anyone have any other ideas?

-Andrew

Edit: Disabling raise on click does not help either.

---

### Post by teambob on 2009-12-22
Sorry to bump this but does anyone have any ideas?

---

### Post by rockdj on 2010-06-07
I'm having this same trouble too. Compiz installed but even singling out the specific Java windows doesn't stop them from stealing the focus.  

As a side note, putting the specific windows as 'Below' under 'Window Rules' in Compiz does make them stay 'below' other windows, but doesn't stop them still stealing the focus away.

Any help is appreciated.

---

