---
title: "quake 3 demo wont install"
date: 2006-12-19
forum: Gaming &amp; Leisure
---

### Post by rajeev1204 on 2006-12-19
hi
 i am not able to install q3 arena demo on my machine

this is what it says

rajeev@rajeev-desktop:~$ sh linuxq3ademo-1.11-6.x86.gz.sh
Warning: unknown mime-type for "-n" -- using "application/*"
Warning: unknown mime-type for "Verifying" -- using "application/*"
Warning: unknown mime-type for "archive" -- using "application/*"
Warning: unknown mime-type for "integrity..." -- using "application/*"
Error: no such file "-r"
Error: no such file "-n"
Error: no such file "Verifying"
Error: no such file "archive"
Error: no such file "integrity..."
OK
Warning: unknown mime-type for "-r" -- using "application/*"
Warning: unknown mime-type for "-n" -- using "application/*"
Warning: unknown mime-type for "Uncompressing Quake III Arena Demo" -- using "application/*"
Error: no such file "-r"
Error: no such file "-n"
Error: no such file "Uncompressing Quake III Arena Demo"
trap: usage: trap [-lp] [arg signal_spec ...]
rajeev@rajeev-desktop:~$



please help

rajeev

---

### Post by lamego on 2006-12-19
Try OpenArena instead:
[http://www.getdeb.net/app.php?name=openarena](http://www.getdeb.net/app.php?name=openarena)
Is easier to install and is open source...

---

### Post by rajeev1204 on 2006-12-21
hi

thanks for the link

i tried that but it wont start.Something about not finding libopenal.so.0 . but i have installed that. so what is happening?


regards

rajeev

---

### Post by lamego on 2006-12-21
I have missed to add that dependency to the package.
Go to the package manager and install the package:
libopenal0a

---

### Post by rajeev1204 on 2006-12-21
hi

i have a 64 bit version so i did a force install of ur deb,

i have installed libopenalo from package manager but its 64 bit library

it would be nice if u could add that to ur deb :) 

that way with a force install it might probably run

thanks for the deb anyway


keep it up


regards

rajeev

---

### Post by MikeeAMD64 on 2006-12-25
I'm having the exact same problem, however, I am not getting any answers from anywhere on the Internet for a solution.  

What pisses me off, is how all these Linux sites have these programs on them, but they don't tell you how to install them at all.  They just expect you to be an expert, and automatically know about chmodding files.

---

### Post by lamego on 2006-12-26
MikeeAMD64,
from GetDeb you are expected to install the program by just downloadind/opening the .deb files just as you do on other OSes. If it didn´t worked out of the box then there is a problem with the package, you can use the contact link and it will be fixed :)

---

### Post by MikeeAMD64 on 2006-12-26
I'm using Edgy on AMD64.  According to a post above, it's 32-bit and you need other packages that are 32-bit to work with it also.

---

### Post by rajeev1204 on 2006-12-29
hi 

hey lamego , i managed to get 32 bit openal but now it is asking for libvorbisfile.so.3 .

that is an unnecessary dependancy - i mean optional.

is it possible for u to remove it from the file?



regards

rajeev

---

### Post by i386DX on 2007-01-03
I have the same problem as the topicstarter. Anyone a solution?
I don't want to use OpenArena... (not at this moment)

---

### Post by rajeev1204 on 2007-01-03
hi
I think maybe the quake 3 demo is corrupt. I tried from different locations but all versions give me same error.

I finally switched to open arena

Its got the same feel .

U should try it maybe

And if u get quake3 demo to install , then let me know too .
That game is still better than openarena:) 


regards

rajeev

---

