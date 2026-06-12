---
title: "Improperly detecting screen; repeatedly defaults to 800x600 'Plug n' Play'"
date: 2008-04-29
forum: Desktop Environments
---

### Post by JamesBowen on 2008-04-29
Okay, after playing a bit with hardy and figuring out the new gizmos (a new necessity which, by the way, I'm not happy with.  Grr), I have discovered the nature of a display problem I've been having.  Essentially, Hardy cannot detect my monitor and defaults it to the 'Plug n' Play' model (even after I manually configure it to give it the exact model number), with a maximum resolution of 800x600 -- not exactly the most usable, expansive resolution.  Regardless of how many times I manually tell it what my monitor is, every time I restart it puts me into 'low graphics mode', and tells me I need to manually configure my screen and video card drivers -- so, there's no way for me to get a resolution that enables me to get any work done.

What can I do to ensure that when I tell it what model my monitor is, it sticks?

---

### Post by CAsurfer on 2008-04-29
Have you tried editing /etc/X11/xorg.conf directly? By doing so, you should be able to specify your resolution manually. This looks like a pretty good guide: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by skankster on 2008-04-30
I had this problem. I worked out that it was probably the video drivers - I  have an NVidia card and it looked to be an issue with the restricted drivers. After several attempts at fixing them, I ended up doing a fresh install and it's worked no problem. Obviously that's not ideal but it was probably for the best considering the state of my system (through experimentation) before the upgrade.

Try installing envyng and see if that resolves it. It didn't with me but I'd messed about with the nvidia packages so much by then I think I'd messed up a dependency or two somewhere.

---

### Post by skankster on 2008-04-30
Also, check this thread:
[http://ubuntuforums.org/showthread.php?t=771810](http://ubuntuforums.org/showthread.php?t=771810)

---

