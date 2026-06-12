---
title: "Cannot login as normal user"
date: 2006-06-08
forum: Desktop Environments
---

### Post by salem7 on 2006-06-08
My Ubuntu was working fine but suddenly it cannot login as normal user. After inserting my user name and password, a message box with the following message shows up:
```

Your home directory is listed as:
'/home/user'
but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session

```
What shall i do?

---

### Post by scxtt on 2006-06-08
what was the user name that you used to login with?  it seems that it's trying to use some generic home directory '/home/user' instead of something like '/home/$username' ... if you can get in as root, run System --> Administration --> Users & Groups to fix the login for the username you want to use ...

---

### Post by salem7 on 2006-06-08
Sorry for the mistake ... i meant '/home/$username' which is '/home/salem'

---

### Post by salem7 on 2006-06-08
Btw, i cant even log in as root either!

---

### Post by scxtt on 2006-06-08
and you're sure /home/salem exists and is accessible by the user salem?

i'd boot into recovery mode and (as root, as recovery mode gives you) check that it exists and is owned by the right user ...

---

### Post by salem7 on 2006-06-08
I  went into recovery mode and checked the ownership of the directory... seems fine to me. What do you think?
```

drwxr-xr-x  3 root  root  4096 May 05:19 .
drwxr-xr-x 23 root  root  4096 Jun 10:59 ..
drwxr-xr-x 45 salem salem 4096 Jun 11:51 salem

```

---

### Post by salem7 on 2006-06-08
My problem still persists.... its halting all my work.... any ideas on solving it please?

---

### Post by scxtt on 2006-06-09
everything seems fine w/ the output you posted ... the only idea i have is to boot to recovery mode and run "fsck" - maybe your filesystem is outta whack?

---

### Post by salem7 on 2006-06-11
Tried that too..... didnt work! :confused:

---

### Post by kvonb on 2006-06-12
Hi,

I'm working on this for you right now but my knowledge is limited.

I would suggest that you boot into recovery mode and run the command: "adduser fred" (change fred to anything you want), fill in the details and then reboot and login as "fred".  Then go to SYSTEM -> ADMINISTRATION -> USERS and GROUPS and look at the settings for your original username.  But be careful, I've had bad things happen to me when I used "Users and Groups", **_make sure that the last button you clicked on was the "PROPERTIES" button before you click on "OK" to exit!!!!!_**  Otherwise it could delete your current account, this happened to me in Breezy.  If your original account is mashed, you can always copy all your files (including hidden) from your old home folder to the new one, the only problem is that you will have to change the owner and group settings for ALL your files, but again be warned some files have unexpected ownership settings and things like vmware and cedega might not work.  On the bright side, you could always make a backup of your original home directory, delete your old user, then re-create it and copy the files back into the "new" home directory!  Hope that makes sense :D

Best of luck.......Kev :)

---

### Post by salem7 on 2006-06-20
Thanks for your elaborated solution.... but unfortunately it didnt work either. I created a new user and when i tried to login normally it gave me the same error message as the one for the original user!! ](*,)

---

### Post by Ashish Meena on 2006-06-20
Well u can do one more thing try booting ur computer with a live  cd and then mount the partition in which u have installed ur ubuntu in case u dont know how to mount 
type " mount /dev/hda* somedir" where * is ur partition no. where ubuntu is installed and somedir can be any directory . And then try to create the  directoy it says not to exist and give ur user permissions to acces it . 
         I hope this will solve ur problem .

---

### Post by salem7 on 2006-06-20
As per my understanding, the problem is as follows:
My home directory 'disappears' (as in, does not exist)when i try to login normally. But when i'm in recovery mode and logged in as root, the directory 'appears' (as in, exists) and i can login as normal. I even tried to add a new user in recovery mode and then tried to login but it was unsuccessful. Whats with the home directory?? Why does it exist when i'm a root and disappears when i try to login in a normal mode??

---

### Post by Ashish Meena on 2006-06-20
Ok have u checked the permissions of  ur home directory ?? Try changing the ownership of home directory to ur user name

---

### Post by salem7 on 2006-06-20
yes i did.... and the permissions are alright. As i said the problem is the home directory completely dissapears when i login as a normal user....

---

### Post by Ashish Meena on 2006-06-20
Well then here does not seem to be any problem with ur home directory . Btw how r u not able to login as root also . 
       Ok are u running X session directly ?? Actually Ubuntu by default does not allow root to allow login in X session . So u may try one more thing U try to edit ur file /etc/inittab and put ur computer in runlevel 2 and try to login on terminal and then try doing startx  .  U may also need to uninstall gdm or kdm whatever it is in ur case . 
        So after putting ur computer in runlevel 2 u would be able to login as root  . Best of lluck  :D

---

### Post by yurtboy on 2006-06-23
Did you figure this one out?
Overall if you can log in as root in single mode then either 
One) your hard drive is filled enough that only root can log in
Two) some how gdm/kdm is having trouble

KDM/Gdm can log in as failsafe mode then that will help understand where things are at.

As root on a terminal ie pressing F1 + Ctrl + Alt and when you are logged in type df and see if anythings says 100% in disk usage?

Try logging in at F7 + Ctrl + Alt
Then go back to F1 and tail /var/log/syslog to see if there are any error reports and dmesg.

Let me know how it goes
[email]alfred@yurtboy.gotdns.com[/email]

---

