---
title: "Strange networking problem"
date: 2006-01-03
forum: General Help
---

### Post by mssm on 2006-01-03
Hi,

I am a longtime reader but this is my first post. I have the following strange problem. 

My system :
AMD 64 laptop with an external USB HD with 4 partitions connected

My OS :
Breezy with the latest kernel

My wireless card : 
Atheros with AR5212 chipset(listed under device manager)

Gateways :
eth0(for wired)
ath0(for wireless)

I always work on the wired network, so I never noticed this problem before. Earlier, I had switched between the wired and wireless network but with the ethernet cable always being plugged in. Moreover, my wireless was not encrypted.

1st problem :
------------
Today, I did the following : with the ethernet cable being plugged I tried to switch to wireless network with now WEP encryption turned on. It's a 128-bit WEP encryption. The tool from System -->Administration -->Netwroking didn't allow me to type the 26-bit long hexadecimal key. I don't know what's the alternate way to do. Does the networking tool in gnome support 128-bit encryption? Kwifimanager was responding after first launch(see below).

2nd Problem
---------------
Next, I unplugged the ethernet cable. All the strange problems started occurring at this point. First, during boot it could not mount the 4 partitions of the extl. HD(later when I plugged the ethernet cable back again it could). This was really strange! Apparently, netwrok has nothing to do with mounting different partitions, right? Next, the network connection applet, synaptic etc. etc. were not working. I started kwifimanager but it's behaviour was erratic. When I clicked on 'Scan for network' button , it hangs almost everytime. After few reboots(booting and rebooting were taking exceptionally long time), I was able to run synaptic and other processes but this problem persists. From command line, I executed : 'iwlist ath0 scan'. The results was segmentation fault.

What caused this segmentation fault? I have no clue. I remember that I worked with wireless before but without WEP key and with ethernet cable plugged in, under breezy without any trouble.

What is the best software for handling wireless network under linux?

One last word : I used hoary for a month. I never had this problem.

Sorry for this long post. Any help will be highly appreciated.

---

### Post by emperon on 2006-01-06
Sorry pal, but it is unlikely you will get an answer. In deed you have clearly identified your problem with detailed hardware info. However, in my opinion it is just too specific. Try to decompose the problem in small parts and investigate over it. People here would only reply (because they know) general issues. Very few of us are kernel gurus.
Of course taking a shot is just good like yours.

Just my opinions...

---

### Post by plewisfdx on 2006-01-07
[QUOTE=mssm]The tool from System -->Administration -->Netwroking didn't allow me to type the 26-bit long hexadecimal key. I don't know what's the alternate way to do. [/QUOTE]

From the command line, try:

#iwconfig ath0 key (your key here)

Keys can be hex, with or without separation dashes, or ascii strings with a preceeding "s:" (without the quotes).

I'm not sure about any of your other problems, hope that helps.

phil

---

