---
title: "remote desktop viewer only shows black screen!!"
date: 2009-06-03
forum: General Help
---

### Post by Mr, Bean on 2009-06-03
Hello,
Im wondering if anyone as an idea on this problem im having using the remote desktop viewer program Vinagre on ubuntu 9.04. When i start Vinagre and input the ip address of the other computer (using Windows Vista Home Premium:() it connects but all it shows is a black screen.
If anyone as any thoughts on this please post your ideas.Also if you need additional info or screenshots just ask!

Any help is much appreciated.:p
thx (in Advance)

---

### Post by XCan on 2009-06-04
Are you logged into your Ubuntu machine?

---

### Post by Mr, Bean on 2009-06-04
Sorry for taking some time to reply, yes im logged into my Ubuntu machine 9.04

---

### Post by tenfishsticks on 2009-06-12
I'm having the same problem, except when I open vinagre, the blank screen show AND the program freezes!  It used to open and in testing it out I was able to 'remote' back to the same terminal.  Afterwards, when I start it up, I get the 'white screen of death'.  I've tried reinstalling with no luck.

I'm working in Intrepid and this is the first time I've tried to use any remote desktop functionality, so I may have screwed up some setting and that's doing it???

---

### Post by bbala2020 on 2009-09-28
When i click on Remote Desktop viewer from the menu, The whole of my screen goes blank. How to fix this? I'm using ubuntu 8.10

---

### Post by mvavrik on 2009-09-29
I'm also having this problem on Ubuntu 9.04 x86_64.  I'm looking into it and will post if I find anything useful.

---

### Post by doas777 on 2009-09-29
the problem is likely compiz on on the target machine:

when you first start the VNC session, carefully press Alt + F2
then carefully type:
```
metacity --replace
``` and hit enter
then close your vnc window and reopen it.

if that fails, try it again (since you are typing blind afterall).

alternatly you could ssh in and run the command that way (i think)

or even better look into FreeNX as an alternative to ubuntu remote desktop (VNC).

---

### Post by mvavrik on 2009-09-30
> the problem is likely compiz on on the target machine:

In my case, the "target" machine is Windows 2003.  I did read somewhere that compiz could be causing the issue on the machine your trying to remote desktop *from*.

Has anyone heard similar?

---

### Post by mvavrik on 2009-09-30
I found that 
```
rdesktop -f [IP]
```

works well for connecting to Windows machines.

---

### Post by doas777 on 2009-09-30
> **mvavrik said:**
> In my case, the "target" machine is Windows 2003.  I did read somewhere that compiz could be causing the issue on the machine your trying to remote desktop *from*.

Has anyone heard similar?


oh gotcha.
run the connect from a terminal as someone else suggested and make not of the error message.
 I found that i could not rdp into some windows boxen when windows had certian versions of the nvidia driver.

---

### Post by VastOne on 2010-03-19
> **doas777 said:**
> the problem is likely compiz on on the target machine:

when you first start the VNC session, carefully press Alt + F2
then carefully type:
```
metacity --replace
``` and hit enter
then close your vnc window and reopen it.

This worked for me and I appreciate your help.

---

