---
title: "Internet"
date: 2005-12-07
forum: Desktop Environments
---

### Post by KIFIKA on 2005-12-07
I have been wanting linux, and ubuntu seemed the way to start. I ordered my cd's about 4 weeks ago and i got them today when i got home from school. After writing some of the files i wanted to keep to a cd i installed it. I loved the interface and every thing, but my only problem was i couldn't connect to the internet. So i was wondering if anyone could help me. 

note: i had to re install windows :mad:  to use the internet

note 2: My ISP is bellsouth, and i have my number username and password 

so can anyone help me, so i can re install ubuntu and get started :confused: :confused:

---

### Post by mcrofutt on 2005-12-07
Hi, and welcome to Ubuntu!!!
 I think a little more information may br in order here. We'll need to know HOW you connect to the internet, i.e., DSL or dial-up. Wireless? I don't know MUCH, but chances are VERY good someone here will be able to get you hooked up!
 ENJOY the Ubuntu EXPERIENCE!:D

---

### Post by Joe_CoT on 2005-12-07
assuming you use dsl:

in the console, type
```
sudo pppoeconf
```

and be ready with your username and password.

this is assuming you connect your computer right to the dsl modem. if you use a router this shouldn't even be an issue.

---

### Post by KIFIKA on 2005-12-07
lol, yea i hope some can help..... i use Dial up

---

### Post by Joe_CoT on 2005-12-07
[How to install Dialup PPP Client (GNOME PPP)?](http://ubuntuguide.org/#gnome-ppp)

---

### Post by KIFIKA on 2005-12-07
Oh yea i guess i should mention when i was trying to figure out somthing, there was a list where i guess it would browse for your modem, and it said somthing about how you couldn't find it.   

sorry for not posting exactly what it said... but i have a short term memory ...

---

### Post by Joe_CoT on 2005-12-07
.... well, in order to tell you how to install the modem, we need to know what modem you have.

---

### Post by KIFIKA on 2005-12-07
56K V.90 modem is all i know also that link you gave me is confusing i mean i dont really understand " Q: How to install Dialup PPP Client (GNOME PPP)?

   1. Read General Notes
   2. Read How to add extra repositories?
   3.

sudo apt-get install gnome-ppp

   4. Read How to refresh GNOME panel?
   5. Applications -> Internet -> GNOME PPP"

and its really really weird because im not what you would call a computer noob.. but i guess its not that weird because i am a ubuntu noob

---

### Post by billpoo90 on 2005-12-07
sudo apt-get install gnome-ppp

Somthing like this you simply copy, open up a terminal (applications/accessories/ terminal from the start bar on the top left of the desktop).

You'll have to get used to terminal, you'll need it a lot setting up ubuntu to how you want it.

---

### Post by KIFIKA on 2005-12-08
And this will do what ? 


i think all i need to do is install my modem, but how ?

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=KIFIKA]And this will do what ? 


i think all i need to do is install my modem, but how ?[/QUOTE]
The "sudo apt-get ..." stuff is how you install stuff on Ubuntu.  Think of it like InstallShield on steroids.  The only hitch is that most of the time, you install stuff from repositories that are on the Internet.  However, the install CD is also configured as a repository, so you can use that.

The Gnome-PPP program helps you configure the Point-to-Point Protocol program (called pppd) that you need to use to connect to the Internet over dialup.  It will also do some nice things for you like dialing the modem and passing control to pppd when it detects a carrier.

---

### Post by KIFIKA on 2005-12-08
Hmmm.. i tried it and when i put it in it said that gnome-ppp was not a valid ______ ( sorry i really do have a small short term memory )

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=KIFIKA]Hmmm.. i tried it and when i put it in it said that gnome-ppp was not a valid ______ ( sorry i really do have a small short term memory )[/QUOTE]
Hmm, I think you might need to enable an extra repository to get it.  You could also just try getting pppconfig.  It is text based, but it will also help you set things up.  You run it from the terminal:
```

$ sudo pppconfig

```

---

### Post by migueljacq on 2005-12-09
pppconfig configures the modem. this is a fairly integral part of dial up internetting - however it helps to know what port your modem is on. Is it an external modem or an internal modem?

if you really want to use gnome ppp (running pppconfig will allow you to turn the modem on and off by just typing 'pon' and 'poff' in the terminal), and you can't find the repository, you can visit

[http://www.gnome-ppp.org/download.php](http://www.gnome-ppp.org/download.php)

and download the package from there and unzip it yourself.

---

### Post by kdirectorate on 2005-12-09
i am using a cable modem with a usb port on my AMD motherboard.. i also have problem connecting to the internet..pls help.. thks

---

