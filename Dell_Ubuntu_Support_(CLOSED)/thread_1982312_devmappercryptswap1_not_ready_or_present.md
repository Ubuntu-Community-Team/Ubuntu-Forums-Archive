---
title: "dev/mapper/cryptswap1 not ready or present"
date: 2012-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paulm2822 on 2012-05-18
A little info/help is appreciated.  I recently installed 12.04 from a USB stick on my mini 9. I chose to encrypt the home directory.  Everything seems to work fine with the exception of one niggling message at boot. "The drive for dev/mapper/cryptswap1 is not ready yet or is not present." A prompt to wait, skip or manual... appears for a few seconds then happily goes to the log in screen

My question is ... did I do something wrong?  If not is there a way to suppress the message?  Is my home directory encrypted?

---

### Post by jbrice on 2012-05-24
You are not alone here. I have an Xubuntu desktop and an Ubuntu server on very different hardware (but both with encrypted home folders and hence encrypted swap files also) that frequently show this error on booting. I think it's probably a timing issue with an impatient boot script waiting for encrypted stuff to be made accessible. I think you can be reasonably sure your home folder is encrypted, or else the error message wouldn't be occurring. 

Even if it is your encrypted home folder that is causing this message, it's fail-safe in that if the boot process times-out on connecting to your encrypted home folder, you will know about it as your home will be inaccessible. However I suspect that it's more likely to be the encrypted swap that is holding things up, but eventually becoming available.

If, at the end of the boot you can see your home folder and you have some swap space, then all is well. Hopefully sometime someone will see the need to change some ill-chosen timing parameters in the relevant boot script.

---

### Post by timur_ba on 2012-10-25
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086)

---

