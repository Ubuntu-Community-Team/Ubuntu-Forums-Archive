---
title: "wireless woes what might be wrong ?"
date: 2006-01-11
forum: General Help
---

### Post by elaspeinreason on 2006-01-11
hello ubuntu community , i am a new user.
let me first thank you for the ablilty to leave windows behind. FORRREVER! :KS 
although i am loving the ubuntu thus far , i am having troubles with the wireless internet. I have searched through your forums already ( and i apologize if i missed a post that could help me ) but the ones that i have seen are either to Technical for me ( haha yes im no dummy but i am new to linux ) or didnt address the problem  

i am currently running a pentium 4 laptop that was built for me. 
- how can i access the internet from my wireless card ( linksys ) ?
- what else as a newbie should i take into consideration or familiarize myself with ?


thank you helpful posters , and have a good day.
be blissful.:p

---

### Post by Dr. Nick on 2006-01-11
Unfortunately linksys is to vague, Do you have a model number for it, also is it internal,usb,pcmcia etc.
Thier may be native drivers already, in that case open system-administration-networking and see if your card is their. If not then search around for ndiswrapper which will use windows drivers in linux. Thier are many tutorials on these forums on how to use it.
[https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation") is a good starting point for general usage to familarize yourself abit. Also go to the help under the menu and it has a nice starter guide aswell

---

### Post by elaspeinreason on 2006-01-11
thank you for the response
i am using a Wireless - B broadband router 
model number BEFW11S4-VN
it is not internal

i really dont know what to do , INTERNET IS A MUST and without it i might have to stick with windows. is there a reason it doesnt detect it right away:confused:  ?

---

### Post by carlosqueso on 2006-01-11
[QUOTE=elaspeinreason]thank you for the response
i am using a Wireless - B broadband router 
model number BEFW11S4-VN
it is not internal

i really dont know what to do , INTERNET IS A MUST and without it i might have to stick with windows. is there a reason it doesnt detect it right away:confused:  ?[/QUOTE]


That's your router.  What we need to know is what wireless card do you have in your computer, and how is it attached.  if you don't know, post the output of typing ```
lspci
``` in a terminal.

---

### Post by elaspeinreason on 2006-01-11
sorry , the wireless card is 
wireless - b 
model number WPC11 v.4 
i did try System -> Administration -> Networking and attempted to activate the ethernet it now says " the interface etho is active " , i unplugged the card and reinserted yet i cannot pick up internet.

---

### Post by elaspeinreason on 2006-01-11
also when you say "  if you don't know, post the output of typing 
Code:
lspciin a terminal. " i dont understand output of typing ?

thhanks.:)

---

### Post by carlosqueso on 2006-01-11
sure....open a terminal by going (if you use gnome) to Applications -> Accesories-> terminal, type ```
lspci
``` and it should spit out a bunch of stuff.....post that back please.

---

### Post by Dr. Nick on 2006-01-11
[quote=elaspeinreason]sorry , the wireless card is 
wireless - b 
model number WPC11 v.4 
i did try System -> Administration -> Networking and attempted to activate the ethernet it now says " the interface etho is active " , i unplugged the card and reinserted yet i cannot pick up internet.[/quote]
 
OK that helps some. If you didnt see a wireless connection option then it isnt picked up :( no big deal though hopefully. Ethernet is not your wireless so it wont do anything to help it.
 
Can you access the internet right now using your wired internet in linux? If you can open synaptic and install ndisgtk and ndiswrapper and get the cd for your wireless card if you have it.
 
 
EDIT
below are 2 tutorials for setting ndiswrapper
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper")
[https://wiki.ubuntu.com/SetupNdiswrapperHowto]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")
 
Try the first one first

---

### Post by elaspeinreason on 2006-01-11
since im working on another laptop in front of the one thats internet isnt working it would take much to long to type in EVERYTHING that was up there ( your right its alot of stuff ) , is there something that i should send back to you ? or a certain line ?

---

### Post by carlosqueso on 2006-01-11
Yeah....is there anything like "Ethernet controller:" or "Wireless Controller:"?  those lines could be helpful

---

### Post by Dr. Nick on 2006-01-11
look for something like this 0000:02:02.0 Network controller: and post what it says. If you have your ubuntu cd then put that in the non internet laptop and install ndiswrapper using the instructions in the 1st link of my above edit
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper")

---

### Post by elaspeinreason on 2006-01-11
0000:02:00.0 ethernet controller: Realtek Semiconductor Co., Ltd. RTL818OL 802.1 1b MAC ( rev 20 )

---

### Post by Dr. Nick on 2006-01-11
hmm thats your wired ethernet, any others show up? This maay not be necessary aslong as you have the driver cd that came with your card.

---

### Post by elaspeinreason on 2006-01-11
unfortunatly i dont that CD is still around, hmm let me search , but what will have to happen if i cant find it ?

---

### Post by elaspeinreason on 2006-01-11
found the CD that came with the card( soooooo happy ) , now what ?

---

### Post by Dr. Nick on 2006-01-11
[http://www.ubuntuforums.org/showthread.php?t=16054&highlight=WPC11+v.4]("http://www.ubuntuforums.org/showthread.php?t=16054&highlight=WPC11+v.4")
 
their is the instructions another user posted on that card aswell.
 
For now thugh have both your ubuntu cd and your wireles driver cd handy.
Insert your ubuntu cd into the non internet laptop and run synaptic, search ndiswrapper and istall that and the ndiswrapper-utils program and then pick up on the links above

---

### Post by Dr. Nick on 2006-01-11
Ill post a cleaner version of that here which may be easier to follow
 
1. Once ndiswrapper is installed remove your ubuntu cd and insert your wireless driver cd
2. Open the cd up and look for this file LSWLNDS5.INF, I assume thats its name going by the other thread, copy that and the .sys file of the same name to a directory on your hardrive. just make a new directory on your desktop or something and drag them 2 files over.
3 Open a terminal and get the the new directory and then
4. run this **ndiswrapper -i LSWLNDS5.INF**
5. Then run ndiswrapper -l and see if both hardware and driver/software show up as restent.
6. If so then run **sudo modprobe ndiswrapper **from a terminal
7. Use the netowork control panel to set it up

---

### Post by oldlag on 2006-01-11
Try going to System>Administration>Device Manager
Then scroll down the devices. You should see something labelled Wireless LAN Controller.

---

### Post by elaspeinreason on 2006-01-11
thank you for the instructions on how to install , im going to try that and see what happens ( be sure to check back every once in awhile ill post to check up )  as for the System>Administration>Device Manager i looked into this and i havent seen any " wireless lan controller " tabs 

thank you.

---

### Post by Dr. Nick on 2006-01-11
Good luck, I have class in a few mins so it will be a few hours before I get back.

---

### Post by timbtwisted on 2006-01-15
You may still be running into some issues because the driver provided with the card is not compatable.  If that is the case here's soemthing you'll want to try.

-  Forget about the driver that came with your card.   Use driver for RTL8180L for Windows XP from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

-  You'll have to unzip the file and then follow these steps that were also mentioned above.

- Open a terminal and get the the new directory and then
- run this sudo ndiswrapper -i NET8180.INF
-  Then run sudo ndiswrapper -l and see if both hardware and driver/software show up as restent.
- If so then run sudo modprobe ndiswrapper from a terminal
- Use the netowork control panel to set it up. System>Administration>Networking

I own this card and followed the steps just described and everything is working fine for me, so I'm fairly certain this will work for you too.

---

