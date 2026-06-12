---
title: "Firefox getting hanged"
date: 2009-01-29
forum: General Help
---

### Post by rawfool on 2009-01-29
Hi, I'm using local internet client with 128KBPS speed. My firefox gets hanged if I try to upload or download heavy files. Wat may be the solution, plz help me out. Thanx.

---

### Post by SqRt7744 on 2009-01-29
what version of ubuntu are you using? What version of flash do you have installed? (type about:config into the addressbar). 

Do the downloads work if you right click on the link, copy the link address, then open a terminal and type

wget paste-link-address-here

?

---

### Post by rawfool on 2009-01-30
I'm using Ubuntu 8.10, and I think I installed the latest version of flash. Actually I didn't get u. can u explain it plzz. Thnx for ur reply dude. 
I'm totally new to Linux platforms and I don't even know ABC of these..I would be helpful if u guide me how to get started with UBUNTU and a few imp things to be learnt while working on Ubuntu. Thanx once again.

---

### Post by SqRt7744 on 2009-01-31
ok...well there are good resources for beginners, even here in the forums I believe. A nice book was released a few days ago for free (as pdf), you can download it and use it as a reference:
[http://www.ubuntupocketguide.com/download.html](http://www.ubuntupocketguide.com/download.html)

re. my question to you, to start a 'terminal' click on applications->accessories->terminal, then enter into the window the command i mentioned in the previous post. I would just like to find out if the problem is really firefox, or something to do with networking in general.

Re. multimedia, a good post can be found here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

have fun with ubuntu!

---

### Post by rawfool on 2009-01-31
First I should thank you for your reply and patience. Now I installed Epiphany Web browser also and I tried to upload about 50MB of data(songs) to a hosting site. The same problem is repeated, this browser also got hanged. 

And I tried that "about:config" in browser and I didn't know which address to copy from it to "wget" in terminal. 

The book you suggested is very simple to understand. Thanks once again dude.

---

### Post by SqRt7744 on 2009-01-31
oh it only happens when uploading then?

---

### Post by rawfool on 2009-02-02
I figured out the problem dude. Actually the problem is with the router, I did the same thing from my friends' computer(windows XP) and the upload got stalled. So we found out that it was the router. 

And now I found that I've installed GNU C Compiler(gcc-4.3) in my system, and I don't know how to start, write and compile C programs in it. I mean where can I find the shortcut to launch C compiler. 
Thanx.

---

### Post by SqRt7744 on 2009-02-02
> **rawfool said:**
> I figured out the problem dude. Actually the problem is with the router, I did the same thing from my friends' computer(windows XP) and the upload got stalled. So we found out that it was the router. 

And now I found that I've installed GNU C Compiler(gcc-4.3) in my system, and I don't know how to start, write and compile C programs in it. I mean where can I find the shortcut to launch C compiler. 
Thanx.

it doesnt have a "shortcut", you can install an IDE such as ajunta if you want, or write your program in any text exitor, then open a terminal window and type gcc your_program.c
to run it type ./a.out

---

### Post by rawfool on 2009-02-03
thnx buddy

---

