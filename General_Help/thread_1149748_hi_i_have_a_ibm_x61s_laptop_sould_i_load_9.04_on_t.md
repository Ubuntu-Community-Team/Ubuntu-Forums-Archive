---
title: "hi i have a ibm x61s laptop sould i load 9.04 on to it"
date: 2009-05-05
forum: General Help
---

### Post by blake7 on 2009-05-05
hi i have a ibm x61s laptop sould i load 9.04 on to it, do you thjink it could run well on the laptop, also i would like to leave aspace on my hard drive  to put window on it. how can i do that????
one more thing is thier a way of loading 9.04 so when the next upgrade comes out, that i can load it on with lest trounble

thank you for your time.....:)

---

### Post by mrtomservo on 2009-05-05
I think 9.04 should run fine on your hardware, it's 1.6ghz dual core, no?

You'll need to be very careful when installing OS'es.  It doesn't sound like you're too experienced, and that's not a bad thing, but if it goes sour, make sure you have another means to get online to get help.

You can use a partition editor to partition the hard drive.  It sounds like you'll want to use about half of your drive for Windows, and half for Ubuntu.  I'd recommend making 1 partition that uses half of the hard drive space, and install Windows.  When you're done with Windows, run the Ubuntu installer and let it use the remaining unpartitioned space.

For easy upgrades, Ubuntu offers a distribution upgrade options for updates.  Some people have problems with this.  So you could also create a separate partition for your /home/ folder and store all your data there, and then when you re-install, all your data files will still be accessible. 

You'll need to do some research before taking on this project, hopefully it will go well!  :)

---

### Post by blake7 on 2009-05-05
thank you for your post

is thier somewhere i can go that does a step by step guid for partition the hard drive???
did you mean when i have a  (separate partition for your /home/ folder) are you saying that i should have 3 partition on my hard drive????

thank you very much for your time

---

### Post by mrtomservo on 2009-05-05
As far as tutorials go, i'd try google and these forums.  If you're using Linux to parition the hard drive, the program you'll probably want to use will be Gparted.  If you boot off the Ubuntu Desktop CD/DVD, it should be in the live desktop under System, Administration, and Partition Editor. There are tons of guides out there for [Gparted]("http://gparted.sourceforge.net/").  


As far as the number of partitions go, i'd say 1 for Windows, and 3 for Ubuntu if you want a separate /home folder.  But again, i'm sure there's a bunch of guides out there.  If there's something you don't understand in a guide or tutorial that you're flipping through, i'm sure someone will be more than happy to assist you!  

:)

---

### Post by BandD on 2009-05-05
There is a good tutorial here [http://www.psychocats.net/ubuntu/wubi]("http://www.psychocats.net/ubuntu/wubi") of how to install ubuntu from within Windows.

There are also many other tutorials on that site.

---

