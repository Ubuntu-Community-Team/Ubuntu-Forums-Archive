---
title: "gconf-sanity-check-2 exited with status 256"
date: 2008-09-11
forum: Desktop Environments
---

### Post by LittleKoy on 2008-09-11
Hello, I'm using Intrepid right now, but I don't think this is actually version-related. When I try to start Gnome, an error message pops up ans says that "gconf-sanity-check-2 exited with status 256"
Lxde runs fine, but several programs (firefox, any gnome program, etc) shows an error about the configuration.

I already tried doing
```
sudo apt-get remove gconf2 gconf2-common
```
```
sudo rm -rf /etc/gconf 
``` (after doing a backup)
```
sudo apt-get install ubuntu-desktop
```

but nothing changed. I read on launchpad (googling I found 1 result!!!) that a guy solved coping /etc/gconf from another installation.

---

### Post by LittleKoy on 2008-09-12
Updates:

if I launch it from terminal, I get an alert message:

Please contact your system administrator to resolve the following problem:
No configuration sources in the configuration file "/etc/gconf/2/path"; this means that preferences and other settings can't be saved. Error reading the file: Failed: Couldn't open path file `/etc/gconf/2/path': No such file or directory

and on the terminal:

Failed to load addresses to delete locks

---

### Post by roadrun777 on 2008-09-13
I have the exact same problem on boot up. What are you loading in a terminal to get the error code?

I tried loading gconf-configure but it doesn't spit any error codes out.

I just get the "gconf-sanity-check-2 exited with status 256" when it first loads the desktop.

There doesn't seem to be anything in the log files about the error, so I don't really know where to go from here.

Btw, I am testing Intrepid.

---

### Post by roadrun777 on 2008-09-17
Ok I solved this one by changing the permissions on one of the XML files in the /etc/gconf folder. I can't find the original text so I don't know which file it was. 
The file was the only one lacking group/other read/execute attributes. All the rest of the XML files had these attributes.

---

### Post by True on 2008-10-14
If anyone still has this issue it appears that this resolves it:

sudo chmod 755 /etc/gconf/gconf.xml.system

Thanks roadrun777 for pointing the way..

---

### Post by Vadi on 2009-04-10
Also try:
> 
mkdir -p /etc/gconf/gconf.xml.system; chmod 755 /etc/gconf/gconf.xml.system

marv on #gnome suggested to try that.

---

### Post by cjsteele on 2009-05-18
Excellent!  This solved the issue in Karmic testing too!  Thanks guys.

---

### Post by rccn on 2009-10-18
Apparently, this can also happen if the permissions of /home/USERNAME are wrong. I had to change the owner of this directory to myself to make it work.

```
sudo chmod -Rc USERNAME:USERNAME /home/USERNAME
```

---

### Post by cjsteele on 2009-10-18
> **rccn said:**
> Apparently, this can also happen if the permissions of /home/USERNAME are wrong. I had to change the owner of this directory to myself to make it work.

```
sudo chmod -Rc USERNAME:USERNAME /home/USERNAME
```

I'd use caution before executing that command because there are pleanty of instances in which that would do horrible things to my system.  So, just a word to the wise.... make sure you know what you're doing before you do that.

---

### Post by lecoeus on 2009-10-24
Let me share with everyone how I solved this problem. I started getting the gconf-sanity-check-2 fail at the startup when I upgraded from Jaunty to Karmic RC. sudo chmod 755'ing /etc/gconf/gconf.xml.system did not solve the problem, but I then did

```
sudo chmod 755 /etc/gconf/gconf.xml.*
```


and the problem was gone. It seems the upgrade somehow changed the permissions of all 3 of the xml folders in there and you have got to change them all back to 755. 

> 

sudo chmod -Rc USERNAME:USERNAME /home/USERNAME



This seems a little dangerous.

---

### Post by ibizatunes on 2009-10-25
i found the fix that works for me
i was getting this error on ubuntu 9.10 
i did 


su to the users

the

sudo chown user -R /home/user (where user is obviously your user name - run as su ) and I am now able to log in.

found the fix here

[http://forums.fedoraforum.org/showthread.php?t=205035](http://forums.fedoraforum.org/showthread.php?t=205035)

---

### Post by klausner on 2009-12-31
> **True said:**
> If anyone still has this issue it appears that this resolves it:

sudo chmod 755 /etc/gconf/gconf.xml.system

Nope. Didn't work for me! Still meed a solution. :(

---

### Post by wyliecoyoteuk on 2010-01-10
I had this after installing zoneminder and mjpg-streamer on Mythbuntu
.
I think it was because they locked shared memory, so other processes couldn't run.
disabling rc.local (the script I used to run them ) cured it.

---

### Post by praveenkumar1511 on 2010-01-10
Freshly installed the system with Ubuntu, but facing the same problem.
Does anything to do with the sys. conf  ?

---

### Post by gawul on 2010-01-12
I found that I had incorrect permissions on the /tmp directory.  They should read:
drwxrwxrwt   15 root root   4096 Jan 11 17:08 tmp

Confirm all users can read/write/execute the directory. Also set the sticky bit. Set the bits correctly with chmod:

chmod ugo=rwxt /tmp

or set it with the octal:

chmod 1777 /tmp

---

### Post by dk4xp on 2010-01-13
> **gawul said:**
> 

chmod 1777 /tmp

You posted that just in time for me :-)

I moved /tmp from the slow boot disk to a new RAID0
by doing   sudo cp -r /tmp /raid/tmp and replacing /tmp by a symbolic link to /raid/tmp

That worked for everything, but then CUPS complained that it could not create
a tempfile,so I moved everyting back and must have messed up the access rights in that processs. 
I have not yet retested printing.

thanks, Gerhard

---

### Post by cendo on 2010-03-23
Thanks! It solved my problem, when after some security updates for Karmic I got the 'gconf-sanity-check-2' error.

---

### Post by midinas on 2010-04-15
In my case the write permissions for the /tmp folder were missing for some reason.

So this fixed the issue:
```
chmod 777 /tmp 
```The logfile /var/log/gdm/:0-greeter.log gave me a hint by telling that the file
"/tmp/gconf-test-locking-file4QI0AV"
could not be created with an error "Permission denied."

I'am not sure if thats related to the issue but the error occured on a reboot after I deleted all files from /tmp.

---

### Post by cymentor on 2010-04-21
Hi all
and thanks to dk4xp

the /tmp folder obviously lacked the executive permissions 

problem solved

---

### Post by budd60 on 2010-04-21
Same problem, but I get /usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256.

When I do:
 locate gconf-sanity-check-2  I get: /usr/lib/libconf2-4/

When I try to cd to that directory I get:
bash: cd: /usr/lib/libconf2-4/ no such file or directory

Ahh, I see these are hidden files (booted from CD). But I can't do anything because they are owned by root.

?

---

### Post by Kr8tion on 2010-06-27
> **budd60 said:**
> Same problem, but I get /usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256.

When I do:
 locate gconf-sanity-check-2  I get: /usr/lib/libconf2-4/

When I try to cd to that directory I get:
bash: cd: /usr/lib/libconf2-4/ no such file or directory

Ahh, I see these are hidden files (booted from CD). But I can't do anything because they are owned by root.

?

i'm having the exact same problem. it keep's asking for the passphrase and when i enter it, i still have the same issues. I don't mind reinstall the o/s, but how can i get my files from out of the home folder when it keep denying permission?

---

### Post by Ofloo on 2010-07-10
i'm having the exact same issue today.

---

### Post by sinner99 on 2010-07-11
yahuh....i moved some drives from different controllers around, but fstab was fine booting, upon login i get this error, so i login as root(i know i know shame shame)and there is noone but root under /home. it appears my entire profile has vanished! backups i know! ugh i sure hope its there.....wth. moving 2 drives to different controllers would cause this. the lucid installed drive didnt move at all, same controller same cable, maybe different power end...messed up. any ideas folks? this is not cool....just vanished it seems. :(

---

### Post by regularjack on 2010-07-19
boot into recover mode, get a root shell, and change the permissions of /tmp as described in comment #18 of this thread. that'll fix it

---

### Post by bredsj on 2010-08-08
After the latest updates I now have the same problem. I have tried all the above advice with no success!

Any more suggestions, please!

---

### Post by AZGLI on 2010-08-10
Installed the latest updates and get this error. I tried all the fixes listed and went from being able to log in as root to not being able to log in at all. My next step is to try from a liveCD, but past that, I am at a loss. Anyone know what has caused this and how to solve it?

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

### Post by mekh on 2011-01-31
Hi All,
Today I faced with the subj problem. Nothing mentioned in this thread didn't help me. The reason of that error was wrong permissions in /var/lib/gdm.

$ls -la /var/lib/gdm

drwxrwx--T  9 root  gdm  4096 30 10:13 ./
drwxr-xr-x 17 root  root 4096 26 02:32 ../
drwx------  2 root  gdm  4096 25 15:30 .config/
drwx------  3 root  gdm  4096 25 15:30 .dbus/
drwxr-xr-x  2 root  gdm  4096 26 03:00 .fontconfig/
drwx------  3 root  gdm  4096 26 10:02 .gconf/
drwx------  2 root  gdm  4096 26 10:02 .gconfd/
drwxr-x--T  2 root  gdm  4096 12 20:13 .gconf.mandatory/
-rw-r--r--  1 root  root 365  12 20:13 .gconf.path
-rw-------  1 root  gdm  2576 26 10:02 .ICEauthority
drwxr-x---  3 root  gdm  4096 25 15:30 Seat1/

All you need is to change root to gdm:
chown -R gdm /var/lib/gdm/

---

### Post by joe joe on 2011-02-23
[COLOR=Black]_[Changing permissions to my /tmp directory solved my issue as well. Thanks for suggestion. ]("http://ubuntuforums.org/member.php?u=996227")_[/COLOR]:D

chmod 777 /tmp

---

### Post by Gartral on 2011-02-28
I'm still having problems after trying all these... i'm going too reload...

---

### Post by toounknown on 2011-05-11
Ok, I solved this in 11.04 for me.  This happened after (failing) to install Doom3 (still won't work).
 
The permissions on \home\user were messed up, fixed that one but then I realized that this may have messed up .gvfs as well...
 
So on a hunch in the term I ran sudo umount .gvfs to unmount it
then I ran sudo chmod 777 .gvfs to give it full rights
then a reboot later everything was back to normal.:P
 
I also was getting the ICEauthority error and had to rename the ICEauthority file.  This was due to permissions as well.
 
Hate to hijack a thread but has anyone gotten the intsaller for doom3 to workon natty yet?  it just fails with a file not found error and there are no other install scripts out there...:confused:

---

### Post by petruha on 2011-05-19
Tried all proposals regarding permissions etc to no avail (on a fresh 11.04 64bit install).
"sudo apt-get install gnome-panel" - FIXED it at once for me.
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269244](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269244)

---

### Post by docsoliday on 2011-06-17
I had the same error due to /tmp permissions.  sudo chmod 777 /tmp fixed it.

To help find this, boot off of a live CD or ssh to the machine from another system and manually run /usr/lib/libgconf2-4/gconf-sanity-check-2 manually.  That will tell you WHAT it's complaining about vs. just complaining.

---

### Post by mcpentax on 2011-07-24
> **docsoliday said:**
>  To help find this, boot off of a live CD or ssh to the machine from another system and manually run /usr/lib/libgconf2-4/gconf-sanity-check-2 manually.  That will tell you WHAT it's complaining about vs. just complaining.

Thanks for this tip. Using ssh from another machine in the LAN I was able to see what was the problem and solved it. (it was a wrong path in a configuration file)

---

### Post by rokky on 2011-08-21
Several replies here mention correcting /tmp by changing permissions to 777.  That will get by in most cases, but to be really complete, that should be 1777, which includes the "sticky bit" setting.  That ensures users cannot remove or rename files they do not own in /tmp - probably 1 of several "sanity checks" that gconf-sanity-check-2 loses its mind over based on other scenarios listed in this thread, and which was my problem after creating a new /tmp on a bigger drive, and forgetting about that chmod setting.

---

### Post by kdub432 on 2011-09-22
I had this problem, turns out my /tmp directory was set with the wrong permissions.
fixed with:

chmod ugo=rwxt /tmp

---

### Post by greenblob on 2011-10-09
I'm getting this issue ON BOOT with an asus EEE PC 901 on 11.04 natty, I get to the BIOS & Ubuntu starts loading then I get this error... **PLEASE HELP!!!**

would using a different version (e.g. 10.10) help?:(:(:(

---

### Post by mrinvader on 2011-11-04
Hi all, just wanted to say 
```
sudo chown -R gdm /var/lib/gdm
sudo chmod 755 -R /etc/gconf/gconf.xml*
sudo chown -R USER:USER /home/USER 
sudo chmod ugo+rwxt /tmp 
```
worked for me!! I dont know which actually was the winner, but these permissions all seem sane (hehe sanity check lol). 

My system is now running great, but only standing on the shoulders of giants! 

Thanks everyone!

-Tom :D

---

### Post by chandanjc1 on 2012-05-19
Thanks for the info, adding permission to /tmp fixed the problem for me on 11.04.

---

### Post by Thad E Ginathom on 2012-08-05
Another instance...

fixing /tmp permissions cured it for me today.

I do wonder what broke it. And I also wonder why the stupid error message. *Can't open /tmp/whatever* might have been a clue!

---

