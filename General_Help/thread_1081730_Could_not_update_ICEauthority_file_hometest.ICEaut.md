---
title: "Could not update ICEauthority file /home/test/.ICEauthority"
date: 2009-02-26
forum: General Help
---

### Post by sharif_aly on 2009-02-26
I have this error on loading the desktop ubuntu

> Could not update ICEauthority file /home/test/.ICEauthority

---

### Post by taurus on 2009-02-26
You probably need to change the permissions and ownership for it to work again.

```
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority 
```
Log out and back in again.

---

### Post by rusyear04 on 2009-04-21
hi there!

i have the same problem... unfortunately it persists even after

```

sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthor

```

after i log off and log in back again the permissions are set to -rw------ again.
can this be somehow related to my "installation history"? i had the previous ubuntu 8.10 and i'm using parallel to it winXP with ext2-read/write-plugin...

thanx in advance!

---

### Post by ubuwwyy on 2009-12-10
Thank you ,I have the same problem.I did it as you say. 
my system started slow ,and my wireless can't connect ,i must restart my system again,then it can connect.

---

### Post by brans041 on 2009-12-30
Any news on this? Having the same problem. I recently adjusted graphics and grub, had some grub issues with the splash screen and my ATI card. Otherwise I have made no changes.  Let me know.

---

### Post by jangirke on 2010-01-23
Hi All!

It works! :lolflag:

---

### Post by pstickar on 2010-01-25
Hi,

only the first command is necessary (change of ownership).

It could be interesting to find out the reason. I have not changed anything since weeks, aside of the normal updates. Another family member has the same problem on another computer. Both are Karmic installations.

Before I changed the ownership of the file, I tried a brute force X restart (ctr-alt-backspace), and got two error messages instead of one. The second one reads something like (sorry, a translation form german into my poor English):

> Error by loading/saving of evolution-alarm-notify configuration. Some of your preferences may not work properly.
The configuration server could not be contacted; possible error causes are, that TCP/IP for ORBit is not active, or that as a result of system crash old NFS-locks are active. Check [http://projects.gnome.org/gconf](http://projects.gnome.org/gconf) for more information.
Details: Connection to session could not be found: Failed to connect to Socket /tmp/dbus-dlIHE2vKhK: Connection refused.


I did visit [http://projects.gnome.org/gconf](http://projects.gnome.org/gconf) but it is not a document intended for a Monday Morning, when one is "allowed" to work.

Best regards,
p.

---

### Post by IanVaughan on 2010-03-23
> **jangirke said:**
> Hi All!

It works! :lolflag:

Just chown and chmod worked for you?
[It doesnt for me! ]("http://ubuntuforums.org/showthread.php?p=9016355")

---

### Post by bigseb on 2010-03-24
> **taurus said:**
> You probably need to change the permissions and ownership for it to work again.

```
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority 
```Log out and back in again.

I too have this problem. 

This might be a really silly question but I assume if I use the above code I must exchange all the 'test's with my username, right?

Just curious but what does this file do. It appeared after I installed Doom 3. What happens if I just delete it?

---

### Post by bigseb on 2010-03-24
> **bigseb said:**
> I too have this problem. 

This might be a really silly question but I assume if I use the above code I must exchange all the 'test's with my username, right?

Just curious but what does this file do. It appeared after I installed Doom 3. What happens if I just delete it?
Went out on a limb and change them all to my username. It worked. Thanks to all that helped!

Still really curious what that was about though. I mean what does that file do? And why did it slow down my startup like that?

---

### Post by Flos Headford on 2010-04-08
I tried all methods presented by the generous members of this list, but with no good fortune. I hope someone will find it useful.
Use a Ubuntu live distribution CD to reach a command-line terminal. First check that your $HOME directory (/home/username) has appropriate permissions, and that all directories can be examined with the "ls" command.
Then use ```
sudo apt-get remove nautilus
``` and remove any nautilus files and folders which might remain in $HOME. Also remove .ICEauthority from /var/lib/gdm (if it exists). Then you can reboot with ```
sudo shutdown -r now
``` and on restart, get to the CLI and use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and remove the CD from its drive. On reboot,  I can only hope that you have the same luck as me, and arrive safely at your usual login form.
Thanks to all, and best wishes,
Phil

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

### Post by suprman2020 on 2010-04-22
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

I was having this same issue and it killed my sound on Lucid. This right here did the trick. Thanks a lot.

---

### Post by kuric on 2010-04-30
sudo chown -R user:user /home/user/.*
(Where user is your username)

**mjcritchie solution** worked for me too. The ICEauthority problem occurred after installing Veetle Player as root in the next reboot.

---

### Post by DjTeriyake on 2010-05-10
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

```
sudo chown -R user:user /home/user/.*
```

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

I had the same issues as **suprman2020** and **kuric**; I installed the Veetle Player to stream online video and on the next restart I got the .ICEauthority error and no sound. Upon running the command provided by **mjcritchie** and logging out and back in again, the .ICEauthority error was gone and the volume tray icon reappeared, however I still had no sound. Restarting gave me sound back and now everything functions normally.

Thanks!

---

### Post by eakergd on 2010-06-19
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org


THANK YOU!  This one fixed it for me.

---

### Post by gandalf2000 on 2010-06-21
I had the same problen and the last fix worked for me.  I think this started after an update.  Also had trouble with Evolution and CouchDB which I had not seen before.  Thank you for the help.

---

### Post by Nausser on 2010-07-13
This fix helped my situation as well on 32-bit Lucid. Mine wasn't so terminal. I only received the error upon logging in. I actually didn't even have a .ICEauthority file or folder in my home directory. Once I issued the command, I restarted and did not receive the error message. I wasn't experiencing any problems, just that one pesky message on login.

ps. now I do have a .ICE authority file in my home folder. I can't open it to see what is inside. gedit isn't compatible with it's contents.

Thanks for the recommendation!

---

### Post by krul on 2010-09-26
This worked for me too:

> sudo chown -R user:user /home/user/.*

thnx

---

### Post by swright007 on 2010-09-28
I tried the fix you mentioned above and got the following error:

chown: cannot access `/home/scott/./.gvfs': Permission denied
chown: cannot access `/home/scott/.gvfs': Permission denied
 
However, upon reboot it worked JUST FINE !!!   Thank you for your advice!

sudo chown -R scott:scott /home/scott/.*       sure did the trick for me.



                               Scott Wright

---

### Post by delsix on 2010-10-03
> **swright007 said:**
> I tried the fix you mentioned above and got the following error:

chown: cannot access `/home/scott/./.gvfs': Permission denied
chown: cannot access `/home/scott/.gvfs': Permission denied
 
However, upon reboot it worked JUST FINE !!!   Thank you for your advice!

sudo chown -R scott:scott /home/scott/.*       sure did the trick for me.



                               Scott Wright

Exactly the same as this for me, many thanks to the clever clogs who solved it=D>

---

### Post by shabaaz on 2010-11-13
> **kuric said:**
> sudo chown -R user:user /home/user/.*
(Where user is your username)

**mjcritchie solution** worked for me too. The ICEauthority problem occurred after installing Veetle Player as root in the next reboot.


for me too,this problem surfaced after i installed veetle plugin.

---

### Post by NetworkCowgirl on 2010-12-03
Try dpkg-reconfigure nautilus. Then reboot.

---

### Post by jack frost on 2011-02-23
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org


thanks.. that worked for me too.

---

### Post by ssdt on 2011-03-10
Is it somehow related to Veetle and about it being installed?

---

### Post by dl456 on 2011-03-17
So, I have the same problem as all y'all but when I  entered the above commands into my terminal, I was prompted to enter my password (which is normal), but when I tried to type in my password the letters and numbers would not appear on the screen.  Weird.  For some reason it made my keyboard not work for that command line all of a sudden.  I repeated this process several times but the same thing happened every time.   I know that my keyboard is working because I am typing this message with it.  Anybody have any ideas.  I know that the message seemed to start appearing around the same time that I got a message stating that my / (root) partition was almost full.  Which is another weird thing because when I check how much of my root partition is used with "GParted" (under system>administration) along with using the "df -H" command in the command line it shows that I have only used about 4.5GB and have about 7GB of unused space on my root partition.  Although, when I use the "Disk Usage Analyzer" (under Applications>Accessories) it shows that my whole root partition is full.   I'm not sure if all of this is connected but it all started happening around the same time.  Any help is appreciated.

---

### Post by travislam on 2011-03-24
I tried dpkg nautilus but nothing appears to happen... I still get the cannot create /home/user/.nautilus error as well. What should I do?

---

### Post by OooBuntuRox on 2011-04-06
> **taurus said:**
> You probably need to change the permissions and ownership for it to work again.

```
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority 
```Log out and back in again.


[SIZE=2]Worked for me first shot. Not sure if it matters during a cut and paste, but I did notice extra blank characters on the first line which I removed before executing the code.[/SIZE]

Thanks, OooBuntuRox :guitar:

---

### Post by trebor79 on 2011-07-06
> **kuric said:**
> sudo chown -R user:user /home/user/.*
(Where user is your username)

**mjcritchie solution** worked for me too. The ICEauthority problem occurred after installing Veetle Player as root in the next reboot.

This also happened to me on Ubuntu 11.04 after installing the Veetle plugin. The above fixed things though after logging out and logging back in.

Thanks!

---

### Post by nicknefarious on 2011-10-05
As above for many others this problem appeared for me after installing veetle on Natty 11.04 (64-bit).

This worked for me after some of the other solutions offered had not worked.

```
sudo chown -R user:user /home/user/.*
```

Replacing "user" in all places with your user name.

Important to note is to boot into recovery and drop into a root shell mode to do it and then reboot. This worked for me because  simply entering the code in a terminal while still logged in did not.

---

### Post by chanca on 2011-12-07
This worked for me, and Vettle was the problem.
Thank you.

---

### Post by publish905 on 2013-03-07
The following option worked for me:
sudo chown -R user:user /home/user/.* 			 		

thanks a bunch mjcritchie - YOU ROCK!

I do not have an .ICEauthority. How do I create one to put in the home directory so I do not have this problem again?  Also, I had an error message that "It seems you do not have the hardware required to run Unity. Use the classic version" - something to that effect. Note all these problems occurred with my system after running Bleachbit. I think Bleachbit messed up some packages. For instance, I also get an error that "there is a problem with the configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256."  

Word of advice - stay away from using Bleachbit on linux. It's better to use for windows, not linux. I wish I had read these warnings before using it: [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean).

---

