---
title: "D620 SSD OCZ Onyx Issues"
date: 2012-02-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cbaron0185 on 2012-02-07
hey everyone, 
I am running a Dell D620 I just bought a OCZ Onyx 32GB SSD to put in it. Before I bought it I did some research and I could not find anything anywhere saying that the drive would not work. I went with the smaller size because I just needed something for Arduino programming and small jobs. I have a server so I can stream music and movies so i was all set for space. 

Now here is the strange part and it really bothers me I can not find any information on why the SSD does not work on the this laptop at all it is running the Intel 945GM chipset.

Basically I installed the drive no issues. I ran the Ubuntu 11.10 installer from both USB Stick the install sees the drive allows me to go through the install normal. The system reboots and comes up, i start getting strange system errors when i am logged in and applications crash upon opening them. One time I got an error saying it could not mount the Onyx drive even though I was already logged in. Eventually the system will lock up and i will have to reboot, to which i get stuck at a grub rescue screen. At this screen it has no idea what the partition was formatted as even tough it was formatted for EXT4. 

When I use a live disk it sees the partitions as "unknown". I have no idea why this happens. It has never happened before, I can pop in a traditional drive with no problems. 

Any information or suggestions I am more than willing to try, or even if you can suggest a reasonably priced SSD for this model laptop. 

Thanks again everyone!

I have spend the past 2 days looking through the forums and I cannot find anything at all. I feel like i am the only one with this problem

---

### Post by cbaron0185 on 2012-02-14
Just for anyone who is looking, it looks to be something with the way the intel chipset interacts with the SSD drive because i tried the drive in another PC with a different chipset worked like a charm. 

I also went ahead and got a different (intel) SSD off of a friend popped that guy in there and works great. So no the OCZ does not appear to work in D620. 

Thanks guys.

---

