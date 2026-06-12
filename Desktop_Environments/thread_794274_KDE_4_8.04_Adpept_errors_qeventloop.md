---
title: "KDE 4 8.04 Adpept errors qeventloop"
date: 2008-05-14
forum: Desktop Environments
---

### Post by robertsaron on 2008-05-14
On my room mates computer when opening Adept the errors are as below:

#24 0xb6e79f90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3

#25 0xb6e79c8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3

#26 0xb6e607df in QApplication::exec () from /usr/lib/libqt-mt.so.3

#27 0x080717b3 in ?? ()

#28 0xb664f450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6

#29 0x08071401 in ?? ()

Not much on google on these or on the forums. She even tried using synaptic and it would not load. Rebooting does not fix the issue. When attempting to uninstall synaptic this is the error it gives: Segmentation faulty tree... 0%

When installing KDE4 8.04 hardy the drive was wiped and a clean install was performed on its own dedicated drive. This was done through the GUI, this was a fresh ISO that was downloaded and installed off of a dvd, even though the image would fit on a cd. there are 3 OSes installed, KDE4 hardy, Ubuntu 8.04, and win xp.

I thought about trying the alternate install, would that fix the errors? Or is there some thing else going on? This is the first time i have seen the errors. I am going to go through the app/event logs tonite and see what else it contains in relation to adept. 

If any logs are posted, please let me know what information is needed, and how to get it.

---

### Post by Xiong Chiamiov on 2008-05-15
Hmm, something to do with the new QT packages?  Are you ok with wiping this install, or is there important stuff on it?  Is there any reason for installing Kubuntu separately from Ubuntu, rather than just installing the kubuntu-desktop package (or kde-core, depending on your needs)?  And why, oh why, are you installing KDE4?

---

### Post by robertsaron on 2008-05-19
After some more searching, I found the answer and a friend helped me out as well. Google.com/linux was not as helpful as it normally is. Even if I were to reinstall, I think the error would come back.

---

