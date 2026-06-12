---
title: "NVIDIA Application Profiles"
date: 2014-09-04
forum: Gaming &amp; Leisure
---

### Post by CatKiller on 2014-09-04
I've been fiddling with this for a while, and I'm clearly missing something.

What I'd like is to have FXAA on Minecraft, but not Steam. I don't mind if I have it on all the time and turn it off for Steam, or off all the time and turn it on for Minecraft. I haven't been able to get either to work.

FXAA works really well for Minecraft, but it makes text all blurry in Steam. I did manage to turn it off for Compiz (flickering textures) with ```
[procname]compiz
GLAllowFXAAUsage false
``` but I can't find any magic to select the other ones I'm interested in.

---

### Post by CatKiller on 2014-10-12
Bump.

---

### Post by dannyboy79 on 2014-10-12
are you saying that you setup app profiles within the nvidia control panel but they aren't working?
did you create the app profile AND setup a rule?
[http://gyazo.com/9129309cb42495d17a3a2459bd4cd1ac](http://gyazo.com/9129309cb42495d17a3a2459bd4cd1ac)

---

### Post by CatKiller on 2014-10-13
Yes and yes.

---

### Post by dannyboy79 on 2014-10-13
whats the procname for steam? you can find out with 
```
ps aux
```
then just simply add it as a rule.

[procname]steam
GLAllowFXAAUsage false

and if you want it always on for minecraft than try (obviously you need to find out the procname for minecraft)
[procname]minecraft
GLAllowFXAAUsage true

To be honest, your question isn't very detailed, you haven't shown us what you've tried and what's not working so it's a little hard to help.

Also, have you read through the documentation?
To enable application profile support globally on a system, edit the file $HOME/.nv/nvidia-application-profile-globals-rc to contain a JSON object with a member "enabled" set to true or false. For example, if this file contains the following string:

{ "enabled" : true }
application profiles will be enabled globally in the driver. If this file does not exist or cannot be read by the parser, application profiles will be disabled by default.

I found it here: [http://us.download.nvidia.com/XFree86/Linux-x86/319.12/README/profiles.html](http://us.download.nvidia.com/XFree86/Linux-x86/319.12/README/profiles.html)

---

### Post by CatKiller on 2014-10-13
> **dannyboy79 said:**
> 
To be honest, your question isn't very detailed, you haven't shown us what you've tried and what's not working so it's a little hard to help.

From the OP you can tell that I know the format, and that I've tried every permutation that seemed feasible to me from the ps output for the java and steam/steamwebhelper processes. Check my posts, I'm not new here, but this is not my speciality. Given the popularity of both Steam and Minecraft, and also the widespread use of nVidia's driver, it seemed reasonable that this was a solved problem and that someone would be able to just point me to the solution, without any of us having to dig through the intricacies of how the driver picks which process to run the settings against. Again, it should be clear from the OP that it's not as straightforward as one might hope. For example, launching Steam spawns at least nine processes. Which of those, if any, is the one that the nVidia driver picks as the OpenGL texture to blur up? None that I can find.

Thank you for replying, anyway.

---

