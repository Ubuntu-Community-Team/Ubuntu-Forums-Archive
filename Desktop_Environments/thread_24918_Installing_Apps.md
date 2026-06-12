---
title: "Installing Apps"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Sleepy_Sentry on 2005-04-08
I have now installed Kubuntu and it is working. Since I don't have Internet yet, I'm going to download the latest version of ndiswrapper, put it on my USB flash drive, and then install it in Ubuntu. How (and please in a newb-friendly way) do I install it?


Thanks!

---

### Post by bored2k on 2005-04-08
sudo dpkg -i filename.deb

[http://packages.ubuntu.com/hoary/source/ndiswrapper](http://packages.ubuntu.com/hoary/source/ndiswrapper)

---

### Post by Sleepy_Sentry on 2005-04-08
Ok thanks. Do I download the source or the utils? Do I need to put the file in a special place?

Do I need Samba or a similar ultility to hook up to my Windows network to share the Internet? The computer with the Linksys wireless-g router uses Windows.

Thanks again!

---

### Post by bored2k on 2005-04-08
[QUOTE=Sleepy_Sentry]Ok thanks. Do I download the source or the utils? Do I need to put the file in a special place?

Do I need Samba or a similar ultility to hook up to my Windows network to share the Internet? The computer with the Linksys wireless-g router uses Windows.

Thanks again![/QUOTE]
 Download ndiswrapper and the utils. No special place, just fire up a terminal in the dir where the files are, and do the command I told you.

---

### Post by Sleepy_Sentry on 2005-04-08
It didn't work. Nothing happened when I typed the command. But I did get this in the terminal:
> sudo: unable to lookup kcwingwalker via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or dir                                                                            ectory


There's not supposed to be a smily in there lol. Part of the message must be the command in the forums for a smily!

---

