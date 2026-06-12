---
title: "Very annoying..."
date: 2006-02-27
forum: Desktop Environments
---

### Post by Mayseth on 2006-02-27
today was my first time installing ubuntu, everything worked and installed fine. logged in, etc. But when trying to use things like firefox or anything that "goes online". It would display an error like "host "google.ca" not found" for example. So i reinstalled my windows.. and the internet connection is fine here. Anyone have any ideas what i can do? :confused:

---

### Post by WackToMack on 2006-02-27
What type of internet connection are you using?

---

### Post by jason.b.c on 2006-02-27
> today was my first time installing ubuntu, everything worked and installed fine. logged in, etc. But when trying to use things like firefox or anything that "goes online". It would display an error like "host "google.ca" not found" for example. So i reinstalled my windows.. and the internet connection is fine here. Anyone have any ideas what i can do? 


did you activate your modem?,  set up your internet connection?, configure everything properly?;)

---

### Post by Mayseth on 2006-02-27
well to my noobish knowledge everything was setup right. i'm on a cable modem.

---

### Post by jamesr on 2006-02-27
How are you connecting to the internet broadband or dialup.

---

### Post by Mayseth on 2006-02-27
broadband

---

### Post by WackToMack on 2006-02-27
[QUOTE=Mayseth]broadband[/QUOTE]

Is your broadband internet connection setup wirelessly?

---

### Post by jamesr on 2006-02-27
Is wired or wireless to the modem from your pc?
Do you have router?


post the outputs of 
sudo ifconfig -a

---

### Post by newuser111 on 2006-02-27
it depends more on whether you are using Pppoe or DHCP

are you using a wireless card or is it connected with an ethernet cable

does your isp make you register mac addresses?

---

### Post by Mayseth on 2006-02-27
[QUOTE=newuser111]it depends more on whether you are using Pppoe or DHCP

are you using a wireless card or is it connected with an ethernet cable

does your isp make you register mac addresses?[/QUOTE]

ethernet cable, and no they dont.

---

### Post by Mayseth on 2006-02-27
ok i went back - during the installation it doesnt detect any "network hardware" but windows recognizes it..

---

### Post by RAOF on 2006-02-28
Open up a terminal:
Type "ifconfig -a".  What does it say?

If there is no "eth0" or anything but "lo", run "lspci", and we'll try to work out what sort of network card you've got (and how to get it to work in linux) from the output of that.

---

### Post by jamesr on 2006-02-28
We are all asking for the same information, could you please supply, that way, we can find out what is happening:-
> post the outputs of 
sudo ifconfig -a
Are you able to get to the console prompt?

It certainly looks, as was suggested by RAOF, at present, as if the NIC is not being recognised.

---

### Post by Swiss on 2006-02-28
a

---

### Post by az on 2006-02-28
From a terminal type

sudo pppoeconf 
and enter your ISP username and password information.

---

### Post by theturner on 2006-02-28
[QUOTE=azz]From a terminal type

sudo pppoeconf 
and enter your ISP username and password information.[/QUOTE]
He's on a cable modem - Typically they don't use any type of PPP...

---

### Post by Swiss on 2006-02-28
Goto: System>Administration>Networking. Activate all of them, then select the card you use, as defult, if that doesn't work go thru the list selecting each as defult until you find one that works, then disable the others.


That might work...

---

