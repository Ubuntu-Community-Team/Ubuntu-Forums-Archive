---
title: "Screen Brightness Keeps on Fading"
date: 2009-06-10
forum: General Help
---

### Post by moldy on 2009-06-10
Hi all

I've just upgraded to 9.04.  I have a couple of issues, but the one that bugs me the most is that my screen brightness keeps on fading.  I put it up to the highest brightness, and within a minute or so, it fades to darker.  It doesn't matter whether i'm using it or not, or whether it is on power or battery.

As soon as I press the increase brightness button, it goes right back up in one hit, then starts slowly fading again.

Another problem (maybe related), is that the on screen brightness monitor doesn't correlate with the actual level of brightness.  The meter moves only fractionally.

My machine is a Dell Inspiron 630m.

I had a search, but couldn't find this exact issue.  Any ideas?

Richard

---

### Post by moldy on 2009-06-10
bump...

---

### Post by Megrimn on 2009-06-11
did you check the settings in "System>Preferences>Power management" ?

---

### Post by shenchen8571 on 2009-06-11
> **Megrimn said:**
> did you check the settings in "System>Preferences>Power management" ?

I can find nothing control area for brightness in the settings "System>Preferences>Power management".

By the way, in my ubuntu, just choose "System>Administration>NVIDIA X Server Settings", choose "Colour correction", there is a brightness controller for you, however it suits for or not depends on different types of video cards.

---

### Post by Megrimn on 2009-06-11
well, I was thinking maybe the "dim display" or "reduce brightness" checkboxes were the culprit...

I didn't know that about the nVidia x server settings, though.  I obviously need to explore that more...

---

### Post by fragos on 2009-06-11
In Power Management there are 3 tabs. On the 1st 2 there are checkboxes. On the "On Battery Power" tab there's "Reduce backlight brightness" which I turned off and "Dim display when idele" which I left on. The results were more acceptable for me.

---

### Post by shenchen8571 on 2009-06-11
> **fragos said:**
> In Power Management there are 3 tabs. On the 1st 2 there are checkboxes. On the "On Battery Power" tab there's "Reduce backlight brightness" which I turned off and "Dim display when idele" which I left on. The results were more acceptable for me.

100% Correctly.

However, I use ubuntu on iMac, there is no "On Battery Power", only can alter in "On AC Power" and "General".

I have changed screen brightness via display settings.

---

### Post by shenchen8571 on 2009-06-12
> **Megrimn said:**
> well, I was thinking maybe the "dim display" or "reduce brightness" checkboxes were the culprit...

I didn't know that about the nVidia x server settings, though.  I obviously need to explore that more...

My video card driver can be found in System>Administration>Hardware Drivers, it tests and defines automatically for me. And have or not the nVidia X driver setting depends on your type of video card. No worries about what I say. You do well! ;)

---

