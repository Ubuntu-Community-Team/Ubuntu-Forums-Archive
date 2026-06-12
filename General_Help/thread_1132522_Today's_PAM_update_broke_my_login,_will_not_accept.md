---
title: "Today's PAM update broke my login, will not accept my password. HELP!"
date: 2009-04-21
forum: General Help
---

### Post by benniboi on 2009-04-21
There were a number of updates this morning April 22 and I noticed that some said PAM. I left my desk and locked the screen and upon returning I found that it will no longer accept my password.

Using the passwd command I get this:

passwd: Authentication token manipulation error
passwd: password unchanged


I have searched the forums and have tried various things to no avail. I can log in with my domain account but not my local one which has all my apps installed under it. I don't want to reinstall the OS as that's pretty drastic, it took me days to customise all the little bits as this is running on a Macbook Air.

Is there any way to remove the updates from this morning?

Any help would be greatly appreciated.

---

### Post by iponeverything on 2009-04-22
> Is there any way to remove the updates from this morning?

Any help would be greatly appreciated. 

From the grub boot menu, choose "rescue"

Get a prompt and run:

```

cd /root/.synaptic/log
ls -ltr 

```

The last file in the list will contain the latest updates made to the system.

```
cat $(ls -tr |tail -1)
```

you can roll back those updates like so:

find the old packages in your apt archive directory

```

cd /var/cache/apt/archives
ls |grep <package name>

``` 

You should find the new and previous versions of the packages there.  
install the previous versions with the command 

```
dpkg -i <package>
```

If several packages were installed try putting them all on the same line like so:

```
dpkg -i <package> <package> <package>
```

---

### Post by benniboi on 2009-04-22
Thank you for that, I succesfully managed to roll back to the previous packages.

However the damage was done when these were installed. I still can't use the paswd command... totally stuck and locked out of my account...

---

### Post by iponeverything on 2009-04-22
Try resetting password from the rescue prompt:

```
passwd <account>
```

---

### Post by benniboi on 2009-04-22
Yeah I have tried that, and I get this:

passwd: Authentication token manipulation error
passwd: password unchanged

If I change the user to my account with sudo -i -u <username>
and then run passwd command, it asks me for my old password and will not accept it...

---

### Post by iponeverything on 2009-04-22
I think that you need to recreate /etc/shadow

```
pwconv
```

BTW -- I am glad that you were able to follow my rollback instructions.

It was the abridged version ;)

---

### Post by benniboi on 2009-04-22
Yeah :) those instructions will come in handy again in the future I'm sure. Thank you for that.

I ran the pwconv command as root and nothing happened. Switching users and executing the same command said "can't lock password" file...

---

### Post by iponeverything on 2009-04-22
Sorry -- My instructions were incomplete.

as root try:

```

mv /etc/shadow /etc/shadow.old
pwconv
passwd <account>

```

---

### Post by benniboi on 2009-04-22
Thanks, did that and still get:

passwd: Authentication token manipulation error
passwd: password unchanged

---

### Post by iponeverything on 2009-04-22
so strange.

does doing:

```

grep <user> /etc/passwd
grep <user> /etc/shadow

```

show the account? Very strange indeed.

---

### Post by iponeverything on 2009-04-22
so strange.

does doing:

```

grep <user> /etc/passwd
grep <user> /etc/shadow

```

show the account? Very strange indeed. 

do you see something like:

```
/etc/shadow:foo:$6$U1Yv7USF$b1.BFu43ehsDHeT3zIhb7TC6ZexkNGiLCqwSRotXl6Z2K7pox/V0/9YlzC06U46DHUoshbgdzBMx5SOB0.iYE1:14356:0:99999:7:::


/etc/passwd:foo:x:1000:1000:foo,,,:/home/foo:/bin/bash
```

---

### Post by benniboi on 2009-04-22
oh wow, when i select Drop to root shell prompt it is asking me for root password for maintenance... did that pwconv command change something?

I didn't change the root password, and actually couldn't with the passwd command constantly failing...

---

### Post by iponeverything on 2009-04-22
pwconv recreate the shadow password file. The root password should now be blank.

It should not be prompting you for password at all.

Anyway can you boot from CD so that we can the copy the backup that we made of shadow file back into place?

Sorry.. I really didn't think this issue was that complex..

---

### Post by iponeverything on 2009-04-22
To move the old shadow back into place, lets boot into single user -- remount the / rw and move the file.


from the grub menu hit -- Choose your regular kernel and hit "e"
to edit. Go to kernel line (i think that it is the second one)
 and hit "e" again

It should look something like this:


```
/boot/vmlinuz-2.6.27-11-generic root=UUID=c864bde0-98d0-48b7-a3db-ca39981fc570 ro quiet splash
```

replace "ro quiet splash" with "ro init=/bin/bash"

After it boots to root prompt do:

```

mount -o remount,rw /
mv /etc/shadow.old /etc/shadow
sync; sync; sync

```

then reboot your system and the old shadow file will be back in place.

---

### Post by benniboi on 2009-04-22
phew... back to the way it was before at least. Thank you.

I ran 

grep <user> /etc/passwd
grep <user> /etc/shadow

and I could see the account in both instances, much like your examples above.

Not sure where to go from here, I am still unable to change my login password. In either case, thank you for your time, much appreciated.

---

### Post by iponeverything on 2009-04-22
Does your passwd still have its suid bit set?

ls -l /usr/bin/passwd

-rwsr-xr-x 1 root root 32988 2008-12-08 13:47 /usr/bin/passwd

Lets try creating a new account to see if the password manipulation works with it, or if the issue is just with the original account.. strange..

---

### Post by iponeverything on 2009-04-22
let me add that your problem more of a glitch, nothing really serious.. I'll come back with few good tests for you try in a bit -- to get to the bottom of what is going on.

---

### Post by benniboi on 2009-04-22
Yeah I get a line pretty much the same as yours.

I tried creating a new user. Seems to create the home directory, then it says

Copying files from /etc/skel

and then the error

passwd: Authentication token manipulation error
passwd: password unchanged

---

### Post by benniboi on 2009-04-22
additionally, when trying to create a new account and it fails, it told me that the root account expired.

I managed to change the expiry date with usermod-e and then try create another account. Fails again with that authentication token error and an additional one, "PAM authentication failed".

I'm convinced that it was the PAM updates this morning that stuffed things up.

---

### Post by iponeverything on 2009-04-22
Make a couple of passwd or login attempts and post about the last 15 or so lines of /var/log/auth.log .

also post the pam config file:

/etc/pam.d/passwd

---

### Post by iponeverything on 2009-04-22
I found the pam update in question and it was in response to this bug:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/295441](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/295441)

the new package spawned this bug report:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/364665](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/364665)

see if you can copy your /etc/pam.d/login file to thumbdrive as login.txt and upload it as attachment.

also does running:

/usr/sbin/pam-auth-update

generate the same errors reported in second of the above bug reports?

---

### Post by benniboi on 2009-04-22
Running /usr/sbin/pam-auth-update as root didn't produce any errors, only when I tried running it as my domain account user which I can still log in with.

Attached are the two files you asked for, plus this morning's lines from auth.log

Interestingly, I removed the x in between the two colons in the root entry in etc/passwd and re-ran the pwconv utility and now when I go to recovery mode it no longer asks me for the password for root, just says press enter to continue and enter shell.

---

### Post by iponeverything on 2009-04-22
Your auth.log seems to be pointing to gnome-keyring-daemon or dbus as the guilty party.  Found the below thread with google.

[http://ubuntuforums.org/showthread.php?p=6450387](http://ubuntuforums.org/showthread.php?p=6450387)

You could try a roll back on the gnome-keyring-daemon stuff.

Whatever the bug is that you have found, it seems to be obscure.

---

### Post by benniboi on 2009-04-22
hmmm looks like there's no fix for it as yet...

Interestingly, when I run passwd -u command it says password changed. I don't know what that's about or whether it really is changing the password. Ran that originally to make sure the account wasn't locked.

it's looking more and more like a reinstall... not looking forward to it, took ages to get all the little features of macbook air going just right... :(

---

### Post by iponeverything on 2009-04-22
your pam.d/passwd file is identical to mine

your pam.d/login file contains one extra module:

```
session sufficient /lib/security/pam_lsass.so
```

---

### Post by benniboi on 2009-04-22
Should I remove it?

---

### Post by iponeverything on 2009-04-22
Maybe try what this guy did:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791)

---

### Post by iponeverything on 2009-04-22
> **benniboi said:**
> Should I remove it?

you can comment it out to see if it helps.

---

### Post by benniboi on 2009-04-22
Hmmm... I did that and was able to change the root and my login password. However the gnome login will still not accept the new password.

---

### Post by benniboi on 2009-04-22
In the end had to revert the changes as the gnome wouldn't even take my domain login anymore. Once reverted I can at least use the domain login.

---

### Post by benniboi on 2009-04-22
Additonally, I've created a new account as well, set the password and all, but gnome login will not accept it.

---

### Post by iponeverything on 2009-04-22
As much as I hate to admit defeat, we have reached the point of diminishing returns. You could invest a lot more time trying to debug this.. (I would, but just because I enjoy banging my head against the wall) -- Or you could do a reinstall and get to where you before this happened in a lot less time.  The good news is that it should be a lot easier the second time around.

Another option would be wait a bit. They just pushed out the pam deb that mucked everything up -- If this affects quite a few people and is not something that manifested because of a unique configuration on your system -- reports will start coming in and it would likely get fixed fairly quickly. 

If you decide to reinstall, I would backup /home and maybe /etc.

---

### Post by benniboi on 2009-04-22
Yeah, I think a reinstall will be needed unfortunately, might just jump straight onto Jaunty. It would be good if apps could be backed up, not looking forward to re-installing Crossover and all the apps with it plus VMware and XP...

But thank you very much for your time, I really appreciate it. I've even learnt a few things along the way! :)

---

### Post by iponeverything on 2009-04-22
I think that Crossover and the installed Apps and the VMware OS image should be portable.

Back the them up and see if allows you bring them up on the new install.

---

### Post by benniboi on 2009-04-22
Do you know how I can back this up? I can't see any backup facilities in Ubuntu as standard. Do I need to load a 3rd party app?

---

### Post by iponeverything on 2009-04-23
everything is builtin.

My personal favourite is is tar.

backup home like so:

tar -zcvf /home.tgz /home/
then move /home.tgz off of the machine.

VMWare should not be an issue at all.. Not sure about Crossover, but my guess is that it will work fine.

I do not know where it installs the applications. My guess would be that they are under you home directory under in a hidden directory called .crossover something.

was crossover via a .deb file?  If so run:

```

dpkg -l |grep -i crossover
dpkg -L <package name>

```

This well tell you where crossover or VMWare installed itself.
If it was under /var/<somewhere> for example you can tar it up like so:

```
tar -xcvf /var.somewhere.tgz /var/<somewhere>

```

You can also just fire off quick email to company to ask best way backup and restore after a situation like this..

---

### Post by benniboi on 2009-04-23
Great, will do that. Thanks again!

---

