---
title: "Broadcast/Console Message"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Rick Myers on 2006-06-27
In Netware (at least older versions) there was a way to send a message to all users connected called Broadcast. Windows calls it a Console Message. As a system admin, I'd like to be able to send a message to everyone connected to my local network from my Ubuntu box. Does Linux in general or Ubuntu specifically provide such a thing?

---

### Post by virilc on 2008-05-31
Try:
```
wall
```
Then the cursor will go to the next line, waiting for your message. I believe you can send multiple lines by just pressing the **ENTER** key at the end of each line. Once you're done, press **CTRL+D** to send to all users logged in.

Note1: You must be logged in as root in order to send to all users. 
Note2: Only users logged in a console/terminal can receive the message.

Goodluck! :)

---

