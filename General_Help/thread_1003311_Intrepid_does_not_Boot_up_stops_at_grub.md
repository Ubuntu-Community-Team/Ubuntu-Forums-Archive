---
title: "Intrepid does not Boot up: stops at grub"
date: 2008-12-06
forum: General Help
---

### Post by Gillette on 2008-12-06
I've got a laptop with XP on it. I installed Intrepid with Wubi and it was working fine. Today when I tried to boot it up it stopped at grub>. I did a chkdsk -r on windows but it did not help. 

Any suggestions on how to get Ubuntu to run again?

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> I've got a laptop with XP on it. I installed Intrepid with Wubi and it was working fine. Today when I tried to boot it up it stopped at grub>. I did a chkdsk -r on windows but it did not help. 

Any suggestions on how to get Ubuntu to run again?

hmm...going to need more details than that! yo! what exactly did the Grub menu say, when it stopped? ;) 

Cheers! :)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
Here is what the screen says:

GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists the possible 
completions of a device/filename. ESC at any time exits.]

grub>

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> Here is what the screen says:

GRUB4DOS 0.4.4 2008-10-27, MEMORY: 639K / 478M, CodeEnd: 0x42910
[Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists the possible 
completions of a device/filename. ESC at any time exits.]

grub>

hmm...it sounds like u pushed Esc after u selected the Ubuntu boot option in the dual boot menu, and then pushed "c" which starts up a command line, instead of a normal boot! ;)

To fix: simply push Esc again (that is, if ur still at that screen!), and then push Enter! this should boot ur computer into Ubuntu!

Cheers! ;)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
Nope, never pushed esc. I've tried booting a bunch of times already. When I push esc now it brings up seven items:

find /ubuntu/disks/boot/grub/menu.1st
find /ubuntu/install/boot/grub/menu.1st
find /menu.1st
find /boot/grub/menu.1st
commandline
reboot
halt

When I do the reboot option it just repeats the whole process.

---

### Post by Gillette on 2008-12-06
There is a Wubi Forum FAQ that says for 8.04:

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again."

I tried this. Took nearly an hour for Windows to do this. But it did not help. I don't know if Windows was not shut down cleanly as my kids were using it.

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> Nope, never pushed esc. I've tried booting a bunch of times already. When I push esc now it brings up seven items:

find /ubuntu/disks/boot/grub/menu.1st
find /ubuntu/install/boot/grub/menu.1st
find /menu.1st
find /boot/grub/menu.1st
commandline
reboot
halt

When I do the reboot option it just repeats the whole process.

hmm...it appears then that ur computer got redirected to the command line then, when u booted! :o and it also sounds like u might be missing a file, specifically "menu.lst"! in order to verify that that is the case, go to My Computer, select the "C" drive, go to the Ubuntu folder, go to "Disks", then "Boot", then "Grub", and check to see if "menu.lst" is there! if it isn't, then u r indeed missing a file, and u will need to obtain it, before u can boot into Ubuntu! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> There is a Wubi Forum FAQ that says for 8.04:

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again."

I tried this. Took nearly an hour for Windows to do this. But it did not help. I don't know if Windows was not shut down cleanly as my kids were using it.

yeah...chkdsk /r DOES help sometimes, but it is definitely not PERFECT!!! ;) It can not be expected to fix all boot problems...and often doesn't! the disk check did not fix my computer either, after a "crc error", and i STILL haven't got the problem fixed! :mad:

but enough about me...see if the file exists, and then post here if it does! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
There is no Discs folder. In the ubuntu folder there are three folders: docs, install, winboot.

The winboot folder contains four files: menu.1st, wubildr, wubildr, wubildr.mbr

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> There is no Discs folder. In the ubuntu folder there are three folders: docs, install, winboot.

The winboot folder contains four files: menu.1st, wubildr, wubildr, wubildr.mbr

well...THERE u have it then!!! we have discovered where the problem lies...if ur "disks" folder is missing, then the only option that i can think of is to uninstall, and then reinstall Wubi! ;) 

Cheers, though...we FOUND the problem! :)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
I found some information in the thread "Wubi Forum FAQ"

It says:

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the windows explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location."

I'm having windows search for the hidden file now.

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> I found some information in the thread "Wubi Forum FAQ"

It says:

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the windows explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location."

I'm having windows search for the hidden file now.

Good idea! ;) Let me know if it finds it or not! :)

Cheers! ;)

-jammanuser

:D

---

### Post by Gillette on 2008-12-06
No luck. Windows did not find found.000

---

### Post by Jammanuser on 2008-12-06
> **Gillette said:**
> No luck. Windows did not find found.000

hmm...i figured that!!! i have searched before my OWN computer for that file (in fact, **just** searched for it!), and never found it, either! but i have Vista, though, not XP...although i doubt that makes a difference...if the file existed, i think would be on **both** operating systems! ;)

Best advice that i can give u...is the same as before! try uninstalling and reinstalling Wubi...and then let me know if that works! :)

Cheers! ;)

-jammanuser

:D

---

### Post by Riven213 on 2008-12-06
My problem is exactly the same as Gilette described. 
I tried to install it from a Ubuntu 8.10 live cd. There were no files in the grub and boot folder as well. Currently I'm downloading ubuntu via the Wubi installer, maybe the live cd was missing somethign (although I guess its improbable...)

---

### Post by Riven213 on 2008-12-06
update: nothing changed :( I've downloaded everything anew and its just the same. damn..... anybody ?

---

### Post by ago on 2008-12-06
[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

---

### Post by Riven213 on 2008-12-06
This has been posted here already and it does not help.

---

### Post by Jammanuser on 2008-12-06
> **Riven213 said:**
> update: nothing changed :( I've downloaded everything anew and its just the same. damn..... anybody ?

hmm...did u first remove the Wubi install that u had **previously** on, which u installed with the Ubuntu LiveCD? if not, then i suggest that u do, before running the downloaded Wubi-installer! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Riven213 on 2008-12-06
I have done it every time. I tried 3 times. Nothing happens.

---

### Post by Jammanuser on 2008-12-06
> **Riven213 said:**
> I have done it every time. I tried 3 times. Nothing happens.

hmm...its VERY strange... :o i don't know why Wubi wouldn't install all of the important files...where **exactly** did u download Wubi from? was it from [HERE]("http://www.wubi-installer.org")? If it wasn't, then u may want to try downloading it from there! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Riven213 on 2008-12-06
yes, it was from here.

---

### Post by Jammanuser on 2008-12-06
> **Riven213 said:**
> yes, it was from here.

hmm...VERY odd! :o 

Well, to be **completely** honest, i have NO idea where to go from here, if u said u did indeed download Wubi from that link, and tried reinstalling it MULTIPLE times...and still obtained the same result!

Worked ok for me...

It seems like we need to wait for someone else to get here who can help... ;)

Cheers! :)

:D

---

### Post by bradch on 2008-12-06
I am having the same problem. I left my comp for a while. screensaver started running, and then I guess it hibernated. Tried moving the mouse but nothing happened, then moved scroll wheel and the background came up. The pointer was not the normal pointer, it was like the curser in a text editer. Nothing else would come up on the screen except the background. Had to hold power button to shut down. Now I have the same problem as above.I guess something happened to do with improper shutdown for me.
ubuntu 8.10 acer aspire 5735z

---

### Post by Jammanuser on 2008-12-06
> **bradch said:**
> I am having the same problem. I left my comp for a while. screensaver started running, and then I guess it hibernated. Tried moving the mouse but nothing happened, then moved scroll wheel and the background came up. The pointer was not the normal pointer, it was like the curser in a text editer. Nothing else would come up on the screen except the background. Had to hold power button to shut down. Now I have the same problem as above.I guess something happened to do with improper shutdown for me.
ubuntu 8.10 acer aspire 5735z

ok guys! it seems like we're having the same problem a LOT, by different people! ;)

bradch: I would suggest rebooting first, to make sure that the problem is consistent...if it is, then we can work from there! :)

Cheers! ):P

-jammanuser

:D

---

### Post by ramaswamyps on 2008-12-06
tried booting recovery kernel?
disable screensaver/slideshow

i have noticed it takes lot of coaxing with mouse and return key to come out of screensaver slideshow
if left on for an hour idle.
i have disabled standby, hybernation, suspend etc.
i had enabled display switch off after 20 minutes of screensaver. it does not work.
screen saver goes on and on and on.
i think the processor is high on usage at these times and it is hot to touch the side of my laptop.

---

### Post by KnutHB on 2008-12-12
I have the same problem here, I spend nearly my whole day just on getting Kubuntu to work.

I tried to install it in English and all the folders were empty, then I tried German and voila... I saw a bar going from left to right telling me it is installing! After a reboot I chose Kubuntu from the menu, I was told to press ESC if I want to enter the menu, I pressed nothing and my computer did a reboot! I tried every entry in the menu and it's always the same: my computer reboots >.<

I'm trying something now, will post after I saw the result.

----

What did I try? I copied the "boot"-folder from /ubuntu/install to /ubuntu/disks/ and restarted Windows. Now I get a new menu with other entries but none work :( Next try would be to download a Kubuntu 8.04.1 ISO and do an upgrade to 8.10. Does anyone know if there is a 8.04.1 with KDE4?

----

Well, there is a ISO with Kubuntu 8.04.1 KDE4 but it does the same as Kubuntu 8.10: Nothing, same problem >.< I will resume tomorrow.

---

