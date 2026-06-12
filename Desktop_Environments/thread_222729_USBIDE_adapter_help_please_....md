---
title: "USB/IDE adapter help please ..."
date: 2006-07-25
forum: Desktop Environments
---

### Post by jimbob on 2006-07-25
I purchased one of these USB/IDE adapters to offline store my files on old drives that were in my parts drawer.

     [http://www.pcmicrostore.com/PartDetail.aspx?q=p:10503470](http://www.pcmicrostore.com/PartDetail.aspx?q=p:10503470)

Unfortunately Linux doesn't want to recognize the USB device but wouldn't you just know it, M$ XP sees it just fine and assigns drive letter E: even without using the CD that comes with it.  Sometimes you have to give them a little credit albeit grudgingly.

If anyone out there has any experience with these things on Linux I would appreciate hearing about them.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]
 




[http://www.pcmicrostore.com/PartDetail.aspx?q=p:10503470](http://www.pcmicrostore.com/PartDetail.aspx?q=p:10503470)

---

### Post by trent dillman on 2006-07-25
Reboot with it plugged in, then check sudo fdisk -l (that's L)

You may have to manually mount the drive. I used to have to do that with a USB IDE enclosure I have (but not anymore - udev finds mine).

---

### Post by jimbob on 2006-07-25
Trent - thanks for the reply.

Problem turned out to be an intermittant HD.  My luck that it worked one time on XP and then failed to come up on Linux causing me to blame Ubuntu.

I put it in the freezer for a while (yea, really - read about this trick somewhere a long ago) and when I took it out Linux automounted it immediately.

Guess I need to find a HD that is slightly more reliable.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

