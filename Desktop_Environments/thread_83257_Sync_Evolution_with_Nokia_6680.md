---
title: "Sync Evolution with Nokia 6680"
date: 2005-10-28
forum: Desktop Environments
---

### Post by ossi on 2005-10-28
Hi!

Does anybody of you know how to synchronize a Nokia 6680 with the Evolution calendar or Adressbook? I would prefer synchronization over cable, but bluetooth is ok too. Do you have to use TCP/IP ? thx for advise

---

### Post by doogle on 2005-11-03
I am trying to do the same thing, if I get it working I will post up how I did it

---

### Post by gab on 2006-03-01
Found any solution yet ... I have a Nokia 6680, but no luck whit syncing Evolution ... Sending files whit blouthooth works fine.

---

### Post by patbuntu on 2006-03-08
I've tried 2 approaches to this.

1: Go to your contacts, mark all and send via bluetooth.  This creates one large vcard file with all your contacts in, which can be imported to evolution.  I know its not sync, but its a start.

2: I messed around with multisync using the instructions here:

[http://multisync.sourceforge.net/wiki/index.php?Nokia6600Instructions](http://multisync.sourceforge.net/wiki/index.php?Nokia6600Instructions)

(I know thats for a 6600 but its worth a shot).  I didn't get the bluetooth connection working, but I did manage to get a connection over t'internet to my machine.  I got about half my contacts into evolution, about a quarter of my calendar duplicated and some entries deleted.

Good luck, but be warned that you probably won't have a great deal of success with this task.  Some of the KDE phone apps whose names I can't remember have a bit more support BTW.

I believe that the Opensync project ([http://www.opensync.org/](http://www.opensync.org/)) is taking over where multisync left off, but i've not had a proper look at it yet.

-Pat

---

### Post by sundancer on 2006-03-14
There seems to be some work on SyncML in the opensync-project.
Here is the guide I'm trying ATM. [http://www.opensync.org/wiki/syncml-guide]("http://www.opensync.org/wiki/syncml-guide")
The Nokia 6680 is explicitly listed as Known to work.\\:D/

---

### Post by kingmonkey on 2006-03-17
Did you get it to work?

---

### Post by sundancer on 2006-03-17
Not yet - there are some patches on the opensync-user mailinglist to include SyncMl-over-OBEX to opensync. But I do not receive anything from my phone in the full sync (it connects, says initialising, then synchronising and finally aborts), but if i test just syncml-obex-client it fetches all contacts as vcards. Thats a progress i think :-D

---

### Post by McLogic on 2007-02-15
Phone and PDA support is really needed for business usrs. They (and I) need contacts and calendar to sync much more then we need a 3D desktop. 

The devs appear to think that once Ubuntu has a few % of the market, the device makers will want the devices to work and the makers will invest time in supporting Ubuntu. I think that it is saddly reversed -- once the devices work, then Ubuntu can grab a few % of the market.

Even when you do hear about people getting phone sync to work, they often have trouble after the first transpher. Data export/import works some of the time, but the syncing of changes never really worked.

---

