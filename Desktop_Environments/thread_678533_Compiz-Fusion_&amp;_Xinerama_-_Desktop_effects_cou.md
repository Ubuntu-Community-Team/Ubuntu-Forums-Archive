---
title: "Compiz-Fusion &amp; Xinerama - Desktop effects could not be enabled."
date: 2008-01-26
forum: Desktop Environments
---

### Post by Deiz on 2008-01-26
I run two LCDs (1280x1024 each, making for a 2560x1024 desktop environment) and enjoy the  functionality afforded by Xinerama, and really can't live without it.

However, I would like some desktop effects, primarily close/minimize animations.

I run restricted Nvidia drivers, and get told that desktop effects can't be enabled when Xinerama is enabled.

Is there a known workaround for this situation?

Interestingly, when I run compiz in terminal, I get this: 

sean@sean-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

Is it normal to have compiz result in a segfault under these circumstances?

---

### Post by rosegarden78 on 2008-01-26
I dunno but I followed instructions [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981") to get mine working.  You need to start with Ubuntu GG 7.10 not Xubuntu or Kubuntu.

---

### Post by zero-9376 on 2008-01-26
use nvidia settings and set it up with twinview instead of xinerama

---

### Post by Deiz on 2008-01-26
> **zero-9376 said:**
> use nvidia settings and set it up with twinview instead of xinerama

To be honest, I consider Twinview vastly inferior to Xinerama - The purpose of multiple monitors, for me, is to have multiple fullscreen applications.

Not one application spanning two monitors.

---

### Post by zero-9376 on 2008-01-26
if i understand what you are saying you want an app to maximise to one of your lcd's only? i dont understand this for me twinview worked like this out of the box, ive been reading similar issues here:

[http://www.thecrumb.com/2008/01/22/ubuntu-nvidia-and-two-monitors/](http://www.thecrumb.com/2008/01/22/ubuntu-nvidia-and-two-monitors/)

but right now i have firefox fullscreen on one of my displays and geany on the other, when i was reading about a problem i was having with urban terror (game) not respecting this fullscreen behaviour something was mentioned about metamodes in xorg.conf. i have just had a look at mine and it does have a metamode line which may be why the apps stick to their displays although urban terror still refuses :(

---

### Post by Deiz on 2008-01-31
> **zero-9376 said:**
> if i understand what you are saying you want an app to maximise to one of your lcd's only? i dont understand this for me twinview worked like this out of the box, ive been reading similar issues here:

[http://www.thecrumb.com/2008/01/22/ubuntu-nvidia-and-two-monitors/](http://www.thecrumb.com/2008/01/22/ubuntu-nvidia-and-two-monitors/)

but right now i have firefox fullscreen on one of my displays and geany on the other, when i was reading about a problem i was having with urban terror (game) not respecting this fullscreen behaviour something was mentioned about metamodes in xorg.conf. i have just had a look at mine and it does have a metamode line which may be why the apps stick to their displays although urban terror still refuses :(

Hmm. I recently tried TwinView again, and lo and behold, windows did maximize to one monitor. I suppose this is because the first time I tried TwinView, my Xorg.conf was a mess as I was having trouble getting both my monitors working.

In any case, I'm now using TwinView, and desktop effects work. Thanks.

---

### Post by jongep86 on 2008-01-31
I had the same thing I think. on my nvidia prop drivers, but in fedora 8

I first trie TwinView, and then it was all 1 big desktop an when i maximize an app it wws on two screens.
TThen I tried Xinerama on 2 serparate X server. That works like a charm.Maximize is ok
Then I enabled desktops effects. That doesn't work.
So I switched back to twinview, and now i see two desktops. So maximize works again as supposed. 
Now I enable desktops effects. Great, works

I think it all about the sequence how you enable the nvidia-settings.

---

