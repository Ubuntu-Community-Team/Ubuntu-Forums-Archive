---
title: "3D Games won't start after installing updates"
date: 2011-11-03
forum: Gaming &amp; Leisure
---

### Post by beefheartvliet on 2011-11-03
Hi, 

I did a few updates yesterday, and now any game that requires (I'm guessing) Open GL, no longer start. Not so much as a little flicker of the game trying to start. 

This is the case for Alien Arena, Extreme Tux Racer, Super Tux cart, and Warsow.
Much simpler games like Mahjongg and Vodvod :-) start without a problem.

Now when I look at what updates were installed yesterday, I See that there were two updates that relate to GL or OpenGL if you like. I'm wondering if this might be the root of the problem. I just don't want to butcher my system, as has taken me a while to get my system running just nice. 
The two updates, I'm referring too are the following, 
libgl1-mesa-dri (7.10.2-0ubuntu2, 7.10.20ubuntu2.1)
libgl1-mesa-glx (7.10.2-0ubuntu2, 7.10.20ubuntu2.1)

I know my games were working fine before the update,

My question is, assuming that this is the issue, how can I get version 2 again, as apposed to the 2.1 update. As when I check the synaptic update manager, it only shows 2.1 available. 

I included a screen-shot of the other updates it installed yesterday. 
I think I have narrowed it down to those two updates as being the culprits though.

I'll hang on and wait to see if any of you guys have suggestions before I tinker, Needless to say, I'll continue hunting for a solution myself.

I'm running Dream Studio 11.04, with Low latency Kernel 3.0.0-13-lowlatency
Using a Radeon HD 5450 (and the AMD Catalyst Control Centre)

The one thing I will try, as I know this isn't  likely to kill my system, is to download an ordinary kernel, and see if that should make a difference. (Needless to say, an idea that has just come to mind)

[[IMG]http://img232.imageshack.us/img232/8813/screenshotosg.png[/IMG]]("http://imageshack.us/photo/my-images/232/screenshotosg.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Cheers

---

### Post by beefheartvliet on 2011-11-03
Just to add, I have just installed 3.1.0-030100-generic. And that don't make a difference either. I'm not sure whether it should or shouldn't have to be fair, I just thought it might be worth a try.

And starting Alien Arena from the Terminal Shows this, So it' has to have something to do with that update from yesterday?

pete@pete:~$ alien-arena
using /home/pete/.config/alien-arena/arena for writing
execing default.cfg
execing config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Initializing OpenGL display
...setting fullscreen mode 8: 1680 1050
Using XFree86-VidModeExtension Version 2.2
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17

And Re-installing Catalyst control centre does nothing also

---

### Post by beefheartvliet on 2011-11-03
Problem solved for now,
What I did was to Force Version of the two updates, by using the Synaptic Package Manager, and selecting the file I wanted to change, and that allowed me to select th version before the update. I then reinstalled the Catalyst Contol Centre again, and Job done.All games, are once again loading.

---

