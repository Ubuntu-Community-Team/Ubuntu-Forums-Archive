---
title: "snapshot during cube rotation?"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by taehC on 2007-10-04
how do i take a snapshot while i have my cube rotating in compiz?

---

### Post by hardyn on 2007-10-04
printscreen button?

---

### Post by taehC on 2007-10-04
tried that already
usually when i press prt scrn it opens up a window to ask where i want to save the screenshot but when it is in the middle of a rotate it doesn't open up even after it stops rotating.

---

### Post by FuturePilot on 2007-10-04
Try Applications>Accessories>Take Screenshot. Tell it to grab the entire screen after a few seconds. Then rotate the cube and wait for it to take a screenshot.

---

### Post by Locutus_of_Borg on 2007-10-04
while still holding the left mouse to keep the cube displayed, hold ctrl and press prnt screen,
at least that's what works on mine. there is a screen shot plug in for compiz that should have the key bindings listed

---

### Post by Chymera on 2007-10-04
Run each of the following lines in a terminal window


gconftool-7 -t str --set /apps/metacity/global_keybindings/run_command_9 "Print"
gconftool-7 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-screenshot"

then just press ye olde print screen button and it should work.

---

### Post by mcavady on 2007-12-30
I had the same problem, however the print screen button did work until I played with the effects!! did manage to unbind the num_pad 1. got that button bk however still cannot use the print screen button (ubuntu studio 7.10).

I tried the typing the above into the terminal and got a (bash commend not found) Eny more suggestions? 

Thanks James

---

### Post by Forlong on 2007-12-30
I assume you hace ccsm installed, since you said, you played with the effects.

Now make sure it's configures like this:

---

### Post by mcavady on 2008-01-02
I have looked at the screens as above and they are configured the same, Is there any other suggestions?

Thanks 

James Mcavady

---

