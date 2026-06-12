---
title: "Virgin Media Mobile Broadband on Ubuntu"
date: 2009-06-22
forum: General Help
---

### Post by PaulUK on 2009-06-22
I have just bought a new netbook with Ubuntu. Have never used the OS before. I need to get a Virgin Media mobile broadband USB dongle working on it. So basically, help!

---

### Post by t0p on 2009-06-22
Read through [this thread]("http://ubuntuforums.org/showthread.php?t=1184045").  I have scattered pearls of wisdom throughout!

:p

---

### Post by 3rdalbum on 2009-06-22
Ubuntu 8.10 and above will automatically set up mobile broadband for you, if it recognises your modem.

If your netbook came with Ubuntu 8.04, I'd advise updating to 8.10 or 9.04 and plugging in the device.

---

### Post by t0p on 2009-06-22
> **3rdalbum said:**
> Ubuntu 8.10 and above will automatically set up mobile broadband for you, if it recognises your modem.


Indeed it will.  But using it this way will not let you use the device's SMS functionality.

Using the **Vodafone Mobile Connect Card Driver For Linux** as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1184045") *will* let you send SMSes.  (Don't worry about the word "Vodafone" in the program's name - it's being developed by/for Vodafone but it works with any provider.)

---

### Post by PaulUK on 2009-06-22
Thank you!

---

### Post by PaulUK on 2009-06-22
> **3rdalbum said:**
> Ubuntu 8.10 and above will automatically set up mobile broadband for you, if it recognises your modem.
 
If your netbook came with Ubuntu 8.04, I'd advise updating to 8.10 or 9.04 and plugging in the device.
 
thanks for this -can you give me an idiot's guide of how I'd go about setting the connection?  It sees the device and I can see the Virgin setup.exe files but it won't run them.  Do I not need them?  Do I just manually configure a network connection using the device?  And if so, how??!!  Like I say, I have never touched Ubuntu before so don't assume any level of technical acumen!
 
I really appreciate this . . . wife's birthday on the weekend and would love to give her a present that actually works :P

---

### Post by PaulUK on 2009-06-22
Cheekily repling to my own message to bring it back to the toip of the list and hope someone will give me a step by step ;)
 
One other piece of detail, I think I am using a netbook version of Ubuntu - desktop basically divided into four sections with big icons - internet, applications, fun and games, files.  
 
On my windows laptop I can see what the dongle dials, so presumably I just set a manual dial up connection to dial the same number and use the dongle as a modem?

---

### Post by t0p on 2009-06-22
> **PaulUK said:**
> thanks for this -can you give me an idiot's guide of how I'd go about setting the connection?  It sees the device and I can see the Virgin setup.exe files but it won't run them.  Do I not need them?  Do I just manually configure a network connection using the device?  And if so, how??!!  Like I say, I have never touched Ubuntu before so don't assume any level of technical acumen!

You don't need the Virgin setup.exe files - they are for Windows, .exes don't work in Linux (well, some work if you use the Wine Windows pseudo-emulator... but that's beside the point.  Forget the .exe files!)

When you plug the dongle into the computer, a wizard should come up offering to set up a mobile broadband connection for you.  If the wizard doesn't come up, don't worry - just right-click the network manager icon (probably up in the top right of the screen, looks like 2 computer monitors), select Edit Connections, then click to add a mobile broadband connection.  You need to select your country and your service provider - for you that'll be United Kingdom and Virgin Mobile, I assume.  Also tick the box for auto connection.  That should be it - except the wizard doesn't always get the username, password and APN (access point name) absolutely correct, so you might have to edit those settings manually if the connection doesn't work now.  Get these settings from Virgin Mobile.

And that should be it - now when you plug in the dongle, the network manager should establish a mobile broadband connection automagically!  But don't forget what I wrote earlier that you won't be able to use the device's SMS functionality this way.  If you want to do that, check out the Vodafone Mobile Connect Card Driver For Linux... as I said, it works with any provider and lets you use more functions of your dongle.

> **PaulUK said:**
> 
I really appreciate this . . . wife's birthday on the weekend and would love to give her a present that actually works :P

I hope everything works fine for her now.  Say happy birthday to her from me! :)

---

### Post by PaulUK on 2009-06-22
> **t0p said:**
> You don't need the Virgin setup.exe files - they are for Windows, .exes don't work in Linux (well, some work if you use the Wine Windows pseudo-emulator... but that's beside the point.  Forget the .exe files!)

When you plug the dongle into the computer, a wizard should come up offering to set up a mobile broadband connection for you.  If the wizard doesn't come up, don't worry - just right-click the network manager icon (probably up in the top right of the screen, looks like 2 computer monitors), select Edit Connections, then click to add a mobile broadband connection.  You need to select your country and your service provider - for you that'll be United Kingdom and Virgin Mobile, I assume.  Also tick the box for auto connection.  That should be it - except the wizard doesn't always get the username, password and APN (access point name) absolutely correct, so you might have to edit those settings manually if the connection doesn't work now.  Get these settings from Virgin Mobile.

And that should be it - now when you plug in the dongle, the network manager should establish a mobile broadband connection automagically!  But don't forget what I wrote earlier that you won't be able to use the device's SMS functionality this way.  If you want to do that, check out the Vodafone Mobile Connect Card Driver For Linux... as I said, it works with any provider and lets you use more functions of your dongle.



I hope everything works fine for her now.  Say happy birthday to her from me! :)
I actually ran some updates which installed something called Mobile Partner - which essentially mirrored the Virgin software.  Exported the Virgin settings from my windows machine to a text file, plugged them into the Ubuntu machine and hey presto, we have mobile broadband on the netbook!
Thank you so much for helping me, look for more dumb questions some time soon!
And I'll pass on your birthday regards!
Have a great day
Paul

---

### Post by jazzert100 on 2009-06-22
[SIZE=4][COLOR=RoyalBlue][COLOR=DarkSlateGray]I installed virgin mobile ,it just would not connect,turns out the auto setup give's the wrong
APN name it should be  " goto.virginmobile.uk "

Changed that and it worked right away.
Here's the original link[/COLOR]

[http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html](http://blog.computershopper.co.uk/2009/01/virgin-mobile-broadband-on-ubuntu.html)


[/COLOR][/SIZE]

---

### Post by PaulUK on 2009-06-23
Yep, that stumped me for a while until I exported to a text file from a windows machine!  Thanks for posting

---

