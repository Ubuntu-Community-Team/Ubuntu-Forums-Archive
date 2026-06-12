---
title: "Can't install xmame or Advancemame! What gives?"
date: 2005-12-21
forum: General Help
---

### Post by wargames on 2005-12-21
I've tried installing both xmame and now Advancemame and neither work on my breezy system. With xmame all I ever get is a blank black screen and then nothing. With Advanemame I always get the error message about not having fb and it does nothing after that.
ex:
Unable to initialize the video driver. The errors are:
fb: Unsupported in X. 

So how the heck do you actually install either of these and get them to work. Why is installing a simple mame emulator so hard?

I've googled and googled, searched and searched and found really nothing.
I tried what it suggested at this link:
[http://linuxanswers.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=603](http://linuxanswers.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=603)

[From link:]

"Well after investigating a little bit I found a site that could solve this problem: [http://br-linux.org/forum/phorum-5.0.12/read.php?1,63535](http://br-linux.org/forum/phorum-5.0.12/read.php?1,63535)
Unfortunately it is in portuguese. But the interesting part was intelligible. Running and compiling AdvanceMAME, as well as AdvanceMENU without framebuffer support.
Code:
./configure --disable-fb

Make sure that you have set the correct environment variables, to execute the command sdl-config. Or else you will get a error message like that:
Code:
configure: error: no video library found. If you have the SDL library installed somewhere try using the --with-sdl-prefix option.

Fix it in following order:
Code:
locate sdl-config

Then check if in /etc/profile the correct environment variables are set and if the directories listed in /etc/profile contain the command sdl-config. Probably not. Do...
Code:
export PATH="$PATH:/usr/local/bin"

e.g. if /usr/local/bin is the directory where sdl-config is located (it's strange, because it should be in there by default, and not only /usr/bin or something similar)

Then go again through the configure and compile procedure
Code:

./configure --disable-fb
make
su
make install

advmenu (First time to create a advmenu.rc profile)
advmenu (Second time to start the emulator)

If you hear "let's rock", then it works. Press F1 inside of AdvanceMenu for the HelpScreen.

I hope this solution works also in Ubuntu, Kubuntu, and the other *nixes"

[End of Post]

This didn't seem to work, or at least it didn't work on my breezy. I don't even know what the "export PATH" command does. Anyone? Do I have to delete this "export PATH" in order to uninstall it?

I have my ATI drivers working correctly.  So what's the problem? Why doesn't xmame work and Advancemame doesn't work either.  Any Linux genius out there who knows what to do? Do I need to do a Tux Linux god dance in my backyard, journey to the center of the earth to find a command or what? I'm a Linux beginner on edge here.

---

### Post by Wallakoala on 2005-12-21
[http://ubuntuforums.org/showthread.php?t=86213&highlight=gxmame](http://ubuntuforums.org/showthread.php?t=86213&highlight=gxmame)
hope this helps

---

