---
title: "Logon issue"
date: 2009-04-05
forum: General Help
---

### Post by Vrekk on 2009-04-05
Whenever I login to my account, i get an error message saying 

User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by the user and should have 644 permissions.  User's $HOME directory must be owned by the user and not writable by others.

Is this a big issue or is it something I can live with untill I upgrade to 9.04 in the upcoming 18 days?  If it is an easy fix i will rather fix it because it is very annoying when i log on.  I dont notice anything after i press OK however.

---

### Post by _Purple_ on 2009-04-05
Check this [link](http://ubuntuforums.org/showthread.php?t=1028643).

---

### Post by ShaunG on 2009-04-05
Try booting into recovery mode.

Then when in recovery mode go to root to drop to a root terminal. Enter your username and password (root) then type 

```
chmod 644 /home/username/.dmrc
```

where username is your username

---

### Post by Vrekk on 2009-04-05
> **ShaunG said:**
> Try booting into recovery mode.

Then when in recovery mode go to root to drop to a root terminal. Enter your username and password (root) then type 

```
chmod 644 /home/username/.dmrc
```

where username is your username

Nope no luck. Still get the error.

---

### Post by ShaunG on 2009-04-05
```
sudo chown username:username ~/.dmrc
```

Followed by 

```
chmod 755 ~
```

---

### Post by Vrekk on 2009-04-05
> **ShaunG said:**
> ```
sudo chown username:username ~/.dmrc
```

Followed by 

```
chmod 755 ~
```

That did it thanks :D

---

### Post by virgil_machine on 2009-04-07
I have a similar but slightly different problem.

I was getting the error about the home directory should have file permission 644.  I had reset some permissions because I was having trouble copying files from other computers on th network.

So, I rebooted in recovery, dropped to shell and changed permissions on home to 644.

Now I can't login in at all.  It tells me it can't find my home/user directory. It correctly tells me that if I log in with root as the home directory I won't be able to do much.

I found a bunch of suggestions in these forums, but nothing has worked...I can see the <user> directory and the .dmrc file it complains about, I have changed the owner to my userid and changed permissions of my user directory to 700 and of .dmrc to 644.

I don't want to reload ubuntu (I have 8.10 64 bit desktop).  Any less drastic suggestions?

---

### Post by virgil_machine on 2009-04-07
Update:  I went in and set the permission of the home directory to 777 (chmod 777 home).

That cleared the problem but the permissions are still wrong.  At least I can boot normally now.

Any guidance on how to set permissions properly on home, home/user and home/user/.dmrc without losing my ability to login?

---

### Post by ShaunG on 2009-04-07
To see permissions you use chmod. To change ownership you use chown.

Man pages are quite helpful. In a terminal man chmod and man chown

Anyways you need to set the ownership of your .dmrc file, and then change permissions of your home directory.

Let's say your username is Bob you would need to type in a terminal

```
chown -R Bob:Bob /home/Bob
chmod 755 /home/Bob
chmod 644 /home/Bob/.dmrc
```

If after this you are still having difficulties try

[CODE]chmod 644 /home/Bob/.ICEauthorityCODE]

---

### Post by virgil_machine on 2009-04-08
> **ShaunG said:**
> 
```
chown -R Bob:Bob /home/Bob
chmod 755 /home/Bob
chmod 644 /home/Bob/.dmrc
```
Thank you. As I said, I've done this in recovery mode command prompt as root because I could not login.  No change.  The problem is on the home directory. When I changed that back to 777 I was able to login, but I get the warnings about home and about .dmrc again. What I want to know is the correct sequence of commands and permissions to get things funtioning correctly...including permissions on home (as well as /home/bob).

By:
> **ShaunG said:**
> If after this you are still having difficulties try
[CODE]chmod 644 /home/Bob/.ICEauthority CODE]/QUOTE]
did you mean
chmod 644 /home/Bob/.ICEauthority ??
If so, where does that fall in the sequence? Is anything else required?

---

### Post by ShaunG on 2009-04-08
> **virgil_machine said:**
> 
did you mean
chmod 644 /home/Bob/.ICEauthority ??
If so, where does that fall in the sequence? Is anything else required?

Yes I did, sorry. Missed an square bracket.

Try that last in the sequence, whenever I've had problems logging in after having borked permissions, that sequence of commands has worked for me. If it still doesn't work after that, I'm afraid I'm at a loss as how to help. Sorry.

Best of luck.

---

### Post by drs305 on 2009-04-08
If you are still having problems with this issue here is a link to the guide I wrote about it:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

Go directly to Section 5 for the quick fix. If that doesn't work, read the rest. If none of it solves your problem let me know so I can expand the guide to cover what isn't working for you.

---

### Post by virgil_machine on 2009-04-08
Thank you.  The directions were similar to other things I've tried, but this worked, with one exception:  when I did the 1st command
```
sudo chown -R username /home/username
``` I got a message something like "unable to access /home/user/.gvfs."  I found
[this thread]("http://ubuntuforums.org/showthread.php?t=791693&highlight=.gvfs&page=2") with instructions to ```
umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs
``` which I did, and then was able to follow your guide.

Thanks to everyone.

---

### Post by drs305 on 2009-04-08
> **virgil_machine said:**
> Thank you.  The directions were similar to other things I've tried, but this worked, with one exception:  when I did the 1st command
```
sudo chown -R username /home/username
``` I got a message something like "unable to access /home/user/.gvfs."  I found
[this thread]("http://ubuntuforums.org/showthread.php?t=791693&highlight=.gvfs&page=2") with instructions to ```
umount /home/[username]/.gvfs
rm -r /home/[username]/.gvfs
``` which I did, and then was able to follow your guide.

Thanks to everyone.

The .gvfs error message is common and not a problem. If I didn't mention that in the guide I'll go back and add it. 

Thanks for the update. Glad you got your full system back.

---

### Post by virgil_machine on 2009-04-11
One other question: this all started when I changed permissions on the home directory (not home/user) to 777. 

I got a warning to change it back to 644.  When I did that, I could not get in at all.  I went to shell prompt from recovery mode and changed it back to 777.  

I could get in, but I got the /.dmrc warning.  The latter is now cleared, but permissions on home are still 777 (aren't they?).  I don't get the warning anymore, but I'm wondering what this is all about.

ls -la yields:
drwxrwxrwx   3 root root  4096 2009-03-15 12:48 home

---

### Post by drs305 on 2009-04-11
As you surmised, it looks like you ran the chmod command on /home instead of on /home/yourusername. So now /home has full access by anyone (777). 

I would guess from what you've provided, unless you ran it multiple times on different folders, that you ran the chmod command recursively (-r) since it changed ~/.dmrc's permissions to 777, which is why you got the error message. 

I prefer not to provide commands on chowning/chmod -ing on entire system folders with sudo since you can really mess up your system. If you are the only user of the machine it is not as important as if you have mulitple users or share a network. For your information, this is what my entry for /home looks like (755):
> 
drwxr-xr-x   3 root root    4096 2009-03-28 22:37 home


---

### Post by virgil_machine on 2009-04-11
Thanks. Would you suggest that I chmod /home to 755 (without -R)?

---

### Post by virgil_machine on 2009-04-12
OK. I changed /home to 755 and it looks like yours:
```
drwxr-xr-x   3 root root  4096 2009-03-15 12:48 home
```

I guess I'm set (for now).

Thanks.

---

