---
title: "Can't log in through Lubuntu GUI login"
date: 2013-02-09
forum: Desktop Environments
---

### Post by jeffd123 on 2013-02-09
I am unable to login to either of my accounts that have passwords through the Lubuntu GUI login.  When I type my password and click login, the screen goes black for a second but then just goes back to the same login screen, with the password box now cleared.

I can login to the "Guest Account" (which has no password) just fine through the GUI.  I know that I am entering the correct password - when I enter a wrong one, it says "Incorrect password, please try again".  I am able to login through SSH using my password just fine.

I installed Lubuntu on top of Ubuntu server inside of a VirtualBox VM (running on an OSX host).

Does anyone have any idea why the Lubuntu login GUI might not be working for accounts with passwords for me?

---

### Post by lordievader on 2013-02-11
Have you changed your password recently?
I had a similar problem once, turned out I had only changed the password to my user-account, but my encrypted home-dir still had the old password. Changing the password for the encrypted home-dir fixed the problem for me.

---

### Post by Big John Australia on 2013-03-28
Hi,
I have installed, Peppermint, Lubuntu and Xubutu.   I experience the same problem with all.  I am connecting to the the internet through a university (RMIT) internet connection.   I have eventually figured out how in "run" to configure the proxy to allow internet access through Chrome, but is crashes constantly.   I downloaded and installed Mozilla Firefox, which works well BUT in neither Chrome or Firefox can I sign into Google to access my mail.  I am completely lost.   This is only a problem at the university.

So I have tried a work around using a wireless connection.  I follow the univerisity wireless setup  using the correct setup but I just cannot connect to the internet.   I am not a geeky but have a reasonable grasp on computer stuff.  
 
THOUGHTS....IDEAS.....I am desparing.

Big John

---

### Post by Big John Australia on 2013-03-28
Whoops sorry...I replied rather than start a new thread!

---

