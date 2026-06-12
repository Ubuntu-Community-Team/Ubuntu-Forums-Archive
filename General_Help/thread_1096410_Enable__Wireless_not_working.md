---
title: "Enable  Wireless not working"
date: 2009-03-14
forum: General Help
---

### Post by pumpkinpatch on 2009-03-14
I just upgraded to the new ubuntu and my wireless seems to be disabled.  I have tried to select enable wireless but it won't allow me.  I'm sure its something simple but what?

---

### Post by masterkoppa on 2009-03-14
This is probably do to the drivers not being open source and not being installed by default. What wireless hardware are you using.
To check this open a terminal and type:

```
lspci
```

and post the output.

---

### Post by pumpkinpatch on 2009-03-14
Command not found.

---

### Post by masterkoppa on 2009-03-14
Huh, are you sure you typed lspci correctly? As far as I know this is the correct command, just tested in my machine. Try again and make sure its typed correctly, no need for sudo or any space before or after.

---

### Post by dhysk on 2009-03-14
> **pumpkinpatch said:**
> I just upgraded to the new ubuntu and my wireless seems to be disabled.  I have tried to select enable wireless but it won't allow me.  I'm sure its something simple but what?

While you look at that two simple things to look at.  One obvious thing is do you have your wireless card's RF switch one?  Second does the command 

iwconfig

list any wireless devices if so then third is that wirless device listed someware when you do the command 

ifconfig

My laptop does this sometimes and I have to 'turn on' the wifi adapter on under the ifconfig command.  It will be listed in iwconfig but not in ifconfig


as an example I run iwconfig and one of the devices listed as having wirless extentions is eth1

its not under ifconfig so i run the command 

sudo ifconfig eth1 up

then i can check the wirless box to connect.

---

### Post by pumpkinpatch on 2009-03-15
I checked iwconfig and indeed there were no wireless extensions. I then used the ifconfig command and used the command "sudo ifconfig eth1 up" and still can't check the enable wireless box.

Sadly I don't know what the RF switch one is.  This is the problem with running ubuntu to and not being computer literate.

I checked out my wireless device and I think what you might be asking for is that its is intel corp. 3945ABG.

---

### Post by dhysk on 2009-03-15
ya if it doesn't show up under iwconfig then ifconfig wont help.  We still would like the output of the lspci command or an lsmod may help as well.  Do you know what button/buttons you have to press in windows to enable disable the wireless card?

Sounds like the wireless drivers are no longer installed if it doesn't show up under iwconfig.

helpfull info may be

Computer name/modle
did it work under ubuntu b4 the upgrade?
lspci & or lsmod print out

---

### Post by pumpkinpatch on 2009-03-15
I have never run widows so no i don't know the buttons.  I have used the buttons for ubuntu and they do not work at this time.  They worked prior to the upgrade and even for the first 3 days of the upgrade then stopped.

There is quite a large print out for lspci I assumed you wanted the Network controller information which is intel corporation Pro/wireless 3945ABG  

I have an ibm think pad, don't know the model.

---

