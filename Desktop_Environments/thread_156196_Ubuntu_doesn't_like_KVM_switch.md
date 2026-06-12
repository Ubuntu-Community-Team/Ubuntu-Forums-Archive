---
title: "Ubuntu doesn't like KVM switch"
date: 2006-04-06
forum: Desktop Environments
---

### Post by bigbear on 2006-04-06
Hi All
Just built a new pc to run Linux and is connected to my windows pc via a Belkin KVM switch.
I can run ubuntu with no problems, the trouble is if I switch to my windows machine and then after a while switch back to ubuntu and move the mouse the screen goes beserk with applications opening and closing.
The only way I can log off is to pull the power plug.
Is there a work around this problem, has anyone else come across this?:-k

---

### Post by Cirrocco on 2006-04-06
the only thing screwed up between my KVM and Ubuntu is:
after I boot up, I can't use my mouse until I unplug then replug.
after that I have no problems switching back an forth.

the thing is: KVMs aren't the simple switch you'd hope them to be, no. they're full of electronics n' stuff - the devil I say.

---

### Post by scooper on 2006-04-07
[QUOTE=bigbear]I can run ubuntu with no problems, the trouble is if I switch to my windows machine and then after a while switch back to ubuntu and move the mouse the screen goes beserk with applications opening and closing.
The only way I can log off is to pull the power plug.
Is there a work around this problem, has anyone else come across this?:-k[/QUOTE]

I didn't have exactly that problem with a KVM and a mouse, but I did have the mouse stop working after switching.  You may want to check if you're using evdev in your xorg.conf as the mouse driver.  When I switched to ExplorerPS/2 it works fine.  I am not near my system right now so I can't post the xorg.conf snippet.  But there are other threads on the subject if you search for evdev and/or kvm.

Good luck!
Steve

---

