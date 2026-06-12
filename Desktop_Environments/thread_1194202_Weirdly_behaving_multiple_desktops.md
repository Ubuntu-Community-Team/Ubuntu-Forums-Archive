---
title: "Weirdly behaving multiple desktops"
date: 2009-06-22
forum: Desktop Environments
---

### Post by amazurenko on 2009-06-22
Hello,

A friend asked me to figure out his difficulties with the multiple desktops. The problem started when I instlled compiz on his computer, but persists when I remove it. Essentially, when he uses the keys to change workspace, the new one has the same windows in the bottom bar, although all are minimized. When he switches by clicking on a desktop in the lower right corner, he is transported to a new workspace, but cannot get back without hotkeys. It also lacks the gnome bars. When he gets back to the original screen, the bottom bar is missing, but reappears when he clicks.

Can anyone help?

Thank you,

amazurenko

---

### Post by ajmctaggart on 2009-07-07
I can confirm I too am having this problem all of a sudden!

My setup is not the easiest to diagnose, though...

Sony Vaio VGN
ATI 64 Bit Ubuntu
Intel and Nvidia Cards 

Has anyone else had this issue!?

---

### Post by ajmctaggart on 2009-07-07
Ok, I fixed mine at least!

Basically, I run a Vaio that can dynamic-switch video cards for speed vs. stamina.  My problem was solved with a few fixes...

I am now using an experimental version of the nvidia-glx-180 (it's actually versioned at 185.14.xxx, the original is 180.44)

For some reason, not sure if it was me or not, compiz was setup with 3 horizontal desktop size and 3 number of desktops...this was where the compiz/menu bar/blank screens crashing was occuring...I now have 3 for the # of horizontal desktops, and number of virtual desktops is at 1...this gives me a triangle instead of the "cube," in compiz...

So, unless there is a lot of users having issues with this, it is probably user error, or the Nvidia driver screwing up your prefs...

I could definitely help you out though, if this problem is still occuring!

Good Luck!
-ajmctaggart

---

### Post by Pogeymanz on 2009-07-07
> **amazurenko said:**
> Hello,

A friend asked me to figure out his difficulties with the multiple desktops. The problem started when I instlled compiz on his computer, but persists when I remove it. Essentially, when he uses the keys to change workspace, the new one has the same windows in the bottom bar, although all are minimized. When he switches by clicking on a desktop in the lower right corner, he is transported to a new workspace, but cannot get back without hotkeys. It also lacks the gnome bars. When he gets back to the original screen, the bottom bar is missing, but reappears when he clicks.

Can anyone help?

Thank you,

amazurenko

Are you sure you are shutting Compiz off? Hit ALT+F2 and type ```
metacity --replace
```

It sounds like you are having confusion with viewports and desktops. Go to the Compiz Settings Manager and click General Options. Change the number of desktops to 1 and the number of viewports to 4 (or whatever number he wants).

When you turn compiz off, there should only be one desktop, but you can easily add more. It's just much easier to deal with compiz when there is one desktop.

---

