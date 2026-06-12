---
title: "WHite screen and no mouse at login"
date: 2015-06-24
forum: Desktop Environments
---

### Post by Jonners59 on 2015-06-24
I tried to boot in to a PC I have not used in 2 weeks and got a white screen instead of the login window  I have tried to reinstall the nvidia card drivers (seem to be spending all my time doing this on machines these days) assuming it may be that as I have only found that to be the cause in my google searching, but that does not work either.  I have done the apt-get update and upgrade and all the apt-get clean, autoclean and autoremove and the purge nvidia, bumblebee, etc and re installing...  But makes no difference.  Even tried to reinstall lightdm.....

Also will ONLY install Nvidia-304 and nothing higher even if I select "current".  The driver it should be on is 352, the latest.

Any help, please????

Conscious that I have not submitted any outputs or other info, so please advise any cmds or like to help fix this....

Running 15.04 64-bit
linux: 3.19.0-21
Intel Core i7-4820k CPU @3.70Ghz
Nvidia GF108 GeForce GT430

---

### Post by Jonners59 on 2015-06-25
Sorted, though still have some desktop issues.

I tried all sorts including changing the bootloader to gdm, nothing made a difference.

I knew that for my card the latest nvidia driver, 352 was also it's latest but as it would not install I force installed it:
```
sudo apt-get install nvidia-352 -f
```

Loads fine now.

---

