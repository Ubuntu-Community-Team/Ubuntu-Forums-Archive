---
title: "Inspiron 1150 - Problems Installing 10.04"
date: 2010-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Natan el Tigre on 2010-09-13
[COLOR=black][FONT=Tahoma]I am trying to install 10.04 on an Inspiron 1150. At present, I have two problems. The first, but seemingly least important is related to:[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]ERROR: Firmware file "b43/ucode5.fw" not found or load failed.[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]Upon searching these forums, I found the following which offers a solution to what appears to be a wireless driver problem:[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][http://www.omattos.com/node/6](http://www.omattos.com/node/6)[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]I followed the instructions, but have been unable to verify that the solution solved the problem because of my second more important problem:[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]Upon trying to install 10.04 from the Live CD, all activity ceases and the screen goes black a few seconds after the Ubuntu splash screen appears. This also occurs when I "Try Ubuntu" using the Live CD. A search through the forums pointed me to "i915.modeset=1". I was able to boot the laptop in "Try Ubuntu" mode by hitting Esc, F6, Esc, and then entering “i915.modeset=1” after "quiet splash" as outlined in the following post:[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][http://ubuntuforums.org/showthread.php?t=1463294&page=4](http://ubuntuforums.org/showthread.php?t=1463294&page=4)[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma]However, I have been unable to make this change permanent in order to boot from the hard drive. When searching the forums again, I found the following solution:[/FONT][/COLOR]
 
[COLOR=black][FONT=Tahoma][http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11)[/FONT][/COLOR]
 
[FONT=Tahoma]However, based on my very limited understanding, it appears that these instructions had me merely editing the "grub" file located on the Live CD and not on the actual hard drive. I then tried using “Alt+F2” and “gksudo nautilus” (which I use on a second working laptop to change file permissions), and it appears to work for editing the correct “grub” file, but I do not know how to make the edit permanent; my efforts to update “grub” using the terminal instruction “sudo update-grub” do not appear to work from within the Live CD environment because I am still unable to boot from the hard drive.[/FONT]
 
[FONT=Tahoma]Hopefully someone can provide me with a step-by-step solution, as I am a near-complete newbie when it comes to Linux (the two other installations I have done so far worked flawlessly). Thank you in advance for any help provided.[/FONT]

---

