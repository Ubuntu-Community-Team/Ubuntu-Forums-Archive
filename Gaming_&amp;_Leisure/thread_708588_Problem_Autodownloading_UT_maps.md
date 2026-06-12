---
title: "Problem Autodownloading UT maps"
date: 2008-02-26
forum: Gaming &amp; Leisure
---

### Post by strik9 on 2008-02-26
Urban Terror has been running fine but when it tries to autodownload a map it says:
 "Cannot autodownload missing file(s), because the cURL library could not be loaded."
anyone have any idea as to what is causing this problem?

---

### Post by FrozenFox on 2008-02-26
Just as it says, you don't have the curl library installed. From the terminal, aptitude search curl returns a bunch of results, the one which you're probably looking for is libcurl3. Try sudo apt-get install libcurl3 in the terminal and see if that helps.

---

### Post by gokussj4nr on 2008-03-12
I had the same problem and your fix worked perfectly, all I needed was that one file, libcurl3.  Thx for you help :D

---

### Post by fdmarco3 on 2008-04-17
i am having this problem too, i have libcurl3 installed, but it's the same, it does not work.... I am in a 64 bit  machine with ubuntu 64 and the 64 version of urban terror.:(

---

### Post by viperdh on 2008-06-15
I am also having the same problem, 64bit urban terror, 64bit ubunut 8.04

Can anyone help with this?  I also have libcurl3 installed

Daniel

---

### Post by t0ddy on 2008-06-30
PT -BR

depois de dar o #apt-get install libcurl3 no terminal
faz um apt-get autoremove pra tirar as libraryes obsoletas

entra no jogo, no console dele e digita cl_curl e bate enter...
ele vai te dar 2 valores... o atual e o default, volte ao default

EN-US

after do:
#apt-get install libcurl3
try:
apt-get autoremove

then enter in game console and
change the cl_curl value back to default



\o
braço
fui

---

### Post by Light- on 2008-07-17
Entering "cl_curl" into the ingame console returns "cl_curl:command not found". also "/set cl_curl default" makes no difference.

Am I missing something here?

---

### Post by sjv123 on 2008-09-24
I also have the same problem with 64 bit ubuntu and 64 bit urban terror.
libcurl3 is already newest version.

---

### Post by perfran on 2008-10-25
just do in UrT console (AltGr+~ for me)
```
/cl_curllib /usr/lib/libcurl.so.3
```

Hope this helps :)

---

### Post by Orange Luna on 2008-11-27
thanks perfram that did the trick!  On my system it's "libcurl.so".

---

### Post by sjv123 on 2009-01-15
/cl_curllib /usr/lib/libcurl.so.3

This line worked for me too, that's great but when I exit and re enter the game I have to type it again. Is there some way to make this permanent?

---

### Post by FDBuff77 on 2009-01-22
I am a user of both Ubuntu x386 and Fedora x86_64. In my fedora install i added the following entry to the /UrbanTerror/q3ut4/autoexec.cfg file:

set cl_curllib /usr/lib64/libcurl.so.4.1.0

Obviously do a search for libcurl.so to see what path and actual filename it is on your OS.

Being that the game loads the autoexec.cfg file every time you start the app you won't have to add the command manually any more.

Hope this helps.

Happy Fraggin...

---

### Post by sebastjanp on 2009-11-02
> **perfran said:**
> just do in UrT console (AltGr+~ for me)
```
/cl_curllib /usr/lib/libcurl.so.3
```

Hope this helps :)

Thanks, it helps ;)

---

### Post by ryry46d9 on 2010-05-20
mythbuntu 10.4 64bit 
```
/cl_curllib /usr/lib32/libcurl.so.3
```
did the trick for ioUrbanTerror.i386
I get no score/ping/ammo when I try running ioUrbanTerror.x86_64 .
 saving that fix for a rainy day

---

### Post by gijoe3k on 2010-05-23
Thanks Perfan, this fixed it for me! :popcorn:

---

