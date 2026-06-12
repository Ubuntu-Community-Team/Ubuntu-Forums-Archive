---
title: "Having some trouble with kernel compiler gcc 4.0."
date: 2006-03-03
forum: Desktop Environments
---

### Post by kuys on 2006-03-03
I'm attempting to install the nvidia drivers for my 7800GT and I've successfully made it all the way into the installiation using the nvidia howto guide via method 2. The problem is when I try to install the drivers it says they have to be recompiled and that the my kernel's newer gcc 4.0 can't compile it correctly. I've followed the 
su
cc=export-3.4
export cc
exit
cc=export-3.4
export cc
sudo sh nvidia-pkg1.run

This is a fresh install of i386.

---

### Post by akiro.yamamoto on 2006-03-03
I think it should look like this
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC

Try this instead.
BTW: Did you already install gcc-3.4

---

### Post by kuys on 2006-03-03
[QUOTE=akiro.yamamoto]I think it should look like this
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC

Try this instead.
BTW: Did you already install gcc-3.4[/QUOTE]

That's exactly what I did. The above with the export was a typo. 
Yes I did. I followed the steps in method 2 many times. After a failed attempt do I have to start from the very first step?

---

### Post by akiro.yamamoto on 2006-03-03
what do you get with this command:
gcc -v
at the terminal.

---

### Post by kuys on 2006-03-03
[QUOTE=akiro.yamamoto]what do you get with this command:
gcc -v
at the terminal.[/QUOTE]

gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)


Should I be loading the .10 kernel release or the .9 kernel?

---

### Post by kuys on 2006-03-04
[QUOTE=kuys]gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)


Should I be loading the .10 kernel release or the .9 kernel?[/QUOTE]


Well I'm still having this problem but I was able to get this to work on my girlfriends comp which has a 6200 using method one. I would like to use method one on this computer but I have a 7800GT and I belive the drivers I should be using are 8*** range. 

Any help from the guru's out there would be much appreciated.

---

