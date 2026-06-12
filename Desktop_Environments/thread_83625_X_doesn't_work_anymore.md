---
title: "X doesn't work anymore"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Cud on 2005-10-29
Hello,
I was trying to install support for my MSI FX5700VE (nvidia) Graphics card and I installed nvidia-glx. Now when I try to boot, at the time when X would normally start I get a black black screen, and nothing else. I don't know if it has anything to do with it but I also uninstalled some packages to fix a dependency problem. Heres the list of packages:
g++ g++-3.3 language-pack-en language-pack-en-base libatk1.0-dev libc6-dev
libc6-i686 libdirectfb-dev libdirectfb-udeb-dev libexpat1-dev
libfontconfig1-dev libfreetype6-dev libglib2.0-dev
libgtk+2.0-directfb-udeb-dev libgtk2.0-dev liblive.com-dev libncursesw5-dbg
libncursesw5-dev libpango1.0-dev libpng12-dev libstdc++5-3.3-dev libx11-dev

and now I get error messages 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_DE:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Do these problems have anything to do with eachother? If so how do I fix it?

---

### Post by Cud on 2005-10-29
solved!
Uninstalled nvia-glx and then reconfigured x

---

### Post by Gezzer on 2005-10-29
after u installed nvidia-glx did u enable it
in a terminal write
sudo nvidia-glx-config enable

then restart X (ctrl+alt+backspace)

---

