---
title: "Remove clock from indicator applet?"
date: 2010-05-11
forum: Desktop Environments
---

### Post by sigdrifa on 2010-05-11
Hi,

the indicator applet on Lucid has a clock, so that I now have two in my panel: the clock applet and the one in the indicator applet. I prefer the clock applet and would like to get rid of the clock in the indicator applet.

It should be possible, since the clock only shows up on my desktop PC, not my laptop.

Ideas, anyone?

---

### Post by pmlxuser on 2010-05-11
strange my just show the clock applet, why not remove the indicator applet and add it again...

---

### Post by sigdrifa on 2010-05-11
> **pmlxuser said:**
> strange my just show the clock applet, why not remove the indicator applet and add it again...

Tried that, unwanted clock still shows up :(

---

### Post by sigdrifa on 2010-05-11
Got it.

There's a package called indicator-datetime. Remove that, and the clock is gone.

Just in case anyone else runs into this.

---

### Post by x-shaney-x on 2010-05-11
Isn't indicator-datetime part of unity?
I don't think this is normal behaviour.

---

### Post by sigdrifa on 2010-05-11
> **x-shaney-x said:**
> Isn't indicator-datetime part of unity?
I don't think this is normal behaviour.

Oops. Just checked, and, yes, it is. I was curious about unity and installed it on the desktop PC. Then I forgot about it :redface:

Well, anyway, I'm glad I got rid of it :) And maybe I should wait for the next Ubuntu Netbook Edition :P

---

### Post by Ahmedmb on 2010-05-20
THX sigdrifa

---

### Post by dilodicus on 2010-08-20
Thank you!
I'm running Maverick Alpha and an update a few days ago added the clock to the indicator applet, this was driving me mad! all fixed now :)

---

### Post by LK-G on 2010-10-11
My need is the opposite. I want to use the datetime from indicator applet and wants to remove the Clock applet (slow to open). Although, my datetime-indicator applet is installed and shows when I login into Unity, I can't see it when I login with normal panel based desktop. Any clues??

Thanks

---

### Post by manosone on 2010-10-11
About the indicator-datetime and other "forgotten" packages.
Using ```
sudo apt-get autoremove 
``` you can get rid of any un-needed packages.

I had the same "problem" too and solve it.Thanks all.



> **LK-G said:**
> My need is the opposite. I want to use the datetime from indicator applet and wants to remove the Clock applet (slow to open). Although, my datetime-indicator applet is installed and shows when I login into Unity, I can't see it when I login with normal panel based desktop. Any clues??

Thanks

I am not sure if i got it right but,if your indicator-datetime is installed,login to gnome and try to add it to the panel,maybe removing first the clock applet.

If nothing happens,check from the synaptic that it is installed and try to delete clock applet.

---

### Post by LK-G on 2010-10-12
Manosone, you got the issue right but I had already tried these steps. I again did them to be sure before replying and the outcome is the same. No datetime indicator applet still to add despite it is (re)installed. Any other ideas?

Thanks

---

### Post by cub on 2010-10-27
Cheers! Just as someone above I tried out Unity and then when I went back into Gnome I had double clock and the menu bar. Uninstalled the indicator- mentioned here and voila, back to normal. :)

---

