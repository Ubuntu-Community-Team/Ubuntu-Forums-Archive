---
title: "Multiple location in Networking"
date: 2006-02-18
forum: Desktop Environments
---

### Post by BlackJack on 2006-02-18
I have wireless at both work and home, both with different SSIDs and WEP keys. When I go into System>Administration>Networking and try to setup different locations I am defining  a new location called “Work” and another called “Home”. I configure the wireless network for each and they work just fine. 

My problem is that it only save the last one to be configured. If I configure my “Home” “Location” it saves it and everything at home works just as it should. I then configure my “Work” “Location” and behold, everything at work is just fine. However when I try to connect at home again and select the “Home” “Location”  it goes through a minute or two (seems like an awfully long time for resetting an interface) even though it says it is using the “Home” Location” it is still set with the configuration for “Work” and I need to manually re-enter the settings for my home network. It does the same thing when trying to go from home to work. I have looked in the Help files, but they seem to be for a different version of this utility and nothing matches what is actually on the screen. I was unable to find anything about this elsewhere on the forum and I hope I didn't just miss something.

Ubuntu 5.10

Anybody able to help out and give me some pointers or point me towards a “How To”?

Thanks..........

---

### Post by procras on 2006-02-18
I have been confused by the network configuration thingy.

I seem to recall that when you load a profile and then make changes to it they are not saved.

To make things stick you can try the Create new location option after you have it the way you want.

Who knows maybe this might work:-k

---

### Post by BlackJack on 2006-02-18
procras,
Tried that and alas, it did not work. If I cannot find anybody here that knows about this one my next step is to try and figure out how to write a script that will manually change the settings and then re-initialize the interface. This is kind of ugly and not the way I wanted to do it, but it would certainly work.

Thanks............

---

### Post by DavidW2 on 2006-02-19
I don't have the exact answer for you but I would like to point you in the right direction.  I knew this problem sounded familiar to something I had read so I searched my bookmarks and found this link.  Hope this helps.  :)

[http://www.wolfteck.com/ifupdown/](http://www.wolfteck.com/ifupdown/)

---

