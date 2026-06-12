---
title: "WTF!! is Default Keyring password?"
date: 2009-05-29
forum: General Help
---

### Post by ManyBeers on 2009-05-29
Title says it all. I don't remember setting any Default Keyring 
password. I believe the only password I ever set was mt account login password. 
   Anyways the reason for this post is I am using Evolution e-mail client on Ubuntu 8.04(2.6.24-24) to access my IMAP e-mail acct. 
which works fine. However I also set up a usenet news acct. and during authentication I was prompted for my Default Keyring password which of course I did not know. I wasn't prompted for a Keyring password for my e-mail acct. why for the Uesnet news acct.?

---

### Post by Yashiro on 2009-05-29
WTF!! is not a very good password. :P

Ubuntu adds and saves passwords to a built in keyring.
If you've never set it up the password for the keyring will be your login password.
(System > Preferences > Encryption and Keyrings to edit stuff)

---

### Post by ManyBeers on 2009-05-29
> **Yashiro said:**
> WTF!! is not a very good password. :P

Ubuntu adds and saves passwords to a built in keyring.
If you've never set it up the password for the keyring will be your login password.
(System > Preferences > Encryption and Keyrings to edit stuff)


Are you saying it is my Login password or I should set it up to be the same as my login password? If the latter how do I do this? Please be explicit. 

I think the reason I am prompted for a keyring password for my Usenet news account is because it uses ssl encryption. Does that make sense?

---

### Post by Yashiro on 2009-05-30
Launch System > Preferences > Encryption and Keyrings 
There should be a *logon* keyring entry. Delete any other keyrings in that list.

Try changing the password for the logon keyring entry.
The *old password* should be the same as the password you log onto Ubuntu with. (Or the password the used when you first installed Ubuntu.)

Set the new password to match your current logon password.

Popups that prompt to *unlock default keyring* will then require you to enter your logon password. To see what passwords are saved to this keyring open Applications > Accessories > Passwords and Encryption Keys. Click the passwords tab.

---

### Post by ManyBeers on 2009-05-30
> **Yashiro said:**
> Launch System > Preferences > Encryption and Keyrings 
There should be a *logon* keyring entry. Delete any other keyrings in that list.

Try changing the password for the logon keyring entry.
The *old password* should be the same as the password you log onto Ubuntu with. (Or the password the used when you first installed Ubuntu.)

Set the new password to match your current logon password.

Popups that prompt to *unlock default keyring* will then require you to enter your logon password. To see what passwords are saved to this keyring open Applications > Accessories > Passwords and Encryption Keys. Click the passwords tab.

I don't have an OLD Keyring password. When I installed Ubuntu 8.04 the only password I recall making is the one for my Login account and that one apparently does not work to unlock the keyring. Did Ubuntu ask during installation for a Keyring password?

---

### Post by Tipped OuT on 2009-05-30
The keyring password would most likely be your log in password. You can just reset it you know.

---

### Post by crazybuntu on 2009-05-30
Here is a simple way to DELETE KEYRING : [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

1. Open up your Home Folder by clicking Places>Home Folder
2. Press CTRL-H (or click View>Show Hidden Files)
3. Find a folder called .gnome2 (it has a period at the beginning of the name)   
   and open it by double clicking on it
4. In side of the .gnome2 folder, there is another folder called keyrings.  
5. Open it up.
6. Delete any files you find within the keyrings folder
7. Restart the computer

8. You will be asked to enter WEP and keyring in startup ; LEAVE KEYRING empty 
and click ok

---

### Post by ManyBeers on 2009-05-30
> **Tipped OuT said:**
> The keyring password would most likely be your log in password. You can just reset it you know.

I have stated it twice in this thread I do not have a Keyring password. Or at least when I enter my Login password it does not work.

---

### Post by Tipped OuT on 2009-05-30
> **ManyBeers said:**
> I have stated it twice in this thread I do not have a Keyring password. Or at least when I enter my Login password it does not work.

> **crazybuntu said:**
> Here is a simple way to DELETE KEYRING : [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

1. Open up your Home Folder by clicking Places>Home Folder
2. Press CTRL-H (or click View>Show Hidden Files)
3. Find a folder called .gnome2 (it has a period at the beginning of the name)   
   and open it by double clicking on it
4. In side of the .gnome2 folder, there is another folder called keyrings.  
5. Open it up.
6. Delete any files you find within the keyrings folder
7. Restart the computer

8. You will be asked to enter WEP and keyring in startup ; LEAVE KEYRING empty 
and click ok

Please follow those above steps.

---

### Post by dgeezer on 2009-06-04
Thank you.

I had inadvertantly left the caps lock key on after entering the WPA key for my home wireless network. This meant that I entered a wrong key for my defaulf keyring password. By deleting the files as you said I was able to enter a new password.

I figured out what I did wrong when I almost repeated the same mistake again.

---

### Post by mcduck on 2009-06-04
> **crazybuntu said:**
> Here is a simple way to DELETE KEYRING : [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

1. Open up your Home Folder by clicking Places>Home Folder
2. Press CTRL-H (or click View>Show Hidden Files)
3. Find a folder called .gnome2 (it has a period at the beginning of the name)   
   and open it by double clicking on it
4. In side of the .gnome2 folder, there is another folder called keyrings.  
5. Open it up.
6. Delete any files you find within the keyrings folder
7. Restart the computer

8. You will be asked to enter WEP and keyring in startup ; LEAVE KEYRING empty 
and click ok

There is absolutely no reason to delete your keyring just to set/change the keyring password.. :D

1. Go to Applications/Accessories/Passwords and Encryption Keys.
2. On the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password"

****
edit: If you are using Ubuntu 8.10 or older, the interface is slightly different:

1. Open Applications/Accessories/Passwords and Encryption keys.
2. Go to Edit/Preferences.
3. On the password Keyrings-tab select the "login"-keyring and click "Change Unlock Password"

---

