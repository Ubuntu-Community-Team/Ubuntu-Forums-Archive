---
title: "[SOLVED] Modem/Sound Help on Dell E520"
date: 2008-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ZeroRider13 on 2008-08-10
Hey, I have a (USB)56k External mini Fax modem from USRobotics with Netzero dial up.    Everything is hooked up and ready to go, but I don;t know what to do from there.  I think it is a serial modem?  After that I put in the dial number with no *70 or anything ebcause I dont have call waiting, then I put in my username and password to netzero, but what is the modem port?  If there is ABSOLUTELY nothing I can do, what 56k modem internal, or external that is very esy to set up with netzero or ubuntu?  I also have a internal conexant 56k data/fax modem that came with the computer if that helps.  

Now with the sound, someone told me when I had Yoper to just do su -, then altasound and i went through a little configuration and my sound worked.  Now that doesnt wor with ubuntu, and I dont know what to do to make my sound work.  I have regular dell USB speakers that came with the computer. 

If anyone could help, that would be awesome, thanks so much.

---

### Post by ms_whosit on 2008-08-10
I don't know anything about NetZero or that modem, however did you see this howto:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

My dell (1525n) came with a driver for the internal conexant modem, thankfully. I was able to get it working with no trouble--I just ran wvdialconf, set the username, password, and dialup number in /etc/wvdial.conf and then did sudo wvdial.

---

### Post by ZeroRider13 on 2008-08-10
Well, Im not sure, lspci recognizes the modem, Im not sure if I can use it though, I didnt back anything up when i switched to ubuntu.  How do I edit things like that on ubuntu?  Also Im looking at the how to right now thanks

Also, that how to doesnt come with a link for us robotics modems...does it?  And how do you edit things, everytime i put what people tell me to edit into the terminal it says permission denied..what do i do, or how do i do it?  Thanks.

---

### Post by ZeroRider13 on 2008-08-10
I've done everything I can from that how to, but it wont work...just one question, when im editing that file like

Phone = 
Username =
Password =

DO I include dashes in the phone number?

If no one else can help me anymore, then what 56k modem is the easiest for ubuntu?  Also any thoughts on the sound problem?

---

### Post by ms_whosit on 2008-08-11
No dash in the phone number. For example, in my /etc/wvdial.conf file, I have (among other things) entries that look like:

Phone = 5554443332
Username = myusername
Password = mypassword

All the other entries (Init1, Init2, Modem, Baud, etc) in your /etc/wvdial.conf file should have been set when you ran 'wvdialconf' first. 

If you are getting "permission denied" errors, my guess is it is because you need to execute the commands as "root". In Ubuntu this is done by putting  sudo before the command, like say I want to start a connection by running wvdial, I would type:

$sudo wvdial

and it asks for my password, then executes the command 'wvdial'. (I always run wvdial as root--it don't seem to work correctly if I don't).

As for US Robotics modems--good luck! I don't know if they can be made to work with linux or not. But you said you have a built-in Conexant modem? Why not use that one? You may have to purchase a driver (the one mine came with is Restricted).

---

### Post by ZeroRider13 on 2008-08-11
WHen I run Wvdial it says

Internet dialer 1.60

I dont know what that means, but aside from that, I dont know I just feel like instead of buying a driver for 20 dollars, it would make more sense to buy an actual modem.  SO is there any 56k modem that is supposedto be really easy to just plug in and use?

ALso I was never asked about Init1 or 2 or anything like that that you said...wheres that, tHhanks and sorry or all the questions, Im sorta new to linux.

---

### Post by ms_whosit on 2008-08-11
Init1 and Init2 got set when I ran wvdialconf. As for your other questions, sorry I'm out of knowledge here. You might try posting in the Networking & Wireless forum--looks like they have a sticky on dialup:

[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

---

### Post by ZeroRider13 on 2008-08-13
Thanks for all your help.

---

