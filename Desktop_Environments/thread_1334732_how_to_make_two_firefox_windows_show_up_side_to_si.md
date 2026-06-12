---
title: "how to make two firefox windows show up side to side?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by expxe on 2009-11-22
in windows 7 i right click the taskbar and select show side by side? how can i get the same thing in ubuntu?

---

### Post by expxe on 2009-11-24
bump, don't tell me ubuntu doesn't have this.....even windows has it

---

### Post by lsk3993 on 2009-11-24
I don't know too much about Ubuntu (new user) but looking at [http://brainstorm.ubuntu.com/idea/22302/](http://brainstorm.ubuntu.com/idea/22302/) it seems that someone else requested this feature and they were linked to a Compiz plugin: [http://wiki.compiz-fusion.org/Plugins/Grid](http://wiki.compiz-fusion.org/Plugins/Grid) is that what you are looking for?

---

### Post by expxe on 2009-11-24
> **lsk3993 said:**
> I don't know too much about Ubuntu (new user) but looking at [http://brainstorm.ubuntu.com/idea/22302/](http://brainstorm.ubuntu.com/idea/22302/) it seems that someone else requested this feature and they were linked to a Compiz plugin: [http://wiki.compiz-fusion.org/Plugins/Grid](http://wiki.compiz-fusion.org/Plugins/Grid) is that what you are looking for?

i see, and how do i access this "compiz" there is no mention on it under applications menu. i want a point and click solution (or a step by step typing solution if it has to come to it)

---

### Post by yossell on 2009-11-24
lsk3993 - thanks, nice find. It never ceases to amaze me how versatile compiz is. It's handy to have a way of positioning windows quickly, and the key presses here do a nice job. I'm not sure it's quite the same as what windows 7 offers, but it looks good. Thanks for the heads-up

@expxe - Compiz is something which controls the look and behaviour of the windows and desktop environment, adding some eye-candy and some functionality. Grid is something in compiz which allows you, by choosing a combination of keys to position the active window at various places on the desktop - centre, left half, top half etc. 

To get it to go I'll assume you've installed the Advanced Effects Desktop Settings (ccsm) - it can be got in the normal way. Note that (I think) it requires 3-d acceleration, and it doesn't always work smoothly on all systems - some people have some trouble with it. You may decide that it's not worth the trouble/risk of trying compiz out just for this. 

Go to system -> preferences -> and choose appearance. The appearance preferences window should show up. Choose the tab 'visual effects' and click on extra. This is the moment of truth as your computer discovers whether it can handle compiz. The computer will try and load a suitable driver. If it cannot find one, you may need to download a suitable one - if you have an nvidia card, you should be in luck. 

If everything goes well, you should now be running compiz. You may find that your windows wobble as you move them, and some other eye-candy effects. You can configure this through the compizconfig menu.

Go to system -> preferences and choose the compizconfig. Scroll down to the category of Window Managment and enable Grid by ticking the box. Click on Grid to bring up a list which tells you which key-bindings perform which actions. You can change the defaults to your choosing.

Compiz can do a number of other things which you may also find useful, and you can turn off the effects you don't like.

---

### Post by expxe on 2009-11-24
> **yossell said:**
> lsk3993 

Go to system -> preferences and c**hoose the compizconfig**. Scroll down to the category of Window Managment and enable Grid by ticking the box. Click on Grid to bring up a list which tells you which key-bindings perform which actions. You can change the defaults to your choosing.
.


i have done everything up to the above, now don't see this option, i am running 9.10 64bit

---

### Post by yossell on 2009-11-24
Ok - on my set-up, there's something under system->preferences called (in its full glory) compizconfig settings manager from which I change the settings.

Go to applications and click add/remove and do a search for compiz. The Advanced Desktop Effects Settings (ccsm) should be an option. Is it installed? If not, I recommend installing it. If it is installed, let me know.

---

### Post by blur xc on 2009-11-24
I use maximumize to achieve effects like that.  To do that, I'd arragne one window on one side of my screen, the other on the other side, and hit super-m, then activate the other window and do the same.  the only caveat is that it acts a bit funny if there are other windows on the same workspace....  It works best if you only have those to windows on the one active workspace.

I have not used the grid plugin, but I might try it now.

BM

---

### Post by expxe on 2009-11-24
> **yossell said:**
> Ok - on my set-up, there's something under system->preferences called (in its full glory) compizconfig settings manager from which I change the settings.

Go to applications and click add/remove and do a search for compiz. The Advanced Desktop Effects Settings (ccsm) should be an option. Is it installed? If not, I recommend installing it. If it is installed, let me know.

i installed the package now and now i can see what you mean. i tried out the left/right thing, its not 100% the way i want it (i would like it to be done how the same in windows), but ill work with this for now, thanks

ps i cant get the super key to work (super key = windows key right?). for example, if i just want to set <Super> by itself to the move right command, it accepts. but when i test it on a window it doesn't work?

---

### Post by blur xc on 2009-11-25
> **expxe said:**
> i installed the package now and now i can see what you mean. i tried out the left/right thing, its not 100% the way i want it (i would like it to be done how the same in windows), but ill work with this for now, thanks

ps i cant get the super key to work (super key = windows key right?). for example, if i just want to set <Super> by itself to the move right command, it accepts. but when i test it on a window it doesn't work?

I don't think you can use the super key by itself for a command.  that'd be like using shift or control by itself.  It has to be used in a key combo.

BM

---

### Post by expxe on 2009-11-26
i take back what i said, after trying for a while i feel the linux left/right way to split the screen is better than how windows does it

thanks again for the help

---

