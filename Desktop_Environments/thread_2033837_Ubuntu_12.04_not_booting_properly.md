---
title: "Ubuntu 12.04 not booting properly"
date: 2012-07-27
forum: Desktop Environments
---

### Post by Marchosius on 2012-07-27
Good day all,

I have made the choice to reinstall my pc and use ubuntu 12.04 as the actual os and not win.

Usually I used ubuntu in a vm to play around and ready my knowledge for when when or rather if I would use it as the main os of my system.

A few days ago I loaded ubuntu on a laptop of mine for use as a web test server and internet sharing. This laptop gives me no problems apart from that it is old.

However, I got myself a new pc a few weeks ago and decided to load ubuntu on it now. After a hassle I was able to install the system on the pc by disabling a few boot options in the install screen of ubuntu(F6).

When I start the system up now it loads the usual orangy background but stays on that. No login no no nothing. The only way I managed to fix this was boot and load recovery mode and from there select "the top option" to continue the boot.

I don't mind this, as I know that nearly no one will figure out this process, so my pc will be secure. But the process is redundant and time consuming having to wait to time the shift keystroke perfectly.

Can anyone point me to a solution for this?

---

### Post by oldfred on 2012-07-27
I have nomodeset in my recovery mode, but I have added it for boots until I install the nVidia proprietary driver.

When you get to grub menu, or use shift key from BIOS until menu appears, use e and look at linux line. Standard mode has splash quiet at end, the recovery mode has other settings without quiet splash to let you see boot process.

What video card/chip do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

