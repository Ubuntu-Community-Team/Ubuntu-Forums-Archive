---
title: "SPEEDTOUCH 330 doenst work on Breezy Badger 5.10?"
date: 2005-12-13
forum: General Help
---

### Post by ElvioNeto on 2005-12-13
i have tried all tutorials i find of ubuntu and nothing even i tried other methods i used in debian based distros and nothing...

help please first time i install ubuntu but if i have no net i gona give up and move to another debian like distro

i have tested kanotix,mepis,kurumin,kalango and many others and i install this modem easely.

---

### Post by 23meg on 2005-12-13
Did you try [this]("https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo")? If you don't state where and how exactly things fail, nobody can help.

---

### Post by ElvioNeto on 2005-12-13
i use pppoe and that howto doenst help me

the problem is i cant create a bridge nas0 in ubuntu so i cant use pppoeconf 

in boot the modem apears to upload the firmware but in gnome i dont have conection

---

### Post by Original Brownster on 2005-12-13
Hi,
I have this modem but use pppoa and it works fine, I used the howto below partly and it worked for me, there is a section on pppoe so it might help you:

check out this [howto]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

Regards

---

### Post by ElvioNeto on 2005-12-13
i going to try again but a dont think its gona work

your pppoa conection dont have to create nas0 bridge

i heard about something wrong whit libatm pack i going to try to replace them


i still need help whit this! if someone have done it please post your steps

---

### Post by Original Brownster on 2005-12-13
[QUOTE=ElvioNeto]i going to try again but a dont think its gona work

your pppoa conection dont have to create nas0 bridge

i heard about something wrong whit libatm pack i going to try to replace them


i still need help whit this! if someone have done it please post your steps[/QUOTE]

Did you read the section about pppoe in the howto? This explains how to create a bridge.

Regards

OB

---

### Post by ElvioNeto on 2005-12-13
but ubuntu 5.10 dont create the bridge thats the problem LOL

i have read 2 or 3 tutorials in portuguese and spanish and that one you post too

and i cant create the nas0 bridge

in version 5.04 was fine but in 5.10 doenst work

i even try other methods i use in 5 diferent debian distros and in ubuntu doesnt work 

i found many people whit the same problem on other foruns

im getting crazy whit this LOL

---

### Post by BodyDrop on 2005-12-22
i get that too. I use pppoe and when i try to connect it states that nas0 cant be found...

incredible how it got worse with the kernels updates, i could do it fine on slack 2.4.x.

but hei, that aside, pm me or smth if you get it working plz, i'm trying to fix it too...

---

### Post by Pete051 on 2005-12-22
That modem works fine for me both for breezy and previously for hoary and warty I just followed the instructions on [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
Good luck
Pete

---

### Post by lois on 2005-12-24
Hello, sorry for jumping in. After trying about every Howtoo and driver / instalation program I found, with no succes and with no sense, the link Pete051 gave:  [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
finally worked!!!

In Ubuntu 5.10, with pppoe and ISP: Telefonica, in Spain.

Not just straight. After reinstalling Ubuntu, just in case I left some mess from prior tryings, and after following all the instructions, the modem worked perfectly but I had no conection. ifconfig showed 'nas0' and 'lo', but no 'ppp0'. I just run pppoeconf afterwards, and, hooops!, there we went.

Thanks everybody for the postings.

---

### Post by Richard Doyle on 2006-01-07
Hi, My name is Richard,
                            I am completly new to Ubuntu and have been trying to connect to the internet using Speedtouch 330 with Virgin .net with no success, any idea of where I am going wrong.
   Ubuntu does not seem to recognise this modem, is there a Linux programme missing.??

---

### Post by Richard Doyle on 2006-01-07
[QUOTE=Richard Doyle]Hi, My name is Richard,
                            I am completly new to Ubuntu and have been trying to connect to the internet using Speedtouch 330 with Virgin .net with no success, any idea of where I am going wrong.
   Ubuntu does not seem to recognise this modem, is there a Linux programme missing.??[/QUOTE]..

---

### Post by Original Brownster on 2006-01-07
[QUOTE=Richard Doyle]Hi, My name is Richard,
                            I am completly new to Ubuntu and have been trying to connect to the internet using Speedtouch 330 with Virgin .net with no success, any idea of where I am going wrong.
   Ubuntu does not seem to recognise this modem, is there a Linux programme missing.??[/QUOTE]
Hi Richard,

Yes it does work, I too am with Virgin and have a speedtouch 330. 
You need to do a bit of configuration.

follow this [Howto]("http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch+howto")

and you should be fine, my config files are below to help you.

Remember, to edit the files in the /etc/ directory that only root can edit you will need to use 'sudo gedit ...' or 'sudo vi ...' 

here is a copy of my /etc/ppp/peers/adslscript  you just need to edit the first line beginning 'user':

user 'yourname@adsl.virgin.net'
plugin pppoatm.so
0.38
noipdefault
usepeerdns
defaultroute
persist
noauth
updetach
nopcomp
noccp
novj

and as per the howto, add this line to the bottom of /etc/ppp/pap-secrets and the same in /etc/ppp/chap-secrets :

"yourname@adsl.virgin.net" * "yourpassword"

If you get stuck just shout.

Regards

---

### Post by jeffreyvergara.NET on 2006-02-09
you guys dont have any problem reconnecting? it seems my connection won't automatic reconnect after I got dc'd

---

### Post by renzokuken on 2006-02-09
i used to have this modem as well, after weeks of trying, getting close, and ultimately failing every time, i binned the little blighter and got myself an ethernet modem, problem solved !!

---

### Post by jeffreyvergara.NET on 2006-02-09
and i dont have $$$ to buy new ethernet modem. ^^

---

### Post by renzokuken on 2006-02-09
shame, cos it makes it so much easier.

mine was only about £30, i'd recommend saving up for one in the near future

---

