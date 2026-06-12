---
title: "My video tearing nightmare"
date: 2014-01-28
forum: Desktop Environments
---

### Post by iagotorrado on 2014-01-28
I am a programming student and very recently I have decided to make the switch from Windows to Linux. I tried with Ubuntu 12.04 LTS, I tried Ubuntu 13.10, and now I am trying out Xubuntu.
I did manage to make Ubuntu 12.04 LTS work quite well, even after installing the GNOME 3 DE, but there is one problem that is making me seriously consider giving up this Linux for life project, and that is video tearing. I am experimenting with my laptop before making the jump on my Desktop PC. My laptop runs with an Nvidia GT520M.
I have tried with CompizConfig settings, Nvidia X Server settings, I have tried with Unity, GNOME 3 and XFCE. I have tried Installing Compton on XFCE (Though maybe I am doing something wrong). I just don't know what else to do. I was thinking on trying more distros like Mint, Manjaro, openSUSE or Fedora, but I fear it will be in vain...
I hope someone out there hears my call and knows how to fix this problem. Thank you very much.

Opi

---

### Post by ajgreeny on 2014-01-28
What driver do you have for the graphic card; open source or the proprietary nvidia, and if the latter which version and how did you install it?

Also having installed compton, what options did you use in the command to run it; just using **compton** will probably not be sufficient, but I'm afraid I have no knowledge of what you need for nvidia cards, having an Intel HD4000 igp here on my machine.

---

### Post by mc4man on 2014-01-28
for xfce & compton see here - 
[http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468)
(though best solution for xfwm still is to disable compositing

As far as laptop & Ubuntu, I'd just use the Intel side of card & compiz, if that has video tearing with your 520M then try 13.10 or wait for 14.04
(personally I consider 14.04 quite usable now.

Here I have a nvidia 660m & there was no tearing at all in 13.10 & now none  in 14.04 using Intel 4000. 
( nvidia-prime has loads of tearing with recent nvidia cards so for me a waste of time.

tear test video here, the bar should not 'break' on it's sides (r. click on link > 'save link as'' to download
[http://ubuntuone.com/6XdNK246Q4sGUp5X6RexIT](http://ubuntuone.com/6XdNK246Q4sGUp5X6RexIT)

---

### Post by ajgreeny on 2014-01-30
Sorry, but your tear-test video link is not valid.

Left click opens a video window which does nothing, and Right click ->"Save lnk as" just downloads an htm file.

Can you check it out for us, please.

---

### Post by mc4man on 2014-01-30
> **ajgreeny said:**
> Sorry, but your tear-test video link is not valid.

Left click opens a video window which does nothing, and Right click ->"Save lnk as" just downloads an htm file.

Can you check it out for us, please.
See no issue here (l. click opens in browser, r. click... saves as an .mp4

Maybe this will work?

---

### Post by ajgreeny on 2014-01-31
Yes, that worked.  Thanks.

No tearing here using Intel i5-3570K HD4000 graphics and compton compositor.

---

