---
title: "Very consistent Firefox problem"
date: 2007-12-12
forum: Desktop Environments
---

### Post by retiefdv on 2007-12-12
I use Ubuntu Feisty with Firefox as my web browser. In Firefox, I have the following add-ons installed: Google toolbar, StumbleUpon toolbar, Forecastfox, Download Statusbar, Google Browser sync, PDF download and ubufox. Each and every time when I open the third Firefox window, it goes grey and hangs completely. This happens irrespective of how many tabs I have open or which web site I am visiting. On my computer, Firefox has a definite 2 window limit!

---

### Post by SomeGuyDude on 2007-12-12
Just out of curiosity, why are you opening multiple windows? I can't really help, but with tabs I don't get the need for more than one.

---

### Post by deserthowler on 2007-12-12
I don't have all of those add-ons but I just opened 4 windows with 3 tabs each with no problems using Feisty.

Earl

---

### Post by K.Mandla on 2007-12-12
> **retiefdv said:**
> I use Ubuntu Feisty with Firefox as my web browser. In Firefox, I have the following add-ons installed: Google toolbar, StumbleUpon toolbar, Forecastfox, Download Statusbar, Google Browser sync, PDF download and ubufox. Each and every time when I open the third Firefox window, it goes grey and hangs completely. This happens irrespective of how many tabs I have open or which web site I am visiting. On my computer, Firefox has a definite 2 window limit!
Perhaps try removing one plugin at a time, and see if that has anything to do with the issue. Personally I would be suspicious of a plugin before I would be suspicious of Firefox.

---

### Post by Tweenk on 2007-12-12
Instead of removing the plugins you can also disable them in th add-ons panel, this is the same as uninstalling them but is temporary.

---

### Post by K.Mandla on 2007-12-12
Ah, thanks. I wasn't aware of that. Cheers. ;)

---

### Post by retiefdv on 2007-12-14
Thanks for all the input. The "culprit" was found to be the Google toolbar plug-in. Once that was disabled, I could open as many Firefox windows as I deemed necessary.
According to information found at the Google Toolbar help page, [http://www.google.com/support/firefox/bin/answer.py?answer=53937&hl=en](http://www.google.com/support/firefox/bin/answer.py?answer=53937&hl=en), Ubuntu 7.10 has incompatible versions of glibc and libstdc, which should explain the problem from Google's side..

---

