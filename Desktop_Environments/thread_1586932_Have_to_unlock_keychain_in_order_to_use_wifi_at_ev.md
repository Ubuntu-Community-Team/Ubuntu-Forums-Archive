---
title: "Have to unlock keychain in order to use wifi at every login"
date: 2010-10-02
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-10-02
I've got a recurring problem on the latest install of Ubuntu 10.4 64 Bit. Everytime I log in, in order to use establish a wifi connection I have to enter my password again to unlock the system keychain. Until I do this no Wifi connection is established.

I've got the system setup on an Acer Aspire Revo which has an RaLink rt3090 card in it. I was using the 2.1.3 driver but have updated to the latest .7 driver and still have them same problem but I suspect this is some sort issue with Ubuntu rather than the driver.

The machine is setup as an HTPC to logs in automatically and boots up Boxee which needs an internet connection so it'd be great to get the internet working from the get go rather than having to enter the password again.

Anyone got any ideas why I'm being asked to unlock the key chain again and to stop this from happening so the wifi works immediately after logged in.

---

### Post by Chris1274 on 2010-10-02
Applications > Accessories > Passwords and Encryption Keys

Right-click on** Passwords: login **and select "Change password." Enter your current password and leave the spaces for the new password blank. It'll ask if you want to continue with "unsafe storage." Click yes.

---

### Post by juliushibert63 on 2010-10-03
Thanks for the amazingly speedy response. It was the default entry in the password application that had to be changed. 

Is there any other way of doing this as obviously as stated when changing the password to a blank one it's leaving my machine vulnerable?

---

### Post by 3Miro on 2010-10-04
Asking people to identify themselves before they can do something is safe. Not asking people for identification is not safe. This is as simple as that.

If you are the only user on your machine and you make sure nobody else uses it/steals it, then not having a keyring password should be fine. Otherwise, the keyring stores more than wifi passwords and even with just the wifi, if some one else gets access to your home wifi, they can hurt you badly.

---

### Post by juliushibert63 on 2010-10-04
> **3Miro said:**
> Asking people to identify themselves before they can do something is safe. Not asking people for identification is not safe. This is as simple as that.

If you are the only user on your machine and you make sure nobody else uses it/steals it, then not having a keyring password should be fine. Otherwise, the keyring stores more than wifi passwords and even with just the wifi, if some one else gets access to your home wifi, they can hurt you badly.

That sort of makes sense. But is there anyway to just allow access to have a blank password for the keychain/wifi part and lock down the rest of the keychain access. The machine is setup as a HTPC so it's in our lounge where more than one person uses it. And I guess like always there's the potential risk of it being stolen, however it's not really used for anything more than download/streaming media and the odd bit of web browsing.

---

### Post by 3Miro on 2010-10-04
> **juliushibert63 said:**
> That sort of makes sense. But is there anyway to just allow access to have a blank password for the keychain/wifi part and lock down the rest of the keychain access. The machine is setup as a HTPC so it's in our lounge where more than one person uses it. And I guess like always there's the potential risk of it being stolen, however it's not really used for anything more than download/streaming media and the odd bit of web browsing.

I am not sure if you can remove the network from the keyring, maybe there is some way to set the Network Manager applet. Maybe if you make it "available to all users".

Having said that, note that there are ways for people to hurt you, simply by getting access to your home network. If you have a home wifi network and someone knows the password, they can hurt you. If all people that know the password are your friends, it is probably OK, if it is some stranger (or someone who will try to go after you personally) then it is not OK.

---

### Post by Jayce71 on 2011-09-14
In Ubuntu 11.04 edit your wifi connection and at the bottom of the window (Wireless tab) tick the option "Available to all users"...
It won't ask for your password anymore when starting up.

---

