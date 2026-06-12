---
title: "Firefox random crashes on Kubuntu (not Flash-related)"
date: 2007-01-08
forum: Desktop Environments
---

### Post by Ereza on 2007-01-08
First of all, sorry if this has already been asked several times, but I have searched in the forums and all what I found was Flash-related.

I was using Firefox 1.5 in Dapper and it worked perfectly. When Edgy appeared, I switched to it (fresh install) and I have been using Firefox 2.0.

I have always had problems with the random crashes. I read here on Ubuntu Forums that it was Flash-related, so I uninstalled it (I had v9 installed). Now I'm having the same problem.

Sometimes, it crashes when opening a new tab. Other times, when I'm just in the middle of writing something in a forum (and therefore I lose everything I wrote), and other times, for example, it dies when I open it and go to the "Bookmarks" menu.

Is there any solution to this? I tried switching to Konqueror, but I don't find it as flexible as Firefox, and I'm used to Firefox.

By the way, I only have one extension installed, Adblock Plus.

The error given when executing "firefox --verbose" from the command-line is:
*The application 'firefox-bin' lost its connection to the display :0.0; most likely the X server was shut down or you killed/destroyed the application.*

---

### Post by frodon on 2007-01-08
I think it's mainly due to firefox 2.0 itself which is far less stable than the 1.5 version. I issue random crashes as well with firefox 2.0 on both windows and linux.

---

### Post by Ereza on 2007-01-08
Thank you for your reply. However, in Windows I don't get these random crashes. Anyway, it seems to me that 2.0.0.1 crashes less than 2.0 did.

---

### Post by EtniesBMX on 2007-02-24
I am also getting more crashes (non-flash related) on Kubuntu than I am on Ubuntu or Windows with Firefox 2.0.0.1.

---

### Post by ax-ax on 2007-08-17
Me to.
(firefox starts after 'failed to open device')
```
axel@Hollywood:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libmyspell.so: undefined symbol: _ZN8Hunspell5spellEPKc
axel@Hollywood:~$  
```
:confused:
It is ReALLy annoying. Suggestions?

---

### Post by tdrusk on 2007-08-17
Firefox is a memory hog, BUT something else could be hogging more memory, causing it to crash. 

Post your system specs. Are you running wireless? If so, are you running the bcm-43xx program that installs wireless cards for broadcom?

I'm just doing some extreme guessing there, but that's what was causing crashes for me. 

I seriously think something 2 things are conflicting (be it your mouse driver and network driver or w/e) because my firefox is working perfectly.

---

### Post by ax-ax on 2007-08-18
My system:
Dell Dimension XPSR450
Pentium II MMX @ 450 MHz
nVidia TNT 1 with nv driver
some wired network card
Soundblaster something
384 MB RAM
standard PS/2 3-button mouse

I also discovered something: Firefox is Feisty but, in some way, libmyspell has upgraded to Gutsy :confused:

I think it uses to crash when i paste or write "åäö" (im from sweden)

---

### Post by vronp on 2007-10-23
I am getting this error after this morning's update to Firefox.


firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libmyspell.so: undefined symbol: _ZN8Hunspell5spellEPKc

---

