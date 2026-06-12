---
title: "adding shutdown command to script"
date: 2009-04-10
forum: General Help
---

### Post by fistikuffs on 2009-04-10
Hi,

I've created a simple rsync script and added it as laucner on the desktop panel so my girlfriend can simply double click the icon to backup her photos to a server/nas. Is it possible for me to add a shutdown command to the script that will execute only once the rsync is complete? This way she can simply double click the launcher and walk away knowing that the data will be backed up and the laptop will be shutdown. Can anyone help with this?

Thanks

---

### Post by VCoolio on 2009-04-10
add
```
&& shutdown -hP now
```
The && makes sure the preceding process is finished.
Edit: I changed shutdown rights to user, normally it requires root. Either you do 
```
sudo chmod u+x /sbin/shutdown
```
or 
write sudo in the first code I gave (&& sudo shutdown etc) and do
```
sudo chmod u+x /path/to/your/script
```

---

### Post by Keith Hedger on 2009-04-10
Add this to the last line of your script if you are running it as root:
```

shutdown -h now

```

or if not:
```

echo "PASSWORD"|sudo -S shutdown -h now

```

Change "PASSWORD" to you admin password, as the password is in clear text this is not wonderfully secure but I'm sure you can trust your girlfriend.

---

### Post by N_Nick on 2009-04-10
> **Keith Hedger said:**
> Add this to the last line of your script if you are running it as root:
```

shutdown -h now

```

or if not:
```

echo "PASSWORD"|sudo -S shutdown -h now

```

Change "PASSWORD" to you admin password, as the password is in clear text this is not wonderfully secure but I'm sure you can trust your girlfriend.

Sorry for posting in this thread but i have a similar problem.
I use a script to unmount my external HD because Ubuntu's unmount doesnt unmount the disk properly (the heads are still spinning".

I must be sudo to execute it so a terminal pops up to ask for my password. Is it possible to use same echo password so that it doesnt ask for my password every time? Something like

```
echo "PASSWORD"|sudo sh script
```

---

### Post by fistikuffs on 2009-04-10
> **Keith Hedger said:**
> Add this to the last line of your script if you are running it as root:
```

shutdown -h now

```

or if not:
```

echo "PASSWORD"|sudo -S shutdown -h now

```

Change "PASSWORD" to you admin password, as the password is in clear text this is not wonderfully secure but I'm sure you can trust your girlfriend.

Hi thanks for the responses, the second line in the second post did it for me:

```

echo "PASSWORD"|sudo -S shutdown -h now

```

I guess that the commands in the first post didn't change the user rights for shutdown. As soon as i used a password it worked great. Not ideal but as you say, i should be able to trust my gf ;)
Thanks for the help everyone, my gf is a new convert to ubuntu and handy little things like this will keep her with ubuntu

---

### Post by sdennie on 2009-04-10
You can add the user to /etc/sudoers for the ability to run /sbin/shutdown without a password.  Something like this:

```

**the_user_name** ALL=NOPASSWD: /sbin/shutdown

```

Then instead of using "shutdown ..." use "sudo shutdown ...".

---

### Post by Keith Hedger on 2009-04-10
N_Nick yes you can use  ```

echo "PASSWORD"|sudo -S sh script

```

to basically run any command but dont forget the "-S" (capital S) as it tells the sudo command to access stdin for the password see the man page for sudo

Thanks to sdennie for his tip as I didn't know that and his way is proably much more secure!

---

### Post by fistikuffs on 2009-04-16
> **sdennie said:**
> You can add the user to /etc/sudoers for the ability to run /sbin/shutdown without a password.  Something like this:

```

**the_user_name** ALL=NOPASSWD: /sbin/shutdown

```

Then instead of using "shutdown ..." use "sudo shutdown ...".

Even better! Thanks.

---

### Post by Alekz_ on 2009-04-16
> **fistikuffs said:**
> Even better! Thanks.

That's probably the best answer, but you can also put a 'stickbit' in shutdown file!

```
chmod +s /sbin/shutdown
```

It'll work too! And you won't need use `sudo` anymore! :)

[]'s

Alekz_

---

