---
title: "kicker panel keeps failing"
date: 2006-03-28
forum: Desktop Environments
---

### Post by krait on 2006-03-28
hi,

my kde kicker panel has suddenly been giving me a lot of problems. It fails every time i log in.[gets the SIGSEGV signal] I have been forced to use gnome because of this.

I have tried reinstalling and even upgraded it to the latest 3.5.2 version, but to no avail.

I would really appreciate some help to solve this.

thanks.

this is the bug trace it gives me:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233540896 (LWP 28496)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#9  0x00000000 in ?? ()

---

### Post by krait on 2006-03-28
no one to help me with this???

cheers

---

### Post by Bukunut on 2006-03-29
krait

I know that many had the problem that the same crash would occur when they logged out but I had not heard of this when logging in, and this was a KDE bug not a specific distro problem. However I thought this was solved.
One thought on this one is to remove all your running programmes in the system tray and replace them back one by one and see if there is a problem occurs with one of them? Also remove any applets you may have additioned to the kicker bar. It may help you track down the culprit.

Bukunut
ps. What is your cpu and what kernel do you have installed? Sorry it's just something from memory stuck out when i saw "libthread_db.so.1"

---

### Post by krait on 2006-03-29
hi,

im running breezy on a IBM R51 lappie. With regards to the kernel, im sure im runnin the most up to date one from the ubuntu reps. About removing the kicker applets, how do i do that? i dont even get a few seconds to do so before it crashes. what i did instead was, completely remove and install kicker again. i even deleted the kicker-applets package, but to no avail. On running kicker frm the terminal,i get the followng:

~$ kicker
Qt: Locales not supported on X server
kbuildsycoca running...
Qt: Locales not supported on X server
qstring_to_xtp result code -2
bharath@sparta:~$ kicker: crashHandler called
KCrash: Application 'kicker' crashing...
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
Qt: Locales not supported on X server
qstring_to_xtp result code -2
Qt: Locales not supported on X server
qstring_to_xtp result code -2
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
-------------------------------------------------------------------------

so ya...

i really appreciate ur help and hope to get this solved soon.

cheers

---

### Post by krait on 2006-03-29
someone, anyone, help!!!im gettin sick of using gnome.

---

