---
title: "Reinstall Ubuntu 18.04.1 in Dual boot."
date: 2018-08-03
forum: Desktop Environments
---

### Post by sardonic2 on 2018-08-03
**"This computer currently has Windows Boot Manager and Ubuntu 18.04.1 LTS on it ..." **

Hi, 
I need to reinstall Ubuntu. Should I proceed with the " erase Ubuntu and reinstall it..." See picture below. 

Will Ubuntu be reinstalled along side windows on its own existing partition ext4?
Thank you for your help.

[IMG]https://s20.postimg.cc/glexjzwyl/Screenshot_2_from_2018-08-03_16-06-19.jpg[/IMG]

---

### Post by ajgreeny on 2018-08-03
You must use the "Something else" option at the bottom of those choices, then re-install the partitions for Ubuntu as they are at present; any of the other choices risk overwriting the whole disk and potentially losing your Windows system.

It would be more helpful if you could show us a screenshot of a gparted window which you can open from the live ubuntu system you use for re-installing.

Please use the attachment icon (paperclip) in the toolbasr of the Reply window's text-box to add images, rather than adding inline as you did; large images make life difficult for users of mobile devices with small screens.

---

### Post by oldfred on 2018-08-03
Why are you reinstalling?

If you have issues, we often like to try to fix them, even though many times reinstall may be quick & dirty solution if you have good backups. 
If you do not have backups then repair is a better choice.

---

### Post by sardonic2 on 2018-08-03
@[URL="https://ubuntuforums.org/member.php?u=27747"][B][COLOR=#C61919][B]ajgreeny
[/B][/COLOR][/B][/URL]
Thank you, here it is!

[ATTACH=CONFIG]280623[/ATTACH]


[ATTACH=CONFIG]280622[/ATTACH]

---

### Post by sardonic2 on 2018-08-03
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")

Hi,
I have this issue and it is quite disconcerting! 

[https://ubuntuforums.org/showthread.php?t=2397439](https://ubuntuforums.org/showthread.php?t=2397439)

---

### Post by oldfred on 2018-08-03
If an upgrade you may still have Unity.
But a new install will be gnome, but you should still have choice on which to use as you log in.

---

### Post by sardonic2 on 2018-08-07
I tried to reinstall Ubuntu 18.04 with "Something else"  but it failed to install the grub " grub-efi-amd64-signed' package failed to install target " In fact I could not install Ubuntu 18.04 in dual boot at all. So what I did was to delete the Ubuntu partitions in windows10 and install a fresh Ubuntu 16.04 alongside Windows10 only to upgrade it to 18.04 and it worked perfectly.

---

