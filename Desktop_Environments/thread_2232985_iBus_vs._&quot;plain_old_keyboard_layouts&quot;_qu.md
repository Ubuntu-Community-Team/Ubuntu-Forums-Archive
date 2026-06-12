---
title: "iBus vs. &quot;plain old keyboard layouts&quot; question"
date: 2014-07-05
forum: Desktop Environments
---

### Post by r_avital on 2014-07-05
Sorry to bug you all with what is probably a super-silly question:

For years, I've been happily typing in English(US), French, and Spanish, using nothing but additional keyboard layouts in what used to be known as "the keyboard applet" -- currently, under System->Keyboard->layouts.  I was always able (and still am) to add up to 4 keyboard layouts (including US English) and switch between them.

Since upgrading to Trusty, I've noticed a new icon in my notification area, for iBus, that lets me do the same thing (except I can have more than 4).  I simply close it and don't worry about it, as I can still type multilingually with the keyboard layouts I had set before.

1. Is there an advantage to one over the other?  How about memory/resources?
2. If not, how do I keep iBus from loading at startup?  I've not seen it in the "startup applications" list.
3. I don't expect it's a good idea to have them both active, correct?

TIA :)

---

### Post by grahammechanical on 2014-07-05
I think that you will find that in 14.04 ibus is enabled by default. In System Settings>Language Support the Keyboard input method system is set to ibus with the option to set it to "none." I cannot tell you what effect setting the input method to "none" will have.

During the development period of Trusty Tahr I tested a few ISO images. I have since tested some Utopic Unicorn ISO images and we do get a keyboard icon in the notification area. It seems the US is default and if we select UK (as I do) we get the app-indicator with two keyboard layouts installed US and UK. Even deleting the US layout does not remove the app-indicator keyboard layout icon from the top panel. Perhaps setting the input method to "none" will achieve that.

I do not think that we have two input methods activated. Just the ibus. This is not something that I worry about. I have a Greek keyboard layout as well as UK English.

Regards.

---

### Post by r_avital on 2014-07-07
Many thanks!

---

