---
title: "compiz switcher not disappearing"
date: 2006-07-27
forum: Desktop Environments
---

### Post by hopstah on 2006-07-27
ok, i just did a fresh install last night to wipe away all of the mistakes that i made while learning ubuntu.  i got everything back and running fine, except that when i hit 'alt tab' for the compiz switcher, it doesn't work right.

the switcher appears and i can tab through all of the windows, but when i release the keys, the switcher just stays there.  the only way to get rid of it is to hit escape, after which i am just brought back to the window that i was working on originally.

does anyone have any clues for this?  it's really aggrivating!

thanks!

---

### Post by MarkSheely on 2006-07-27
I read in the compiz forums that the solution was to try removing "Splash" from "apps/compiz/plugins/fade/screen0/options/window_types" in gconf-editor.

I tried this, and it didn't help me, so I'm stuck with the same problem you are.  Would you give it a shot and see if it works for you?

--Mark

---

### Post by [h2o] on 2006-07-27
I have the same problem. Really annoying. Removing "Splash" from Fade did not help anything.

---

### Post by andyjeffries on 2006-07-27
Same here too (only happened since latest compiz update (to quinn25)).  Also, I can only force it to a much earlier version using synaptic, anyone know a better way so I can just go back to quinn24 or 23?

---

### Post by hopstah on 2006-07-27
well, i found the solution while looking for a remedy for another problem i was having - namely that my num lock and caps lock were both doing nothing.  when i fixed that problem, the problem of the switcher was fixed as well.

what you need to do is edit your ```
sudo nano /etc/gdm/gdm.conf-custom
``` file and remove (or comment out) the "-kb" at the end of the line that was added to the bottom of the file.

Before edit: (yours may differ slightly)```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

After edit: ```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo # -kb
flexible=true
```

this will magically fix three problems in one!!!

i hope you all have the same luck that I did :)

---

### Post by andyjeffries on 2006-07-28
It fixes the task switcher problem, but I can't use my "Windows-key" shortcuts now, nor does Alt-1-8 switch viewports as I had it set up to.

This is just a duff release.  Anyone know how to go back a version or two?

---

### Post by andyjeffries on 2006-07-28
I've found out how to downgrade:

Go to [http://www.beerorkid.com/compiz/archives/](http://www.beerorkid.com/compiz/archives/)

Download the old version you require (due to some wierd printf formatting on that page you'll need to hover over each link to see the version number) and install it using dpkg -i.

Going back to 23 has fixed my windows key problems and my task switcher problem.  However, my <Alt>1 - <Alt>8 don't work to switch my workspace still!  How long has it been since I rebooted for an update to take effect (rhetorical)!??!!

---

### Post by andyjeffries on 2006-07-28
Replying to myself, wierdo, blah blah!

Anyway, found out if I revert back to quinn20 my Alt key is back working properly.  Locked the version using Synaptic, so screw testing new released...

---

### Post by MarkSheely on 2006-07-28
Thanks for posting the fix - it worked like a charm.

What does commenting out "-kb" do?  How is that changing compiz?

--Mark

---

### Post by BitTorrentBuddha on 2006-07-30
Hey, quinn26 is out and this problem went away, but the windows key shortcuts on mine still haven't returned.

---

### Post by alcamus on 2006-07-31
Many thanks for this fix. I was having the same problem and couldn't get a solution anywhere. Now everything is running beautifully and once again I'm knocked out by Linux.

---

