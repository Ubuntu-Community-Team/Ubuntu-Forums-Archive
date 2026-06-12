---
title: "Rename user / Change username"
date: 2009-01-03
forum: General Help
---

### Post by defcon3 on 2009-01-03
Hello: 

I recently bought a new laptop and wish to give my (old) one to my sister. She likes it and is used to the ubuntu interface and all but... each time at login she has to put in my username and password - neither are easy [healthy paranoya]

What I wish to do is basically rename my existing user from ***john*** to ***monica*** - in doing that I wish ***monica*** to retain *all* settings that ***john*** had to date. I though I could just create new user ***monica*** and copy /home/***john*** to /home/***monica*** but alas, no. 

So, how do I change the username in a way that will change the /home from /home/john to /home/monica, give ***monica*** the same sudo rights ***john*** had, etc. etc. etc.

---

### Post by albinootje on 2009-01-03
... 
Just tested the suggestion by taurus. 
It does work fine so far.

I recommend using vipw like this to avoid typos and syntax errors :
```

export EDITOR=nano
vipw
vipw -s
vipw -g

```

---

### Post by taurus on 2009-01-03
Boot into recovery mode from GRUB menu.  Then, change /home/john /home/monica.

```
mv /home/john /home/monica
chown -R monica:monica /home/monica
```
Now, you need to change the word **john** to **monica** in both /etc/passwd & /etc/group.

```
nano -B /etc/passwd
nano -B /etc/shadow
nano -B /etc/group
```
When you are done, reboot and see if she can log in as monica with the same password that you used as john.

```
shutdown -r now
```

---

### Post by defcon3 on 2009-01-04
First off, thank you very much for the tip - worked like a charm! 

One note to those who will use it though ;) 

You should perform 
```
chown -R monica:monica /home/monica
```
*after* you actually go through the 3 files listed (passwd, shadow, group) - since the user is not existing (yet) at the time and you will get an error message. 

Thank you again!

---

### Post by heindsight on 2009-01-04
```
chown -R monica:monica /home/monica
```
I'm not sure that's even necessary, internally the file ownerships are represented using the UID and GID (user/group id), it only gets printed as names for convenience of the user. since you are renaming the user:group john:john to monica:monica, user monica will have the UID as john and group monica the same GID as group john so any files that belonged to john would automatically belong to monica after the name change.

One thing to be careful of is that in various places there may be 'hardcoded' references to /home/john or there may be symlinks somewhere pointing to /home/john (or files under /home/john) and these will all be broken when you rename the directory (i know, i once did this on a previous system). Of course there's no rule that says that monica's home dir must be /home/monica - you could just have monica using /home/john as home dir (just don't change the home dir entries in the password file)

---

### Post by tommygunner on 2009-02-16
Great post!

It worked good for me but I have one lingering problem. After booting up, I get a message box:

```
Unlock Keyring
Enter password for default keyring to unlock
NetworkManager Applet (user/bin/nm-applet) wants access to the default keyring, but it is locked.
```

I used to never see this box. The odd thing about this is that it only works with the old password. After I changed the login name info, I set a new password. However, with the network, only the old one works.

I'm wondering if anyone knows why it is doing this and what I need to change.

---

### Post by heindsight on 2009-02-17
I would assume that when the keyring was first created it was encrypted using your password as key, and even though you've changed your password, the keyring is still encrypted with the old password.

You can change the unlock password for your keyring by going to System>Preferences>Encryption and Keyrings selecting your keyring in the Password Keyrings tab and clicking the Change Unlock Password button.

---

### Post by tommygunner on 2009-02-20
Thanks Heindsight. ngs. It didn't see any keyrings or anything in the GUI. I managed to fix this by deleting the login.keyring file in .gnome2/keyrings/

Now it doesn't pop up anymore.

---

