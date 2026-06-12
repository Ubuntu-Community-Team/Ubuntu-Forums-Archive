---
title: "Compiz Fusion slowed down start up"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by killaray on 2007-06-24
after and installation of Compiz Fusion my start up has suffered quite noticeably, has anyone had a similar slow down on there system after installing? my pc hangs while loading my start up apps such as Pidgin, Gdesklets and awn... yet the PC is still useable, the notification area is frozen untill the apps r opened up.. also my window decoration isnt visible until all is loaded

---

### Post by Franz1234 on 2007-06-24
I have similar Problems.
After installing Compiz Fusion the XGL seesion slowed down and I cannot work anymore. And Compiz Fusion is also not starting up.

---

### Post by killaray on 2007-06-24
can anyone help me speed things back up?

---

### Post by bazooze28 on 2007-06-24
i have the same problem.  some help would be greatly appreciated !!!

---

### Post by ChrisBC on 2007-06-25
Bump with exactly the same problem.  Can someone point us in the right direction?  Tell us what output you need to diagnose the problem?  Anything?

---

### Post by Gifty85 on 2007-06-25
Same problem here... :-?

---

### Post by NumberOne on 2007-06-25
I also suffer the slow startup!!!!

---

### Post by schnupi on 2007-06-25
yea same thing here..its fairly annoying

ive compiz fusion(compiz --replace) and emerald(emerald --replace&) seperate in the startup session...did anyone try those start up scripts?!are they any use?... there was an update this morning but it didnt fix that problem

---

### Post by kevinlyfellow on 2007-06-26
What you need to do is to set metacity as the window manager to start with again.  Open up gconf (alt-f2 and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity (or any other fast loading window manager).  Then go to your session gui (alt-f2 and run gnome-session-properties) and put in a new startup program.  Call it what you want (compiz-fusion possibly?) and use the command `compiz --replace`  Make sure it is checked and your done!

---

### Post by speaker219 on 2007-06-26
Eh, this was never a problem for me.

---

### Post by killaray on 2007-06-26
> **kevinlyfellow said:**
> What you need to do is to set metacity as the window manager to start with again.  Open up gconf (alt-f2 and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity (or any other fast loading window manager).  Then go to your session gui (alt-f2 and run gnome-session-properties) and put in a new startup program.  Call it what you want (compiz-fusion possibly?) and use the command `compiz --replace`  Make sure it is checked and your done!

worked beautifully... wuts a faster loading window manager? i wanna see how fast i can get it... also if i change it to another window manager will things start lookin different even though i have compiz takin over?

---

### Post by mid_night gypsy on 2007-06-26
Howdy,
 I tried kevinlyfellow suggestion witch gave me a gray colored background. System was lock, I couldn't do anything with it. I found a work around using kevinlyfellow suggestion and that was to add metacity --replace as a grub boot option. Now my desktop boot as fast as it did with Beryl, using CompizFusion. Thanks,gypsy

---

### Post by schnupi on 2007-06-26
but wait what about emerald?! can i still use emerald?!

edit: i just tried what kevin suggested but instead putting in metacity i just typed in emerald ... for some weird reason it just jumped to metacity anyways but i didnt have that startup lag
edit2: ok got emerald working...i realised that i was using an emerald wrapper to start emerald because i was using it with compiz before and it didnt work without a wrapper.. i just had to add emerald --replace& as a startup session entry and remove the old wrapper entry and it worked like a charm

---

### Post by kevinlyfellow on 2007-06-26
> **killaray said:**
> worked beautifully... wuts a faster loading window manager? i wanna see how fast i can get it... also if i change it to another window manager will things start lookin different even though i have compiz takin over?

It won't effect the way compiz will look since compiz is a window manager which will replace the one initially loaded.  I tried it with icewm, and I honestly didn't notice a difference.  I think metacity is probably about as fast as it gets.  Go ahead and experiment with different window managers and see if any are faster.  BTW do not try twm, I already did and it doesn't work.

---

### Post by kevinlyfellow on 2007-06-26
> **mid_night gypsy said:**
> Howdy,
 I tried kevinlyfellow suggestion witch gave me a gray colored background. System was lock, I couldn't do anything with it. I found a work around using kevinlyfellow suggestion and that was to add metacity --replace as a grub boot option. Now my desktop boot as fast as it did with Beryl, using CompizFusion. Thanks,gypsy

That's interesting... I've never heard of that before.  Where do you put the option?  Is it on the kernel line?

---

### Post by mid_night gypsy on 2007-06-26
kevinlyfellow,
 Well, there's two way to try grub boot options, First, at grub screen witch is your choice o.s. boot if you have windn't xp ,your menu screen. Select ubuntu kernel etc. hit e arrow down to the line that has splash in it, hit e again add a space then metacity --replace hit b for boot. If this works sudo gedit /boot/grub/menu.lst and add your boot option(s). I just got off work (truck driver) ,but I was thinkin' of tryin' compiz --replace -c emerald & ... to see if that makes it boot to compiz faster (with emerald). Thanks,gypsy

---

### Post by kevinlyfellow on 2007-06-26
> **mid_night gypsy said:**
> kevinlyfellow,
 Well, there's two way to try grub boot options, First, at grub screen witch is your choice o.s. boot if you have windn't xp ,your menu screen. Select ubuntu kernel etc. hit e arrow down to the line that has splash in it, hit e again add a space then metacity --replace hit b for boot. If this works sudo gedit /boot/grub/menu.lst and add your boot option(s). I just got off work (truck driver) ,but I was thinkin' of tryin' compiz --replace -c emerald & ... to see if that makes it boot to compiz faster (with emerald). Thanks,gypsy

I'll have to give it a shot.  I was a little surprised to hear that there are kernel options for the window manager, but come to think of it, I've seen it before with knoppix and gobolinux.  Thanks for the tip.

---

### Post by kevinlyfellow on 2007-06-26
> **mid_night gypsy said:**
> kevinlyfellow,
 Well, there's two way to try grub boot options, First, at grub screen witch is your choice o.s. boot if you have windn't xp ,your menu screen. Select ubuntu kernel etc. hit e arrow down to the line that has splash in it, hit e again add a space then metacity --replace hit b for boot. If this works sudo gedit /boot/grub/menu.lst and add your boot option(s). I just got off work (truck driver) ,but I was thinkin' of tryin' compiz --replace -c emerald & ... to see if that makes it boot to compiz faster (with emerald). Thanks,gypsy

I just tried putting the word compiz as a kernel boot perimeter and it worked beautifully!  I don't know about emerald (I like my metacity theme) but I think you can leave out the replace option, since what this appears to do is override the gconf option (I'm running compiz, but my gconf thinks I'm running compiz).  I booted without stalling, but I also updated compiz this morning, so I'm not sure if they fixed the problem, or using it as a boot parameter is just a good workaround.  Anyways, thanks for the cool tip :-)

---

### Post by mid_night gypsy on 2007-06-26
kevinlyfellow,
 Your very welcome, anytime. gypsy
P.S. goolgle compiz.wrapper this what I'm tryin' right now seems to pretty good.

---

### Post by kevinlyfellow on 2007-06-26
> **mid_night gypsy said:**
> 
P.S. goolgle compiz.wrapper this what I'm tryin' right now seems to pretty good.

Hmmm... I'm not sure what exactly your talking about.  The file /usr/bin/compiz is a wrapper for the real window manager /usr/bin/compiz.real.  Is this what your referring to?  It does allow you to set the window decorator in that wrapper, so it would end the need for anyone to run emerald seperatly of the wrapper.

I did notice that I didn't have a fallback manager set in it, so everyone should be on the lookout for that.

---

### Post by kevinlyfellow on 2007-06-26
It looks the latest update has resolved the issue (compiz can be run immediately w/o another wm), can someone confirm this?

---

### Post by DSn0wMan on 2007-06-27
No, It still takes 5 minutes to load only compiz after this mornings update.

---

### Post by rfurman24 on 2007-06-27
> **kevinlyfellow said:**
> What you need to do is to set metacity as the window manager to start with again.  Open up gconf (alt-f2 and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity (or any other fast loading window manager).  Then go to your session gui (alt-f2 and run gnome-session-properties) and put in a new startup program.  Call it what you want (compiz-fusion possibly?) and use the command `compiz --replace`  Make sure it is checked and your done!

Thanks. I had no idea where to start. Beryl is sooooo smooth but I am starting to hate compiz fusion. I think the beryl team should have stay where they were.

---

### Post by kevinlyfellow on 2007-06-27
> **rfurman24 said:**
> Thanks. I had no idea where to start. Beryl is sooooo smooth but I am starting to hate compiz fusion. I think the beryl team should have stay where they were.

I actually started finding a workaround because I had the very same problem with beryl.  And actually the solution is the same!

I think things will get better with time.  Both Compiz and Beryl were quite stable (I actually decided to switch from beryl to compiz because it was more stable).  But mixing code can be a complicated process and I have faith that things will smooth out soon.  Just think of the bug squashing that will be going on in compiz-fusion as gutsy gets closer to being released!  I feel that compiz-fusion is dangerously alpha right now.

---

