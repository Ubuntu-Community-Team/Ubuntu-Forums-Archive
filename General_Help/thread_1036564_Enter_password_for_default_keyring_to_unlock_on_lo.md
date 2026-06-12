---
title: "Enter password for default keyring to unlock on login"
date: 2009-01-10
forum: General Help
---

### Post by RobSoko315 on 2009-01-10
Hey,

I'm new to Linux/Ubuntu, and I just changed my user name password(the only user name on my computer) and ever since, when I log in, I get the following message:

"The application 'NewtworkManager Applet' (usr/bin/nm-applet) wants access to the default keyring, but it is locked"

And asks for my password.  The weird thing is that only my old password works.  

Does anyone know what I'm doing wrong?

Thanks in advance,


Rob.

---

### Post by caro on 2009-01-11
You aren't doing anything wrong.  The keyring password hasn't changed.  If you don't want to enter the password for the keyring, change it to match your login password.

Applications > Accessories > Passwords and Encryption Keys

---

### Post by garnser on 2009-01-11
You could do the following:

# killall -9 gnome-keyring-daemon
$ rm -fr ~/.gnome2/keyrings

By doing this you'll "reset" your keyring, the drawback is that you'll have to re-enter all keys you've earlier stored in the keyring.

/Jonathan

---

### Post by RobSoko315 on 2009-01-11
> **caro said:**
> You aren't doing anything wrong.  The keyring password hasn't changed.  If you don't want to enter the password for the keyring, change it to match your login password.

Applications > Accessories > Passwords and Encryption Keys

Thanks, I got it to work now.

---

### Post by twa on 2009-02-03
> **garnser said:**
> You could do the following:

# killall -9 gnome-keyring-daemon
$ rm -fr ~/.gnome2/keyrings

By doing this you'll "reset" your keyring, the drawback is that you'll have to re-enter all keys you've earlier stored in the keyring.

/Jonathan

My gnome keyring was hosed and the commands I found above fixed it.  Thank you!

---

### Post by sehe on 2009-05-04
> **caro said:**
> You aren't doing anything wrong.  The keyring password hasn't changed.  If you don't want to enter the password for the keyring, change it to match your login password.

Applications > Accessories > Passwords and Encryption Keys

Exactly *how* can I change the supposed 'keyring password'. I can't find any such option in said application. 

Also, I don't recall ever setting a keyring password. However, it does work when I use my *old* logon password... Ermmm. sounds a little bit bug-like

---

### Post by zeezam on 2009-12-28
> **caro said:**
> You aren't doing anything wrong.  The keyring password hasn't changed.  If you don't want to enter the password for the keyring, change it to match your login password.

Applications > Accessories > Passwords and Encryption Keys

Same login as the ubuntu user or the wpa login?

I tested with the same password as the ubuntu user but I need to enter password after every login...

---

### Post by no_angst on 2010-03-03
> **zeezam said:**
> Same login as the ubuntu user or the wpa login?

I tested with the same password as the ubuntu user but I need to enter password after every login...

If you're getting prompted because of the wireless:

1) Right click your wireless (Network Manager) icon in the tray and click Edit Connections.

2) Click the Wireless tab, highlight your wireless connection, then click Edit.

3) At the bottom there is a checkbox called "Available to all users". Click it then click Apply to save your change.

It will ask for your password because it is a system-wide change, but that's it! You, or anyone else you make an account for can now log on and get the wireless connection without anyone having access to your keyring.

Jim

---

### Post by G-Fru on 2010-03-07
ok, so i was in the middle of writing my first post to say how i had followed the instructions in this forum and my problems had gone away when my computer booted me out and sent me to the login screen. That was after opening firefox and then navigating to the reply section of this forum and typing 2 or 3 sentences.

I'm new to ubuntu (6 hours and counting) but am impressed so far and after a few teething problems my concerns are minimal, but this login issue is bugging me. When i setup Ubuntu I selected auto login.

Firstly when i would startup i would be taken straight to the desktop and after a few seconds shown a window with the text "enter password for to unlock your login keyring" (yes that is exactly what it said, maybe someone should look at that), it then said "the login keyring did not get unlocked when you logged into your computer".

So i would proceed to login, i thought it was all about my user password, being a newb, and so proceeded to type in my password. My password contains the number 2, and when i'd get to this number the screen would go blank and send me to the login screen. I thought this was to do with the number of characters i put in or something... but no i tested every key on the board and only the number 2 sent me back to the login screen as soon as it was pressed. (This could be a hint to someone who knows more about this than i do)

So after reading this post i followed the advice and set the wireless setting to "available to all users" and the next time my computer logged in fine, as is started this post with. But now i am wondering if my problem is also related to something else...

anyone have any ideas? remember i am fairly useless so please if you want me to do anything be gentle;)

btw, Please forgive me for being long winded, but as i said i am new and feel  that more info is always helpful when troubleshooting.

---

### Post by mister_playboy on 2010-03-07
> **sehe said:**
> Exactly *how* can I change the supposed 'keyring password'. I can't find any such option in said application. 

Also, I don't recall ever setting a keyring password. However, it does work when I use my *old* logon password... Ermmm. sounds a little bit bug-like

I agree with you.  The way this is handled is pretty dumb.  When you first install Ubuntu, your keyring password is automatically set to be the same as your login password, so users are completely unaware of its existence until they change their login password and the two no longer match.

---

### Post by spiderbatdad on 2010-03-07
This is handled by right clicking on the word login  in the encryptions and keyrings password window. This open a  menu with the option to change password. Yes it's a little bit hard to find, if you don't know it's there.

---

### Post by grantbuntu on 2010-05-02
In Lucid, I don't even see that option.  BTW nothing seems to not be working if I cancel the warning about the password mismatch.

---

### Post by rajeev1204 on 2010-05-09
I have this problem with 10.04 even though my login password and 'keyring' (whatever that nonsense is ) is the same.

---

### Post by alexandremrj on 2010-05-15
All passwords from wireless to empathy are stored in the keyring, and this is unlocked when the user logs in with a password.

This issue occurs when the user autologins because there isn't a password and what usually happens is that there is a auto wireless (and its password is stored in the keyring). So as refered here, enable wireless for all users (when possible - attention if you are using work credentials and another user uses your pc) and will only get that prompt when empathy or other programs need a password already stored.

---

### Post by ikkarus on 2010-05-20
good night guys!
i have an problem and need some help!
well... i have the lucid lynx here, the mysql workbench try to use the gnome-keyring-daemon when i try to connect on db... but the keyring is not running... how i fix it?
sorry for my "orrible" english.. :(

obrigado! :P

---

### Post by plentyTypos on 2010-06-17
> **grantbuntu said:**
> In Lucid, I don't even see that option.  BTW nothing seems to not be working if I cancel the warning about the password mismatch.

I've recently installed Lucid too and I think that the GUI features of that "Passwords and Encryption Keys" thing must have changed in this release. Anyway if you go to Applications->Accessories->Passwords and Encryption Keys and then in the window that opens select the "Passwords" tab, then right-click on the "Passwords: login" item. In the pop-up menu there should be an item called "Change Password". In there I typed the first password I had used when I installed Ubuntu as the "Old" password and the current password as the new one. Now it seems that the keyring password is updated to be the same as the login password.

Did I forget to mention that this is for those who like me are new to Ubuntu, have perhaps changed their login passwords, and are now trying to figure out how to update their keyring passwords to match, per various postings here.

Hopefully that helps some people.

---

### Post by psychoelf on 2010-07-01
Wow, just found this.  Maybe this should be a little easier for the end user.  How would I have known to right click?!  I've been checking everywhere and clicking everywhere.  Think of people like my mother!!! I don't want her calling me when things like this popup! :D

---

### Post by nickdc on 2010-07-03
> **alexandremrj said:**
> All passwords from wireless to empathy are stored in the keyring, and this is unlocked when the user logs in with a password.

This issue occurs when the user autologins because there isn't a password and what usually happens is that there is a auto wireless (and its password is stored in the keyring). So as refered here, enable wireless for all users (when possible - attention if you are using work credentials and another user uses your pc) and will only get that prompt when empathy or other programs need a password already stored.

I've had this problem recently too, but I'm pretty sure I activated autologin when I first installed, so I've only ever entered the one password, and for a while I was happily using the system without knowing anything about the "keyring", only using my password when I needed to authorise specific activities, like initiating an update. No mention of keyrings. Suddenly now I'm getting this annoying pop-up within a few moments of auto-login. It makes auto-login a little pointless! It's nothing to do with wireless as I don't have wireless. There's no option I can see for the wired connection (Auto eth0) to be configured differently.

Would be grateful for advice.

---

### Post by propan0 on 2010-08-20
> **nickdc said:**
> I've had this problem recently too, but I'm pretty sure I activated autologin when I first installed, so I've only ever entered the one password, and for a while I was happily using the system without knowing anything about the "keyring", only using my password when I needed to authorise specific activities, like initiating an update. No mention of keyrings. Suddenly now I'm getting this annoying pop-up within a few moments of auto-login. It makes auto-login a little pointless! It's nothing to do with wireless as I don't have wireless. There's no option I can see for the wired connection (Auto eth0) to be configured differently.

Would be grateful for advice.

Same situation here, I don't even have a wireless connection.
I've setup to use autologin, since this computer never leaves my house, and well, I get the message for the keyring. Seems to me they should be syncronized (though I admit it sounds scary) to be autologgedin and auto unlocked... otherwise, there's not much point in autologin afik.

---

### Post by erichouse98 on 2010-08-27
> **no_angst said:**
> If you're getting prompted because of the wireless:
 
1) Right click your wireless (Network Manager) icon in the tray and click Edit Connections.
 
2) Click the Wireless tab, highlight your wireless connection, then click Edit.
 
3) At the bottom there is a checkbox called "Available to all users". Click it then click Apply to save your change.
 
It will ask for your password because it is a system-wide change, but that's it! You, or anyone else you make an account for can now log on and get the wireless connection without anyone having access to your keyring.
 
Jim
 
This fixed my "password for default keyring" issue.
Thanks for the help.

---

### Post by bwestover on 2011-01-31
I have this problem on Lucid (10.04)

I do not have a wireless connection, and I am not using auto-login.

The password for login is the same as for the keyring.

---

### Post by shantiq on 2011-03-15
> **spiderbatdad said:**
> This is handled by right clicking on the word login  in the encryptions and keyrings password window. This open a  menu with the option to change password. Yes it's a little bit hard to find, if you don't know it's there.



wow talk about cryptic   the guys who put this together thought they were James Bond maybe:KS:KS:KS:KS


on maverick i had to go

1. systems/preferences/password and encryption keys
2. right click on the word "login" and unlock


but thanx guys it worked

---

### Post by govindg279 on 2011-07-13
Thanks, it works fine now!!

--Govin

---

### Post by JamesFlamingo on 2011-11-19
p, li { white-space: pre-wrap; }  > I agree with you. The way this is handled is pretty dumb. When you first install Ubuntu, your keyring password is automatically set to be the same as your login password, so users are completely unaware of its existence until they change their login password and the two no longer match.


I just love this answer. You explained the issue!! Thanks you so much. Now in the future i do not have to dicker around with rote instructions. :)

I was able to remember the password i used to Install Ubuntu and that turns out to be my so called password keyring. I can't believe that one is effectively locked out of ones own system for changing the password on an administrative account. By the way there are four choices of keyrings in the manager that i did not understand - and when i try to make new ones it asks for the old one. HAHAHA!

---

### Post by n411303 on 2012-05-20
Precise Pangolin: I was getting asked to enter my default keyring password every time I connected to my secure network drive for the first time after login. I did not get this from other home pcs, so knew it was something to do with the default keyring.  My default password is same as my login password. I tried all the solutions I read on Ubuntu forums. 

The solution was actually EASY.  

When the GUI dialog box opens saying an application wants to access the default keyring there is a button to expand "details".  Here I was offered a number of choices one of which was to have this particular keyring always unlocked when I'm logged in. Problem solved!

The real problem here is Ubuntu is showing a button to see "details" which sounds like its only a route to more information.  In actual fact, "details" is a route to an expansion of the GUI dialog to offer the user the opportunity to modify settings.  

This Ubuntu dialog box could better designed.

---

### Post by oldos2er on 2012-05-20
Old thread closed.

---

