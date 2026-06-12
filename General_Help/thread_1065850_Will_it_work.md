---
title: "Will it work?"
date: 2009-02-10
forum: General Help
---

### Post by Azren0 on 2009-02-10
A friend of mine has just recently started using ubuntu within OpenBox, hes had fun playing around with it and getting use to the general layout and getting a sense of how the system is laid out, but the trouble was the only way to get an network connection was to bridge the connection, Now he wants to go with a full installation of ubuntu and completely remove Windows.

Before i help him with the installation and setting up, i was wondering if either 8.04 or 8.10 will work out of the box? i have some experience with ubuntu and various Wifi fixes, so if its just the case of using a fix it shouldn't be a problem as long as im pointed in the right direction. I have not yet currently tested 8.10 on his laptop, so i was hoping to find someone who has we could give me an answer, but Any help at all would be appreciated!

The model of his laptop is; TOSHIBA EQUIUM A300D -13X 

If any other information about the system is needed, Just ask!

---

### Post by mb_webguy on 2009-02-10
My suggestion is just to boot up the LiveCD and see how it works.  The LiveCD will be slower than an actual installed OS, but it should give him a good idea of how Ubuntu will work on his system.

---

### Post by jjpcexpert on 2009-02-10
> **Azren0 said:**
> A friend of mine has just recently started using ubuntu within OpenBox, hes had fun playing around with it and getting use to the general layout and getting a sense of how the system is laid out, but the trouble was the only way to get an network connection was to bridge the connection, Now he wants to go with a full installation of ubuntu and completely remove Windows.

Before i help him with the installation and setting up, i was wondering if either 8.04 or 8.10 will work out of the box? i have some experience with ubuntu and various Wifi fixes, so if its just the case of using a fix it shouldn't be a problem as long as im pointed in the right direction. I have not yet currently tested 8.10 on his laptop, so i was hoping to find someone who has we could give me an answer, but Any help at all would be appreciated!

The model of his laptop is; TOSHIBA EQUIUM A300D -13X 

If any other information about the system is needed, Just ask!
Heck you have a big dilemma. Maybe you could go onto the Wiki, i dont have an account there.

---

### Post by jjpcexpert on 2009-02-10
> **jjpcexpert said:**
> Heck you have a big dilemma. Maybe you could go onto the Wiki, i dont have an account there.
> Or use Restricted Drivers Manager/Hardware manager.
Quoted due to importance.

---

### Post by Azren0 on 2009-02-10
When I tried 8.04 on Live CD he didn't have a network connection - That's why he we decided to use OpenBox to bridge the connection so that he could use Ubuntu with a Internet connection. If 8.10 doesn't work out the box, I was just wondering if anyone has this laptop and managed to get the systems to pick up the NIC.

Cheers

---

### Post by Bölvaður on 2009-02-10
> **Azren0 said:**
> When I tried 8.04 on Live CD he didn't have a network connection - That's why he we decided to use OpenBox to bridge the connection so that he could use Ubuntu with a Internet connection. If 8.10 doesn't work out the box, I was just wondering if anyone has this laptop and managed to get the systems to pick up the NIC.

Cheers

Yeah.. I checked out the specs and they seem pretty shy about the wireless network card, so I guess it is from a "lesser manufacturer", if so to speak.
What you can do is run the live-cd again and look for the correct model which you can find on the hardware list (type "lshw" in the terminal, applications&#8594;accessories&#8594;terminal and look for the wireless card).

You may need to use a wraparound for a windows driver for that card, but it is a problem that just needs to be tackled when it is due.

Btw you might want to tell your friend to mainly browse the internet on the virtualmachine (note that [openbox]("http://en.wikipedia.org/wiki/Openbox") is a window management system).
A guy I "know" uses ubuntu in a virtualmachine for browsing to avoid viruses.

if you need further help with the computer when you get more info on the card, you can make a new thread dedicated to that particular problem AND MAKE A DESCRIPTIVE TITLE THAT WE UNDERSTAND. Most advanced users ignore threads named "noob here" "help please" and "will it work" so you will end up with help from other beginners ^.^

---

### Post by Azren0 on 2009-02-11
Lol my bad I meant VirtualBox ^^ :P I've changed the Title for the post, I know the name wasn't very descriptive.  I'll try the LiveCD again with the command you posted and see what it gives me!

---

