---
title: "Battery Charge Monitor"
date: 2005-03-22
forum: Desktop Environments
---

### Post by barfoos on 2005-03-22
Hello there,

I just installed ubuntu and everythings works so very much out of the box,
that I'm still speechless. (used debian testing before and nothing worked out
of the box).

The only thing that bugs me is the following:

I use my noteboook 50% of the time on AC power and with
the battery unit not installed. Now when I loginto gnome he tells me everytime
that my battery very low and that i should do something about this.
All I actualy do about this is, that i press ok.
Then the programm recognizes that I'm on AC power and doe not disturb me again.
Even when I logout and login back again, it seems to remember this and does not warn me again.

Is there anything I could do about this?

thanks

  barfoos

---

### Post by lorap on 2005-03-23
hi friend!
i've ubuntu installed on my notebook.
after installation i was surprised to see that ubuntu realized i do have a notebook cause i saw the power meter icon at the right upper corner.if it's your case then place the mice over it,press the right button and choose Properties option.then once you've the small popup window open you go to the second tab and unmark the upper checkbox after what right at the same moment check it again and you'll see the battery immidiatly at the panel (this option's checked by default but,probably,because of a small bug doesn't work until you uncheck and check it again).
there's also checkbox lets you watch the battery charge percentage.

if the power meter doesn't appear at all,i.e.ubuntu didn't recognize you've a notebook then place the mice over the panel,press right button & choose from the list power meter (or battery meter,i'm not at my pc right now),after what everything is the same.
have a nice day!
pavel

---

### Post by jsgotangco on 2005-03-23
Does anyone notice that your Battery monitor does not refresh dynamically when its plugged or unplugged; you will need an X.org reset to resfresh the status.

---

### Post by lorap on 2005-03-23
mine one's working good.
no additional libraries've been needed being installed.
i.e.i plug or unplug the power cable the changes occur at the very same moment.
but look,it probably depends on the board you've or on other things.
pavel

---

### Post by MichaëlVD on 2005-05-31
[QUOTE=jsgotangco]Does anyone notice that your Battery monitor does not refresh dynamically when its plugged or unplugged; you will need an X.org reset to resfresh the status.[/QUOTE]

I have the same problem with my Dell Inspiron 5100.

Does anyone have a solution?

Thanks!

---

### Post by groovywombat on 2005-09-29
anyone else not able to see the time remaining?  i suppose it's not a big deal but it'd be nice.

---

### Post by netsyd on 2005-09-29
[QUOTE=groovywombat]anyone else not able to see the time remaining?  i suppose it's not a big deal but it'd be nice.[/QUOTE]

I assume you've gone into the preferences and selected show time/percentage remaining? 

As for the x restart issue... I think Pavel might be right. It likely depends on the board and what messages it is capable of, or it may simply have issues with ACPI (broken). My NC4000 does fine recognizing it, but I had to dump ACPI in favor of APM. :???:

---

