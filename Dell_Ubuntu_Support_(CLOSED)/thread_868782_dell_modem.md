---
title: "dell modem"
date: 2008-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SVWander on 2008-07-24
I am sitting here in the dark with the power out because of hurricane Dolly. The storm has made me aware of a big problem with using Ubuntu. A week or so ago I tried to get the modem working to access my dialup account when my DSL goes out. I was never able to get it working. Does someone know where instructions might be found. There is another squall line heading this way. XP is much too slow on this Dell Inspiron 1200. I would be really grateful for any help.
Tim

I would like to point others to the solution to the problem of not having a dialup modem for the Dell Laptop. I found these sites which were helpful: 

[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=13897&query.id=8883#M13897](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=13897&query.id=8883#M13897)

And more than the one above . . . this site had all the information I needed to get my modem working. However I don't really understand what it was doing OR if it is entirely safe to do. When I added one of the repositories I got a warning message. But following the instructions I was able to get it working.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Driver_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Driver_Does_Not_Work)

---

### Post by ms_whosit on 2008-07-27
Did you read this howto:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Summary is that many softmodems are made for Windows and don't have drivers for linux. So you need to see if you have one you can use. If not, you should be able to purchase one that will work with linux. My Inspiron 1525 n came with a Conexant HSF modem and driver. It worked out of the box using wvdial. 
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

P.S. If you're using it during a storm (or even if you're not), it's important to route the line through a surge protector. I once fried my hard drive, modem, and the PCI slot the modem was in when I failed to do this (at least, that seems to be the most likely explanation.)

---

### Post by SVWander on 2008-08-01
Thank you for your help. Sorry I didn't get back to you sooner. tm

P.S. Normally during a hurricane lightening is not a major concern but the computer is needed more AFTER the storm than during it. Phone lines are repaired quicker than power lines so the need for the modem. The last major storm through here we were without power for a week. tm



> **ms_whosit said:**
> Did you read this howto:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Summary is that many softmodems are made for Windows and don't have drivers for linux. So you need to see if you have one you can use. If not, you should be able to purchase one that will work with linux. My Inspiron 1525 n came with a Conexant HSF modem and driver. It worked out of the box using wvdial. 
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

P.S. If you're using it during a storm (or even if you're not), it's important to route the line through a surge protector. I once fried my hard drive, modem, and the PCI slot the modem was in when I failed to do this (at least, that seems to be the most likely explanation.)

---

