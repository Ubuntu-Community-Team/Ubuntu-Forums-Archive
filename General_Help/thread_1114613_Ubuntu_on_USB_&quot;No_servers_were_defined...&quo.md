---
title: "Ubuntu on USB: &quot;No servers were defined...&quot;"
date: 2009-04-02
forum: General Help
---

### Post by alexkrycek on 2009-04-02
Hi,

I'm a Windows/Mac user who recently decided to try out Ubuntu. So I installed Ubuntu 8.10 on my 8 GB USB drive.

Everything was going fine until recently, when at boot time I got the following error message:

"No servers were defined in the configuration file and XDMCP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration."

If I can't login (presumably because Ubuntu is on a flash drive), then I'm not sure how to fix this.

Someone on a [COLOR="Blue"]_[different forum]("http://www.linuxquestions.org/questions/linux-desktop-74/no-servers-were-defined-in-the-configuration-error-during-boot-after-editing-gdm.conf-646124/")_[/COLOR] had advised a user experiencing this problem to run the following commands:

apt-get remove --purge gdm
apt-get install gdm

I'm not even sure what these commands do, but in any case, I'm not sure where to run these. I've tried running the repair option at the beginning, but I'm told that that function is not available.

If I can't fix through Ubuntu, is there any way I can do repair work by mounting the USB drive on another computer and going through the files?

I'd appreciate any suggestions. Thanks in advance!


------------------------------
OCZ ATV 8 GB USB drive
Asus Eee PC 900
------------------------------

---

