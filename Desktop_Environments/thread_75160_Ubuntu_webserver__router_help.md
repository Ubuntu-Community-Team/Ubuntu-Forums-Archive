---
title: "Ubuntu webserver / router help"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ixus_123 on 2005-10-13
Note:  Wasn't sure where to put this as it didn't seem to fit anywhere.  Mods if you think it would be better served in another forum area please move it for me :)

My router has dies & I want to set up my old computer as a websever to serve maybe a blog & some photos.  Is setting up ubuntu as a router (for home use say 3 computers max) just a question of buying a pci card with some ethernet sockets?

Would it be okay to have the router / firewall / webserver all running from the same box or should one really have a separate firwall first in line?

I've been thinking about using Mamboserver & Gallery - anyone have any Ubuntu tips for these or alternative software that make setting up a blog quite easy & good looking?

I notice quite a few sites have a similar look & feel to Ubuntus - it this a template / some kind of installable software?  The more help I can get the better as I have no web design experience.

thanks

---

### Post by KingBahamut on 2005-10-13
Joomla -- the Mambo team moved, is a much better solution. I love Mambo and live and breathe it =). 

Coppermine is much better than Gallery in my opinion , but thats just me. 

Yes you can have those services all running on the box, and actually if you install firestarter, you can enable connection sharing on it, and it will give you the proper sharing access to give your other boxes connection.

---

### Post by ixus_123 on 2005-10-13
Wow!  Thanks for the fast reply.  I was going to come back to this tomorrow to check for replies.

I'll checkout coppermine - thanks :)

I'm also goign to search for the needed howtos & sucj & try *& find a cheap ethernet pci card.

---

### Post by KingBahamut on 2005-10-13
[http://newegg.com](http://newegg.com) 

or

[http://pricewatch.com](http://pricewatch.com) 

I trust both sources. 
I can link you to the How Tos you need in a bit.

---

### Post by Dr. Nick on 2005-10-13
Yeah you have to connect each computer to a seperate lan card aswell, or just buy a 4 or 5 port hub and hook it to one nic, I did similar awhile ago, 2 nics 1 got "internet in" the other went out to a cheap hub uplink port and 2 computers plugged into hub.

Running them all on the same system is possible but AFAIK the system wont protect itself, only those behind it. I could be wrong but the firewall computer may be similar to a regular DMZ.

I think this site is a "template" not sure where to get it thuogh. And unfortunaltely havent used the programs mentioned.

Good Luck

---

### Post by ixus_123 on 2005-10-13
[QUOTE=Dr. Nick]Yeah you have to connect each computer to a seperate lan card aswell, or just buy a 4 or 5 port hub and hook it to one nic, I did similar awhile ago, 2 nics 1 got "internet in" the other went out to a cheap hub uplink port and 2 computers plugged into hub.

. . .

Good Luck[/QUOTE]
Dr Nick, I'm curious about this.  I only have one PCI slot to use & the motherboar has built in ethernet port.  I was hoping a card in this style would work

[http://www.digidave.co.uk/product_info.php?products_id=69&osCsid=d21985ab9acc7573925d323364b6ea25]("http://www.digidave.co.uk/product_info.php?products_id=69&osCsid=d21985ab9acc7573925d323364b6ea25")

Are you saying a etup like this wouldn't work?  I'd really like to have things as neat as possible so if I have to buy  a hub I may as well go the extra way & get a new router.

Thanks :)

---

### Post by Dr. Nick on 2005-10-13
Hmm never seen one of those :) That should work, Im really not sure, just check the chipset for linux compatabality. What I was getting at is every computer needs an IP address to connect. You can only assign 1 IP to a card so technically you would need a card for every IP or computer you wish to connect. That card says its a router so It may indeed take the IP its given and split it up for you. Which may be a bit more secure and theoretically should work. I would like someone to confirm this though as I have never gone that route before.

---

