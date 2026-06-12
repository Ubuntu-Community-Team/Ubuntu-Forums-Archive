---
title: "Problem at Boot...ICEauthority and Nautilius???"
date: 2010-12-31
forum: Desktop Environments
---

### Post by robbrownu on 2010-12-31
(apologies in advance if I"m posting in the wrong spot...this is my first time on this board)
 
My new install of Ubuntu on my Dell PC had been working fine until this morning. 
 
It gets to the login, I enter my password and get the following errors. After a long pause, where it seems to freeze on my password login screen, the message says: 
 
1. Could not update ICEauthority file /home/robert/.ICEauthority
2. There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256).
3. Nautilus could not create the following require folders: /home/rober/Desktop, /home/robert/.nautilus. Before running Nautilus, please create these folders or set permissions such taht Nautilus can create them.
 
Rebooting in recovery mode doesn't solve the problem. I also went to the boot screen and tried a few of the obvious selections (freeing up space, fixing errors, etc.).
 
I've read a few threads, and it seems like there's an obvious fix to this that involves creating some folders using command prompts. Problem is, I'm an ubuntu noob, and don't know exactly what steps to follow. 
 
Can someone give me step/step instructions on what to do? I frankly don't even know what Nautilus is, and I'm willing to uninstall it if that's easy (and one can provide instructions).
 
Thanks!
Rob

---

### Post by robbrownu on 2010-12-31
uh oh...may have made the problem worse.
 
I followed some of the suggestions in the following chain of posts here.  Using this, I was able to log in, but I entered what seems to be a perfectly clean version of Ubuntu...with no access to my files.
 
[http://art.ubuntuforums.org/showthread.php?t=1553056&page=3](http://art.ubuntuforums.org/showthread.php?t=1553056&page=3)
 
 
Some of the commands I entered in the terminal included:
 
sudo chown -R Robert:Robert /home/Robert
 
AND 
 
sudo nano /etc/gdm/custom.conf
 
 
Anyone got any other ideas?

---

### Post by ajgreeny on 2010-12-31
From your post #2 note that your username will be** r**obert, not **R**obert.  Usernames can not have uppercase letters.

Try again with ```
sudo chown -R robert:robert /home/robert
```note the lower case for **robert** in all places.

---

### Post by robbrownu on 2010-12-31
Thanks for trying to help.  I'm really banging my head against the walll!
 
hmmmm....typed in that command with the lowercase r, and am still not finding any files.   It booted right up, but when i log in, nothing of my old files or settings is there....
 
Any other ideas?

---

### Post by ajgreeny on 2010-12-31
I note you have another thread on this subject which starts half way in.  This may well be confusing for people, so please don't do that if you can avoid it in future.

Can you please post here the output of ```
ls /home
```which will show all the users you have made, either on purpose, or by mistake.  We can then try to sort out your problem a bit further, as I do not think those files and folders will have been deleted, just moved somewhere, and now hidden from you.

---

### Post by robbrownu on 2011-01-01
Thanks for responding.
 
Typing ls /home only lists one user: robert

---

### Post by robbrownu on 2011-01-01
One more thing I found another command recommended by another chain of posts, that suggested printing the output of ls /home.  This is that output:
 
total 16
drwxr-xr-x  4 root   root   4096 2010-11-22 15:58 .
drwxr-xr-x 22 root   root   4096 2010-12-26 09:07 ..
drwxr-xr-x  3 root   root   4096 2010-11-22 15:58 .ecryptfs
drwxr-xr-x 28 robert robert 4096 2011-01-01 08:57 robert

Hope this helps

---

### Post by ajgreeny on 2011-01-01
What exactly was that command you typed?  Open a terminal again and use the up cursor key if you can't remember, to scroll through previous commands used.

You seem to have an encrypted filesystem in there ```
drwxr-xr-x  3 root   root   4096 2010-11-22 15:58 .ecryptfs
```which is not in my list of entries in /home.  Otherwise all seems to be OK.

Did you have an encrypted /home originally, as if so that may be the main difficulty I am having?  If that is the problem, I am afraid I can't help any further as I have never used encryption on a file system, and have no idea where to go from here.

I still believe that the files are in there somewhere, but how you can actually get to them is another thing entirely.  I would suggest to you, however, that in future you don't just type commands you have found on the internet without asking what they do first.  We could probably have avoided a lot of this headache for you, if you had asked first, and then acted more slowly.

---

### Post by robbrownu on 2011-01-01
I've not encrypted anything knowingly!  
 
I know I acted hastily.  I was in a rush to get to a document I couldn't access, and my misplaced confidence convinced me it'd be "easy" once I saw that there were similar problems on the message boards.
 
The command that I typed to get the second reading where you saw the encrypt file was
 
ls /home

---

### Post by ajgreeny on 2011-01-01
You must, therefore have some aliases in your ~/.bashrc file (or ~/.bash_aliases), as the command **ls /home** would normally just show the folder names, ie the usernames on the system, without all the other info shown, and certainly not the three root entries yours shows.  That normally needs **ls -la /home**

Do you have many of these customisations on your system?  This may be a total red-herring, as it still should not make any difference to this encryptfs problem, but I just want to try as far as I can, though I am running out of ideas.

Just a final thought; try running nautilus as root with the command **gksudo nautilus** to see if any other files and folders become visible that way

---

### Post by robbrownu on 2011-01-01
forgive me....i'm a bit of a noob.  Can you elaborate on what you're asking me to do?  I'm not familiar with Nautilus.

---

### Post by ajgreeny on 2011-01-02
I am suggesting you start nautilus with root permissions from terminal using the command ```
gksudo nautilus
```then just search around a bit to see if you can find your files and folders.

Just make sure you are careful, as if you delete any files from there, you will definitely be lost, so simply search around a bit.

Another thought;  if you can remember the names of any missing files, use the commands ```
sudo updatedb
``` then ```
locate <filename>
```and you might be lucky and find where they are.  I don't hold out too much hope, however, but you never know!

---

### Post by robbrownu on 2011-01-04
Opened Nautilius via the terminal.  The window opened, and there were  some files available, but only operating systems related files.  I  couldn't find my folder in there.

Got the following code in the terminal:

[INDENT]robert@robert-OptiPlex-GX260:~$ gksudo nautilus
Initializing nautilus-gdu extension

(nautilus:1973): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1973'
Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned  error 255: net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1973): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:1973): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL'

[/INDENT]

---

### Post by Qazjap11 on 2011-01-06
Have exactly the same problem. I'm quiet sure the problem is that the encryption isn't mounting (check ~ folder by la). I'll update if find a solution :)

---

### Post by johnaaronrose on 2011-01-28
I am now getting 'Problem with configuration server  /usr/lib/libgconf2-4/gconf-sanity-check exit with status 256'. I've  tried logging in with Session of 'Failsafe Gnome' -  sometimes it's OK  & sometimes it isn't.
 
 PS I first used sudo chown user:user /home/user/.* to correct the.ICEauthority problem following advice in thread 
[http://ubuntuforums.org/showthread.php?p=10405265#post10405265](http://ubuntuforums.org/showthread.php?p=10405265#post10405265)
Perhaps I should have used sudo chown /user:user /home/user/.ICEauthority rather than sudo chown user:user /home/user/.*
I've subsequently tried sudo chmod 1777 /tmp, which made no difference

---

### Post by johnaaronrose on 2011-01-30
Login is now working fine. I found a message (I've forgotten where) about 'deleting' .ICEauthority. The suggested method is:
mv /home/user/.ICEauthority /home/user/.ICEauthority.bak 
(where user is your login id).

This has the advantage that the .ICEauthority file can be restored by
mv /home/user/.ICEauthority.bak /home/user/.ICEauthority 
 even if the above method doesn't work.

Since both my login users only gave a 'blank' desktop (i.e. no menus or  quick launch icons) when I attempted the standard login, I logged into  the user with administrative privileges by changing the Session (at the  bottom of the screen) to root login (i.e. not one of the Gnome ones)  after selecting/keying in the login id but before keying in the  password.

After login I discovered that a much smaller .ICEauthority file had been  created (1kb versus 60+) for that user. I opened a Terminal &  repeated the command for my other user but with sudo before mv. I then  restarted and was able to login for my first Administrative user, logout  & login successfully for my second Desktop user.

---

