---
title: "connect to internet on ubuntu"
date: 2005-12-22
forum: Desktop Environments
---

### Post by arvsr1988 on 2005-12-22
hey... i just installed ubuntu yesterday... everything works fine and it recognizes my pcmcia card... i want to connect to the internet through ADSL and i have no clue where to look for it ... i tried system --> administration --> networking but it doesnt work...can someone help me do this asap because i wanna start using linux.... its cool and all that.... btw im a linux noob and i dont have a single clue how to input all that code and what not..... ty....

---

### Post by manicka on 2005-12-22
You were looking in the right place. The Networking control panel is where you enter you're connection details. 

Tell us more about your setup and what you tried to do.

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=arvsr1988]hey... i just installed ubuntu yesterday... everything works fine and it recognizes my pcmcia card... i want to connect to the internet through ADSL and i have no clue where to look for it ... i tried system --> administration --> networking but it doesnt work...can someone help me do this asap because i wanna start using linux.... its cool and all that.... btw im a linux noob and i dont have a single clue how to input all that code and what not..... ty....[/QUOTE]
You should start troubleshooting by reviewing this sticky and familiarizing yourself with some of the more common pitfalls:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")
If you find you are still having problems, you should post some more information about your network setup, what appears to be working or not working, etc.

---

### Post by arvsr1988 on 2005-12-22
hey whatever i click on the system-->administration menu, it doesnt work.... also on the wired ethernet thing... theres a whole bunch of commands on that thing to type... where am i supposed to type all that?? sorry... im a noob to linux...

---

### Post by manicka on 2005-12-22
[QUOTE=arvsr1988]hey whatever i click on the system-->administration menu, it doesnt work.... also on the wired ethernet thing... theres a whole bunch of commands on that thing to type... where am i supposed to type all that?? sorry... im a noob to linux...[/QUOTE]

What do you mean by 'it doesn't work' what is or is not happening?

The commands in the how-to are typed in a terminal

Applications-->Accessories-->Terminal

---

### Post by arvsr1988 on 2005-12-22
when i click system--->administration--->networking, it says starting networking for a while on the taskbar and then it goes away and nothing appears on the screen... also just to let you know the network connections symbol on the top right of the desktop (near the time) has a red circle with a white dash on it....

---

### Post by fordfan753 on 2005-12-22
[QUOTE=arvsr1988]hey whatever i click on the system-->administration menu, it doesnt work.... also on the wired ethernet thing... theres a whole bunch of commands on that thing to type... where am i supposed to type all that?? sorry... im a noob to linux...[/QUOTE]

And a noob to networking...

Tell us your layout...are you using a cable modem, adsl modem? what make/model? Is it connected through USB or Ethernet? This should help people to determine what settings you need to use.

---

### Post by arvsr1988 on 2005-12-22
hi, i'm using ADSL and its connected to my labtop via an ethernet... my labtop has a pcmcia card... pcmcia card make is TMK32 (chinese company) and modem make is xasda digital tech (chinese too)

---

### Post by fordfan753 on 2005-12-22
You should find your laptop PCMCIA ethernet card in System > Administration > Networking

You'll be able to go to properties, where you can use a static (stays the same) or a dynamic (changes itself sometimes) ip address. Personally I like static, but dynamic is easier to configure.

To set a dynamic address, check the box that says "this device is configured", then under connection settings change the box to say "DHCP", and click ok, on the screen with the devices listed you may have to activate your card using the activate button.

Hope that helps, otherwise it may be a DNS thing. Most ADSL modems/routers will function as DHCP servers, so it should work....

---

### Post by arvsr1988 on 2005-12-22
does this have to do with anything?? when i log in, there is a message that goes like this:

"could not look up internet address for gzdsl38804784 (this was the system name that i put because when i installed ubuntu it asked me how i should identify this system to my network so i put in my ADSL username, i think i need to change this too...). This may prevent gnome from operating correctly. It may be possible to correct the problem by adding gzdsl38804784 to  the file /etc/hosts"

there are two options under this message: one is "try again" and one is "Log in anyway". I clicked try again twice or thrice but the same thing appeared over and over again so i clicked "log in anyway" all the time.

i think this is the source of the problem with teh whole system administration thing.... could i get some quick help that could solve this problem and get me on to the internet?

---

### Post by fordfan753 on 2005-12-22
This probably is the source of the problem, I don't have the time now (last minute xmas shopping with friends) but when I get home I'll have a think about how to fix this.

---

### Post by arvsr1988 on 2005-12-22
hey fordfan could you get on msn please cuz its easier to fix the problem that way right?? my msn is [email]arvsr1988@hotmail.com[/email]... thanks

---

### Post by anil_robo on 2005-12-23
[quote=arvsr1988]hey fordfan could you get on msn please cuz its easier to fix the problem that way right?? my msn is [EMAIL="arvsr1988@hotmail.com"]arvsr1988@hotmail.com[/EMAIL]... thanks[/quote]
If your internet is not working, how would you come online on msn? :rolleyes:

---

### Post by arvsr1988 on 2005-12-23
Im Using My Windows Pc God!! If U Have Something Good To Say Please Say It.... I'm Really Desperate To Get This Os Fixed

---

### Post by agheba on 2005-12-23
have you tried with: 
```
sudo pppoeconf
```
from a terminal?

---

### Post by arvsr1988 on 2005-12-23
ok everyone.... ive reinstalled ubuntu and everything is good.... my network is connected.... but the problem is that i have an ADSL and i need to input my username and password. I cannot figure out where to do that because in my network properties i have an ethernet which is set to DHCP and i have a modem.  However the ADSL doesnt need a phone number to dial so i'm stuck.... please help?? quick support is appreciated

---

### Post by rikai on 2005-12-23
Who is your ISP?
What brand/model is your router?

---

### Post by fordfan753 on 2005-12-23
The ADSL settings like username and password are typed into your modem. The way to usually get to modems and routers (apart from cisco routers) is to type their IP address into the address bar of your favourite web browser. If you don't know the IP address it's usually a class A or class B....ie 10.x.x.x or 192.168.x.x

Here are the usual suspects, just go down the list till something works:
10.1.1.1
10.1.1.254
192.168.0.1
192.168.0.254
192.168.1.1
192.168.1.254

When you get the right address you'll get to a screen with input username and password, this is **not** the ISP password, but just the modem/router password, and it's normally u: admin p: admin

The next screen should have your ISP details, type them in, then save, and reboot the modem/router, to make sure they are saved in NVRAM and you're using the right configuration.

---

### Post by mike123456 on 2005-12-25
i had my adsl modem turned on when i installed ubuntu 5.10 breezy badger and when it finished installing i was on the internet,ubuntu did find the modems settings and installed it.

---

