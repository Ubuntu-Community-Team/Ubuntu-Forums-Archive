---
title: "making internet conection"
date: 2005-11-14
forum: Desktop Environments
---

### Post by troughton on 2005-11-14
ok i am new to ubuntu and am running off a router so i just networked my computer to the router to get online but as my frends have seen me using ubuntu and i have been telling them how good it is they keep asking for it on there computers so i installed it on a frends compute the other day but was unable to get him online as he has a modem that ubuntu has found but i cant find out where to put in the detales to conect him to his internet provider and without an internet conection i cant update his system to show him the full ability of ubuntu can some one help me and tell me how to make an internet conection for him ????

---

### Post by Kyral on 2005-11-14
Uhhh what kind (56k, DSL, ISDN,Cable) of internet conn does he have?

---

### Post by not_yet on 2005-11-14
if your on dial-up 

System / Administration / Networking

choose the type of connection you have

---

### Post by troughton on 2005-11-14
it is a usb dsl conection

---

### Post by Lambert on 2005-11-14
What's the make and model number of the dsl modem?

You can look [here]("https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28dsl%29") to see if it helps.

Or search using the model number in the forums or on google. When you google add terms like ubuntu or linux to the search term. You might find a post somewhere with information.

If nothing, come back here with the information. Post the output of 

```
sudo lshw -C bus
or just
sudo lshw
```

Look specifically for the section on the dsl router.

---

### Post by troughton on 2005-11-16
it is a speed touch 330 modem but ubuntu has installed the modem that is not the problem the promblem is what program do i use to make an internet conection so i can conect to his isp with a usb modem the only option i have found that is close is under netowrking but that is for dile up conection not dsl we have the install cd and the live cd but without an internet conection we cant update the software to get the internet conection software and this is a problem i need a help with as ubuntu is now growing in speed round here as people find out about it there are now 8 users round my frends and more still pestering for it and internet conection is importent for ubuntu

---

### Post by drtvasudevan on 2005-11-16
open firefox browser and start browsing.
if you are unable to type about:config int eh url box and scroll down to network.dns.IPv6disable 
right click on the value to toggle to true.
close browser and reopen again to browse.

this worked for me.
for some reason dsl/adsl modems seem to have a problem here with the value set false.

tv

---

### Post by Lambert on 2005-11-16
Look here to see if it helps.

[https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28PPOE%29](https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28PPOE%29)

---

### Post by Original Brownster on 2005-11-16
I have a speedtouch 330 and got it working ok.

Check out this [howto]("http://www.ubuntuforums.org/showthread.php?t=44763&highlight=speedtouch+howto")

If you need any help like copys of my configs I can send them to you.

---

