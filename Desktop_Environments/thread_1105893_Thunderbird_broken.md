---
title: "Thunderbird broken"
date: 2009-03-25
forum: Desktop Environments
---

### Post by kobusven on 2009-03-25
Hi

I tried to do a manual installation of the Thunderbird software, thunderbird-2.0.0.21.tar.gz, but something went horribly wrong. It seemed that TB installed correctly, but when I launch TB, it comes up with the following error message: (from the command line) "/usr/local/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory". I tried to remove the software with synaptic package manager, and to re-install it again - no luck. Can somebody please advice on what I should do, as I have to get to my archived e-mail very urgently. Kobus

---

### Post by Mujaheiden on 2009-03-25
backup your ~/.mozilla-thunderbird/ folder and install TB from synaptic.

then copy your backuped profile folder back in. if youre lucky.

Dont fool around with manual install files when you need your email anytime soon.

---

### Post by kobusven on 2009-03-26
Hi Mujaheiden - thanks for the feedback - it still does not work. When I tried to start it from the icon, it started and the icon disappeared after a while. From the command line, it still gives the same error as previously. Regards

---

### Post by Yashiro on 2009-03-26
> /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libstdc++5
/usr/share/doc/libstdc++5/copyright
/usr/share/doc/libstdc++5/README.Debian
/usr/share/doc/libstdc++5/changelog.Debian.gz
/usr/lib
/usr/lib/libstdc++.so.5.0.7
**/usr/lib/libstdc++.so.5**

Run:
> sudo apt-get install libstdc++5
> sudo ldconfig
Then try running Thunderbird.

Although it's more likely to be a path config issue if you did this from a tarball.
(And did it incorrectly.)

If you do the above, then re-install Thunderbird using the **Synaptic Package Manager** program or apt-get it should all correct itself.

I'm guessing that with 6 posts you are new? 
Best stick to using Synaptic for program updates instead of source tarballs.

---

### Post by kobusven on 2009-03-26
Hi Yashiro - thanks for the feedback - and yes - I am fairly new to Linux, although I am trying to "catch up". I got TB working again - but now - how do I get my mail back. I moved the folder to a "save" place, and copied it back, after I first started TB. I closed it and the copied it, and then opened it again - I thought it will pick up the mail settings etc, which it did not. Any Ideas? Regards

---

### Post by kobusven on 2009-03-27
Hi - Thanks for the help - I managed to solve the problem, but it seems that I have lost a few mails. Stiil looking to see if I can get them back. Regards

---

