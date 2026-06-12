---
title: "Compiz on Radeon 9600 AMD 64 with Ubuntu Feisty Fawn  :)"
date: 2007-05-24
forum: Desktop Environments
---

### Post by crush21 on 2007-05-24
Ok... i have been through it all... spent an entire week trying to get these desktop effects to work and after much reading of all sorts of forums i did not find the answer.... 

I'm posting this in hopes of saving you a whole lot of time....
Its actually quite simple... ie: you dont have to do anything behind the scenes. Xorg, AIGLX, Extensions... none of it! (crazy i know...)
This is what i did, hope it works for you!

Make sure you install **ubuntu feisty fawn _64_ bit version on your 64bit system!!!** Sorry, cant help 32bit users as this is where i wasted my time... even though i have a 64bit i accidentally installed 32bit ubuntu, desktop effects WILL NOT work... trust me...
I would do a clean install of ubuntu 64 if you've played with your Xorg.config file a bit etc...
Just to be safe... then install any updates that pop up.



After you have installed the **64bit **version and installed updates, simply enable compiz desktop effects

*System > Preferences > Desktop Effects*

This is where i was expecting the white screen of death but to my surprise it worked! :D

Thats 90% done!   i know i know.... "whatever!!!" but i spoke to some linux experts (my boss) and he says that it will most certainly affect it as these effects are experimental, but anyway, i took his word and to my surprise it worked!

Then to get a nice windows manager up and running install gnome-compiz-manager

*System > Administration > Synaptic Package Manager*
   *Enter your password*
[I]
Search for:[/I] gnome-compiz-manager
*Mark it for installation and Apply*

*After install, reboot*


**_My Problem_**
Now there is a catch... This i still need help with...
It works, even when you reboot, BUT if i switch my computer off and back on (not rebooting) then when i log in i still get the white screen of death, Ctrl + Alt Backspace and re-logging in does not work.

I then reboot and it works. Any idea why this is? It only does this if effects are enabled.
If they are disabled then first login works. but when i enable it, "white screen...." i then leave it on and reboot and voila... why...why!!!!!

Any help is always appreciated. Let me know if this method works for you too and also for other readers.


My specs:   

[I]AMD Athelon 64 3000+
ATI Radeon 9600 Pro 128MB
[/I]

---

