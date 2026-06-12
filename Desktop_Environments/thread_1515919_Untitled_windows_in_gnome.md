---
title: "Untitled windows in gnome"
date: 2010-06-23
forum: Desktop Environments
---

### Post by haggyfleish on 2010-06-23
Hi Experts


I a totaly newby to Ubuntu .... I have a T400 lenovo.  My release of Ubuntu is Lucid and i'm using the desktop gnome. 

I do have a strange empty x-windows called 'untitled window', how do it find out who or what process it is referring to ?

my second question is that i have no notions of security and firewall protection, could someone using the proper tools may see what i have on the screen? 

Please help. 

Thanks.
'
regards,
Haggy

---

### Post by labinnsw on 2010-06-24
> **haggyfleish said:**
> my second question is that i have no notions of security and firewall protection, could someone using the proper tools may see what i have on the screen?

See the "Keeping Your computer Safe" topic in the "Ubuntu Help Center."

---

### Post by brawnypandora0 on 2011-05-01
I hae the sam e probem. Its extremel annoying nd I think it's lagging my computer. Clicking on the x won't close it. PLASE HELP!!!

Is there a Ubuntu equivalent of "Force Close" a la Windows Task Manager? I started getting this problem a few days ago...it occurs the moment I login and then never stops.

---

### Post by Copper Bezel on 2011-05-01
Yeah, run [font="Courier New"]xkill[/font] and click the offending application. I have the command set to a keybinding in Compiz.

Weird error, though; before you kill it, let's find out what it is.

Run this in a terminal and click on the window,

```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
```

and post the result, if you would.

---

