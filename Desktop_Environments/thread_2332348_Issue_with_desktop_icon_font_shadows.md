---
title: "Issue with desktop icon font shadows"
date: 2016-07-30
forum: Desktop Environments
---

### Post by tys3 on 2016-07-30
I've recently noticed that I'm getting weird drop shadows under the desktop icon fonts all of a sudden. I've tried removing desktop icons and then re-adding them with no success and a system reboot doesn't resolve it either. Nothing under "Settings" -> "Desktop" -> "Icons" seems to help. I'm running Xubuntu 16.04 with an AMD R9 280 GPU.

Anyone know what might be causing this? Any help will be appreciated. Thanks.

---

### Post by Dennis N on 2016-07-30
This problem was the topic of this thread, and two solutions are there:

[https://ubuntuforums.org/showthread.php?t=2331783](https://ubuntuforums.org/showthread.php?t=2331783)

---

### Post by tys3 on 2016-07-31
Editing the **gtkrc** file and changing line 531 to read **textstyle = 0 **only removes the dark shadows, but leaves the offset white font. Also changing the theme to something else (to Greybird and using Moka icons) doesn't seem to make a difference (see attached).

---

### Post by Dennis N on 2016-07-31
Nothing will change unless you reboot your computer. Did you do that?

---

### Post by tys3 on 2016-08-01
> **Dennis N said:**
> Nothing will change unless you reboot your computer. Did you do that?

Yes. I've attached what it looks like when I make the change to the **gtkrc** file. It's still got the offset, just minus the shadow.

---

### Post by Dennis N on 2016-08-01
As I said in the other thread, I did not try the gtkrc change in Numix but just switched theme (to Greybird). Now, to test, I switched the theme back to Numix and tried out the **textstyle = 0** suggestion. Two things happened as a result: the dark shadow text is not used, AND my text aligment (of the white text) switched from left-aligned to centered. I see in yours you got rid of the shadow, but the text alignment did not change to centered - yours is still left-aligned.

Is this a general problem with your Desktop icon text? That is, are other themes aligning the text correctly to centered? 

_Note_: For me, I find it is sufficient to just log out and in to see the changes. Quicker than reboot.

I found the link to the bug report where I believe I saw those workarounds. You can study the discussion and see if any suggestions might be useful:

[https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1598316](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1598316)

The Greybird theme for me has centered text under Desktop icons, with correct shadow as it should be, so I stick with that.

---

### Post by tys3 on 2016-08-02
Yes upon checking it, other themes (Greybird at least) centre the text correctly after reboot. I'm using the Arc Theme BTW.

Thanks for the link. I'll go through it and find out if there are any possible fixes I can use.

---

