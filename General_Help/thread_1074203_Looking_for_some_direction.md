---
title: "Looking for some direction"
date: 2009-02-18
forum: General Help
---

### Post by staf0048 on 2009-02-18
Hi everyone,

I'm trying to get my laptop to link up with my Bushnell Northstar GT so that (eventually) I might be able to use a program such as Stellarium to find objects in the sky and have my computer direct the telescope to the proper location so that I can view the real thing.  Possibly a big project, I don't know, but was wondering if anyone new of a place (website, book, etc) that would help me get started in trying to get these two computers talking to one another.  I have no idea what type of OS is on the telescope (I assume Unix, hopefully Linux), but I do know that the only connection available is via modem.

I've probably bitten off more than I can chew here, but I'm really just doing this as an experiment and learning experience.  Hopefully something good will come of it . . .

---

### Post by geraldm on 2009-02-19
I think your question needs to be much more simple.  
You need to provide details about the device, and how it is connected to your laptop.  ethernet, usb, serial ?  
The device would need a driver of some kind, so you would need to know the protocol that needs to be used.

It probably  would be easier to search for a driver for the device.  

Gerald

---

### Post by staf0048 on 2009-02-19
It's connected via modem, like what you'd use for dial-up.  I wasn't looking for someone to give me the complete answer per se, but more of a guidence on where to look for more info: resources, websites, etc, that could help me figure out how to connect to these two.  I suppose a networking book would be a good place to start??

I like your idea about searching for a driver first - that clearly would make this process a whole lot esier.

---

### Post by staf0048 on 2009-02-22
Well, no luck find the drivers I need, but I did find a book on it.  I'm posting the link to the book here in case anyone with the same curiosity comes across this thread.  

The book is called Device Drivers for Linux, and is available for download for free here:  [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

It might be a lot of work, but I've got time . . .

---

### Post by mattjackets on 2011-03-11
Sorry to bump an old thread, but very few people are interested in this system on the web.

I've been tinkering with the Bushnell Northstar goto system for a few days now and have managed to learn a little from it.  How are you interfacing it with your computer?  There is a second 4P4C modular jack on the controller, but no information on what it's purpose is...do you know what it's for?

The route I've taken is trying to reverse-engineer the ttl-level serial communication between the controller and the tripod.

To answer your question about what OS runs on the telescope, there isn't one.  The majority of the work is done by a PIC microprocessor.  As for the handheld controller, I'm not sure what kind of "brains" it has, but I doubt it's anything like embedded linux.

Anyway, if you're still reading this thread, reply with the details on how you're connecting your laptop and maybe that'll help.

---

