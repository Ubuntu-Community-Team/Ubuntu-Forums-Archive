---
title: "Configuring twinview with svideo (tv-out) in jaunty (NVIDIA)"
date: 2009-05-05
forum: General Help
---

### Post by yousillygoose on 2009-05-05
Hey hey!
This has been a persistent problem with ubuntu releases (gutsy was the last one to do it right!).  I was wondering if it was possible to configure nvidia-settings to output with twinview through an svideo cable to a tv?

I tried it and could not get it working.  Any feedback is appreciated.

Rob

---

### Post by kpkeerthi on 2009-05-05
1. Connect your TV
2. gksudo nvidia-settings
3. Click 'Detect Displays"
4. Set resolution for TV and mode (clone or left-of, right-of etc)
5. Click on "Save to xorg.conf" (changes will stick on reboot if you complete this step)

---

### Post by yousillygoose on 2009-05-05
This is the thing: I know all of this.  It doesn't work.  It acts like it sets up twinview but nothing outputs to the tv.  This is a common problem with ubuntu, like I said.  Is there any fix?

---

### Post by kpkeerthi on 2009-05-05
> **yousillygoose said:**
> This is the thing: I know all of this.  It doesn't work.  It acts like it sets up twinview but nothing outputs to the tv.  This is a common problem with ubuntu, like I said.  Is there any fix?

I didn't know about that since you didn't mention what you have tried so far. Not sure why it is not working for you though.

---

### Post by yousillygoose on 2009-05-05
Sorry for not being clear.  Yea, I configure twinview like you are supposed to.  My laptop thinks it is outputting to the tv (my desktop does not end on the right side of my screen but continues to where to tv screen would be).  It makes for a big hassle when I want to watch a movie on the tv! I don't like running things in separate x sesions but that is the only way I have ever gotten it to work since Gutsy.  There HAS to be some workaround to enable twinview (successfully), but I just can't find it!

---

### Post by manzdagratiano on 2009-12-24
Was a bug-report filed for this? I did not find one. I have the same issue - no output on TV.

---

