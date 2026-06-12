---
title: "text in ubuntu is blurry but not everywhere..??"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Felix21685 on 2006-03-30
hey guys,

i thought installing the NVIDIA drivers would have helped but it didnt do anything

this does not happen only in webbrowsers it happens in terminals as well..

what happens is that when i for example maximize a terminal and i type 
kkkkkkkkkkkkkkkkkkkkkkkkkk
all across the screen every 2-3 inches on screen the font gets blurry then back to normal then to blurry and so on..

ive tried searching but didnt find quite a description like this one anywhere
thanks for the help in advance guys,

---

### Post by DJ Scribblinni on 2006-03-30
Are you using an LCD screen?  Cause I have the same problem on my second monitor which is an LCD, but the problem does not exist on my laptop.  I do know there some settings on the panel itself that adjust it, but I never get the fuzziness to go away completely...

---

### Post by rfruth on 2006-03-30
I've not heard of this (but that doesn't mean much) is it a hardware or software problem ?

---

### Post by Felix21685 on 2006-03-30
its on an LCD screen yes but doesnt happen in windows or anything.
i think its software..

---

### Post by aduckie on 2006-03-30
I remember that Microsoft had released a program that made text more visible for LCD screens. I can't remember the name of the program though. Might work with WINE or Cross?

---

### Post by Felix21685 on 2006-03-30
no one else has this problem in linux?

---

### Post by drummer on 2006-03-30
First, check your monitor settings (hardware), mine has an auto-calibrate button that gets everything in focus. Also, go to System>Preferences>Fonts and enable subpixel hinting (of something like that, i'm not at my comp atm) There are different options (4 IIRC) and one has 'LCD' in brackets next to it. Choose that one since it is best for LCD screens.

---

### Post by Felix21685 on 2006-03-31
ok thanks drummer ill try that when i reboot into linux tom morning.

---

### Post by saVe on 2006-03-31
i had the same problem with my lcd and it vanished after i turned the refresh rate down to 60hz.

---

### Post by Felix21685 on 2006-03-31
[QUOTE=saVe]i had the same problem with my lcd and it vanished after i turned the refresh rate down to 60hz.[/QUOTE]

[QUOTE=hw-tph]Ctrl+Alt+Backspace is sort of an emergency exit. Does your environment freeze so often that using this is the only way out? If not you should exit gnome gracefully using System -> Logout, or just restart the gdm script from a terminal.


Håkan[/QUOTE]


saVe !!! YOU DID IT MAN :)  saweeet  thats what it was..
awesome..
thanks alot man..it was getting annoooyyying..

man i love this forum :)
thx alot.
the refresh rate was set at 75 Hz and i changed it to 60Hz and the text is normal now.

ill add some keywords so if anyone searches for this again they can find this:
blurry text, random blur, random blurry text, screen, messed up, :)

---

### Post by beuno on 2006-11-06
I'm having the same problem.
Font is set to subpixel for LCD and refresh rate is set to 60hz.
It's a SyncMaster 740N.
Any ideas?

---

### Post by beuno on 2006-12-26
Small but desperate bump

---

