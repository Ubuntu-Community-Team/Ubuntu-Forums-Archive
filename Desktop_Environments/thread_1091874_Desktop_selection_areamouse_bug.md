---
title: "Desktop selection area/mouse bug"
date: 2009-03-09
forum: Desktop Environments
---

### Post by humphreybc on 2009-03-09
I've come across this problem a few times, mainly it seems to occur after I have left the computer for more than 20 minutes and come back to it. 

Basically I go to click something, or use the selection tool to select some icons on the desktop and then ubuntu will freeze. 
The mouse will still move and scrolling will go to my next desktop, but I cannot click anything. Sometimes the keyboard will still work and other times it will not, and then sometimes after about 30secs of being unresponsive it will fix itself, but the selection will stay frozen on the desktop.

Also I've noticed that after ubuntu has unfrozen, icons on the desktop cannot be clicked anymore.

Is this a common issue and is there a fix?

---

### Post by EnsignR on 2009-03-28
I think I am having the same problem.

If you open a tty (eg ctrl-alt-F1) and then switch back to X (ctrl-alt-F7) can you then click on something else - but only one. I have to successively switch back and forth between tty and X to get do anything. Keyboard shortcuts still work.

Does the same thing happen for you?

I had this problem intermitantly with Gutsy, usually 1st time I logged in form cold boot, but it would fix itself when I logged out and back in again (most times).

Yesterday I used the update manager to update to Hardy. I had the occasional hitch with the above last night, but in general it was working (after I figured I needed to change my /etc/fstab to stop fsck bitching on boot, but thats another story).

Today however I cannot get a login with the mouse working properly.

Prior to upgrading I had the login manager automagically login a dummy guest account. I then used to log out of that and into my account, usually without problems. The mouse issue never seemed to happen to guest. It made me think that the problem might have been with my gtkrc file. However since the upgrade the guest account is also effected.

nb. when you switch back from tty to X a context menu is drawn on the screen, where your 1st click didn't work. It's as if you right clicked, it doesnt draw the context menu but your mouse it tied to it stopping you from clicking elsewhere.

nb. When problem arises highlighting of icons doesnt work either.

---

### Post by EnsignR on 2009-03-30
HELP!! I am in hell or at least purgatory.

Yesterday everything, for no apparent reason, was working smoothly. Today back to the same old tricks with the mouse.

It's impossible to practically do anything.

I've found other workarounds using xte, but frankly they don't work for me.

Can anyone offer any suggestions. At this point all I can think of trying is a clean install of Intrepid - the prep for which (moving documents etc prior) would be a horrible pain in the butt.

I really need to get this sorted as there is some urgent work I need done, which is near impossible without a usable mouse.

Any suggestions would be greatly appreciated.

cheers

---

