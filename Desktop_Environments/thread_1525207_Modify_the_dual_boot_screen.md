---
title: "Modify the dual boot screen"
date: 2010-07-06
forum: Desktop Environments
---

### Post by rahul_cse25 on 2010-07-06
I have a dual boot system with Windows vista and ubuntu.The trouble which i face is that when the computer boots up my screen from which i have to select the os to boot is cluttered with useless stuff.Something like ubuntu(recovery mode),memtest etc,along with normal ubuntu and vista.Can anyone tell me how to get rid of this i just want to keep vista and ubuntu as my dual boot screen and nothing else.

kindly help.

---

### Post by cutekazuya on 2010-07-06
hi mate,

assuming you are using ubuntu 10.04

first backup the current file

```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg-backup
```

then edit the file

```
sudo gedit /boot/grub/grub.cfg
```

grub.cfg file is the one you have to edit, "menuentry" is what you want to lookout for e.g.

menuentry "Memory test (memtest86+)"

I would be very careful editing stuff in this file, you might end up not being able to boot.

---

### Post by oldfred on 2010-07-06
You are not to edit grub.cfg. It will get updated anyway with the next change to grub or kernel.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true


One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by rahul_cse25 on 2010-07-07
sorry to say i am a bit confused , are their any risks performing this operation? Is their a chance that if something goes wrong i will not be able to boot into windows vista as well,leave alone ubuntu? As i am a complete novice i am really wary of taking chances against my laptop.

---

### Post by krishnandu.sarkar on 2010-07-07
> **rahul_cse25 said:**
> sorry to say i am a bit confused , are their any risks performing this operation? Is their a chance that if something goes wrong i will not be able to boot into windows vista as well,leave alone ubuntu? As i am a complete novice i am really wary of taking chances against my laptop.

Well...I'd say why do you want to edit the GRUB menus?? The menus that you said as ususefull are really usefull. Like Ubuntu(Recovery Mode) will come handy if anytime Ubuntu refuses to boot into. Memtest always come handy to isolate problems by testing memory.

Well...knowing how you can achive what you want is different thing. Check it out...But I'd say not to apply the changes. As you may need all of them sometime.

And for the answer of your question it is YES. You may end up with nothing....both Vista and Ubuntu may become unbootable if you do not perform it carefully.

---

### Post by Parvaaz^^ on 2010-07-07
> **krishnandu.sarkar said:**
> Well...I'd say why do you want to edit the GRUB menus?? The menus that you said as ususefull are really usefull. Like Ubuntu(Recovery Mode) will come handy if anytime Ubuntu refuses to boot into. Memtest always come handy to isolate problems by testing memory.

Well...knowing how you can achive what you want is different thing. Check it out...But I'd say not to apply the changes. As you may need all of them sometime.

And for the answer of your question it is YES. You may end up with nothing....both Vista and Ubuntu may become unbootable if you do not perform it carefully.

I would recommend to abstain form using sudo commands (from my own experience) unless you are absolutely sure about what you are doing, as it was noted here that you might end up getting nothing.

---

### Post by rahul_cse25 on 2010-07-07
I did not know that they might come handy for me,anyway thanks for the valuable feedback.

---

### Post by krishnandu.sarkar on 2010-07-08
Well...If you really want then take your time to read those carefully. And always be carefull. If you are afraid I'd say keep the Ubuntu in dual boot intact, install another one in Virtual PC and then try. :)

---

