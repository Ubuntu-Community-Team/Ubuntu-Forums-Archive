---
title: "Firefox 108.0.1 display error"
date: 2023-01-01
forum: Desktop Environments
---

### Post by maverickuk on 2023-01-01
Hi,

I am relatively new to the Ubuntu desktop mostly a windows user. I had a machine at home running xubuntu for some time but this displayed an error just before xmas about no more updates. I took this as an opportunity to update the machine with fresh install etc and installed 64 bit Ubuntu 22.04. I had been running this for a few days without any problems and was tidying up things making sure updates all done etc when in software update centre it told me that there was an update for Firefox, this had been working without fault from the fresh installation. I believe the installer package for Ubuntu installed version 103 of Firefox. After i installed the Firefox update (108.0.1) it has broken it, it does not display correctly now, flashes at me in the browser area, shows what appears to be some chinese characters (not all but some) etc. Is this a known issue and been reported?

In the meantime i went back in to the sowafter download area and installed 'WEB', this also appears to have some sort of bug, everything works but when i go to close it using the 'x' top right, it locks up the computer.

Lastly I've just installed 'Chrome', at the moment this appears to be working ok.

I would like to fix the firefox issue, i am no sys admin so dont really understand the syntax of some of the Ubunut commands of what they do but i can generally follow them, I can get to terminal etc without problem.

Thanks for any help.

Kevin

---

### Post by TenPlus1 on 2023-01-01
You could try removing the Firefox snap version and installing the .deb release to see if it works for you any better - [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by maverickuk on 2023-01-01
Thank you @TenPlus1, completed this (following your link) and it all installed but same result.

Cheers

Kevin

---

### Post by ajgreeny on 2023-01-01
Sounds as if maybe your Firefox profile has problems of some sort so close Firefox then rename your hidden .mozilla folder in your home and finally start Firefox again to see if it now runs as it should.

---

### Post by maverickuk on 2023-01-02
Thanks @ajgreeny

renamed .mozilla to .oldmozilla restarted Firefox same result, checked home folder .mozilla had been re created by Forefox.

Thanks

Kevin

---

### Post by ajgreeny on 2023-01-03
A new hidden .mozilla folder is normal behaviour so don't worry about that.
Not sure why you're having those problems though, so start Firefox in terminal with command **firefox** and see if you get any warnings or error messages.

---

### Post by maverickuk on 2023-01-03
Hi ajgreeny,

These are the results

maverickuk@maverickuk-Precision-WorkStation-T7400:~$ firefox
[GFX1-]: glxtest: VA-API test failed: missing or old libva-drm library.
[2023-01-03T19:57:31Z ERROR glean_core::metrics::ping] Invalid reason code startup for ping background-update

I then closed firefox and the following appeared
[2023-01-03T19:57:53Z ERROR viaduct::backend::ffi] Missing HTTP status
[2023-01-03T19:57:53Z ERROR viaduct::backend::ffi] Missing HTTP status



I guess with the errors it may point to something?

Thanks

Kevin

---

