---
title: "DRBL Server. Clonezilla. How do I do this?"
date: 2008-12-09
forum: General Help
---

### Post by Roasted on 2008-12-09
I'll be pretty detailed about what I am looking for in hopes of somebody graciously helping me out.

I work for a school district. We have hundreds of computers. And yes, we have volume licensing that covers any educational computer that is on premises. I assure you there are no issues with that.

Moving along, we have a hard drive cloner. This cloner is sweet... but it has a drawback. When you clone with it, it brings the hardware profile down... meaning if I clone an HP computer to a Dell, often times the Dell will freak out when I try to boot. This is a problem, considering we have dozens of different model computers that I run across daily.

What I need is the ability to clone computers at my desk in the tech office without having to worry about what exact kind of computer it is to make this work. If Clonezilla can do what I need, I'll be sooo incredibly happy and maybe for once I'll be able to take a day off! (considering I often times work weekends as a result of not having an efficient means of getting work done, hence my interest in Clonezilla).

Several questions here.

- I have an HP computer that is a spare. P4, 1GB RAM, 80gb SATA HDD... and I also have a 10/100 5 port Netgear switch to work with. I have dozens of PCI NIC cards, all 10/100, so the amount of NICs I need won't be an issue. It says I need at least 2 NIC's in order to make Clonezilla work. How? How does this work? Do I plug in the computer with the image to one port, and the computer I want to clone to the other? Is that how that works?

...basically... does Clonezilla work off of a switch? Or does Clonezilla work off of a local machine loaded with network connections?

If I had a 24 port switch, how could I utilize that entire switch to clone other machines? Do I plug in the HP DRBL Ubuntu Server into any ole port in the switch? To the uplink port? How do I hook this up?

What I'd like:

To be blunt, here's what I'd like.

I'd like the ability to set up dozens of different computers on my own... then I'd like to use Clonezilla on these computers and "extract" the image off of them. Meaning, I'd receive an ISO file of the exact image that is on the computers in question. Basically I'd be creating a library of ISO Images for the student computers, based on the different computer models we have and whatnot.

So I could essentially make a fully loaded image for our Compaq Deskpros, along with our HP D530s and Compaq D510s. 

Then, if I ever come across another HP D530 that needs a fresh install, I can just pick that image from my little library of saved images and restore it to the computer.

How would I do this?
How would I set this DRBL server up?
How would I 'extract' images off of the test computers?
How would I wire everything up?

I've googled and googled and googled. And each time I'm still left with questions. I hope somebody here can help me... Thank you for your time in reading this!

---

### Post by Roasted on 2008-12-10
*bump*

Clonezilla is the almighty free option to Ghost and nobody has used it????

EDIT - How about this... if the above is just too crazy to set up, which by the sounds of it, it sounds like it definitely is, what if I can dual boot my work issued Dell laptop and somehow image a computer from my laptop to the computer in question?

Example - I walk in a lab. One computer is down. Bad HDD. Well I carry 1 HDD with me at all times. So then I whip out the pre-saved image that's on my Ubuntu partition... then... can I command Ubuntu on my Dell laptop to push the image to the computer in question? Without all of this server jazz?

---

### Post by johndoesacc on 2009-03-27
You can follow [the clonezilla guide on the sysadmin wiki]("http://sysadmin.wikia.com/wiki/Clonezilla"). It guides you through the CD step-by-step to backup/restore from/to a USB disk or a network server.

---

### Post by Roasted on 2009-03-27
Not to crap on Clonezilla but I never could get it working. I still use Clonezilla LiveCD faithfully but I have since moved my mass cloning to another open source cloning program that is Linux based known as FOG and have had very minimal issues. Thanks for the update though!

---

