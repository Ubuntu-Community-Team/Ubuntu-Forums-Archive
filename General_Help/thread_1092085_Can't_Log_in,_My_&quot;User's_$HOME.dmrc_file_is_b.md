---
title: "Can't Log in, My &quot;User's $HOME/.dmrc file is being ignored&quot;"
date: 2009-03-10
forum: General Help
---

### Post by Token-Ring on 2009-03-10
I'm not sure what happened. But today I installed a bunch of programs after finishing a Ubuntu build, the last of which was either vsftp or open-ssh. When I restarted my computer and tried to log on I was given this error after entering my username and password.

```
User's $HOME/.dmrc file is being ignored. This 
prevents the default session and language from 
being saved. Files should be owned by user and have 
644 permissions. User's $HOME directory must be 
owned by user and not writable by other users. 
```

I click ok, and after a while this pops up:

```
The GNOME session manager was unable to lock the
 file '/home/evan/.ICEauthority'. Please report this as a 
GNOME bug. Sometimes this error may occur if the file's 
directory is unwritable, you could try logging in via 
the failsafe session and ensuring that it is.
```

So I try switching the session to failsafe GNOME and I get the same set of errors. So I assume the FTP server must have changed the 
permissions on my home directory or something, but I can't log in to fix it.

Any one have any suggestions to fix this? Some magical command that makes everything better possibly?

---

### Post by iaculallad on 2009-03-10
Boot using the recovery mode. While on the terminal, try performing the following commands below:

```
chmod 644 ~/.dmrc
chmod 700 ~
```

~ represents you're home directory.

As in:

```
chmod 644 /home/your_username/.dmrc
chmod 700 /home/your_username

```
After successfully executing the commands above, restart:

```
shutdown -r now
```

---

### Post by Token-Ring on 2009-03-10
Well that made progress. I did what you said and got no errors. But when I tried to log in I got the same first error about my file being ignored. But I get a new second message:

```
You Session only lasted less than 10 seconds. If you 
have not logged out your self, this could mean that 
their was some installation problem or that you may 
be out of diskspace. Try logging in with one of the 
failsafe sessions to see if you can fix the problem. 

View Details:

/etc/gmd/Xsession: Beginning session setup...
Can't create dir /home/name/Desktop
Can't create dir /home/name/Desktop
Can't create dir /home/name/Templates
Can't create dir /home/name/Public
Can't create dir /home/name/Documents
Can't create dir /home/name/Music
Can't create dir /home/name/Pictures
Can't create dir /home/name/Videos
Setting IM through im-switch for local=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/Xll/xinit/Xinput.d/default.

(seahorse-agent:5528): libgnomevfs-WARNING **: Unable to create ~/.gonme2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/name/.gnome2/': Permission denied 

```

I hope I don't have to type that again...

I think I am going to log back in to recovery mode and try to create a new user account to I can at least log in. Any other suggestions?

Thanks for your help so far.

---

### Post by taurus on 2009-03-10
Did you create a new user and move stuff from one account to another because the first error message was about /home/evan but the second error message was about /home/name?

---

### Post by Token-Ring on 2009-03-10
No, I was hoping to create a new account to log into with and fix the permissions from there. But I quickly found out their are too many configuration files required for me to make an account from console and log into easily.

I think if I can just change the permissions for my home folder and everything in it I should be fine. But I don't know how to do that from command line.

Also, home/name and home/evan are the same. I forgot that I changed the name when I typed the second post.

---

### Post by taurus on 2009-03-10
We are still talking about /home/evan account right.  

While at the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, try

```
sudo chown -R evan:evan /home/evan
sudo chmod -R 755 /home/evan
sudo chmod 600 /home/evan/.dmrc 
sudo chmod 600 /home/evan/.ICEauthority
```
Now press <Alt>F7 to get back to GUI login screen and log in.

---

### Post by pmlxuser on 2009-03-10
i think you can check this thread

[http://ubuntuforums.org/showthread.php?t=866726](http://ubuntuforums.org/showthread.php?t=866726)

same problem was solved

---

### Post by Token-Ring on 2009-03-10
HUZZAH! Your suggestion worked taurus! Everything logs in just fine.

Thank you guys for your help.

---

