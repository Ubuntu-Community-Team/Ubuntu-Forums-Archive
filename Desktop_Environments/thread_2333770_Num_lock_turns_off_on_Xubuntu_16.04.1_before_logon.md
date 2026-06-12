---
title: "Num lock turns off on Xubuntu 16.04.1 before logon"
date: 2016-08-12
forum: Desktop Environments
---

### Post by kahukowhai on 2016-08-12
Well. I know this topic has been canvassed many times in these forums. Some workarounds of this issue have been posted, some of which are version dependent and/or cause other problems, mostly using a program called numlockx.

I just want to see if this is a forum issue or should it be a bug report issue.

I have used Linux Mint, Lubuntu and Debian Jessie and in all of these related distributions, the num lock is not being turned off before logon on these distributions. (Naturally I have checked to see that the Num Lock is being turned ON in the Bios)

Therefore this problem appears to be specific either to Xubuntu, or Xfce, or some other component.

I have gone through the OS specific settings, many of them, and have also attempted to discover a workaround using the numlockx program. But as I do not know much about how to get specific startup applications to run, before logon, I don't know of any way of running this program to set the Num Lock to On before the login window appears.

---

### Post by Dennis N on 2016-08-13
Maybe login screen setting for Num Lock is set by lightdm (which is not your user session). numlockx would not run until after you login anyway.

---

