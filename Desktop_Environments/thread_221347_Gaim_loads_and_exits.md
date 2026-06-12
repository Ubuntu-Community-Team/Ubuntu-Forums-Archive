---
title: "Gaim loads and exits"
date: 2006-07-23
forum: Desktop Environments
---

### Post by ssodhi on 2006-07-23
Hello.
I recently installed BreezyBadger Ubuntu straight off the cd. I updated with everything it said in the top right hand corner (I don't _think_ it did an upgrade).

Anyways I added some applications (Mostly from the "Programming" section).
To tell the truth I was like a little kid in a candy store at the time and I may have added something...bad...anyways now to the point.

When I load Gaim it logs on with the account that I told it too before I had this problem. The screen loads for literally a few seconds and just quits.


Any ideas as to what might cause this problem? I've been on google a fair bit but to tell the truth I really am at a loss as to what exactly to google.


Thanks,
Sodhi


Edit: Sorry, didn't realize I was in DapperDrake section. Trying to figure out how to delete it at the moment. If a mod was to read this, could you move it to the appropriate section, please? Sorry for the trouble.

---

### Post by Ziox on 2006-07-23
open up terminal and then type:

gaim

what does it give in return? what does it print?

---

### Post by ssodhi on 2006-07-23
"Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
[http://gaim.sourceforge.net/bug.php](http://gaim.sourceforge.net/bug.php)

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
[http://gaim.sourceforge.net/gdb.php](http://gaim.sourceforge.net/gdb.php). If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted"


Thanks for that, btw. What a nifty little thing to have built in. 
The Windows version is usually "You are an idiot. You broke teh programmez. Don't blame Microsoft."

---

### Post by amunimanghi on 2006-07-23
I would try to reinstall gaim and see if it still happens.

---

### Post by Ziox on 2006-07-23
yeah...maybe file a bug...and Windows...don't even remind me please...

EDIT: or reinstall, as suggest by amunimanghi.

---

### Post by ssodhi on 2006-07-23
Well it worked eventually. 
I followed the linky that it gave me and did a backtrace.
After a gazillion 
"(no debugging symbols found)"

I got a:
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1219709248 (LWP 10586)]
0xb6a7d711 in msn_object_new_from_string () from /usr/lib/gaim/libmsn.so


Maybe this can help solve the problem if it happens to someone else who has a  clue what that means :-)

Then it crashed and I'm having the problem again. Time to reinstall Gaim.



(Quick irrelevant question, is it "game" or "jee-aim"?)

---

### Post by Ziox on 2006-07-23
i've always pronouced it "game"...

---

### Post by ssodhi on 2006-07-23
Ok I removed completely and reinstalled an I am _still_ having this problem.


Errm...it isn't minimizing to some kind of a system tray by any chance, is it?

---

### Post by Ziox on 2006-07-23
it could be minimzing, but from the output it had returned...dont' think so

---

### Post by rune_kg on 2006-07-23
Hey

I'm in Dapper. Have the excact same problem. It started just after I logged in from MSN-messenger client on an XP box.

Cheers

Rune Kaagaard
Copenhagen

---

### Post by ssodhi on 2006-07-23
Hi,
Could you try backtracing?
I'm on Windows atm (That is how I found the PC when I got home, I swear to you :D) so I can't pull up the link that the terminal gives you.

Go to terminal, type Gaim. You get an error message of sorts with a link in it.

Post your results :-)

---

### Post by ssodhi on 2006-07-24
Holy...something..., guys!

I reformatted (I didn't have much installed as it is) and updated to Dapper.


STILL having this problem. It is really starting to do my head in, now.

---

### Post by rune_kg on 2006-07-24
> **ssodhi said:**
> Hi,
Could you try backtracing?
I'm on Windows atm (That is how I found the PC when I got home, I swear to you :D) so I can't pull up the link that the terminal gives you.

Go to terminal, type Gaim. You get an error message of sorts with a link in it.

Post your results :-)

Hey 

Did the backtrace, and what I got was this:
(gdb) bt full
#0  0xb6aa6fb1 in msn_object_new_from_string () from /usr/lib/gaim/libmsn.so
No symbol table info available.
Cannot access memory at address 0xbfebf73c

C YA

Rune Kaagaard
Copenhagen

---

