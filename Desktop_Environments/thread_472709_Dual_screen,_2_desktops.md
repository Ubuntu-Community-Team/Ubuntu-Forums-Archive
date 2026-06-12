---
title: "Dual screen, 2 desktops"
date: 2007-06-13
forum: Desktop Environments
---

### Post by lynxus on 2007-06-13
Hi guys,
When i used FedoraCore 6  i had the option in system to choose dual screen , 1 screen being 1400xwhateveritis and the other on 1024x768 . Both had their own desktops so they both had a set of desktop icons.

Anyway.

I cant seem to do this on Ubuntu.

Beause my other screen can do higher than 1024 it means i have to use that on my laoptop screen so thats no good.

How can i do the above? 

I have a IBM R51 with ATI radeon.

just want 2 desktops one screen on 1024x768 and my laptop screen on normal 1400xwhatever


Please!.
I may have to ditch ubuntu if i cant get this working. :( me no wanna.

---

### Post by reclusivemonkey on 2007-06-14
Can you please attach, NOT post, your /etc/X11/xorg.conf file.

What you describe is possible, as long as you have your xorg set up correctly. There is a GUI for the nvidia driver, but you should still be able to "roll your own" for an ATI card.

---

### Post by lynxus on 2007-06-21
OK here you go,

It wont let me upload.conf files. so please rename to .conf after.

Then again, it does open as a .doc anyway.

Thanks
Graham

---

### Post by kuja on 2007-06-21
One thing you could try is copying over the xorg.conf file from the FedoraCore install, it may work without modification if you are lucky.

---

### Post by lynxus on 2007-06-21
I thought of that, but no longer have that installation as it was wiped when i Ubuntu-fied my machine lol

---

### Post by reclusivemonkey on 2007-06-21
I've taken a look at your xorg.conf, and there is no configuration for dual screens. When I get home I will check the xorg.conf I have for my MythTV setup, which I should be able to tweak for you.

---

### Post by reclusivemonkey on 2007-06-21
Try adding the following to your xorg.conf file, in the "Screen" section;

```

Option         "TwinView"
Option         "SecondMonitorHorizSync" "30-70"
Option         "SecondMonitorVertSync" "50-160"
Option         "MetaModes" "1440x900"
Option         "TwinViewOrientation" "Clone"

```

But make sure you substitute the correct values for your monitor.

---

