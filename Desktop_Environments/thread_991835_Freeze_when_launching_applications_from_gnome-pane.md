---
title: "Freeze when launching applications from gnome-panel"
date: 2008-11-24
forum: Desktop Environments
---

### Post by Kharlos on 2008-11-24
This seems to only be an issue when I'm using 2 xservers with Intrepid Ibex. I didn't have this issue with Hardy Heron at all.
I have 2 monitors: left and right. Left is default and everything there works fine. But if I click on any of the application icons on the gnome-panel on the right screen, I get a gnome-panel blank pop-up that says "error" in the title.
Once that comes up I can move my mouse and things in the background keep running but I can't select anything.
If I have a terminal open I can kill gnome-panel, it restarts and everything is fine until I try and launch an application from the panel again.
While things are 'frozen', I notice the cpu jumps up to ~95% for the process gnome-panel.
I've reinstalled all of the gnome utilities and even reinstalled ubuntu (this time with amd64) and I'm still having the same issue.
I can't find anything in the error logs indicative of what might be causing this.

my specs:
nvidia 8600GT
AMD phenom quad core (does the same with my dual core box as well)
4 gb ram

I switched to xubuntu in between the i386 -> x64 change to see if the xcfe panels have this issue. They don't.

Any tips for troubleshooting this would be VERY appreciated. I can provide some screen shots to illustrate all of this as well if necessary.

---

### Post by joesapo on 2008-11-24
Same issue here... :/

nVidia/Compiz

---

### Post by Kharlos on 2008-11-25
You think killing compiz would fix the issue then?
Whats weird is I was playing with it for like a half hour last night, shutting off desktop effects, locking everything to the panel and then suddenly it started working. Step by step I loaded everything that I changed and it didn't stop working until I rebooted. Now I'm doing all those things again and nothing.
pretty funny really...
I vow though, if I figure out what it is that fixed it, I'll share... :-)

edit: Ok, got it to work again and it won't stop working anymore... lol. All I did was set the visual effects to none, then back to normal, none again, and normal again. And then (I swear this is partly out of superstition) opened properties of the broken panel after which I clicked the desired app and VOILA!
Make sure that if you are doing this, you keep a terminal or the gnome system monitor open so you can kill gnome if it craps out. And if that, theres always ctrl-alt-backspace.

Although its not ideal, I'm so sick of messing with this for now. But I'd LOVE to hear any more ideas.

---

### Post by bestchicken on 2008-11-25
Thanks Karlos, had exactly the same problem (but also noted that I could start apps on the panel by right clicking and selecting launch, and starting items off the menus put them on the other screen)

Setting visual effects to none and then back to normal, just once, fixed it.

---

