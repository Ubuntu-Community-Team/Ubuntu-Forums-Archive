---
title: "Make KDE apps more stable in GNOME"
date: 2008-02-04
forum: Desktop Environments
---

### Post by TWO on 2008-02-04
Does anybody know if there is any way to make KDE applications more stable under GNOME?

Amarok, for example, when played under GNOME is really resource intensive and it infrequently crashes.

Many Thanks 

TWO

---

### Post by hyperair on 2008-02-04
There isn't. But Amarok runs fine for me. About the same CPU usage as Exaile. One thing about Amarok is that it tends to get sluggish when you have a huge music library. So, switching your database backend to MySQL as shown here: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by TWO on 2008-02-04
> **hyperair said:**
> There isn't. But Amarok runs fine for me. About the same CPU usage as Exaile. One thing about Amarok is that it tends to get sluggish when you have a huge music library. So, switching your database backend to MySQL as shown here: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

Thank you! I'll have a look into that. That might be part of the problem. It is quite resource intensive when it's checking my library...

---

### Post by hyperair on 2008-02-04
Just so you know, before I used MySQL as the backend, my Amarok used to crash a lot. Annoyed the hell out of me, so I jumped from music player to music player, just to come back to Amarok at the end of the day. None are as feature-rich as Amarok.

---

### Post by TWO on 2008-02-04
> **hyperair said:**
> Just so you know, before I used MySQL as the backend, my Amarok used to crash a lot. Annoyed the hell out of me, so I jumped from music player to music player, just to come back to Amarok at the end of the day. None are as feature-rich as Amarok.

Yeah, I have to agree! Amarok is brilliant! I'll give that a try and hopefully the problem will be solved! :)

---

### Post by TWO on 2008-02-04
**(This message should be prior to the next one but I made a mistake.)**

The following error appears in Amarok too:

[I]MySQL reported the following error: Access denied for the user 'amarok'@'localhost' (using password: YES)

You can configure MySQL in the Collection section under Settings->Configure Amarok[/I]

---

### Post by TWO on 2008-02-04
> **hyperair said:**
> There isn't. But Amarok runs fine for me. About the same CPU usage as Exaile. One thing about Amarok is that it tends to get sluggish when you have a huge music library. So, switching your database backend to MySQL as shown here: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

OK. I just followed a slight variant to the page you suggested. 
[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)
(Mike's Ubuntu Blog.)

There seems to be a database access error though.

The following command:*** mysqlcheck -p --auto-repair --all-databases*** gives the following message in the Terminal:** *mysqlcheck: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect***

Furthermore, when trying to select the library folder in the "Build Collection" option of the "Context" tab, the sub folders of the partition where my files are are greyed out. 

Could you tell me where I am going wrong?

Many Thanks 

TWO

---

### Post by hyperair on 2008-02-05
From the command you posted, it seems that you've keyed in the wrong password for root@localhost while connecting to the MySQL server.

---

### Post by TWO on 2008-02-05
> **hyperair said:**
> From the command you posted, it seems that you've keyed in the wrong password for root@localhost while connecting to the MySQL server.

Hm...I'm not sure what I'm doing incorrectly here. I'm 100% sure that the password I entered in is the one that I set.

I just followed instructions from the following site and changed my password again: [http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/)

It has produced the same results again, but I am certain that I have keyed in the correct password.

---

### Post by hyperair on 2008-02-05
Try ```
mysql -u root -p
```
If you can log in using that code then your password should be correct. 

By the way, if you don't have anything of utter importance in your MySQL database, try removing the folder /etc/mysql, then start from scratch.

---

### Post by TWO on 2008-02-10
The password that I used once prompted after entering that code worked in the terminal yet Amarok is still spitting out that error.

I'll delete the folder, set it up again and see what happens.

---

### Post by TWO on 2008-02-13
> **hyperair said:**
> Try ```
mysql -u root -p
```
If you can log in using that code then your password should be correct. 

By the way, if you don't have anything of utter importance in your MySQL database, try removing the folder /etc/mysql, then start from scratch.

It appears I might have just done something silly by manually deleting the MySQL folder in /etc/. Even after reinstalling MySQL via the terminal, the folder is not restored.

How do I go about restoring the folder?

Thanks

TWO

---

### Post by hyperair on 2008-02-14
What happens when you try to set it up according to the article?

---

### Post by TWO on 2008-02-14
> **hyperair said:**
> What happens when you try to set it up according to the article?

I can't complete the stages in the article as a new problem has come up now where when using the *$ apt-get* command, the Terminal is now asking me to run *dpkg --configure -a* because "dpkg" was interrupted. On doing so, the terminal displays the following:

> Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.



The computer is now at 100% CPU usage and it isn't clear what the culprit is. That dkpg reconfigure command doesn't seem to be doing anything either as the Terminal doesn't show any further messages after that point.

---

### Post by hyperair on 2008-02-14
Good grief. Sorry, my bad, I told you to remove the wrong directory. The correct thing to do was remove everything inside /var/lib/mysql, but leave /var/lib/mysql around. Now what you need to do is restore the /etc/mysql folder. Navigate to /var/cache/apt/archives in nautilus. 
Right click on the deb called... "mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb". I'm assuming you're on an i386 architecture, but if you're not, then replace i386 with whatever your CPU architecture is. 
Click open with Archive Manager. If it's not there, you should go to properties->open with and add it there. 
Inside the deb there should be two files. data.tar.gz, and control.tar.gz. Open data.tar.gz. Grab the /etc/mysql folder from there, extract it to your desktop or something. Then, copy the whole folder into /etc. Basically you'll have restored your /etc/mysql folder. 
Then run sudo dpkg --configure -a.

---

### Post by TWO on 2008-02-14
> **hyperair said:**
> Good grief. Sorry, my bad, I told you to remove the wrong directory. The correct thing to do was remove everything inside /var/lib/mysql, but leave /var/lib/mysql around. Now what you need to do is restore the /etc/mysql folder. Navigate to /var/cache/apt/archives in nautilus. 
Right click on the deb called... "mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb". I'm assuming you're on an i386 architecture, but if you're not, then replace i386 with whatever your CPU architecture is. 
Click open with Archive Manager. If it's not there, you should go to properties->open with and add it there. 
Inside the deb there should be two files. data.tar.gz, and control.tar.gz. Open data.tar.gz. Grab the /etc/mysql folder from there, extract it to your desktop or something. Then, copy the whole folder into /etc. Basically you'll have restored your /etc/mysql folder. 
Then run sudo dpkg --configure -a.

Ah, phew! Thank you very much for your help. I really do need to get myself more familiar with the workings of my Ubuntu system; I envy you for your know-how! :)

It also appears that I hadn't followed the instructions from [http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup](http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup) concisely enough so the set-up is fine now and Amarok has finally loaded my songs which is great, and is noticeably much quicker than before! I'm glad to have Amarok back now, as it is easily the best music player on Linux in my opinion! 
Now with it being less demanding on my system, I'm looking forward to laying to rest the ongoing problem for me of searching for a decent music player!

Thanks once again!

TWO

---

### Post by hyperair on 2008-02-14
No problem ;) I'm glad I could be of help. Either way technical know-how comes naturally through experience, not to worry =P

---

### Post by nandotron on 2008-02-15
Hi guys, 

i did a search around the forums for an answer to this but didn't come up with anything.  I'm trying to configure amarok to use nautilus as it's default file browser.

for example, when i right-click on a song in amarok > Edit track information > click on the folder icon, to open the folder that houses the file, amarok uses firefox to open the folder.  is there a way to make it use nautilus without losing firefox as my default external web browser for links clicked in amarok?

Also, does anybody know what package i need to install to get the proper artist icons in the collection browser window in amarok.  It should be like a little blue figure, but i have a white page as in the image.

I'd really appreciate any help with this, thanks guys!

nando

---

### Post by TWO on 2008-02-20
> **nandotron said:**
> Hi guys, 

i did a search around the forums for an answer to this but didn't come up with anything.  I'm trying to configure amarok to use nautilus as it's default file browser.

for example, when i right-click on a song in amarok > Edit track information > click on the folder icon, to open the folder that houses the file, amarok uses firefox to open the folder.  is there a way to make it use nautilus without losing firefox as my default external web browser for links clicked in amarok?

Also, does anybody know what package i need to install to get the proper artist icons in the collection browser window in amarok.  It should be like a little blue figure, but i have a white page as in the image.

I'd really appreciate any help with this, thanks guys!

nando

I was unaware that it did that, but when I tried it gave me the same result. Erm...what does the program do on a KDE system with the same action?

My collection browser window also appears the same as you describe...I didn't realise that that's not how it should be!

I'll have a look around too.

---

### Post by TWO on 2008-02-20
Here's another one for anyone who can help.

Any ideas on how to get Amarok to change my album art? When I ask the program to remove the currently assigned album art or to change it it doesn't seem to want to do some. 

I like to keep my files organised, so if anyone has any suggestions, please share them! :popcorn:

Many Thanks

TWO

---

### Post by TWO on 2008-02-20
> **nandotron said:**
> Hi guys, 

i did a search around the forums for an answer to this but didn't come up with anything.  I'm trying to configure amarok to use nautilus as it's default file browser.

for example, when i right-click on a song in amarok > Edit track information > click on the folder icon, to open the folder that houses the file, amarok uses firefox to open the folder.  is there a way to make it use nautilus without losing firefox as my default external web browser for links clicked in amarok?

Also, does anybody know what package i need to install to get the proper artist icons in the collection browser window in amarok.  It should be like a little blue figure, but i have a white page as in the image.

I'd really appreciate any help with this, thanks guys!

nando

I just downloaded the kubuntu-desktop and I now see the effect of which you were speaking on the collection browser window. They appear with little blue figures.

AmaroK seems to be running even quicker on the Kubuntu Desktop too, but maybe that's for obvious reason, it's KDE...

Completely off topic though, I wonder if anyone could tell me why OpenOffice is starting up quicker on the Kubuntu desktop over the Ubuntu? Is this just me, or is common?

---

### Post by TWO on 2008-02-20
> **nandotron said:**
> Hi guys, 
Also, does anybody know what package i need to install to get the proper artist icons in the collection browser window in amarok.  It should be like a little blue figure, but i have a white page as in the image.

nando

nandotron, try installing the kde-core package. According to: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) it is "the bare minimum required of KDE."

---

### Post by hyperair on 2008-02-20
Little blue figures appear for me even on GNOME. But that's probably because I installed kubuntu-desktop already on my computer.

Also, for setting Nautilus as the default file manager (and Firefox as your browser), try setting "gnome-open" as your browser.

---

### Post by TWO on 2008-02-20
> **hyperair said:**
> Little blue figures appear for me even on GNOME. But that's probably because I installed kubuntu-desktop already on my computer.

Also, for setting Nautilus as the default file manager (and Firefox as your browser), try setting "gnome-open" as your browser.

Yeah, that appears to be the case for me on Amarok in GNOME too.

Which do you prefer to use hyperair, KDE or GNOME, because I'm trying to decide which one I like more right now...

---

### Post by hyperair on 2008-02-20
I prefer GNOME, but that could be just because I'm more used to it than KDE. I might switch in the future, when KDE4 becomes more stable, gets configuration to modify the panels and such.

---

### Post by TWO on 2008-02-20
Is this how panels are modified on Kubuntu?

[http://www.mutube.com/mu/kubuntu-like-you-ubuntu/](http://www.mutube.com/mu/kubuntu-like-you-ubuntu/)

---

