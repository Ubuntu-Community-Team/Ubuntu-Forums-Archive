---
title: "no wireless internet icon?"
date: 2010-05-28
forum: Desktop Environments
---

### Post by owners4life5 on 2010-05-28
hello all,

i have a desktop computer with lucid installed that uses a wireless connection. the problem is, in the notification area, my wireless internet icon is not there.

there are two users on the computer, one with privileges and one without. i am the one with privileges. to connect to the internet though, i have to swap to the other account and use their account to connect to the internet, because their wireless icon is still visible. 

as i am sure you can guess this is really annoying and i was wanting to know if anyone could help me.

everything is greatly appreciated.

thanks
:popcorn:

---

### Post by isaacj87 on 2010-05-28
For the account that is giving you trouble, try this:

Navigate to System -> Administration -> Users and Groups

Choose the account that the wireless icon is not working. Click "Advanced Settings" and authenticate yourself. Now, move over to the "User Privileges" tab. There will be an item called, "Connect to wireless and ethernet networks." Make sure this is checked.

Now, log out and make sure *both* accounts are completely logged out. (Meaning don't "switch")

Does that work? I've been playing around with my user accounts and I had the same issue.

---

### Post by dustinmarlowe56 on 2010-05-28
is it an issue of the wireless icon having once been there but now disappeared? if it is and you just need to be able to access that icon to simply connect to the internet then you can just reset your panel. I have a custom script for doing this

sudo vi /etc/bin/resetpanel

#insert this into the file
gconftool --recursive-unset /apps/panel
rm -rf /home/marlowe/.gconf/apps/panel
pkill gnome-panel

#save the file and then run

sudo chmod +x /etc/bin/resetpanel

now finally:

user@computername:~$ resetpanel




so also now whenever you cause something to go wrong with the panel you will have the resetpanel command to restore the defaults.

---

### Post by owners4life5 on 2010-05-28
@ isaacj87:
your suggestion worked! thank you very much, i will tell the other user to log off instead of switching users from now on. if this problem occurs again, i'll use your info

@ dustinmarlowe56:
i am sorry for not using your suggestion but thank you very much for the quick reply. i appreciate it

cheers!
:popcorn:

---

