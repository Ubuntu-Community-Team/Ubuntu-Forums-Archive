---
title: "No effects with XGL (only fade in/out)"
date: 2006-12-19
forum: Desktop Environments
---

### Post by linbetwin on 2006-12-19
I have installed xgl by following the instructions at ubuntuguide, but the only effect I see is windows fading in on open and fading out on close. No spinning cube, no wobbly windows, no transparency or shadows. I admit I don't know all the shortcuts for these tricks, but I know a few from SUSE 10.1 (the only distro on which I was able to install xgl successfully). Is this a known problem? Am I doing something wrong?

And another thing: under xgl, System Monitor now shows me some strange values for RAM use. Some applications seem to be using 4.0 GB of RAM, although I only have 1 GB of physical RAM and a 1 GB swap.

Thanks for your help!

---

### Post by linbetwin on 2006-12-20
Nobody else has this problem? :(

---

### Post by EnderTheThird on 2006-12-20
First check [here]("http://wiki.beryl-project.org/wiki/Tips/Default_Commands") ([http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)) for a list of all of the keyboard shortcuts and commands.

Now open a terminal and let us know the output of the following:
```
glxinfo
```
That will tell you what driver you're using along with a bunch of other stuff.  What video card do you have?

You'll also want to check Beryl Settings (selected by clicking on the Beryl icon in the notification area) to make sure all of those effects are even activated.  If they are, check your Keyboard settings to make sure you have the right keyboard type selected.  I had problems with getting some of the effects to work when my Super, Ctrl, and Alt keys weren't registering quite right because I didn't have the correct keyboard selected through System -> Preferences -> Keyboard.

I'm pretty sure XGL messes with the RAM usage reporting, which is why you're showing 4GB being used when it really isn't, but I could use some backup on that statement.

---

### Post by linbetwin on 2006-12-20
EnderTheThird, thank you for your reply. I do not have access to my Ubuntu machine right now, but this is what I can tell you:

- I did not install beryl, only xgl (i.e.: compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome) by following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

- I did this on a fresh install of Edgy, on which I installed and enabled the nvidia-glx driver (I have an NVIDIA GeForce 6600 GTX video card).

- My keyboard is en-us.

---

### Post by EnderTheThird on 2006-12-20
If you have an nvidia card, you'd probably be better off running Compiz/Beryl with AIGLX.  XGL is kind of a hack to get all of the pretty 3D desktop effects, which is mostly only used by people whose drivers don't support AIGLX (read: ATI users, like me).

I would check out this link: [_http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA_]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA").  Like I said, I'm an ATI user, so I haven't specifically used that howto, but I did use the Beryl Wiki to set up Beryl with XGL on my ATI box, so you should be in good hands.  Beryl seems to be getting more attention than Compiz, with a lot more work currently being done on it.  Compiz is supposed to be more stable, albeit with fewer features, but I haven't had any problems with Beryl at all.

You can probably go ahead and undo what you did while following that guide as well.  It's kind of a pain, yes, but I think it will be worth it.  I just set up Beryl with AIGLX on an i810 laptop my friend has and it runs better than on my 2.8 P4 with an ATI 9800 AIW Pro with XGL.  You also run into fewer problems with GL applications (such as Google Earth) if you're running Beryl under AIGLX.  So give it a shot and let us know how it works out for you!

---

