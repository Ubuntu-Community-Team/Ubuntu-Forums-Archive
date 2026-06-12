---
title: "Enabling Desktop Effects Stopped Gnome"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by hoggbottom59 on 2007-05-08
Hello everybody peps

I recently let my system upgrade to Feisty 7.04 which I've been quite happy with.
That is until I was stupid enough to enable Desktop Effects and select wobbly windows.

My system now boots as far as gnome but displays a white screen. The mouse cursor moves and my hard drive light flashes. I left it for a while but nothing seems to be happening.

I tried other installed kernels but the same problem.

I used a Knoppix dvd to boot. I found the Compix section in gconf-editor. I removed both wobbly and switcher from the  Compiz-general-allscreens-options activeplugins key.

This doesn't seem to have resolved the problem.

Does anyone know how to turn off the Desktop Effects via terminal so I can do the change in Knoppix and reboot?
 

Thanks,
Leon.

---

### Post by warjowuch on 2007-05-09
Try cntrl-alt F8, ps ax | grep compiz and then kill "processnumber" from compiz
Maybe try without | grep compiz.

After that, you do cntrl alt f7 to go back to gnome. By the way, cntrl alt f8, the f8 could be f1-f6 also (and I thought a few more)

---

### Post by warjowuch on 2007-05-09
Oh, another thing, you are sure your openGL/direct rendering is enabled?
Seems to me it is not. I had kinda the same problem myself.

---

### Post by hoggbottom59 on 2007-05-09
Ok I'll try these ideas out.
I'm not bothered about getting the Desktop Effects working as I had previously had a working system.

My Suspend now works with Feisty so that's one step further. Before it failed to work and I had to restart.

What I do want is a working system again.


Leon.

---

### Post by hoggbottom59 on 2007-05-09
Thanks this worked to get back into a normal working Gnome.

I'll have to work out how to permanently turn it off if this hasn't.

Leon.

---

### Post by hoggbottom59 on 2007-05-09
This has turned it off so it's now usable but I have no bar on my windows!

Leon.

---

### Post by warjowuch on 2007-05-10
just remove the whole compiz-thing and desktop-effects, if you don't need them.
And check with glx-info if you have direct rendering...
No wondow bars is a but not usefull :-)

---

### Post by hoggbottom59 on 2007-08-12
I managed to get the screen back to normal.
I can't remember how though.

I will post here again if I remember how.

Leon.

---

### Post by scossio on 2007-08-12
> **warjowuch said:**
> Oh, another thing, you are sure your openGL/direct rendering is enabled?
Seems to me it is not. I had kinda the same problem myself.

How do I get to this Window for OPEN GL to make sure I have it enabled. This is what I dont know how to do, Sorry New to Ubuntu 7.04 My Problem is that everything was working fine, Then I began to mess with terminal adding things from COMPIZ. after doing this.....when i go to System>Preferences>desktop effects, I get the pop up to enable. But when I now hit enable it kind of like doesnt do anything, it moves the screen for a second and it looks like its trying to apply the effects but it cant. I was also able to see before a box that pops up asking me if i want to keep the current settings or if i want to keep the new settings, this box no longer pops up......any one know the root cause to this? how do I undo everything......is there a way to return ubuntu back to its original state as when first installed?

---

