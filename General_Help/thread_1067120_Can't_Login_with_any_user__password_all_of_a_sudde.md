---
title: "Can't Login with any user / password all of a sudden??"
date: 2009-02-11
forum: General Help
---

### Post by n5wy on 2009-02-11
This is weird. Things have been going fine for several days on my system. Yesterday, I rebooted and when the gnome login screen came up it rejected my usual user/pwd. I did the usual check for caps lock and tried again. Still rejected. Same thing happens if I try to use a failsafe gnome session login. I found out that I could not login using any valid user/pwd on the system. The gnome login screen would take nothing, so I dropped to terminal shell and still the same thing. I cant get past the shell login prompt. 

I am totally locked out of the system. 

I rebooted to recovery mode, dropped to root shell. I looked at the sudoers file to see if it changed, it looks the same as the default posted on the help page. 

Does anyone have any ideas on how to recover from this? It has to be a corrupt password file, or bad permission settings somewhere? I dont have anymore clues. 

I have also tried to add a new user from the root shell prompt. I added the new user, gave the new user admin priviledges, and rebooted. When I tried to login with the new user/pwd I get the same thing. 

What can I do to fix this problem?

I can boot up with live cd and try to fix something, but I dont want to make things worse without knowing what to do.

---

### Post by unutbu on 2009-02-11
Boot into Recovery Mode, drop to a root shell, and type
```
ls -l /etc/passwd
getent passwd USER
```
Replace USER with your username.

Please copy down the output and post it here.

---

### Post by Old *ix Geek on 2009-02-11
At a root prompt, change your password:
```
passwd YOURUSERNAME
```

You'll be prompted [twice] for your new password.

Reboot and see if you can now login.

---

### Post by n5wy on 2009-02-11
> **unutbu said:**
> Boot into Recovery Mode, drop to a root shell, and type
```
ls -l /etc/passwd
getent passwd USER
```
Replace USER with your username.

Please copy down the output and post it here.


I get the following:

-rw-r--r-- 1 root root 2106 Feb 11 15:15 /etc/passwd

for the second cmd, 

root:x:0:0:root:/root:/bin/bash  (for user= root)

and

jrodgers:x:1000:1000:,,,:/home/jrodgers:/bin/bash  (for my username)



If I try and reset the password from the root recovery terminal with 

passwd USEERNAME

I get the following error,

passwd: Authentication token manipulation error
passwd: password unchanged

Something is screwed up and I cant figure out what I may have done yesterday before shutting down that would have changed things to cause the login problem for any user account on the system. What should I try now?

---

### Post by Old *ix Geek on 2009-02-11
I just did a quick search and found some info that **may** solve your problem.  Take a look at this page: [http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/](http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/)

---

### Post by n5wy on 2009-02-11
Well I tinkered with **pwconv** and it didnt work. I am still stuck on trying to figure out what would have caused this in the first place. 

I suspect that a recent (like yesterday or day before) update or software install did something it wasnt supposed to. The reason I say this is that I have two hard disk drives for this laptop. One had an install of ubuntu on it that was about a month old. I removed that HDD and put another one in and installed a fresh ubuntu, did the updates, and installed all the stuff as it was before identically. The idea was to be able to swap physical drives as a fast way to be back up and running when I do something stupid. 

This problem popped up yesterday, so I swapped drives thinking things would be OK until I could figure out what I did wrong. When I swapped the backup HDD drive in, I was able to login and work for a while. But after I shutdown and rebooted later, I got the same no login problem that occurred the first time. 

I REALLY dont want to have to go through all the reconfiguring with a fresh install just to get back to a known state, so I would like to sort this out. Linux is a learning experience, but times like these are frustrating when you dont have a clue what to do next.

Since I have done the pwconv and it didnt work, should I try to add a new user at the recovery root console, then reboot and try to login with the new username?

---

### Post by Old *ix Geek on 2009-02-11
Try manually editing your /etc/shadow file.  The point is to make sure that there's a matching entry in it for the user whose entry exists in /etc/passwd.  MAKE A COPY FIRST!

---

### Post by n5wy on 2009-02-11
I will try the manual edit of /etc/shadow and /etc/passwd to compare entries. 

However, I just noticed something new that may be relavent. When the machine was rebooting and scrolling stuff across the screen, I noticed somethng new. There was an error message I dont remember seeing before. It said that it couldnt mount /dev/shd and /dev/pts  because these were invalid mount points. 

There is no such filesystem or mount point defined in /etc/fstab, /etc/mtab. If I do a "fdisk -l" or "df -h" there is no such thing listed. 

Does /etc/shd and /etc/pts refer to some sort of virtual mount point for the shadow file?

---

### Post by n5wy on 2009-02-11
The same users exist in both files. 

I tried to change the password of a user with
```

passwd USERNAME

```

but still get 

```
passwd: Authentication token manipulation error 
```

I have likewise-open installed on this machine as it is used in a MS AD environment. Could this have caused a problem with the PAM files after running successfully for a couple of weeks?

---

### Post by lord.buddha on 2009-03-19
This has happened to me twice now.  Once last year on 8.04... so I rebuilt over xmas, and last week it happened again on 8.10 after applying 75 days worth of updates ...  

I also have Likewise installed.

Did you ever get a solution/or fix it yourself ?

I have to say my collegue uses OpenSUSE 11.1 and the built in AD integration just works and does not break.  As a built in feature it seems to be much more reliable.   Am tempted to switch.

---

### Post by fieroboom on 2009-03-19
> **n5wy said:**
> 
If I try and reset the password from the root recovery terminal with 

passwd USEERNAME

I get the following error,

passwd: Authentication token manipulation error
passwd: password unchanged

This error usually indicates a mismatch of usernames between /etc/shadow & /etc/passwd. Please run these commands and copy/paste the output of both.
```
grep jr /etc/passwd

grep jr /etc/shadow
```
:D
-Paul

---

### Post by lord.buddha on 2009-03-20
So logged in under my AD account (which I had previously given sudo access)

This would be funny if wasn't so hilarious :-

I have no name!@isis-ws-056:~$ sudo su -
[sudo] password for waded: 
su: Authentication failure
(Ignored)
root@isis-ws-056:~# 

So checking passwd and shadow ...

```
root@isis-ws-056:~# grep isis /etc/passwd
isis:x:1000:1000:isis,,,:/home/isis:/bin/bash
root@isis-ws-056:~# grep isis /etc/shadow
isis:??????????????????????????????:14241:0:99999:7:::
root@isis-ws-056:~# 
```

Nothing wrong there that I can see.  

I am very sure that it was the updates that broke the pam stack.   I was unfortunately too stupid to back up /etc before applying the updates and especially stupid given that updates have broken local account authentication before when using Likewise.

5:15PM in NZ:  Beer time.

---

### Post by smhickel on 2010-01-30
So, did we ever figure out how to get access back into the box after the PAM update messed up local admin login? I am all ears!!! Thanks!

Steve

---

### Post by lord.buddha on 2010-01-30
Sorry, never did manage to get back in except in maintenance mode.  I had to re-install.   This actually happened to me on a number of occasions but has not happened for a year now.  

The difference... I don't know if it is significant, but, my admin account, "isis" was the same as the domain I was joined in to and I had also set the option to assume default domain such that I didn't have to prefix my domain account with the domain when I logged in.

PS. I still don't keep backups of my etc... some people never learn, but the machine is just for dev, not a server.

---

### Post by smhickel on 2010-02-04
Thanks for the response. Here are my thoughts. I believe there was a pam update that happened. I answered no to the question it asked. Don't recall what the exact question was but it had to do with pam change of a .conf file or some such. 

I was able to login in as the admin user via webmin (not at the login screen of ubuntu though). I did not have sudo rights as webmin admin users though. But I could read (other command prompt in webmin) the pam files in the pam.d folder under etc. I have an identically configured server also joined into a domain with likewise-open 5.3. I compared one of the pam files (I think it was common-auth(?)). It was completely different than the one on the working server. My guess is I need to copy the pam.d folder to a flash drive and copy that puppy on top of the pam directory (or perhaps file by file that are different)  and see if that fixes it. I believe the update broke the pam authentication system and having likewise-open had changed things from a default pam install. 

I opened a bug on the launchpad but have not heard anything from that attempt yet.

Hope that helps.

Steve

---

### Post by deenpac on 2010-02-05
I am having the same problem BUT I AM A NEWBIE and don't understand some of the things you are saying to do above. 

I am completely locked out of my laptop and have NO CLUE how to fix this.

Please, please explain to me in lay-person's language what to do.

Thank you!!
-d

---

### Post by madfrog on 2010-04-13
I had the same problem after upgrading from 9.04 to 9.10
 
I dropped to the root shell, and did the following:
 
mv /etc/pam.d/common_auth /etc/pam.d/common_auth.broken
mv /etc/pam.d/common_account /etc/pam.d/common_account.broken
mv /etc/pam.d/common_password /etc/pam.d/common_password.broken
mv /etc/pam.d/common_session /etc/pam.d/common_session.broken
 
Then I did a ls -al /etc/pam.d |more to get the dates of the files changed by the upgrade.
 
cp /etc/pam.d/common_auth.pam.old /etc/pam.d/common_auth
cp /etc/pam.d/common_account.pam.old /etc/pam.d/common_account
cp /etc/pam.d/common_password.pam.old /etc/pam.d/common_password
cp /etc/pam.d/common_session.pam.old /etc/pam.d/common_session
 
 
After restoring the files from the backup files, everything went back to normal. I am now able to log on to the system and change my passwords

---

