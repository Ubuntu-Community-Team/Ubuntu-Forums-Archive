---
title: "Cannot send email"
date: 2006-01-19
forum: Desktop Environments
---

### Post by mikeymouse on 2006-01-19
If I try to send an email using evolution it says ' no route to host'.
 I cannot send using  Thunderbird or Sylpheed. I can receive emails just fine with all 3 email programs.
 I am using Ubuntu 5.1 with all updates applied.
 It seems to me that the email program is not even getting out of my computer as I can get the 'no route to host' even when i am not online.
 My email configurations are correct as I have 4 other operating systems setup and working correctly. I even have ubuntu 5.1 on a small harddrive with no updates applied and i can send from evolution just fine..
 Any help would be appreciated.
 Thanks .. mikeymouse

---

### Post by darth_vector on 2006-01-19
do you have a firewall installed? are you allowing outgoing connections on port 25?
try```
telnet www.google.com 25
``` and see if you can get a connection.

---

### Post by mikeymouse on 2006-01-19
I do not have a firewall running:
I entererd in terminal what you suggested and it said..'Unable to connect  remote
hoste'
 Thanks mikeymouse

---

### Post by mikeymouse on 2006-01-20
If this means port 25 is closed how would i go about opening port 25 so I can send email?  
 Thanks  mikeymouse

---

