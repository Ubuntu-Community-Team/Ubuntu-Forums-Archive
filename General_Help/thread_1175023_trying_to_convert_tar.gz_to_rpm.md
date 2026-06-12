---
title: "trying to convert tar.gz to rpm"
date: 2009-05-31
forum: General Help
---

### Post by lilmale1 on 2009-05-31
is there a way to convert tar.gz to rpm 

i'm a newbie so please tell me clearly 

or step by step

i will appreciated it thanks

---

### Post by Tibuda on 2009-05-31
There's much more info you need to create a rpm than available in a tar.gz. You can convert rpm to deb and deb to rpm using alien, but tar.gz is different. First, why do you want to create a RPM package?

---

### Post by lilmale1 on 2009-05-31
i want to see if i can run file cx88-0.0.4.tar.gz to rpm

the original file cx88-0.0.4.tar.tar i renamed it to tar.gz

and it did unzip. looks to be and unzippable file

but no readme file is in there and cannot compile it any way

i tried ./configure, make, make install. or simply make on its own

and didn't work.


i want to run it with diffent extension and see if that will work

like rpm or deb looks to be more troubleling. so rpm is my best bet.

---

### Post by bacardiandwatermelon on 2009-05-31
What are you trying to install? Are you trying to compile something from source?

---

### Post by lilmale1 on 2009-05-31
its a like a capture card

i think i may have found that driver correctly

i got a way of checking if it works with kaffeine

it tells me weather dvb cards are present

wich is that capture card

wich is that driver i need to install cx88-0.0.4.tar.gz

yes from source

---

### Post by Tibuda on 2009-05-31
Renaming the extension won't work. Can you post a link to the website where you downloaded this file from?

---

### Post by Chronon on 2009-05-31
.deb and .rpm are like package containers.  You need to have a compiled binary already to make a functional package.  This is not a method to avoid building the source code.  

This is a cx88 driver?  Isn't that in the kernel already?

---

### Post by lilmale1 on 2009-05-31
well, somebody else said that too that it should read because its in the kernel.

but still not showing on kaffeine

---

### Post by oldos2er on 2009-05-31
What's the make/model of your DVB card?

---

### Post by lilmale1 on 2009-05-31
its a dvb-s digistar geniatech.com

card. for watching free-to -air television

it is to watch sateelite dish

---

### Post by oldos2er on 2009-06-01
Can you post the output of this command
```
dmesg | grep dvb
```
entered in a terminal?

---

### Post by lilmale1 on 2009-06-01
it doesn't show anything just goes to the same line

---

### Post by oldos2er on 2009-06-01
Please try
```
dmesg | grep video
```

---

### Post by lilmale1 on 2009-06-01
dmesg | grep video
[    1.374359] pci 0000:05:00.0: Boot video device
[   31.812224] Linux video capture interface: v2.00
[   32.944518] cx88[0]/0: registered device video0 [v4l2]

---

### Post by lilmale1 on 2009-06-02
ok i noticed v4l2 wasn't for this

and that u were righ kernel is already there for this


so how do i uninstall v4l2 

i think its messing up device

because i think i just had to follow some procedures that i found on here


[http://www.linuxtv.org/wiki/index.php/Geniatech_DVB-S_Digistar#Drivers](http://www.linuxtv.org/wiki/index.php/Geniatech_DVB-S_Digistar#Drivers)

---

### Post by yanom on 2009-06-18
RPM is horrible. If you knew how bizantine a system it is, you would avoid it. stick to DEB

---

