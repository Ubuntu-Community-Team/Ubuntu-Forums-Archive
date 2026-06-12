---
title: "wTorrent + rTtorrent installation script: Installing wTorrent on Ubuntu in 3 steps"
date: 2009-02-08
forum: General Help
---

### Post by devinw on 2009-02-08
I had to reconfigure my wTorrent box recently, and had some trouble getting everything working. I wrote this script in an attempt to make the installation of wTorrent and rTorrent dead simple.

The script and the configuration files are a combination of the information posted on these guides:
[http://www.wtorrent-project.org/trac/wiki/DebianInstall/](http://www.wtorrent-project.org/trac/wiki/DebianInstall/)
[http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/](http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/)
[http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/](http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/)

I've tested this on a base Ubuntu Server 8.10 installation. If you're already running an apache webserver, you may want to configure lighttpd.conf to listen on port 81, or another less commonly used port.

Just uncomment line 89 in lighttpd.conf:
```
server.port = 81
```


[SIZE="4"]**Installing**[/SIZE]

1. Download and extract the configuration files and install script to the home directory. If the server is down for any reason, you can download the attached tar file.

```
cd
wget http://76.76.238.18/wtorrent-installer.tar
tar xf wtorrent-installer.tar
```


Feel free to look over the script and configuration files. If necessary, You may want to modify the configuration files to suit your needs before executing the script.


2. Run the installation script and if prompted, enter your password

```
wtorrent-installer/install.sh
```
**Optional step:** install.sh installs rTorrent from the Ubuntu repositories. I've found the version in the repositories to be somewhat unstable. If you'd like to install the latest version of rTorrent from SVN, you can run rtorrent-svn-upgrade.sh. After it removes the rTorrent package, it will download, build, and install the latest versions of XMLRPC-C, rTorrent, and libTorrent. If you decide to upgrade to the SVN version of rTorrent at a later time, all your torrents should be kept.

After running the script, you may have to add /usr/local/lib to your ld.so.conf. See this post: [http://ubuntuforums.org/showpost.php?p=3711097&postcount=25](http://ubuntuforums.org/showpost.php?p=3711097&postcount=25)


3. Visit [http://your.servers.ip.address/install.php](http://your.servers.ip.address/install.php) to complete the configuration.



[SIZE="4"]**Uninstalling**[/SIZE]

If you need to uninstall rTorrent/wTorrent, just run uninstall.sh.

```
wtorrent-installer/uninstall.sh
```


The last step asks if you would like to continue removing packages:

> THE FOLLOWING PACKAGES WILL NOW BE REMOVED: rtorrent screen mc lighttpd gawk php5-cgi php5-common php5-sqlite php5-xmlrpc php5-curl sqlite subversion. If you use this server for anything besides rTorrent/wTorrent, this could adversely affect your system, and you should consider skiping this step and removing any undesired packages manually. If you do not use this server for anything besides rTorrent/wTorrent, you can safely remove these packages. Continue removing said packages? [y/N]


If the server's sole purpose is rTorrent/wTorrent, you can safely remove these packages by typing 'y'. If you use the server for anything else, you should probably skip this step and remove any undesired packages manually.

---

### Post by pandaking on 2009-03-11
I tried using this, but I already have a apache installed, so I uncommented the line as suggested but still got this error:
```
 * Starting web server lighttpd
2009-03-11 22:30:55: (network.c.300) can't bind to port:  80 Address already in use [fail]
invoke-rc.d: initscript lighttpd, action "start" failed.

```

:(

---

### Post by devinw on 2009-03-11
Did you uncomment the line after running the script, or before?

If you edited /etc/lighttpd/lighttpd.conf, then you'll need to restart lighttpd with: ```
sudo /etc/init.d/lighttpd restart
```

Remember to set the rTorrent scgi port to 81 when you run install.php.


Let me know if that helps.

---

### Post by devinw on 2009-03-11
oops, double post during downtime.

---

### Post by pandaking on 2009-03-12
Nope, same kind of error. And I uncommented that line before running the script - it's as if it just ignored it though:

```

* Stopping web server lighttpd                                                       [ OK ]
* Starting web server lighttpd
2009-03-12 16:26:37: (network.c.300) can't bind to port:  80 Address already in use
                                                                                     [fail]
```

I have also tried "apt-get remove lighttpd" and then re-running your script, but to no avail.

---

### Post by devinw on 2009-03-12
Please post the output of: ```
cat /etc/lighttpd/lighttpd.conf | grep server.port
```

---

### Post by pandaking on 2009-03-12
Sure:
```
xx@xxx:~$ cat /etc/lighttpd/lighttpd.conf | grep server.port
# server.port               = 81

```

Which looks to be commented out? If so that's odd because I uncommented it out in your script's .conf file...


EDIT:
Well I manually edited "*/etc/lighttpd/lighttpd.conf*" and restarted litghttpd and now it's running fine.
I can access it at [http://myserver.com:81](http://myserver.com:81)

Only problem now is that [http://myserver.com:81/install.php](http://myserver.com:81/install.php) gives me a 404 :P

EDIT 2:
I seem to have fixed that by doing "*sudo userdel "rt"*" and then re-installing the script.
It's currently "*Downloading wTorrent...*" which it's been doing for about 4 mins now, so I will keep you updated.

EDIT 3:
Just my luck. Wtorrent's website is down atm. Will retry again later.

---

### Post by devinw on 2009-03-12
Glad you got things sorted out! Remember to set the rTorrent scgi port to 81 on the install.php page, and you should be all set.

For future reference, the uninstall.sh script 'resets' everything. It deletes the rt user, removes the INIT script, removes wTorrent, etc. It also asks if you would like to dpkg --purge any installed packages (including lighttpd). dpkg --purge differs from apt-get remove in that it completely removes the package, including config files.

[http://www.wtorrent-project.org/](http://www.wtorrent-project.org/) appears to be down, and so is the svn repository that the script downloads from. Hopefully it will be back up soon...

EDIT: [www.wtorrent-project.org](www.wtorrent-project.org) is back up. Does it work now?

---

### Post by pandaking on 2009-03-14
Yes thanks, seems to have worked, many thanks :D

ALthough on a side note, there are not many options oviously avaialble to set in wtorrent, I am actually a bit dissapointed after running utorrent with wine it feels like a real downgrade. Will give it a try for a few days though...

---

### Post by robotcontrolledbiodomes on 2009-03-15
Just tried this on a new 8.10 server installation (only installed the openSSH package). Works great.

thanks

---

### Post by alexlaban on 2009-03-22
I've been trying to install rTorrent myself with guides on the but then by mistake I found this thread when I ran into a problem during the installation of wtorrent so I though I could as well just give this a try since it's a lot easier. Now the problem I'm getting is ```

Adding rt user to run the rTorrent process...
adduser: The user `rt' already exists.
Failed to create the 'rt' user.
If you are trying to re-install rTorrent/wTorrent, run uninstall.sh first.

```
I've deleted the rt user and rt group manually and tried running uninstall.sh but keeps getting the same error >.<


Edit:Tried it on another server I got there when I go to "serverip":81 (changed to port 81 and restarted) I come to an empty directory.

Edit2: Edited the script so it would only run the last part (downloading wtorrent) now I got it running perfectly on my Vana server but I still don't get it working on Nifel which is my torrentserver and then server with hdd space (other one runs on 64gb :/), how should I do to remove all the traces from my tries on the torrent server so your script will work.

Edit3: Tried to change the user to wt everywhere but I still get the same error but with wt.

Edit4: Found out what was causing my problems. [https://bugs.launchpad.net/ubuntu/intrepid/+source/shadow/+bug/238755/+viewstatus](https://bugs.launchpad.net/ubuntu/intrepid/+source/shadow/+bug/238755/+viewstatus)

---

### Post by devinw on 2009-03-23
Glad you got everything figured out!

If you followed other guides and built rTorrent from source, there could be conflicts - the uninstall script only accounts for the changes that the install script makes.

---

### Post by DDM on 2009-04-01
I formatted my server's / partition and was dreading setting wtorrent back up, but this script worked perfectly and saved me a headache. Thank you.

I have a quick question: is there a way to have ClamAV scan the recently downloaded files? I'm not familiar enough with the syntax of either ClamAV or .rtorrent.rc.

Also, here's a little tip:
I have my little server make 12 audible beeps with random frequencies whenever a torrent completes by doing this..

# sudo apt-get install beep
# sudo nano /usr/local/bin/beeper

Add this to the file:```
#!/bin/bash

# $RANDOM range: 0 - 32767 
RANGE=10000 # Max frequency
MAXCOUNT=12 # Number of beeps
count=1
LENGTH=80 # Beep length
echo
echo "$MAXCOUNT random numbers:"
echo "-----------------"
while [ "$count" -le $MAXCOUNT ]    
do
  number=$RANDOM
  let "number %= $RANGE"
  echo $number
  beep -f $number -l $LENGTH #$number
  let "count += 1"  # Increment count.
done


```
# sudo chmod +x /usr/local/bin/beeper

Add this to your .rtorrent.rc file:```
on_finished = do_a_beep,"execute=beeper" 
```

That way, I don't need to be at a computer to know when a torrent has finished downloading and I don't need to F5 constantly for a torrent I'm anxious to get my hands on.

---

### Post by candee050687 on 2009-04-06
Thank you for making this a little easier.

I keep getting one fatal error when I run install.php

> Fatal error: Uncaught exception 'PDOException' with message 'could not find driver' in /var/www/torrents/lib/cls/PDOe.cls.php:52 Stack trace: #0 /var/www/torrents/lib/cls/PDOe.cls.php(52): PDO->__construct('sqlite:db/datab...', NULL, NULL) #1 /var/www/torrents/cls/install.cls.php(187): PDOe->__construct('sqlite:db/datab...', NULL, NULL, Array) #2 /var/www/torrents/cls/install.cls.php(75): install->saveConfig(Array) #3 /var/www/torrents/lib/cls/Web.cls.php(106): install->__construct() #4 /var/www/torrents/install.php(32): Web::getClass('install') #5 {main} thrown in /var/www/torrents/lib/cls/PDOe.cls.php on line 52

I have php5-common and php5-sqlite installed, as those are the only posted solutions to this error.  I only modified the scripts slightly, by changing the download locations and the user name.  I also changed the install location.

Sorry, it was my mistake.  It is running like a dream after a restart.

---

### Post by devinw on 2009-04-06
Thanks for the beeper tip!

> **DDM said:**
> I have a quick question: is there a way to have ClamAV scan the recently downloaded files? I'm not familiar enough with the syntax of either ClamAV or .rtorrent.rc.

I've never used ClamAV, but you should be able to do something similar to the beeper command: ```
on_finished = scan_complete,"execute=ClamAV command here"
```

Any spaces in the ClamAV command are represented by commas. For example: "clamav files" is "clamav,files".

@candee050687
Glad it works now.

---

### Post by AnjinSan on 2009-04-12
Okay, first time when i try to install wtorrent and rtorrent it fails, till i found your script, that time work, i tested it and work anyway, then i though to make a fresh install, i`ve installed just apache, the rest of files was downloaded by your script, and now it doesn`t work, i got Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).  in install.sh.

What i`m wrong? i did not change anything in your script.

L.E. It work at least, but only after i chmodded /var/www to 777. I see that your script just chmodded /conf .

---

### Post by mocka on 2009-04-12
I have now tried to (re)install the script several times but I keep receiving almost the same error as pandaking did;

```

2009-04-12 17:12:51: (network.c.300) can't bind to port:  80 Address already in use
                                                                 [fail]
Failed to restart lighttpd. Please check /etc/lighttpd/lighttpd.conf.
If you are trying to re-install rTorrent/wTorrent, run uninstall.sh first.

```

I've tried the solution in pandaking's second edit:
> EDIT 2:
I seem to have fixed that by doing "sudo userdel "rt"" and then re-installing the script.

Though it just answers that there is no user named "rt".

I'm very new to Ubuntu so please bear with my ignorance :p

EDIT: Oh well, I'm reinstalling the whole OS to see if it works.

EDIT2: It didn't help one bit, I'm still receiving the same error.

---

### Post by AnjinSan on 2009-04-12
mocka you have to change lighttpd.con port, open lighttpd.conf from your wtorrent-installer directory and look for server.port = 81 and remove the # in front of it. After you do that just run uninstall.sh again, and that`s all.

Anyway i got a issue, if i put a tracker url in the line he download the .torrent file add it in rtorrent and the message are Tracker: [Failure reason "Invalid passkey! Re-download the .torrent from "]  that in wtorrent, and in rtorrent are : Could not unlink tied file: Permission denied. 
What i have to do?

---

### Post by mocka on 2009-04-12
Thanks for the reply AnjinSan. The strange thing is that I have already done as you told me to. At the moment I'm reinstalling Ubuntu Server Edition without LAMP to see if it solves the problem.

EDIT: Installing this script without LAMP installed did the trick. For some reason would the lighttpd reset each time I used the script, so editing it did not help. I think that if I install LAMP now, that will go well as I have fixed the port in lighttpd now. 

One a little offtopic question though; how do you configure rTorrent?

---

### Post by devinw on 2009-04-12
@AnjinSan
You shouldn't need to give everyone write permissions to /var/www. The defaults should be fine, but try this:
```
sudo chmod -R 774 /var/www/
sudo chown -R root.www-data /var/www/
```

[QUOTE=AnjinSan]Anyway i got a issue, if i put a tracker url in the line he download the .torrent file add it in rtorrent and the message are Tracker: [Failure reason "Invalid passkey! Re-download the .torrent from "] that in wtorrent, and in rtorrent are : Could not unlink tied file: Permission denied.
What i have to do?[/QUOTE]
This happens when you add a torrent file via URL in wTorrent?


@mocka
When you install the LAMP packages during the Ubuntu Server installation, it installs [apache]("http://www.apache.org/"). You can run wTorrent on apache, but this script uses [lighttpd]("http://www.lighttpd.net/"), which is another another open source webserver.

You can't run two services (like apache and lighttpd) on the same port. The solution is to either change the port lighttpd listens on (as AnjinSan suggested), or to stop/remove apache. Sounds like you got things working by reinstalling Ubuntu without LAMP.

You can configure rTorrent by editing /home/rt/.rtorrent.rc. There are several options that you can uncomment. For some ideas as to what you can do, check [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks). You can also check rTorrent's man page: man rtorrent

---

### Post by AnjinSan on 2009-04-12
The issue come even when i add the torrent via URL or from local disk, i dont know where is the problem now ... wtorrent tell me that torrent file are added corectly and start correctly... but rtorrent dont want to get it. Is not your script fault anyway, it might be something wrong with my 8.10... as i post in last page, i did a fresh install in the morning, and i get all updates at that time... if you have any solution, i`m glad to try, i dont found too much support for rtorrent, the peoples founded on #rtorrent channel are nasty :D

---

### Post by mocka on 2009-04-12
Thank you devinw. How do I restart rtorrent after having edited the configuration file?

I'm having a permission problem. Whenever I try to add files or folders to the folders rTorrent use, I'm rejected by the server. I tried to figure out a workaround for this so I tried to copy a finished torrent file to another directory on the computer, this, however, only results with rTorrent being incapable of hashing the torrent, because of lacking permissions.

As I've already said, I'm very new to Ubuntu (or linux at all) so don't be too hard on me :p

---

### Post by devinw on 2009-04-12
> **AnjinSan said:**
> The issue come even when i add the torrent via URL or from local disk, i dont know where is the problem now ... wtorrent tell me that torrent file are added corectly and start correctly... but rtorrent dont want to get it. Is not your script fault anyway, it might be something wrong with my 8.10... as i post in last page, i did a fresh install in the morning, and i get all updates at that time... if you have any solution, i`m glad to try, i dont found too much support for rtorrent, the peoples founded on #rtorrent channel are nasty :D

Does changing the permissions like this fix it?
```
sudo chmod -R 774 /var/www/
sudo chown -R root.www-data /var/www/
```

You could also try making var/www/torrents/ writable by all, but it shouldn't be necessary unless rTorrent is creating symlinks or something: ```
sudo chmod -R 777 /var/www/torrents/
```


> **mocka said:**
> Thank you devinw. How do I restart rtorrent after having edited the configuration file?
```
sudo /etc/init.d/rtorrent restart
```

> **mocka said:**
> I'm having a permission problem. Whenever I try to add files or folders to the folders rTorrent use, I'm rejected by the server. I tried to figure out a workaround for this so I tried to copy a finished torrent file to another directory on the computer, this, however, only results with rTorrent being incapable of hashing the torrent, because of lacking permissions.

Only the rt user (or root, of course) can write to /home/rt/torrents/. An easy way to create files/folders in a user's home directory, while keeping the correct permissions intact, is to temporary 'become' that user with: ```
sudo su - rt
```
You can now write to /home/rt/ - type exit when you're done.

This article explains Linux permissions pretty well: [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by mocka on 2009-04-13
> 
Only the rt user (or root, of course) can write to /home/rt/torrents/. An easy way to create files/folders in a user's home directory, while keeping the correct permissions intact, is to temporary 'become' that user with: ```
sudo su - rt
```
You can now write to /home/rt/ - type exit when you're done.

This article explains Linux permissions pretty well: [http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

Thanks for the explanatory link. The problem is that I want to seed some torrents I've already downloaded. Therefore it does not help to do "sudo su - rt" as I then can't access the files outside the rTorrent folders.
I have tried "chmod -R 777 /home/rt/torrents" but the output is only that the action is denied because of lacking permissions.

---

### Post by devinw on 2009-04-13
Only root or the owner of a file/folder can change permissions. You can use [sudo]("http://ubuntuforums.org/showthread.php?p=7064686#post7064686") to execute a command as root.

This will make /home/rt/torrents/ writable by all: ```
sudo chmod -R 777 /home/rt/torrents/
```

btw, if you're seeding completed torrents, the rt user only needs read permissions to wherever the torrent data is.

---

### Post by mocka on 2009-04-13
Wonderful, finally I'm able to move files to the torrents directory. Anyhow, after having added a finished torrent I get the following error in wTorrent:

rTorrent Message: Storage error: [Hash checker was unable to map chunk: Permission denied] 

May this be because I wrote "chmod -R 775 /home/rt/torrents" and not 777?

---

### Post by AnjinSan on 2009-04-13
I have issues with: hash check and other suspicious error "Download event action failed: Bad return code".

With hash check, the problem is, if i let it disabled at 99% rtorrent get stuck, hdd led still turned on, and after a while it stop, but rtorrent screen are not responding, and wtorrent say "no connection with rtorrent", or smth like that.after i close it and reopen, the files are deleted, like nothing there.

The issue with "Download event action failed: Bad return code" come after a torrent is finished and are ready for upload. But i did not set any directory to move after finish.

L.E. If i load a torrent pack, i set in wtorrent which file to download and which not. but seems that rtorrent dont listen to settings, wtf?!

---

### Post by devinw on 2009-04-13
> **mocka said:**
> Wonderful, finally I'm able to move files to the torrents directory. Anyhow, after having added a finished torrent I get the following error in wTorrent:

rTorrent Message: Storage error: [Hash checker was unable to map chunk: Permission denied] 

May this be because I wrote "chmod -R 775 /home/rt/torrents" and not 777?

Does it work if you chmod to 777? It shouldn't be necessary to give everybody full permissions, but if you think it might work, try it! You can always chmod 775 again :). What's the owner and group of the files in /home/rt/torrents/? You can check with 'ls -l /home/rt/torrents/'.


> **AnjinSan said:**
> I have issues with: hash check and other suspicious error "Download event action failed: Bad return code".

With hash check, the problem is, if i let it disabled at 99% rtorrent get stuck, hdd led still turned on, and after a while it stop, but rtorrent screen are not responding, and wtorrent say "no connection with rtorrent", or smth like that.after i close it and reopen, the files are deleted, like nothing there.

The issue with "Download event action failed: Bad return code" come after a torrent is finished and are ready for upload. But i did not set any directory to move after finish.

L.E. If i load a torrent pack, i set in wtorrent which file to download and which not. but seems that rtorrent dont listen to settings, wtf?!

What does your rtorrent.rc look like? I'm not sure why the 'files to download' settings wouldn't be reflected in rTorrent. You could create a trac ticket on wTorrent's project page: [http://www.wtorrent-project.org/trac/](http://www.wtorrent-project.org/trac/)

---

### Post by mocka on 2009-04-14
> **devinw said:**
> Does it work if you chmod to 777? It shouldn't be necessary to give everybody full permissions, but if you think it might work, try it! You can always chmod 775 again :). What's the owner and group of the files in /home/rt/torrents/? You can check with 'ls -l /home/rt/torrents/'.


devinw, thanks a lot for your help! I solved the problem by changing the permission to 777.

It is probably with little importance now but the owner of the /home/rt/torrents directory is rt.

By the way: Strange thing is that I have to do the chmod command whenever I add new files or folders to make gain access to them through rTorrent.

---

### Post by devinw on 2009-04-14
> **mocka said:**
> By the way: Strange thing is that I have to do the chmod command whenever I add new files or folders to make gain access to them through rTorrent.

This is probably because you moved the files as root (using sudo). This is fine, but if you do an ls -l on the folder you moved the files to, you'll find that the owner is now root. The permissions for these newly created files are dictated by your umask - the default umask in Ubuntu is 022. So, if you do an ls -l on the folder you moved the files to, you'll probably see something like this:
```
-rw-r--r-- 1 root root 22528 2009-04-14 13:45 file.txt
```

There are a couple of ways to give rt write permissions to the newly created file. You can give everyone on the system (including rt) write permissions with 'sudo chmod 777 file.txt'. Now things should look like this:
```
-rwxrwxrwx 1 root root 0 2009-04-14 13:48 file.txt
```

You could also make rt the owner with 'sudo chown rt file.txt'. That would look like this:
```
-rw-r--r-- 1 rt root 0 2009-04-14 13:56 file.txt
```


Permissions in Linux are a great thing, but they can be a little tricky to work around at times. :D

---

### Post by AnjinSan on 2009-04-14
What do you say about stopping fstab on my torrent partition?!

---

### Post by devinw on 2009-04-14
> **AnjinSan said:**
> What do you say about stopping fstab on my torrent partition?!

What do you mean stop fstab?
fstab is the file systems table, it defines mount points.

---

### Post by AnjinSan on 2009-04-14
Damn, the issue with hash check was created by on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/done/ ;d.set_directory=/home/rt/torrents/done/", i think it try to copy files to the default folder, but that folder are on a ntfs partition so when hash finish at 99% it stuck and the screen become unusable, so i put a # in front of that line, and now i`m testing to see if there is some issues, but i see that the "doing"folder have the file downloaded, but wtorrent, keep the root in default folder, that is not a problem now anyway. A great script man, i`m foreigner, so i misread that line with on_finished.

Have a nice day.

P.S. Maybe someone will made a tutorial on how to tweak system performance and optimize for ubuntu,for dummies of course :D.

---

### Post by devinw on 2009-04-14
Awesome, glad you figured it out!
There's a lot of [cool things you can do with rTorrent]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks").

Cheers,
Devin

---

### Post by AnjinSan on 2009-04-16
Ok, sorry to ask you x stuffs, another question i have for ya, since i`m finished rtorrent bugs, how i can stop my hdd led?! Since i`m uploading with 7000 KB, it`s all time on, but on xp it was not anytime turned on, how i can fix it? I though is something there that access hdd too much. What i can check and what is safe to stop in case? Thanks

---

### Post by devinw on 2009-04-16
> **AnjinSan said:**
> Ok, sorry to ask you x stuffs, another question i have for ya, since i`m finished rtorrent bugs, how i can stop my hdd led?! Since i`m uploading with 7000 KB, it`s all time on, but on xp it was not anytime turned on, how i can fix it? I though is something there that access hdd too much. What i can check and what is safe to stop in case? Thanks

I've never had a problem with the disk activity LED being annoying, but you could try disabling polling on your hard drive: [http://ubuntuforums.org/showpost.php?p=5416239&postcount=10](http://ubuntuforums.org/showpost.php?p=5416239&postcount=10)
You can always physically unplug the cable from the motherboard, or cover the light with duct tape. :D

---

### Post by tkhobbes on 2009-04-23
Hi there, thanks this is a really useful script! :)

However, I have some problems with configuring the paths, as follows:

1. I can surf to [http://my.ip:81/install.php](http://my.ip:81/install.php)

2. I want the configuration to be so that .torrent-files are in **/home/myuser/downloads/torrents** and the finished downloads shall be stored in **/home/myuser/incoming**.

3. I changed these lines in /home/rt/.rtorrent.rc:

```
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/myuser/incoming/ ;d.set_directory=/home/myuser/incoming/"
```

and later:
```
# Default directory to save the downloaded torrents.
directory = /home/myuser/downloads/torrents/
```

and again later:
```
schedule = watch_directory,5,5,load_start=/home/myuser/downloads/torrents/*.torrent
```

4. In the web-installation, I enter
[LIST]"/home/myuser/incoming" into "Folder to save uploaded torrents"
[/LIST]
[LIST]and "/home/myuser/downloads/torrents" into "Default folder to save torrent data:"
[/LIST]
*(And I obviously change the SCGI port to 81 - all the rest I leave as it is)*

5. When I then try to save, I get an error message "**cannot write to torrents folder, please check permissions**" - and the "Default folder to save torrent data" jumps back to "/home/rt/torrents/doing"....

The mentioned folder belongs to myuser:rt with 770.

I don't understand this.... what's wrong??

---

### Post by devinw on 2009-04-23
There are three folders:
[LIST=1]
[*]The folder where the uploaded .torrent files are stored. This is the "Folder to save uploaded torrents" in install.php.
[*]The folder where the torrent data is kept. This is "Default folder to save torrent data" in install.php.
[*]The folder where rTorrent moves the torrent data when the download is complete. This is defined in the .rtorrent.rc file.
[/LIST]

So, you have to decide where you want the torrent data to be stored until the download is complete - you probably don't want this to be the same as the .torrent directory. The default 'unfinished downloads' directory is /home/rt/torrents/doing/.

> When I then try to save, I get an error message "cannot write to torrents folder, please check permissions" - and the "Default folder to save torrent data" jumps back to "/home/rt/torrents/doing"....

The mentioned folder belongs to myuser:rt with 770.
Try changing the "Folder to save uploaded torrents"'s group to www-data.

---

### Post by mocka on 2009-04-23
wTorrent+rTorrent has been working really well for a good while now. Anyhow, I had to reinstall the script to get wTorrent and rTorrent working again after the upgrade to 9.04. 

The problem is that after I had edited the rtorrent configuration file, I restarted rTorrent. When I then try to enter wTorrent it says that it fails to connect to rTorrent. So what I was wondering was how to restart wTorrent, to see if that is the solution.

---

### Post by devinw on 2009-04-23
> **mocka said:**
> wTorrent+rTorrent has been working really well for a good while now. Anyhow, I had to reinstall the script to get wTorrent and rTorrent working again after the upgrade to 9.04. 

The problem is that after I had edited the rtorrent configuration file, I restarted rTorrent. When I then try to enter wTorrent it says that it fails to connect to rTorrent. So what I was wondering was how to restart wTorrent, to see if that is the solution.
wTorrent is a [web application]("http://en.wikipedia.org/wiki/Web_application"), it can't be restarted. However, you can restart lighttpd (the web-server that hosts wTorrent).

Try this: ```
sudo /etc/init.d/lighttpd restart
```

---

### Post by tkhobbes on 2009-04-24
> **devinw said:**
> 
Try changing the "Folder to save uploaded torrents"'s group to www-data.

I played around with groups and permissions - now, the config file is saved. However, when I try to either
[LIST]start a torrent download by putting a .torrent file in my watch directory[/LIST]
[LIST]upload a .torrent file via wtorrent webinterface ("add torrent")[/LIST]
nothing happens. In the latter case, I get the error message 
```

Error: Impossible to create file on given directory, please check permisions

```

The directory /home/myuser/downloads/torrents/, where the .torrent-file shall be placed (and also unfinished torrent data shall be put) is owned by myuser:rt with 770. Also, the directory /home/myuser/incoming/ (where finished downloads shall be moved to) is owned by myuser:rt, 770. Finally, I added www-data to the group rt, and the user rt to the group myuser.... does not work....

---

### Post by mocka on 2009-04-24
> **devinw said:**
> wTorrent is a [web application]("http://en.wikipedia.org/wiki/Web_application"), it can't be restarted. However, you can restart lighttpd (the web-server that hosts wTorrent).

Try this: ```
sudo /etc/init.d/lighttpd restart
```

I tried to restart lighttpd but there was no difference in the outcome, I still get the following error:

"Error: could not connect to rtorrent"

I tried to change the port of rTorrent to the same port as lighttpd use, though it didn't solve the problem.

---

### Post by devinw on 2009-04-24
> **tkhobbes said:**
> The directory /home/myuser/downloads/torrents/, where the .torrent-file shall be placed (and also unfinished torrent data shall be put) is owned by myuser:rt with 770. Also, the directory /home/myuser/incoming/ (where finished downloads shall be moved to) is owned by myuser:rt, 770. Finally, I added www-data to the group rt, and the user rt to the group myuser.... does not work....

Try this:
```
sudo chmod -R 774 /home/myuser/downloads/torrents/
sudo chown -R rt.www-data /home/myuser/downloads/torrents/
```

If myuser needs write access, you could make myuser the owner and add rt to the www-data group.

---

### Post by devinw on 2009-04-24
> **mocka said:**
> I tried to restart lighttpd but there was no difference in the outcome, I still get the following error:

"Error: could not connect to rtorrent"

I tried to change the port of rTorrent to the same port as lighttpd use, though it didn't solve the problem.

Well, you can check to see if rTorrent is starting correctly like this.
[LIST=1]
[*]Stop rTorrent: ```
sudo /etc/init.d/rtorrent stop
```
[*]Log in as rt: ```
sudo su - rt
```
[*]Run rTorrent: ```
rtorrent
```
[/LIST]

Do you get any errors? If rTorrent opens correctly, what does it say at the bottom of the screen?

---

### Post by mocka on 2009-04-24
Thank you, I managed to solve the problem now by following your steps. When I tried to start rTorrent through rt account, I got the following error message:

"Invalid port_range argument."

Obviously I had done something wrong when I assigned the port. My error was that I wrote port 52099 instead of 52099-52099.

EDIT: It seems like rTorrent started working properly again though wTorrent still cannot connect to rTorrent.

---

### Post by devinw on 2009-04-25
> **mocka said:**
> It seems like rTorrent started working properly again though wTorrent still cannot connect to rTorrent.

Did you restart rTorrent and lighttpd after making changes to the rtorrent.rc?
```
sudo /etc/init.d/rtorrent restart
sudo /etc/init.d/lighttpd restart
```

---

### Post by rgabi88 on 2009-04-25
I just installed  wTorrent + rTtorrent with Debian 5, using the installation script.
The trick was to install only the base system of Debian using the netinstall disk. [COLOR="Red"]DO NOT install anything else[/COLOR], as shown below!!
 
[CENTER][IMG]http://flipsidereality.com/blog/wp-content/uploads/rtorrent_imgs/22.png[/IMG]
image from [http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/]("http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/")[/CENTER]

[COLOR="Red"]During installation DO NOT CREATE USER "rt"!![/COLOR] The installation script will do the trick!

Update and upgrade system:

> apt-get update
> apt-get upgrade

After the update and upgrade, install ssh:

> apt-get install ssh -y

and make the server start at boot every time

> update-rc.d ssh defaults

now start the ssh server

> /etc/init.d/ssh start

you should be able to connect to the server from a windows machine using putty or a linux machine using ssh.

Thanks to DEVINW

Installing

1. Download and extract the configuration files and install script to the home directory. (....)

> cd
wget [http://76.76.238.18/wtorrent-installer.tar](http://76.76.238.18/wtorrent-installer.tar)
tar xf wtorrent-installer.tar

Feel free to look over the script and configuration files. If necessary, *_you may want to modify the configuration files to suit your needs_* before executing the script. (*I did not!*)

2. Run the installation script and if prompted, enter your password


> wtorrent-installer/install.sh

3. Visit [http://your.servers.ip.address/install.php](http://your.servers.ip.address/install.php) to complete the configuration.

Here, on install.php, do not change anything. Just fill in username and password and confirm.. I used another username and password, different from root or rt.

Rename or delete install.php
.
Visit [http://your.servers.ip.address/](http://your.servers.ip.address/)

THAT IS!!!

----------------------------------------------------
THANKS to DDM: (usefull)

"Also, here's a little tip:
I have my little server make 12 audible beeps with random frequencies whenever a torrent completes by doing this..

> # sudo apt-get install beep
# sudo nano /usr/local/bin/beeper

Add this to the file:


> #!/bin/bash

# $RANDOM range: 0 - 32767 
RANGE=10000 # Max frequency
MAXCOUNT=12 # Number of beeps
count=1
LENGTH=80 # Beep length
echo
echo "$MAXCOUNT random numbers:"
echo "-----------------"
while [ "$count" -le $MAXCOUNT ]    
do
  number=$RANDOM
  let "number %= $RANGE"
  echo $number
  beep -f $number -l $LENGTH #$number
  let "count += 1"  # Increment count.
done

# sudo chmod +x /usr/local/bin/beeper

Add this to your .rtorrent.rc file:


> on_finished = do_a_beep,"execute=beeper"

That way, I don't need to be at a computer to know when a torrent has finished downloading and I don't need to F5 constantly for a torrent I'm anxious to get my hands on."
----------------------------------------------

you can install also Samba to access the box as here: [http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/]("http://flipsidereality.com/blog/linux/rtorrent-with-wtorrent-on-debian-etch-complete-howto/")
Afte this, you can download files and upload .torrent files to watch directory..
And... IT WORKS!!!! :popcorn::guitar:

---

### Post by mocka on 2009-04-25
rgabi88, it should be enough just to leave the Web server uninstalled. 

devinw, after restarting both processes, I now cannot connect to the wTorrent UI at all. I will try with a fresh reinstall.

---

### Post by tkhobbes on 2009-04-26
> **devinw said:**
> Try this:
```
sudo chmod -R 774 /home/myuser/downloads/torrents/
sudo chown -R rt.www-data /home/myuser/downloads/torrents/
```

If myuser needs write access, you could make myuser the owner and add rt to the www-data group.

Still did not help; /home/myuser/downloads/torrents belongs to myuser:www-data with chmod 774; and user rt is in the www-data group.... error message still is "Error: Impossible to create file on given directory, please check permisions"...

---

### Post by devinw on 2009-04-26
> **tkhobbes said:**
> Still did not help; /home/myuser/downloads/torrents belongs to myuser:www-data with chmod 774; and user rt is in the www-data group.... error message still is "Error: Impossible to create file on given directory, please check permisions"...

Well, I don't see any reason why that shouldn't work.

Have you confirmed that rt is in the www-data group? ```
groups rt
```

New groups don't take effect on a user until the next time that user logs in - have you rebooted the machine?

---

### Post by tkhobbes on 2009-04-26
Yes, rt definitively is in www-data - and I have rebooted.

I have now switched back to the original configuration - THIS WORKS NEITHER on my box..... I am going to reinstall everything now.

---

### Post by omgtrash on 2009-05-01
i can't seem to connect to rtorrent

                               
     
                           **Error:** cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).         
     
     
what should be changed in the install.php screen? all i've changed is the port to 81, where my lighttpd is running.

---

### Post by devinw on 2009-05-01
> **omgtrash said:**
> i can't seem to connect to rtorrent

                               
     
                           **Error:** cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).         
     
     
what should be changed in the install.php screen? all i've changed is the port to 81, where my lighttpd is running.

The defaults should be fine. The rTorrent scgi port should be 80, unless you have lighttpd running on a different port. Did you modify the configuration files before running the script?

---

### Post by omgtrash on 2009-05-01
> **devinw said:**
> The defaults should be fine. The rTorrent scgi port should be 80, unless you have lighttpd running on a different port. Did you modify the configuration files before running the script?

No, I did not modify any configuration files. The only thing i changed was the lighttpd port, otherwise everything is the same. I set my scgi port to 81 (because my lighttpd port is 81 as well). I've been killing my self trying to get this working, i found your script yesterday hoping it would fix my problems but same error. Any idea on what I should do?

oh also forgot to mention, running on debian etch 4.0.

---

### Post by devinw on 2009-05-01
> **omgtrash said:**
> No, I did not modify any configuration files. The only thing i changed was the lighttpd port, otherwise everything is the same. I set my scgi port to 81 (because my lighttpd port is 81 as well). I've been killing my self trying to get this working, i found your script yesterday hoping it would fix my problems but same error. Any idea on what I should do?

Have you checked if rTorrent is starting correctly like this? [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)

Also note the rTorrent version at the top of the screen. Did you build rTorrent and libTorrent from source before running the script? That can sometimes cause conflicts if the built rTorrent isn't removed before running the script.

---

### Post by omgtrash on 2009-05-01
> **devinw said:**
> Have you checked if rTorrent is starting correctly like this? [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)

Also note the rTorrent version at the top of the screen. Did you build rTorrent and libTorrent from source before running the script? That can sometimes cause conflicts if the built rTorrent isn't removed before running the script.

rTorrent 0.8.4/0.12.4

Yes, i did build it from the source. I tried removing it and uninstalling the script then reinstalling but no luck. I've followed the steps in that link then restarted lighttpd accordingly. I have apache2 running aswell, could this be an issue?

edit: i'm getting no errors about scgi anymore, is this normal? i thought it was normal to receive errors upon starting rtorrent.

---

### Post by devinw on 2009-05-02
> **omgtrash said:**
> rTorrent 0.8.4/0.12.4

Yes, i did build it from the source. I tried removing it and uninstalling the script then reinstalling but no luck. I've followed the steps in that link then restarted lighttpd accordingly. I have apache2 running aswell, could this be an issue?

edit: i'm getting no errors about scgi anymore, is this normal? i thought it was normal to receive errors upon starting rtorrent.

Did you uninstall rTorrent and libTorrent with 'make uninstall'? I doubt running apache on a different port would be a problem, but you could always try stopping apache if you think it might be causing problems. Did you configure apache with mod_scgi?

After starting lighttpd and rTorrent, what is the output of 'sudo netstat -anp | grep LISTEN'?

---

### Post by AnjinSan on 2009-05-11
Okay, a friend ask me, if is possible to make 8 differents webui, each one have different ip adresses, so, he had a server with 8 ip`s, but my question is, is that possible? And how i can do it?

---

### Post by touficjohn on 2009-05-13
Thanks a lot for this!
Worked great!

You should get the guys over at wTorrent to host/link your script.

---

### Post by devinw on 2009-05-13
> **AnjinSan said:**
> Okay, a friend ask me, if is possible to make 8 differents webui, each one have different ip adresses, so, he had a server with 8 ip`s, but my question is, is that possible? And how i can do it?

I'm not exactly sure what you're trying to do. You want to have 8 different IPs point to the same server? ISPs usually charge extra for more static IPs, it would be much cheaper to use domain names and virtual hosts. Are you talking about internal IPs? Please clarify. :)

---

### Post by ja2ui0 on 2009-05-15
devinw, thanks for the scripts - they make much simpler a rather convoluted set of instructions.

Any thoughts on a simple way to make wTorrent / lighttp listen over https?  I'm not crazy about the idea about a server that will soon be inet-facing transmitting passwords over plain text.

---

### Post by devinw on 2009-05-16
> **ja2ui0 said:**
> devinw, thanks for the scripts - they make much simpler a rather convoluted set of instructions.

Any thoughts on a simple way to make wTorrent / lighttp listen over https?  I'm not crazy about the idea about a server that will soon be inet-facing transmitting passwords over plain text.

I've never set up wTorrent with https/ssl, but I've heard something like this works well.

[LIST]
[*]Run lighttpd on a port other than 80, and make sure it is not accessible from the outside.
[*]Install apache with SSL: [http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/](http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/)
[*]Set up a reverse proxy from apache to lighttpd.
[/LIST]

---

### Post by rgabi88 on 2009-05-17
does any one know how to update/upgrade rtorrent and libtorrent (installed with devinw' script) to latest versions?

---

### Post by arkique on 2009-05-19
ignore all the jibber jabber below. I have managed to install using your script but for some dumb reason rtorrent stop responding if i click on to many in wtorrent. " Well then do not click so much" I hear your say. well i wish i was doing it quickly. sometimes just chaning tabs from public/private or adding something from rss seems to make it throw its toys.

i just get

*Error: could not connect to rtorrent*

Below that it just says:
[B]
No torrents found[/B]

when i try and restart rtorrent it seems to come right somtimes. any ideas?

ark





[I]i have managed to get everything running and from what i can see rtorrent is running as it should but i just cannot get wtorrents to work  :(

i keep getting 

*"Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up). "*


from what i can gather i have the right port "81" and am using "rt" as user and pass. im sure i am just making a massive newb mistake here. 

any help is appreciated.

ark[/I]

/edit: i have fired a vm and and attempted to use the script on a fresh install and same error.. i must be making the same mistake... *sigh.  no sleep for me tonight

/edit: i made an assumption that my vm was a clean image. 1 install later i am running on my test machine :D. now i just have to figure out why the other machines does not work, thats the easy bit.

---

### Post by AnjinSan on 2009-05-22
arkique maybe you changed something there, something is wrong and it dont work.
devinw, i will try the virtual server thing, with domain names for sure, but for that i need some rtorrent sessions right?
Maybe i can change my friend opinion, to make him choose a one rtorrent session, and every user will be forced to the default user directory. Sorry for my bad english. :P

---

### Post by HollowMac on 2009-06-09
Hello,

I am French, so excuse me if my english is bad [-o<

To start, a big "thank you" for your script :p

If I am here, it is because i meet an error "404 - Not Found".

I have uncomented well the "server.port = 81", and I tried to install wtorrent with "http://ip-server:81/install.php" and "http://ip-server/".

An idea ?

Thanks ):P

edit : oho : wtorrent works successfully now ! I tried a new install, and it is good :) But to can run successfully install.php without a error, i have to reboot my server. Thanks a lot devinw for your script :)

---

### Post by devinw on 2009-06-10
**@HollowMac**
Glad you figured it out!


**@rgabi88, arkique**
The version of rTorrent in the Ubuntu repositories is somewhat buggy - I've had some problems with it myself. I've included a script entitled rtorrent-svn-upgrade.sh in wtorrent-installer.tar. It will remove the rTorrent package, then download, build, and install the latest versions of XMLRPC-C, rTorrent, and libTorrent. All the torrents that are already in rTorrent should be kept. After running the script, you may have to add /usr/local/lib to your ld.so.conf. See this post: [http://ubuntuforums.org/showpost.php?p=3711097&postcount=25](http://ubuntuforums.org/showpost.php?p=3711097&postcount=25)

Give it a shot and let me know if it works for you!

---

### Post by HollowMac on 2009-06-10
I personalized my torrent directories. I remarked that i can't change the directory where are stocked files .torrent : i have a message when i add a torrent which say to me "Permission denied.....", even if i give the right permissions to the user "rt" ot the group "www-data". On the other hand, i can personalize the directory "doing".

Bizarre.

---

### Post by HollowMac on 2009-06-10
Does anyone know why .torrents are saved as 12387635841toto.torrent and not toto.torrent (for example) ?

Thanks ;)

---

### Post by devinw on 2009-06-12
What are the permissions of the directory where you have the uploaded .torrent files stored?

All uploaded .torrent files are prefixed with the current timestamp. This allows different torrents with the same name to be uploaded, and also allows multiple users to download the same torrent.

---

### Post by HollowMac on 2009-06-15
> **devinw said:**
> 
All uploaded .torrent files are prefixed with the current timestamp. This allows different torrents with the same name to be uploaded, and also allows multiple users to download the same torrent.
Thanks for this information. :KS

The directory where was stored my .torrents had permissions for rt and the group www-data.

Have you any idea to store data torrents in other directory than the default directory ?
I tried for 2/3 days and i don't succeed. My .torrents are stored in ~/torrents/watch and i want to store data in ~/video. I don't succed to "move complete" data with "on_finished" or "on_hash_done".
Besides, the best solution would be to store data directly in ~/video in order to check older data if they exist.

:(

---

### Post by ericab on 2009-06-17
i just cant get it to work;
after untaring,
i run "sudo sh wtorrent-installer/install.sh"
and it tells me:

wtorrent-installer/install.sh: 17: function: not found

:?

---

### Post by AnjinSan on 2009-06-18
@HollowMack do you want to share your .rtorrent.rc settings? use [www.pastebin.com](www.pastebin.com) for paste the whole conf file. And give us the link, i can watch on your config and i can help it to work.
@ericab why sudo sh? just run ./install.sh , this dont need sudo.

---

### Post by ericab on 2009-06-18
alright, no sudo, but i still have a "wtorrent-installer/install.sh: 17: function: not found" error...

---

### Post by HollowMac on 2009-06-18
> **AnjinSan said:**
> @HollowMack do you want to share your .rtorrent.rc settings? use [www.pastebin.com]("http://www.pastebin.com") for paste the whole conf file. And give us the link, i can watch on your config and i can help it to work.

Eventually, it seems to be a problem with my Home-Server (Ve-Hotech VHS-4) and permissions with directory created in factory :P

---

### Post by patrcik111 on 2009-06-23
Hi, when starting lighttpd i always get 

Duplicate config variable in conditional 0 global: fastcgi.server
2009-06-23 15:06:33: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 273 pos: 14 parser failed somehow near here: (EOL)

Somebody got any idea???
In line 273 in my lighthttpd.conf stands the following:

 auth.backend = "htdigest"

Thanks in advance!!!!

---

### Post by ericab on 2009-06-23
> **ericab said:**
> i just cant get it to work;
after untaring,
i run "sudo sh wtorrent-installer/install.sh"
and it tells me:

wtorrent-installer/install.sh: 17: function: not found

:?

can someone give me some help for the above quoted issue ?

---

### Post by Lama on 2009-06-30
Thanks devinw, great script and guide!
Works perfectly for me, and its much faster and simpler then torrentflux.

---

### Post by AnjinSan on 2009-07-14
@ericab did you finished installing it?
when you run ./install.sh before it give dir and after that run the installer, if there is the same error, copy paste the text from "dir" command to last line of error.

---

### Post by delubu on 2009-07-22
I can't seem to make it work. everything is installed and when i run this command in browser i get

**[http://myIP/install.php](http://myIP/install.php)**


> 
**Object Not Found**

The requested URL '/install.php' was not found on the RomPager Advanced server. 





I tried runing that command from another computer and get the same message.

---

### Post by lordratner on 2009-07-23
Ok. here are my problems/questions. I'm completely new to the whole linux thing, so bear with me.

It looks like this script is made to be run on a fresh install of linux. I say this because it wiped out my /var/www folder. 

I used this tutorial ([http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3)) to get things going, then I ran your script. I was able to get to the install.php page, but it seems to have killed ISPConfig and a few other things.

Next: What am I supposed to throw into the settings options on the install.php page? I'm getting "**Error:** cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)." And I cant figure out what username and password it wants.

Next: Is the script set up to save the actual downloaded files (from any torrent) into the /var/www/torrents folder? If so, why would you want them in the "website section" of the server?

Please dont take any of my questions as accusatory. I really have no idea what I'm doing, and am trying to better understand both linux and your script. I love what you made since it's so easy, but I'm just trying to figure out if I can make it work without killing other things. 

Thanks for all your help!!
Seth

---

### Post by JJRabbit on 2009-08-11
Does it work on Ubuntu 9.04 - Jaunty Jackalope ?

---

### Post by cprophecy on 2009-08-14
I am running ubuntu 9.04 server. I did not find this script until now so I've done everything manually, according to several guides found on the wtorrent homepage:

[http://www.wtorrent-project.org/trac/wiki/DebianInstall](http://www.wtorrent-project.org/trac/wiki/DebianInstall)
[http://www.wtorrent-project.org/trac/wiki/wTorrentInstall](http://www.wtorrent-project.org/trac/wiki/wTorrentInstall)
[http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/](http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/)

I am at the point where i can connect to the server at [http://192.168.0.100/install.php](http://192.168.0.100/install.php) 

I click 'try configuration' and it gives me the vague error message at top:

Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).

I'm not sure where to go from here. I dont know if rtorrent/wtorrent has logging which could help pinpoint the problem. I have tried googling this error which is how I came upon this thread. If anyone knows how to determine the cause of the connection failure I would appreciate the help.

---

### Post by flaerpen on 2009-08-16
EDIT: I think I solved it! I did:

```
sudo su
cd /etc/lighttpd
user=anotheruser;pass=****;echo $user:XML-RPC:`echo -n $user:XML-RPC:$pass | md5sum | cut -b -32` >> htdigest
```

and then went to [http://local-ip/install.php:](http://local-ip/install.php:) 
RT_AUTH: true
RT-USER: anotheruser
RT-PASSWORD: **** 
and of course the username and password for a user in wtorrent.
---------------------------------------------------------------------------------------------------------

Hi! I used this script to install and configure wtorrent+rtorrent some days ago. It worked great for a while but after i restarted lighttpd and rtorrent it now says: 

[HTML]Error: could not connect to rtorrent[/HTML]

I then stopped the rtorrent process and did:

```
sudo su - rt
```

... and started rtorrent to see if there was any problem starting it up. There was none and rtorrent worked properly when I added a torrent-file manually. 

The only change I did in the script was that instead of using /var/www/ I'm using /home/anotheruser/www/. I've changed the lighttpd.conf and as I said, it worked the first time. I've also changed to listening ports in .rtorrent.rc. 

I then tried to reinstall everything with the script but I can't get to work! 


.rtorrent.rc: [http://pastebin.com/m64ceeab1](http://pastebin.com/m64ceeab1)
lighttpd.conf: [http://pastebin.com/m3150491e](http://pastebin.com/m3150491e)
user.conf.php: [http://pastebin.com/m77272313](http://pastebin.com/m77272313)


I'm using Ubuntu Server 9.04 and nothing else than Opendchub, Samba, SSH and wtorrent+rtorrent running.

(The reason I stopped and started lighttpd and rtorrent was that I had to unplug my external disk where all the torrent-downloads was and format it with ext4 instead of ntfs. The server itself hasn't been restarted thou.)

---

### Post by devinw on 2009-08-25
My apologies everyone, it seems I've neglected this thread for a while. If anyone is still having problems with the script, I'll be happy to do my best to help. I'm paying attention now. :)

---

### Post by DarkBabar on 2009-08-29
Thank you for your excellent script! By spending some of your valuable time you have made my life, and surely the lives of many others, a little bit easier, and for that I am deeply grateful.

---

### Post by JedMeister on 2009-09-03
Thank you so much devinw. I just installed wTorrent/rTorrent using your script and it worked a treat. I am running it on an 8.04 (Hardy) headless server, and other having to edit your script to remove the sudo.s (I'm running root and don't have sudo installed) I didn't touch a thing. I also used your rTorrent upgrade script which was painless too.

Awesome job!

And delubu, if you're still looking for an answer...
> **delubu said:**
> I can't seem to make it work. everything is installed and when i run this command in browser i get

**[http://myIP/install.php](http://myIP/install.php)**

I tried runing that command from another computer and get the same message.I could be wrong but I think your problem may be that you are using the link verbose. You need to change it to _your IP address_ so something like [http://xxx.xxx.xxx.xxx/install.php](http://xxx.xxx.xxx.xxx/install.php) where you replace the xxxs with the numbers that make up your IP. If you are using on the PC its installed on [http://localhost/install.php](http://localhost/install.php) should work. If you are using it over a LAN then you need the IP of the PC its running on (find it using the ifconfig command on the PC). If you are using it on the net then you'll need to port forward your router to your PC (assuming you're using some sort of router/modem setup). That's a whole forum topic on its own.

---

### Post by MeRodent on 2009-09-06
Hoping for some help.

Firstly great to see an easy installation script. 

However I need to make a few modifications and have ended up with a half working wtorrent/rtorrent set up.

Running ubuntu 8.04LTS server with LAMP installed. rTorrent 0.8.5/0.12.5

As I need apache running I changed a couple of things. 
lighttpd to port 81 and docroot /var/web/ leaving /var/www/ for apache.

All the scripts seem to have worked but while I can connect to wtorrent and it will accept a torrent for download - going as far as listing the torrent file in /var/web/torrents/ it does not start the torrent download.

On a previous install this worked for the first (admin) user but not for other users. 
Previously the admin user was also a user on the ubuntu system (whether that had anything to do with it working?)

I have also notice that there is no .torrent.rc files in any users. Should there be one in /home/rt/ or should there be ubuntu users to match the wtorrent users?

---

### Post by devinw on 2009-09-06
> **MeRodent said:**
> All the scripts seem to have worked but while I can connect to wtorrent and it will accept a torrent for download - going as far as listing the torrent file in /var/web/torrents/ it does not start the torrent download.

What's the output of this? ```
ls -l /var/web/
```

> **MeRodent said:**
> I have also notice that there is no .torrent.rc files in any users. Should there be one in /home/rt/ or should there be ubuntu users to match the wtorrent users?

You don't have to have system users for every wTorrent user. I would though, because that way you can have each user download to their home directory.

---

### Post by MeRodent on 2009-09-06
> **devinw said:**
> What's the output of this? ```
ls -l /var/web/
```

```
$ ls -l /var/web/
total 36
drwxrwxr-x  3 www-data www-data 4096 2009-09-06 16:20 cls
drwxrwxr-x  3 www-data www-data 4096 2009-09-06 16:41 conf
drwxrwxr-x  3 www-data www-data 4096 2009-09-06 19:02 db
-rwxrwxr-x  1 www-data www-data 1480 2009-09-06 16:20 index.php
drwxrwxr-x 10 www-data www-data 4096 2009-09-06 16:20 lib
-rwxrwxr-x  1 www-data www-data  136 2009-09-06 16:20 sqlite_migration.sh
drwxrwxr-x  3 www-data www-data 4096 2009-09-06 19:03 torrents
drwxrwxr-x  3 www-data www-data 4096 2009-09-06 19:03 tpl_c
drwxrwxr-x  9 www-data www-data 4096 2009-09-06 16:20 wt

```

And rt is a member of rt, tty and www-data

---

### Post by devinw on 2009-09-08
Well, if rt is a member of www-data, that should work. Try this:
sudo chown rt.www-data /var/web/torrents/
sudo chmod 770 /var/web/torrents/

If you have multiple users, that's a good way to set permissions. Users won't have access to other user's torrents.

You could try opening rtorrent without screen like this: [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)
Then see if anything is printed at the bottom of the screen when you add a torrent from wTorrent. You can also try adding a torrent from /var/web/torrents/ by hitting backspace, then typing the path of the .torrent.

---

### Post by MeRodent on 2009-09-08
Nope. Still no go.

Starting rtorrent by rt gives:

```
( 8:10:17) Using 'epoll' based polling.
( 8:10:17) XMLRPC initialized with 518 functions.
( 8:10:17) The SCGI socket is bound to a specific network device yet may still p
ose a security risk, consider using 'scgi_local'.method.set_key = event.download
[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6991] [U 0/0] [D 0/0] [H 0/3
```Does rtorrent need a .rtorrent.rc file? As I said earlier I can't find this anywhere.

Had a bit of a play around and found the .rtorrent.rc file in /user/rt/  <-- off course it's a hidden file so doesn't show up if you don't look for it. :P

A bit more of a play around and I found that I can load a torrent in directly using rtorrent and it appears where it's supposed to and wtorrent lists and runs the torrent.

What seems to be happening is that wtorrent writes a torrent file (long hex no.torrent) in /var/web/torrents/ and either rtorrent doesn't recognise it as a torrent or is not looking at the directory. I've also tried copying these to /home/rt/torrents/watch/ with no response.


Played around further to find that the reason the torrents weren't listing or downloading was that they were in fact not torrents. They were links to the torrent download page, not the torrent. When I actually added the torrent link it worked.


:(

Thanks for your help though devinw.

---

### Post by MeRodent on 2009-09-09
Quick question regarding .rtorrent.rc file.

adding:

```
schedule = throttle_1,05:00:00,24:00:00,download_rate=0
schedule = throttle_2,12:00:00,24:00:00,download_rate=10

```should set the rtorrent to download without throttling between 5:00am and Midday local time and throttle back to 10kb/s (just under 75MB total) outside those times shouldn't it?

Alternatively is there an option to set download rate to off?

---

### Post by Squishy on 2009-09-10
> **devinw said:**
> I've tested this on a base Ubuntu Server 8.10 installation. If you're already running an apache webserver, you may want to configure lighttpd.conf to listen on port 81, or another less commonly used port.
You might want to mention that this wipes the /var/www/ totally clean in your instructions and the install.sh

---

### Post by pendhu on 2009-09-10
Thanks [devinw]("http://ubuntuforums.org/member.php?u=766005")

Your script worked a treat, I've been having an awful time trying to install wTorrent+rTorrent the past week, stumbled here and found this thread what a life saver, I did a fresh install of Ubuntu Server 8.10 downloaded your script tweaked the configs and ran the install.sh and Bobs your uncle! 

Great work =D>

---

### Post by welshboykev on 2009-09-11
hi im very very new to linux and ubuntu and realy only lerning it the hard way by trial and error ive only ever used windows b4 and recently switched my server over to linux i like rtorrent/wtorrent i have used it b4 and its seams very stable indeed but im having BIG problems with installing this i have tryed everything in the above posts and faild badly and hoping on some help with my problem 

i keep getting port 80 is already in use even after editing the lighttpd to port 81 maybe some1 here can shed some light on this problem for me here is a copy of what ive dun 

root@ks29141:~# wtorrent-installer/install.sh
Installing rTorrent and required packages...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtorrent is already the newest version.
screen is already the newest version.
mc is already the newest version.
lighttpd is already the newest version.
gawk is already the newest version.
php5-cgi is already the newest version.
php5-common is already the newest version.
php5-sqlite is already the newest version.
php5-xmlrpc is already the newest version.
php5-curl is already the newest version.
sqlite is already the newest version.
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
DONE
Adding rt user to run the rTorrent process...
DONE
Copying rTorrent configuration file and creating folders...
DONE
Copying rTorrent INIT script...
 System startup links for /etc/init.d/rtorrent already exist.
DONE
Starting rtorrent: rtorrent.
Copying lighttpd configuration file...
DONE
Restarting lighttpd...
 * Stopping web server lighttpd                                          [ OK ] 
 * Starting web server lighttpd                                                 2009-09-11 22:58:16: (network.c.300) can't bind to port:  80 Address already in use 
                                                                         [fail]
Failed to restart lighttpd. Please check /etc/lighttpd/lighttpd.conf.
If you are trying to re-install rTorrent/wTorrent, run uninstall.sh first.
root@ks29141:~# cat /etc/lighttpd/lighttpd.conf | grep server.port
# server.port               = 81
root@ks29141:~# sudo /etc/init.d/lighttpd restart
 * Stopping web server lighttpd                                          [ OK ] 
 * Starting web server lighttpd                                                 2009-09-11 22:59:03: (network.c.300) can't bind to port:  80 Address already in use 
                                                                         [fail]
root@ks29141:~# cat /etc/lighttpd/lighttpd.conf | grep server.port
# server.port               = 81



any and all help would be gr8tly appreciated thankyou :)

---

### Post by devinw on 2009-09-11
@MeRodent
Glad you figured it out. I haven't used rTorrent throttling much. This might be of help: [http://ubuntuforums.org/showthread.php?p=3465476](http://ubuntuforums.org/showthread.php?p=3465476)

@Squishy
Very good point. It might be better to have the script check if /var/www/ is empty when it runs. I'll look into it when I get a chance.

@pendhu
Glad everything worked for you!

@welshboykev
You need to uncomment # server.port = 81. Remove the #, so it looks like this: ```
server.port = 81
```
Then restart lighttpd.

---

### Post by welshboykev on 2009-09-11
arrr yes its all installed i told you im a total n00b :/ anyway i got a new problem now i have managed to download and install everything ok i can get connected to [http://myip:81/install.php](http://myip:81/install.php) where you compleat the install by adding user name and password but when i click on the try config i get an error like others have mentioned b4 ....

**Error:** cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).

so i started and stoped the lighttpd and also rtorrent and also rebooted server still same error 

i also did this
[FONT=monospace]
[/FONT]sudo chmod -R 777 /var/www/torrents

and get this

root@ks29141:~# ls -l /home/rt/torrents/
total 12
drwxrwxrwx 2 777 rt 4096 2009-09-12 00:05 doing
drwxrwxrwx 2 777 rt 4096 2009-09-12 00:05 done
drwxrwxrwx 2 777 rt 4096 2009-09-12 00:05 watch

so to me it looks like i have permissions 

then i tryed what you said on previous post test rtorrent


[LIST=1]
[*]Stop rTorrent:  	Code:
 	sudo /etc/init.d/rtorrent stop 
[*]Log in as rt:  	Code:
 	sudo su - rt 
[*]Run rTorrent:  	Code:
 	rtorrent 
[/LIST]
at the bottom of rtorrent i have this error

( 2:01:13) Using 'epoll' based polling.
( 2:01:13) XMLRPC initialized with 409 functions.
( 2:01:13) The SCGI socket is bound to a specific network device yet may still pose a security risk, consider using 'scgi_local'.

now im totaly lost and my head herts :'(

and thankyou very much devinw for your time and effort in helping everyone here

---

### Post by MeRodent on 2009-09-13
> **welshboykev said:**
> 

[LIST=1]
[*]Stop rTorrent:      Code:
     sudo /etc/init.d/rtorrent stop
[*]Log in as rt:      Code:
     sudo su - rt
[*]Run rTorrent:      Code:
     rtorrent
[/LIST]
at the bottom of rtorrent i have this error

( 2:01:13) Using 'epoll' based polling.
( 2:01:13) XMLRPC initialized with 409 functions.
( 2:01:13) The SCGI socket is bound to a specific network device yet may still pose a security risk, consider using 'scgi_local'.

The good news here is that the message at the bottom of the screen is not an error (just advisory. This means rtorrent is running correctly.

Try running wtorrent after starting rtorrent (using sudo su - rt) as wtorrent will connect to rtorrent if everything is set up properly. This will let you know if it is simply a problem with starting up rtorrent.

---

### Post by xa+im on 2009-09-13
im having this error after configure lighttpd ( [http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/comment-page-1/#comment-769](http://robert.penz.name/82/howto-install-rtorrent-and-wtorrent-within-an-ubuntu-hardy-ve/comment-page-1/#comment-769))


***4. lighttpd setup***
 This sections shows how to setup lighttpd for rtorrent XML RPC and for wtorrent. Add "mod_scgi" to the server.modules in /etc/lighttpd/lighttpd.conf and add following there too:
 url.access-deny = ("~", ".inc", ".db", ".tpl.php", ".cls.php",)
 Create following file /etc/lighttpd/conf-available/10-scgi.conf with following content:
 
scgi.server = (
"/RPC2" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5000, # Port specified in .rtorrent.rc
"check-local" => "disable"
)
)
)

 Enable following two configs by setting a symlink:
 
# cd /etc/lighttpd/conf-enabled/
# ln -s ../conf-available/10-cgi.conf .
# ln -s ../conf-available/10-scgi.conf .

 Restart the lighttpd:
 /etc/init.d/lighttpd restart




 root@ks304603:~# /etc/init.d/lighttpd restart
 * Stopping web server lighttpd                                          [ OK ]
* Starting web server lighttpd Duplicate config variable in conditional 0 global: scgi.server
2009-09-13 23:13:38: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 254 pos: 15 parser failed somehow near here: (EOL)
                                                                         [fail]
anyone could help me i had it running but somehow the .rtsession got locked
and rtorrent wouldn’t run and .rtorrent.rc got blank i had to configure it all over again now its all ok again just lighttpd missing i cant iniciate it to configure the Wtorrent install.php

---

### Post by devinw on 2009-09-13
> **welshboykev said:**
> arrr yes its all installed i told you im a total n00b :/ anyway i got a new problem now i have managed to download and install everything ok i can get connected to [http://myip:81/install.php](http://myip:81/install.php) where you compleat the install by adding user name and password but when i click on the try config i get an error like others have mentioned b4 ....

**Error:** cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).

Did you set the rTorrent scgi port to 81?

---

### Post by devinw on 2009-09-13
> **xa+im said:**
> 
 root@ks304603:~# /etc/init.d/lighttpd restart
 * Stopping web server lighttpd                                          [ OK ]
* Starting web server lighttpd Duplicate config variable in conditional 0 global: scgi.server
2009-09-13 23:13:38: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 254 pos: 15 parser failed somehow near here: (EOL)
                                                                         [fail]

Could you post your lighttpd.conf? Use [pastie.org]("http://pastie.org/") or similar.

---

### Post by Kipaki on 2009-09-15
Hi everybody !

I'm french, so forgive my english.

First of all, thanks for the script, it's awsome !

But, I have some troubles when I want configure wtorrent, I have access to 

[http://localhost/install.php](http://localhost/install.php)

But, when I want click on "Try configuration", I have the following error message :

**Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).**

I haven't modified any files, I just execute the script.
So, lighthttpd.conf, rtorrent.rc and user.conf are the same than in your package ;)

Any ideas ? 

thanks

---

### Post by devinw on 2009-09-15
> **Kipaki said:**
> But, when I want click on "Try configuration", I have the following error message :

**Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).**

Is rTorrent starting correctly? Try running rTorrent without screen, and see if there are any errors: [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)

---

### Post by Kipaki on 2009-09-16
Thanks for your answer.

When I execute your commands, I have this message :

rtorrent: XMLRPC not supported.

Once again, thanks for helping me.

---

### Post by devinw on 2009-09-16
That's strange. Did you install rTorrent before running the script?
You can try running the rtorrent-upgrade.sh script. It will download the latest SVN version of rTorrent and compile it with XMLRPC support.

---

### Post by Kipaki on 2009-09-16
Yes, rTorrent was installed because I'd tried a lot of tutorials ;)

But, before  executing install.sh, I ran uninstall.sh ! Maybe it's not enough ?

Now, I've executed rtorrent-upgrade.sh, and after, install.sh, I don't have the error message about XMLRPC ! So i suppose rtorrent is ok.

But same error when I try the configuration :
[[IMG]http://www.picdo.net/fichiers/2009/9/16/012edcc4-8455-4c10-ac51-101941e7eca2_dsdsf.JPG[/IMG]]("http://www.picdo.net")

did I do something wrong?

rTorrent scgi user etn password must be the same than in the user.conf of wtorrent ?

Enable auth for the scgi folder : Should I choose "True" ? I suppose that if I choose "True", it must be the same in the user.conf ?

Thanks

---

### Post by devinw on 2009-09-16
All the defaults on install.php should be fine. The only fields you have to fill in are User and Password.

When you open rTorrent, what version is displayed at the top? Also, did you restart rTorrent and lighttpd after running rtorrent-upgrade.sh?
```
sudo /etc/init.d/rtorrent restart
sudo /etc/init.d/lighttpd restart
```

---

### Post by Kipaki on 2009-09-17
Thanks for your help.

I did it !

It works.

I've just uninstall everything, next I did the install properly and everything is fine.

---

### Post by djbon2112 on 2009-09-18
Hello everyone. I'm seeing an error that a lot of people in this thread have, but I can't seem to find a solution.

"Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)."

I literally JUST created the Xen VM that this is running in (Debian Lenny w/Sid), and did nothing except run the OP's scripts, and I still get that error with all the default values. Also, when I try to upgrade to SVN, I get an error about "package libtorrent11 does not exist". However removing that particular entry from the first few lines of the script (uninstall part) fixes that issue. Any suggestions of what I should do next?

---

### Post by devinw on 2009-09-18
@Kipaki
Glad you figured everything out!

@djbon2112
[http://ubuntuforums.org/showpost.php?p=7953783&postcount=104](http://ubuntuforums.org/showpost.php?p=7953783&postcount=104)

---

### Post by HollowMac on 2009-09-19
> **djbon2112 said:**
> Hello everyone. I'm seeing an error that a lot of people in this thread have, but I can't seem to find a solution.

"Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)."

Try with port number 81 : it works for me :)

---

### Post by maxnutter on 2009-09-19
i'm struggling with the "Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)." issue, and i am banging my head against a brick wall.

my .rtorrent.rc isn't in my root directory, does it have to be?
the correct directory is listed in the /etc/init.d/rtorrent file,
but when i run rtorrent it says "Could not read resource file: ~/.rtorrent.rc" at the bottom.

if i copy the .rtorrent.rc file to the root directory i get this message when i try to run rtorrent:
"rtorrent: Error in option file: ~/.rtorrent.rc:1: Could not bind address: Name or service not known."

argh! please help!

---

### Post by MeRodent on 2009-09-19
A quick question.

Is it possible to replace the index.php file as I've accidently deleted it on my server (thought I was deleting the index file for apache).

Or do I need to reinstall wtorrent completely?

---

### Post by devinw on 2009-09-21
> **maxnutter said:**
> i'm struggling with the "Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)." issue, and i am banging my head against a brick wall.

my .rtorrent.rc isn't in my root directory, does it have to be?
the correct directory is listed in the /etc/init.d/rtorrent file,
but when i run rtorrent it says "Could not read resource file: ~/.rtorrent.rc" at the bottom.

if i copy the .rtorrent.rc file to the root directory i get this message when i try to run rtorrent:
"rtorrent: Error in option file: ~/.rtorrent.rc:1: Could not bind address: Name or service not known."

argh! please help!

The rt user needs to run rTorrent. The .rtorrent.rc file is in /home/rt/.
You're getting the 'Could not bind address' error because rTorrent is already running in screen as the rt user. The first line in the rtorrent.rc specifies the scgi port (5000) - you can't have two instances of rTorrent using the same port.
Have you tried this? [http://ubuntuforums.org/showpost.php?p=7953783&postcount=104](http://ubuntuforums.org/showpost.php?p=7953783&postcount=104)

---

### Post by devinw on 2009-09-21
> **MeRodent said:**
> A quick question.

Is it possible to replace the index.php file as I've accidently deleted it on my server (thought I was deleting the index file for apache).

Or do I need to reinstall wtorrent completely?

```
sudo wget http://www.wtorrent-project.org/trac/browser/trunk/wtorrent/index.php?format=raw -O /var/www/index.php
```

---

### Post by maxnutter on 2009-09-21
> **devinw said:**
> The rt user needs to run rTorrent. The .rtorrent.rc file is in /home/rt/.
You're getting the 'Could not bind address' error because rTorrent is already running in screen as the rt user. The first line in the rtorrent.rc specifies the scgi port (5000) - you can't have two instances of rTorrent using the same port.
Have you tried this? [http://ubuntuforums.org/showpost.php?p=7953783&postcount=104](http://ubuntuforums.org/showpost.php?p=7953783&postcount=104)

thanks for the help.

if i start as rt (as in post 104/44), rtorrent starts, with "Could not read resource file: ~/.rtorrent.rc" at the bottom.

if i copy the .rtorrent.rc file to /home/rt and run rtorrent as rt i get "Error in option file: ~/.rtorrent.rc:1: Could not bind address: Name or service not known.", even after stopping rtorrent.

:(

---

### Post by devinw on 2009-09-21
It seems like another instance of rTorrent (or something else) is already using port 5000. What's the output of this?
```
sudo netstat -lnp | grep 5000
```

---

### Post by maxnutter on 2009-09-21
> **devinw said:**
> It seems like another instance of rTorrent (or something else) is already using port 5000. What's the output of this?
```
sudo netstat -lnp | grep 5000
```

i don't get any output ... it should be said that i'm being naughty here; i'm running Debian 4.0, not Ubuntu, but yours is the best rtorrent/wtorrent guide i've found!

---

### Post by arryo on 2009-09-22
Hi [devinw]("http://ubuntuforums.org/member.php?u=766005"),

Thank you very much for your great script and support. I have made rtorrent and wtorrent run perfectly. But I have a little problem, im using my ubuntu server as webserver too. After I have wtorrent running, my webserver not runnung any more. I guess because they are sharing the same port. What should I do to recover my webserver

Thanks again, devinw

---

### Post by MeRodent on 2009-09-23
> **arryo said:**
> Hi [devinw]("http://ubuntuforums.org/member.php?u=766005"),

Thank you very much for your great script and support. I have made rtorrent and wtorrent run perfectly. But I have a little problem, im using my ubuntu server as webserver too. After I have wtorrent running, my webserver not runnung any more. I guess because they are sharing the same port. What should I do to recover my webserver

Thanks again, devinw


I have the same setup ie:

lighttp serving on port 81 to run wtorrent
apache2 serving on port 80 as a general web server

In order to do this I changed the wtorrent script to port 81 for lighttp and /var/web/ as docroot leaving port 80 for apache2 and /var/www/ as docroot for apache2.

From memory (and it's bad so it may not have happened) the wtorrent script overwrote the contents of /var/www/ which I then copied to /var/web/ 

You may need to change port and docroot again in /etc/lighttp/lighttp.conf 

After this I deleted the contents of /var/www/ and installed the html files (accidently deleting the index.php from /var/web/ in the process - therefore my previous question).

To access wtorrent navigate to [http://my.server.address:81/](http://my.server.address:81/)
To access standard html navigate to [http://my.server.address/](http://my.server.address/)

You can if you want have a link to [http://my.server.address:81/](http://my.server.address:81/) in your main html file as I do in order to simplify things too.

---

### Post by arryo on 2009-09-24
Thank you for your reply. But let me see if I understand you correctly.
 
- My current docroot for webserver is /var/www, so now I should change it to /var/web and copy the content of my website to /var/web
- Now I go to /etc/lighttp/lighttp.conf and change my docroot to /var/web, and uncomment server port again? 
 
> **MeRodent said:**
> I have the same setup ie:
 
lighttp serving on port 81 to run wtorrent
apache2 serving on port 80 as a general web server
 
In order to do this I changed the wtorrent script to port 81 for lighttp and /var/web/ as docroot leaving port 80 for apache2 and /var/www/ as docroot for apache2.
 
From memory (and it's bad so it may not have happened) the wtorrent script overwrote the contents of /var/www/ which I then copied to /var/web/ 
 
You may need to change port and docroot again in /etc/lighttp/lighttp.conf 
 
After this I deleted the contents of /var/www/ and installed the html files (accidently deleting the index.php from /var/web/ in the process - therefore my previous question).
 
To access wtorrent navigate to [http://my.server.address:81/](http://my.server.address:81/)
To access standard html navigate to [http://my.server.address/](http://my.server.address/)
 
You can if you want have a link to [http://my.server.address:81/](http://my.server.address:81/) in your main html file as I do in order to simplify things too.

---

### Post by maxnutter on 2009-09-24
> **MeRodent said:**
> I have the same setup ie:

lighttp serving on port 81 to run wtorrent
apache2 serving on port 80 as a general web server

In order to do this I changed the wtorrent script to port 81 for lighttp and /var/web/ as docroot leaving port 80 for apache2 and /var/www/ as docroot for apache2.

From memory (and it's bad so it may not have happened) the wtorrent script overwrote the contents of /var/www/ which I then copied to /var/web/ 

You may need to change port and docroot again in /etc/lighttp/lighttp.conf 

After this I deleted the contents of /var/www/ and installed the html files (accidently deleting the index.php from /var/web/ in the process - therefore my previous question).

To access wtorrent navigate to [http://my.server.address:81/](http://my.server.address:81/)
To access standard html navigate to [http://my.server.address/](http://my.server.address/)

You can if you want have a link to [http://my.server.address:81/](http://my.server.address:81/) in your main html file as I do in order to simplify things too.

i have apache working on port 80, but lighttpd on port 81 comes up with:


Warning: require_once(wt/cls//ListT.cls.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/lib/inc/utils.inc.php(40) : eval()'d code on line 4

Fatal error: require_once() [function.require]: Failed opening required 'wt/cls//ListT.cls.php' (include_path='/var/www/localhost/htdocs/wtorrent/') in /var/www/lib/inc/utils.inc.php(40) : eval()'d code on line 4

---

### Post by MeRodent on 2009-09-25
> **maxnutter said:**
> i have apache working on port 80, but lighttpd on port 81 comes up with:


Warning: require_once(wt/cls//ListT.cls.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/lib/inc/utils.inc.php(40) : eval()'d code on line 4

Fatal error: require_once() [function.require]: Failed opening required 'wt/cls//ListT.cls.php' (include_path='/var/www/localhost/htdocs/wtorrent/') in /var/www/lib/inc/utils.inc.php(40) : eval()'d code on line 4


Looks like your wtorrent was setup to point to /var/www/ (the default if you don't change the path in the script)

You should be able to fix this by changing the line

define ('DIR_EXEC', '/var/www/');

to 

define('DIR_EXEC', '/var/web/');

in /var/web/conf/user.conf.php

---

### Post by MeRodent on 2009-09-25
> **arryo said:**
> Thank you for your reply. But let me see if I understand you correctly.
 
- My current docroot for webserver is /var/www, so now I should change it to /var/web and copy the content of my website to /var/web
- Now I go to /etc/lighttp/lighttp.conf and change my docroot to /var/web, and uncomment server port again?


You don't need to change docroot for apache. leave it as /var/www/

You need a separate docroot for lighttp (I chose /var/web/) and edit it in lighttp.conf along with uncommenting the port.

---

### Post by maxnutter on 2009-09-25
> **MeRodent said:**
> Looks like your wtorrent was setup to point to /var/www/ (the default if you don't change the path in the script)

You should be able to fix this by changing the line

define ('DIR_EXEC', '/var/www/');

to 

define('DIR_EXEC', '/var/web/');

in /var/web/conf/user.conf.php

that works, thanks, but when i log in i get:

Warning: disk_total_space() [function.disk-total-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 317

Warning: disk_free_space() [function.disk-free-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 317
0 b/
Warning: disk_total_space() [function.disk-total-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 321
0 b
Free:
Warning: disk_free_space() [function.disk-free-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 313
0 b 

also, the install.php file still can't talk to rtorrent :(

---

### Post by MeRodent on 2009-09-26
> **maxnutter said:**
> that works, thanks, but when i log in i get:

Warning: disk_total_space() [function.disk-total-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 317

Warning: disk_free_space() [function.disk-free-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 317
0 b/
Warning: disk_total_space() [function.disk-total-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 321
0 b
Free:
Warning: disk_free_space() [function.disk-free-space]: No such file or directory in /var/www/cls/rtorrent.cls.php on line 313
0 b 

also, the install.php file still can't talk to rtorrent :(

Please keep in mind I'm no genius here. :P

What's the output of 

```
grep /var/www /var/web/install.php
```

or 

```
sudo grep -rI /var/www /var/web/
```

I'm guessing that your install.php is pointing to /var/www 
If so change the /var/www to /var/web in the script.

The first line will show if /var/www is set in your install.php script and the second will look for /var/www in all text files in the /var/web directory (there should be no reason for any files to point to /var/www from /var/web - I think).

---

### Post by ThomasL on 2009-10-10
devinw,
you made this so simple to setup I have been trying to compile it for a few days and just could not get it to work.

I found your post and in less than fifteen minutes I am up and running!

Thanks for all your help here.

---

### Post by pablogrb on 2009-10-16
Worked perfectly on Ubuntu Jaunty Server, no issues. You deserve free beer!

---

### Post by Cyberrad on 2009-10-20
What a great script.  I was able to get this to work on Ubuntu Server 9.04.

However, I tried the same steps on another clean box with Ubuntu Server 9.04 and I keep getting the error "This is not a torrent file" from wtorrent.  All of my searches on the error have come up with nothing.  Has anyone else seen this behavior?

Edit:  Actually it looks like the error is coming from rTorrent.  rTorrent throws: Could not create download, the input is not a valid torrent.  I tested the file against the other box and the files are valid so I think rtorrent is giving me a false positive.

---

### Post by MadMcMurphy on 2009-10-24
Amazing script!  Massive thank you! :P

My only issue - wTorrent can no longer connect to rTorrent after a restart (process or machine).  Though, straight after running the script (before a restart), it ran perfectly.  Any ideas?

P.S. Just did a couple of tests, 

[B]'install.sh' --> WORKING! :P

'install.sh' -> Reboot --> NOT WORKING :mad:

'install.sh' -> Reboot -> 'uninstall.sh' -> Reboot -> 'install.sh' --> NOT WORKING :mad:[/B]

Would this not indicate that something doesn't get properly uninstalled? 

Thank you in advance!

---

### Post by devinw on 2009-10-26
Yes it does seem like something might not be getting uninstalled.
Have you tried restarting lighttpd after restarting rtorrent?
And have you made sure rtorrent is starting correctly? [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)

---

### Post by MadMcMurphy on 2009-10-27
I did restart lighttpd and it didn't affect wTorrent until I restarted rTorrent or rebooted the machine.  I also ensured that rTorrent was starting correctly, can't tell you how many times I've done that! :D
 
I decided to run a few more tests to work out what was the culprite, I tried ruTorrent - worked first time.  I believe the problem is with wTorrent and not your script, I'm now using ruTorrent and I'm very happy with it.
 
Massive thankyou, I couldn't of got close to this without your script and I'm happy to of hit these road blocks as I feel significantly more confident with Ubuntu.

---

### Post by devinw on 2009-10-27
Glad you got everything figured out!
I'm actually considering expanding the script to work with other WebUIs like ruTorrent. I'll be sure to post in this thread if anything happens with that.

---

### Post by jimey on 2009-10-27
hi Devinw~  thank you for making those amazing scripts.

i use the newest version which include svn-update.

and i have a problem that is the newest rtorrent coud't work..


i have used the earlier version before

it's fine.

and my wtorrent d't have any problems.

today i used the newest scripts and updated my rtorrent by svn

and there are some problems.

first one is the wtorrent show that 

> Error: cannot connect to rtorrent

and i read your posts, and i checked up.

i try > /etc/inid.t/rtorrent -stop

and  > sudo su - rt

> rtorrent

and i get this meassage 

> 
rtorrent: Command "get_handshake_log" does not exist.


i think rtorrent 0.8.5 version deleted this method or other reason.

---

### Post by Dethecus on 2009-10-28
I have the same problem as jimey.

Also:

Download event action failed: Command "get_tracker_dump" does not exist

---

### Post by rssurvivor on 2009-10-28
It seems the problem is universal and related with rTorrent, all other webuis give the same error.

---

### Post by gryffin11 on 2009-10-29
Hi

I know this guide is for 8.10, but im wondering if anyone can help me getting this installed on 6.06 (using due to low ram requirements)

heres the error from the install.sh script:

```
Restarting lighttpd...
 * Stopping web server lighttpd
   ...done.
 * Starting web server lighttpd
Undefined config variable: alias.url
Undefined config variable in conditional 1 global/HTTPremoteip=~127.0.0.1: alias.url
2009-10-29 23:02:12: (configfile.c.805) source: /etc/lighttpd/lighttpd.conf line: 201 pos: 2 parser failed somehow near here: (EOL) 
   ...fail!

```

lighttpd.conf

```
############ Options you really have to take care of ####################

## modules to load

# mod_access, mod_accesslog and mod_alias are loaded by default

# all other module should only be loaded if neccesary

# - saves some time

# - saves memory

server.modules              = ( 

            "mod_access",

            "mod_alias",

            "mod_accesslog",

			"mod_scgi",

			"mod_fastcgi",

#           "mod_rewrite", 

#           "mod_redirect", 

#           "mod_status", 

#           "mod_evhost",

#           "mod_compress",

#           "mod_usertrack",

#           "mod_rrdtool",

#           "mod_webdav",

#           "mod_expire",

#           "mod_flv_streaming",

#           "mod_evasive"

 )

## a static document-root, for virtual-hosting take look at the 

## server.virtual-* options

server.document-root       = "/var/www/"

## where to send error-messages to

server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested

index-file.names           = ( "index.php", "index.html", 

                               "index.htm", "default.htm" )

## Use the "Content-Type" extended attribute to obtain mime type if possible

# mimetype.use-xattr = "enable"

#### accesslog module

accesslog.filename         = "/var/log/lighttpd/access.log"

## deny access the file-extensions

#

# ~    is for backupfiles from vi, emacs, joe, ...

# .inc is often used for code includes which should in general not be part

#      of the document-root

url.access-deny            = ( "~", ".inc" )

######### Options that are good to be but not neccesary to be changed #######

## bind to port (default: 80)

# server.port               = 81

## bind to localhost only (default: all interfaces)

## server.bind                = "localhost"

## error-handler for status 404

#server.error-handler-404  = "/error-handler.html"

#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts

server.pid-file            = "/var/run/lighttpd.pid"

## 

## Format: .html

## -> ..../status-404.html for 'File not found'

#server.errorfile-prefix    = "/var/www/"

## virtual directory listings

dir-listing.encoding        = "utf-8"

server.dir-listing          = "enable"

## send unhandled HTTP-header headers to error-log

#debug.dump-unknown-headers  = "enable"

### only root can use these options

#

# chroot() to directory (default: no chroot() )

#server.chroot            = "/"

## change uid to  (default: don't care)

server.username            = "www-data"

## change uid to  (default: don't care)

server.groupname           = "www-data"

#### compress module

#compress.cache-dir          = "/var/tmp/lighttpd/cache/compress/"

#compress.filetype           = ("text/plain", "text/html")

#### status module

# status.status-url = "/server-status"

# status.config-url = "/server-config"

#### url handling modules (rewrite, redirect, access)

# url.rewrite                 = ( "^/$"             => "/server-status" )

# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#

# define a pattern for the host url finding

# %% => % sign

# %0 => domain name + tld

# %1 => tld

# %2 => domain name without tld

# %3 => subdomain 1 name

# %4 => subdomain 2 name

#

# evhost.path-pattern = "/home/storage/dev/www/%3/htdocs/"

#### expire module

# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool

# rrdtool.binary = "/usr/bin/rrdtool"

# rrdtool.db-name = "/var/www/lighttpd.rrd"

#### handle Debian Policy Manual, Section 11.5. urls

#### and by default allow them only from localhost

$HTTP["remoteip"] =~ "127.0.0.1" {

	alias.url += ( 

		"/doc/" => "/usr/share/doc/",

		"/images/" => "/usr/share/images/"

	)

	$HTTP["url"] =~ "^/doc/|^/images/" {

		dir-listing.activate = "enable"

	}

}

#### variable usage:

## variable name without "." is auto prefixed by "var." and becomes "var.bar"

#bar = 1

#var.mystring = "foo"

## integer add

#bar += 1

## string concat, with integer cast as string, result: "www.foo1.com"

#server.name = "www." + mystring + var.bar + ".com"

## array merge

#index-file.names = (foo + ".php") + index-file.names

#index-file.names += (foo + ".php")

#### external configuration files

## mimetype mapping

include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files, 

## read /etc/lighttpd/conf-available/README first

include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

scgi.server = (

 "/RPC2" => # RT_DIR

  ( "127.0.0.1" =>

   (

    "host" => "127.0.0.1", # Ip where rtorrent is listening

    "port" => 5000, # Port specified in .rtorrent.rc

    "check-local" => "disable"

   )

  )

 )

 fastcgi.server = ( ".php" => (( 

                     "bin-path" => "/usr/bin/php-cgi",

                     "socket" => "/tmp/php.socket"

                 )))

auth.backend = "htdigest"

auth.backend.htdigest.userfile = "/etc/lighttpd/htdigest"

auth.require = ( "/RPC2" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 ),

 "/torrents" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 ),

 "/db" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 )
)

```


Thanks

---

### Post by devinw on 2009-10-29
> **rssurvivor said:**
> It seems the problem is universal and related with rTorrent, all other webuis give the same error.

Yes, it is. There's a ticket and patch for it here: [http://libtorrent.rakshasa.no/ticket/1888](http://libtorrent.rakshasa.no/ticket/1888)

---

### Post by devinw on 2009-10-29
@gryffin11

I'm not sure why lighttpd is giving you problems on 6.06, but you could try removing the alias section that's giving it trouble. It's just the default configuration and not necessary at all.
Remove this section from your lighttpd.conf:
```
$HTTP["remoteip"] =~ "127.0.0.1" {

	alias.url += ( 

		"/doc/" => "/usr/share/doc/",

		"/images/" => "/usr/share/images/"

	)

	$HTTP["url"] =~ "^/doc/|^/images/" {

		dir-listing.activate = "enable"

	}

}
```

Then see if lighttpd will restart.

---

### Post by boblemur on 2009-10-30
Hey i am trying to install wtorrent also, and i am getting

500 - internal server error

error.log reports:
```
2009-10-30 19:45:54: (mod_fastcgi.c.2494) unexpected end-of-file (perhaps the fastcgi process died): pid: 2928 socket: unix:/tmp/php.socket-3 
2009-10-30 19:45:54: (mod_fastcgi.c.3326) response not received, request sent: 818 on socket: unix:/tmp/php.socket-3 for /install.php , closing connection 
```

access.log reports:
```
192.168.1.3 192.168.1.1 - [30/Oct/2009:19:45:54 +1100] "GET /install.php HTTP/1.1" 500 369 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20091020 Ubuntu/9.10 (karmic) Firefox/3.5.3"

```

im running karmic, so there may be something different for karmic, but im unsure what it could be. do you know where i could git any more information? more error logs etc... 

also should it make a difference that im not using the same directories for my download locations ( i have updated them in all the config files though so i cant see it being an issue)

any more information would really help, im ready to give up on this stupid ui and just stick to cli :)

---

### Post by gryffin11 on 2009-10-30
> **devinw said:**
> @gryffin11

I'm not sure why lighttpd is giving you problems on 6.06, but you could try removing the alias section that's giving it trouble. It's just the default configuration and not necessary at all.
Remove this section from your lighttpd.conf:

Then see if lighttpd will restart.

Thanks, I made these changes and lighttpd starts with some warnings: 
```
2009-10-30 22:17:55: (server.c.871) WARNING: unknown config-key: auth.backend (ignored) 
2009-10-30 22:17:55: (server.c.871) WARNING: unknown config-key: auth.backend.htdigest.userfile (ignored) 
2009-10-30 22:17:55: (server.c.871) WARNING: unknown config-key: auth.require (ignored) 
```

But when I try to connect to rtorrent on the web interface I get 
```
Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).
```

When starting rtorrent I get the following error 
```
rt@ubuntu:/root/wtorrent-installer$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:1: Variable "scgi_port" does not exist.

```

It is in this file though, the first line:

```
  GNU nano 1.3.10          File: /home/rt/.rtorrent.rc                          

scgi_port = localhost:5000

# Move completed torrents to /home/rt/torrents/done/
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/$

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

.....
.....
.....

```

Anyone have any idea what could be causing this?

Thanks

---

### Post by boblemur on 2009-11-01
gryffin11: this may be caused because the version of rtorrent you have may not have xmlrcp-c flag enabled at compile time, and hence does not support being talked to by the lighttpd. however with later versions of ubuntu it does.

for me i can see that rtorrent is listening on 127.0.0.1:5000, as well as the port that it is bound to (for the actual torrenting) using this command:
```
:~$ netstat -nlp | grep rtorrent
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.0.1:5000          0.0.0.0:*               LISTEN      1034/rtorrent   
tcp        0      0 10.1.1.2:6932           0.0.0.0:*               LISTEN      1034/rtorrent 
```

so if you cant start rtorrent then its obviously not going to be listening. but if you try following the instructions here:
[http://forum.buffalo.nas-central.org/viewtopic.php?f=19&t=4407]("http://forum.buffalo.nas-central.org/viewtopic.php?f=19&t=4407")

only follow steps 1 and 2 then you should try the command above once you start rtorrent to see if rtorrent is listening on that port then try continuing.

---

### Post by devinw on 2009-11-03
> **boblemur said:**
> gryffin11: this may be caused because the version of rtorrent you have may not have xmlrcp-c flag enabled at compile time, and hence does not support being talked to by the lighttpd. however with later versions of ubuntu it does.

Yeah, it's possible that the rtorrent package in the dapper repos doesn't have xmlrpc support. gryffin11, you can try running the rtorrent-svn-upgrade.sh script to build rtorrent with xmlrpc support.

> **boblemur said:**
> Hey i am trying to install wtorrent also, and i am getting

500 - internal server error

error.log reports:
```
2009-10-30 19:45:54: (mod_fastcgi.c.2494) unexpected end-of-file (perhaps the fastcgi process died): pid: 2928 socket: unix:/tmp/php.socket-3 
2009-10-30 19:45:54: (mod_fastcgi.c.3326) response not received, request sent: 818 on socket: unix:/tmp/php.socket-3 for /install.php , closing connection 
```

access.log reports:
```
192.168.1.3 192.168.1.1 - [30/Oct/2009:19:45:54 +1100] "GET /install.php HTTP/1.1" 500 369 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20091020 Ubuntu/9.10 (karmic) Firefox/3.5.3"

```

im running karmic, so there may be something different for karmic, but im unsure what it could be. do you know where i could git any more information? more error logs etc... 

also should it make a difference that im not using the same directories for my download locations ( i have updated them in all the config files though so i cant see it being an issue)

any more information would really help, im ready to give up on this stupid ui and just stick to cli :)

I haven't tried the script on Karmic, so there might be a problem specific to the newest release as you said. Has anyone else used the script on Karmic?
I'll let you know if I get a chance to test it out.

Googled and found this: [http://redmine.lighttpd.net/boards/2/topics/2188](http://redmine.lighttpd.net/boards/2/topics/2188)
Just a shot in the dark, but maybe you have huge PHP error logs?

---

### Post by herbster on 2009-11-03
I posted to the ticket on wtorrent Trac: [http://www.wtorrent-project.org/trac/ticket/279#comment:5](http://www.wtorrent-project.org/trac/ticket/279#comment:5)

I simply cannot get past this error at install.php:

```
Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up).
```

I have rtorrent running just fine, same netstat output as few posts above, all is well with it but wtorrent will absolutely refuse to go past this install.php, grrr...

---

### Post by gryffin11 on 2009-11-03
Thanks, got it working, I had to compile it all manually. Unfortunately the svn script wouldn't work because the default version of curl for dapper is too old, so that also needs to be compiled from source, which the script doesn't do.

---

### Post by MadMcMurphy on 2009-11-03
I'm back trying to get wTorrent working :)
Fed up of ruTorrent!  If it's not ever changing column widths then it's sluggish performance :(

Does anyone know if a 64bit OS would cause any issues? - [http://www.wtorrent-project.org/trac/ticket/372](http://www.wtorrent-project.org/trac/ticket/372) (I don't know whether this applies to us, but I figured sharing the link couldn't hurt :))

---

### Post by eqisow on 2009-11-03
Some notes on the lighttpd config:

1) You can mount /RPC2 in the torrent directory, so you only need one protected directory instead of two.

2) "method" => "basic" is not secure. You either need to use "method" => "digest", SSL, or both.

Personally, I'd only recommend using a script like this if you already know what you're doing and want to save time. It's pretty important to know how your server is set up so that you can administer it properly.

---

### Post by Darz0re on 2009-11-04
**EDIT :SOLVED, WASNT PUTTING PORT 80 INTO THE WTORRENT INSTALL.PHP AND I CHANGED MY LIGHTTPD.CONF TO THIS [http://pastebin.com/d1c7d1467](http://pastebin.com/d1c7d1467)** 

Thanks anyway, best regards, Darz0re



Hi, 

  Let me first saw that I have spent the last two days trawling through wtorrent guides online trying to fix my issue and this thread has been amazing in terms of ideas and new things to try. Thanks for the time and effort that you have put into this thread!.

I'm not running Ubuntu but Debian 5.0 64 bit and am running into the classic "Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up)." error on install.php and was hoping maybe you could help me resolve this issue. I am attempting to install wTorrent Advanced (I personally use rutorrent on my own server and it works amazingly well, the server I help maintain for friends has 5 users so rutorrent may not work well for them)

In order to cut down on possible issues i have cut down my config files to the minimun as you will now see.
I also amn't using any auth at the moment as I want to get the basic working right before I add to it :)

This is the .rtorrent.rc that I am using ( [http://pastebin.com/m2f6374e](http://pastebin.com/m2f6374e) )

My lighttpd.conf file ( [http://pastebin.com/m2ee9ce4b](http://pastebin.com/m2ee9ce4b) )

My output of " netstat -np -l | grep rtorrent" is as follows

```
tcp        0      0 127.0.0.1:5000          0.0.0.0:*               LISTEN      6977/rtorrent
tcp        0      0 0.0.0.0:58961           0.0.0.0:*               LISTEN      6977/rtorrent
```My output of "tail -f /var/lighttpd/error.log" is as follows. 
```

2009-11-04 21:03:38: (mod_fastcgi.c.2610) FastCGI-stderr: XML-RPC: xmlrpcmsg::parseResponse: no response received from server.
```rtorrent is running as its own user in /home/rtorrent which is writible for lighttpd

Any help here would be great! I'm really stumped :(

Thanks in Advance!

Darz0re

---

### Post by MadMcMurphy on 2009-11-05
I just installed Ubuntu 9.10 Server 64bit on one of my VM's.  Used the install.sh script and it works (after a reboot aswell).
After running the svn script it instantly stops working.

Anyone got any clues?

Thanks :D

---

### Post by Cyberrad on 2009-11-13
> **Cyberrad said:**
> What a great script.  I was able to get this to work on Ubuntu Server 9.04.

However, I tried the same steps on another clean box with Ubuntu Server 9.04 and I keep getting the error "This is not a torrent file" from wtorrent.  All of my searches on the error have come up with nothing.  Has anyone else seen this behavior?

Edit:  Actually it looks like the error is coming from rTorrent.  rTorrent throws: Could not create download, the input is not a valid torrent.  I tested the file against the other box and the files are valid so I think rtorrent is giving me a false positive.

I just tried this with a fresh 9.10 and I am still getting the same error.  Anyone have any ideas on what might be going on?

---

### Post by lain on 2009-11-14
After much configuring (using this script, doing the guides manually, googling) i finally got rtorrent to talk to wtorrent.

First of all, thank you for the script. I got mine up almost flawlessly without this script first following this guide:
[http://blog.vintaku.com/2009/01/11/how-to-install-rtorrent-and-wtorrent-on-ubuntu-804/](http://blog.vintaku.com/2009/01/11/how-to-install-rtorrent-and-wtorrent-on-ubuntu-804/)
but i never got rtorrent to talk with wtorrent.
uninstalled everything from that guide, used your script and installed everything, followed that guide to manually install wtorrent, and everthing worked. The reason i had to manually install wtorrent after running your script was because i got a bunch of php errors (i think) and it couldn't find all the php files.
I haven't tried torrenting yet but atleast now rtorrent/wtorrent are reporting that they're fully working.
Thanks again!
(This was on a newly installed ubuntu 9.10 server i might add).

I have a question, is it possible to configure this so that it's only possible to access wtorrent via the internal network (192.168.x.x), and not through internet?
the only reason i actually got wtorrent was to have a web interface that i can control from all the other computers in my network, but i'm not interested in having control over it from the internet. I was thinking that this could add some security, since i'm not entirely certain how secure my fileserver (mind you, i've just started using linux), and would like to minimize the amount of services that can be connected from 'the outside'.

---

### Post by dcorwin822 on 2009-11-14
> **lain said:**
> After much configuring (using this script, doing the guides manually, googling) i finally got rtorrent to talk to wtorrent.

First of all, thank you for the script. I got mine up almost flawlessly without this script first following this guide:
[http://blog.vintaku.com/2009/01/11/how-to-install-rtorrent-and-wtorrent-on-ubuntu-804/](http://blog.vintaku.com/2009/01/11/how-to-install-rtorrent-and-wtorrent-on-ubuntu-804/)
but i never got rtorrent to talk with wtorrent.
uninstalled everything from that guide, used your script and installed everything, followed that guide to manually install wtorrent, and everthing worked. The reason i had to manually install wtorrent after running your script was because i got a bunch of php errors (i think) and it couldn't find all the php files.
I haven't tried torrenting yet but atleast now rtorrent/wtorrent are reporting that they're fully working.
Thanks again!
(This was on a newly installed ubuntu 9.10 server i might add).

I have a question, is it possible to configure this so that it's only possible to access wtorrent via the internal network (192.168.x.x), and not through internet?
the only reason i actually got wtorrent was to have a web interface that i can control from all the other computers in my network, but i'm not interested in having control over it from the internet. I was thinking that this could add some security, since i'm not entirely certain how secure my fileserver (mind you, i've just started using linux), and would like to minimize the amount of services that can be connected from 'the outside'.


Append this to the end of your lighttpd config file in /etc/lighttpd/ .  Make sure you change server to your server's host name!  To find out your servers host name just run the command 'hostname' and it's result is what your gonna need to place in there. Don't forget to restart the service! Do "sudo service lighttpd restart"

```

# Deny access from everyone but in the 192.168.x.x network
$HTTP["host"] == "server" {
  $HTTP["remoteip"] != "192.168.0.0/16" {
   url.access-deny = ( "" )
  }
}

```

---

### Post by lain on 2009-11-14
> **dcorwin822 said:**
> Append this to the end of your lighttpd config file in /etc/lighttpd/ .  Make sure you change server to your server's host name!  To find out your servers host name just run the command 'hostname' and it's result is what your gonna need to place in there. Don't forget to restart the service! Do "sudo service lighttpd restart"

```

# Deny access from everyone but in the 192.168.x.x network
$HTTP["host"] == "server" {
  $HTTP["remoteip"] != "192.168.0.0/16" {
   url.access-deny = ( "" )
  }
}

```

Thanks, but there isn't a way to test this is there? i tried connecting another computer to my isp-modem (which gives me different ip's) and i could still access it through the internet-ip the server has. i was thinking it was pointless trying to test it from one of the other computers because they are all connected to the server, and the server acts as a dhcp server, giving them 192.168.x.x ip's. they can still access the server through the isp-ip.

EDIT:
Tried this instead and it seems to work:

```

# Deny access from everyone but in the 192.168.x.x network
  $HTTP["remoteip"] !~ "192.168.0.*|192.168.1.*|127.0.0.1" {
   url.access-deny = ( "" )
  }

```

---

### Post by devinw on 2009-11-16
Cyberrad, is this helpful?
[http://www.wtorrent-project.org/trac/ticket/377](http://www.wtorrent-project.org/trac/ticket/377)

---

### Post by Cyberrad on 2009-11-17
> **devinw said:**
> Cyberrad, is this helpful?
[http://www.wtorrent-project.org/trac/ticket/377](http://www.wtorrent-project.org/trac/ticket/377)

Looks promising!  What file is he talking about that he edited?  Could you make that out?  I assumed that he was referring to the wtorrent code so I went through a good bit but I couldn't find the if.

---

### Post by devinw on 2009-11-17
You know what? I can't find the file either. I posted a comment on that ticket, hopefully the OP there can clear things up.

---

### Post by Cyberrad on 2009-11-18
> **devinw said:**
> You know what? I can't find the file either. I posted a comment on that ticket, hopefully the OP there can clear things up.
Maybe he is referring to a rtorrent file.  For me it is rtorrent that is kicking the error to wtorrent.  It doesn't make sense to edit wtorrent's check if it doesn't work for rtorrent.

I grabbed the old wtorrent-installer.tar from the server I have working dated February and tried that last night.  I got the same result.  So this seems to be something that is wrong with the version in the repositories.

---

### Post by madhartigan on 2009-11-18
Being new to ubuntu and wanting to install this, I have a few basic questions.

1) Will this work on my fresh 9.10 install (w/OpenSSH installed from the install disk)?

2) Do I need to make any modifications to the install.sh file for this to work?

3) Should I run this as root or as a user?

4) It says to download to the /home directory.  Is that /home/user or actually /home?


Thanks for your time.  I'm looking forward to utilizing this script.

---

### Post by Cyberrad on 2009-11-18
> **madhartigan said:**
> Being new to ubuntu and wanting to install this, I have a few basic questions.

1) Will this work on my fresh 9.10 install (w/OpenSSH installed from the install disk)?

2) Do I need to make any modifications to the install.sh file for this to work?

3) Should I run this as root or as a user?

4) It says to download to the /home directory.  Is that /home/user or actually /home?


Thanks for your time.  I'm looking forward to utilizing this script.

1. There was one person that said it worked for them on 9.10.  It should work with 9.10 but I had an issue.  I am using 9.10 Server x64.  Which one are you using?
2. No modifications are needed on the install.sh script.
3. I would run it as a user.  The script will ask for the sudo password for the user.
4. The home directory is the ~ directory which is /home/{user}.

---

### Post by madhartigan on 2009-11-18
I'm also using the x64 version of 9.10 server.

I'll give it a shot as user and see how it works.

Thank you for the reply!!

---

### Post by AnalBeard on 2009-11-19
devinw: can i first say thank you for massively simplifying something that is proving to be a bit of a nightmare. 

now, i do have a small issue. everything runs fine with the install script, until it tries to restart lighttpd, then i get the following error:

```

Starting web server: lighttpdDuplicate config variable in conditional 0 global: fastcgi.server
2009-11-19 18:32:58: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 271 pos: 13 parser failed somehow near here: (EOL)
 failed!
Failed to restart lighttpd. Please check /etc/lighttpd/lighttpd.conf.

```

this is my lighttpd.conf:

[http://pastebin.com/m1a198141](http://pastebin.com/m1a198141)

the offending line appears to be:

**auth.backend = "htdigest"**

i should mention that i'm running this on debian lenny but that shouldn't affect anything.

---

### Post by madhartigan on 2009-11-19
At the end of the install, I go to [http://my.servers.ip/install.php](http://my.servers.ip/install.php) and it displays a text display of the PHP script.

I followed the howtoforge guide for Ubuntu 9.10 Perfect Server (ISPConfig2) install so if that helps to diagnose this situation, there you go.

Not sure why .php files aren't properly executing, but help would be appreciated.

Thanks!!

---

### Post by Cyberrad on 2009-11-20
> **madhartigan said:**
> At the end of the install, I go to [http://my.servers.ip/install.php](http://my.servers.ip/install.php) and it displays a text display of the PHP script.

I followed the howtoforge guide for Ubuntu 9.10 Perfect Server (ISPConfig2) install so if that helps to diagnose this situation, there you go.

Not sure why .php files aren't properly executing, but help would be appreciated.

Thanks!!
It sounds like you don't have php installed.  I am pretty new to Linux so I am not sure how to check this but make sure you have php installed.  To install type "sudo apt-get install php5".

---

### Post by Cyberrad on 2009-11-20
Devinw, It looks like you need to update the rtorrent-upgrade-svn script.  One of the lib files have changed.  I forget which one though... Sorry.

Edit: It is libkadm55.

---

### Post by welshboykev on 2009-11-23
hi i just like to say this is by far the easyest way i have found to install wtorrent and rottent but i been having a few problems latley everything works amazingly but all of a sudden it will come up with an error on wtorrent saying cannot connect to rtorrent and to get everything running again i have to do this in the terminal sudo /etc/init.d/rtorrent restart or reboot the server  and this can happen 2 - 3 times a day i have changed the lighttpd to post 81 and tryed 80 but the same problem every time so i wasn't sure if there's was something i had dun previously that could be conflicting with it so i did a full reinstall of ubuntu8.04,32x did all the updates for it then only thing i installed was wtorrent/rtorrent and this still happens i have tried to install a newer version 0.8.5 manually but being a compleat novice of linux i couldn't get anything to work 

so my question is is there something simple im missing that's making wrorrent not connect to rtorrent 

also is there a simple way of updating rtorrent to 0.8.5 or 0.8.4 after this install by doing something like adding info to  gksudo gedit /etc/apt/sources.list

like i said im a complete novice to linux and trying to teach myself by trial and error , so i realy do appreciate any help you guys can give 

thankyou so much in advance guys

---

### Post by AnalBeard on 2009-11-26
> **AnalBeard said:**
> devinw: can i first say thank you for massively simplifying something that is proving to be a bit of a nightmare. 

now, i do have a small issue. everything runs fine with the install script, until it tries to restart lighttpd, then i get the following error:

```

Starting web server: lighttpdDuplicate config variable in conditional 0 global: fastcgi.server
2009-11-19 18:32:58: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 271 pos: 13 parser failed somehow near here: (EOL)
 failed!
Failed to restart lighttpd. Please check /etc/lighttpd/lighttpd.conf.

```

this is my lighttpd.conf:

[http://pastebin.com/m1a198141](http://pastebin.com/m1a198141)

the offending line appears to be:

**auth.backend = "htdigest"**

i should mention that i'm running this on debian lenny but that shouldn't affect anything.

after a lot of perseverance/swearing/etc i finally solved my problem: i used apache. admittedly this was fraught with issues too, the chief among which was that lovely box that said 'cannot connect to rtorrent'. so in case anyone else is having this problem, i compiled xmlrpc-c with the 'super stable' version and this seems to have done the trick.
```
svn co https://xmlrpc-c.svn.sourceforge.net/svnroot/xmlrpc-c/super_stable/ xmlrpc-c
```
thought i'd mention this just in case anyone else was having the same issue. rtorrent and libtorrent were compiled with the latest svn code so the problem was obviously caused by xmlrpc-c

---

### Post by mysoogal on 2009-11-29
setting up rtorrent when your a newbi is really like asking your first girlfriend on your first date to have sex with you, its just not going to work out, the next best thing is sudo apt-get install transmission ;)

add the deb sources

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted universe

## Add comments (##) in front of any line to remove it from being checked.

## Use the following sources.list at your own risk.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse


## MAJOR BUG FIX UPDATES produced after the final release

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse


## UBUNTU SECURITY UPDATES

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse



sudo apt-get update,


next sudo apt-get install transmission

, log into VPS with TightVNC Viewer

just open terminal window, and type transmission bingo ! go into settings and enable the web interface for transmission, enable the system tray icon ! close transmission, thats about it ! ohh dont forget to set the path to /var/www/ 


setting up utorrent wih wine is kinda easy to when you have remote desktop ;)

always buy VPS with root :D

---

### Post by bba67 on 2009-11-30
Hello, I try to go on my install.php, but my browser only give me the choice to open or download it...
What can I do to run it? a parsing problem?

Thanks for answers :)

---

### Post by devinw on 2009-11-30
> **bba67 said:**
> Hello, I try to go on my install.php, but my browser only give me the choice to open or download it...
What can I do to run it? a parsing problem?

Thanks for answers :)

Sounds like PHP hasn't been set up correctly. Running the script should take care of this though - did you run install.sh on a fresh Ubuntu install?

---

### Post by bba67 on 2009-11-30
What I thought... no it isn't a fresh install of ubuntu, and can't really do any new.
But isn't it a way to resolve the problem? without re-install ubuntu?

---

### Post by devinw on 2009-11-30
Did you install PHP before running the script? Could be a conflict there.
Also, are you running another webserver (like apache) on your box?

---

### Post by bba67 on 2009-11-30
Thanks to help me, I uninstall apache and what I had install before, so it must be clean and i don't have any other service that use apache.

I'm really stuck

---

### Post by devinw on 2009-11-30
Try this:
Purge any unneeded php5 packages:```

sudo apt-get remove --purge apache2 libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl
```
Then run the uninstall.sh script. When it asks if you want to remove packages, say yes. Finally, run install.sh again.

---

### Post by bba67 on 2009-11-30
One last question before i try it, why does svn co svn not work? it's waiting waiting and it says that's no response, so I installed it manually but would prefer to let this work to.

Thanks for your great help

---

### Post by devinw on 2009-11-30
What's the exact svn command you ran?
As long as you have the subversion package (sudo apt-get install subversion), things should work. I don't think the wTorrent or rTorrent repositories are down.

---

### Post by bba67 on 2009-11-30
I run that svn co svn://wtorrent-project.org/repos/trunk/wtorrent/ in "root" and it don't gives me anything...
svn: Can't connect to host 'wtorrent-project.org': Connection timed out


and subversion is actually installed

---

### Post by devinw on 2009-11-30
I just checked out the latest revision of wTorrent without any problems using the same command you did.
Might be a stupid question, but are you sure your server has an internet connection? :)

---

### Post by bba67 on 2009-11-30
Hmm, I'm only connect with ssh over and all the things I have done worked but this not...
And I don't find the solution.

---

### Post by devinw on 2009-11-30
I'm not sure why you might be having trouble accessing the wTorrent subversion repository. That problem aside, were you able to get your server to execute PHP scripts instead of sending them to the browser?

---

### Post by bba67 on 2009-11-30
I'm still searching for both, and no I can't change anything...
Actually I'm a little bit in trouble with the apache2.conf, i thought it was httpd.conf but it changed in apache2.
And I would add AddType application/x-httpd-php .php so it was in httpd.conf but the files are very different and httpd.conf is empty...

---

### Post by devinw on 2009-11-30
install.sh installs and configures lighttpd, so you don't need apache at all. You should really run lighttpd on a different port if you want to continue using apache for other things, but for testing purposes you could simply stop apache (sudo /etc/init.d/apache2 stop), and then start lighttpd (sudo /etc/init.d/apache2 stop).

---

### Post by bba67 on 2009-11-30
I completely removed apache and the other packages or libs but it's still the same.

---

### Post by bba67 on 2009-11-30
Somehow I advanced and had this:
Fatal error: Smarty error: the $compile_dir 'tpl_c/' does not exist, or is not a directory. in /var/www/lib/smarty/Smarty.class.php on line 1092

and with your script I removed tcl_c, because I had the same thing(doesn't exist)
sudo chown -R www-data:www-data db torrents tpl_c

---

### Post by devinw on 2009-11-30
Sounds like PHP is working now!
This may be helpful to you: [http://ubuntuforums.org/showthread.php?t=962435](http://ubuntuforums.org/showthread.php?t=962435)

---

### Post by bba67 on 2009-11-30
I have allready resolved that, I'm now on my install.php, but yet I'm stuck there:
Error: cannot connect to rtorrent, please check host, folder and port values (and user/password if you have auth set up). 
I've set up the port 9998 with is the port of the webui?(no?), and localhost, with /RPC2 and no user or pass.

---

### Post by devinw on 2009-11-30
All the defaults on install.php should be fine. The rTorrent scgi port is whatever port lighttpd is running on.
You should also make sure rTorrent is running.

---

### Post by bba67 on 2009-12-01
The port 80 is open and lighttpd running on it, and I made chmod on my folders, so I don't really see where is the problem.

---

### Post by bba67 on 2009-12-01
Hey, I finally had it to work, the script correctly run(no manual installation of wtorrent), I have access to the install.php and yet know why I have the error said before.

I used the ps aux and rtorrent was not in the process list, so I'd try to launch it under root or any other user...
No errors to show, but still not work, not launched.

Any idea?

---

### Post by raab on 2009-12-01
Using this script on debian lenny 64bit, works great.

However, once I do the svn upgrade it seems to break xmlrpc connectivity between wtorrent and rtorrent.

Not sure why :/

I had this issue prior to using your script so I completely wiped everything and started with your script.

Turns out it was the latest unstable of rtorrent :|

---

### Post by Cas07 on 2009-12-03
This was a handy topic to find! Good work devinw. :)

I ran the script on Ubuntu 9.10 Server with only the following minor problems found: 
[INDENT]
There is a permission issue that required me to *chmod -R 777 /var/www* and then repeat the permission setup for wTorrent, from the script.

I think there is a problem with install.php for wTorrent as it can return a PDOException error when trying to update an existing database. I realised i had an old database already in the folder so deleting it solved the problem. 

The script to download SVN versions needs altering to account for libkadm55 being no longer available in 9.10. I judged that using libkadm5clnt6 was a suitable replacement and seemed to placate the script. 

The final problem I encountered, also in the SVN script, was the build of rTorrent failing with a library conflict. The solution was to completely remove libxmlrpc-c3 by running *sudo apt-get autoremove* then rerun the script.
[/INDENT]

After ironing out these issues both rTorrent and wTorrent are working together perfectly! Now i can start tinkering with the configs :P

P.S. Its a minor point but I feel that script is installing quite a few unnecessary/irrelevant packages.

---

### Post by yataf on 2009-12-05
I'm getting the PDOexception too, where is the database file for me to delete? I've googled it and it seems thats what people did to fix the problem but I don't know where it's at. In my wtorrent folder's db folder all I have is a .htaccess file.

---

### Post by Cas07 on 2009-12-06
Despite the earlier success of wTorrent accessing rTorrent, it worked for about 10mins then for some unknown reason it then completely refused to connect again to rTorrent no matter what i tried! 
So I abandoned rTorrent and decided to test out the new release of Deluge 1.2.0rc4. I've found a surprising gem that has nearly all the features I'm looking for, looks good, and was a breeze to setup.


> **yataf said:**
> I'm getting the PDOexception too, where is the database file for me to delete? I've googled it and it seems thats what people did to fix the problem but I don't know where it's at. In my wtorrent folder's db folder all I have is a .htaccess file.

IIRC the file should be here: /var/www/db/database.db

---

### Post by devinw on 2009-12-06
@bba67
If you're getting "Error: could not connect to rtorrent" on install.php, give this a shot: [http://ubuntuforums.org/showpost.php?p=7136951&postcount=44](http://ubuntuforums.org/showpost.php?p=7136951&postcount=44)

@yataf
Default location for the wTorrent database: /var/www/db/database.db

@Caos
Thanks for the detailed report. I actually badly need to update the OP (possibly create a new thread), because there's now an improved version of the script hosted on github. It includes support for ruTorrent among other things. Here's the project url: [http://github.com/daymun/rtorrent-webui-installer](http://github.com/daymun/rtorrent-webui-installer)
If you're comfortable forking the project and making some of the changes you listed, that would be great. Shoot me a pm if you're interested or have any questions.

Edit: glad Deluge is working for you.

---

### Post by Cas07 on 2009-12-07
> **devinw said:**
> 
@Caos
If you're comfortable forking the project and making some of the changes you listed, that would be great.

Oh that is interesting, i may revisit rTorrent in the future and therefore possibly help out. The hours lost so far on indecipherable bugs mean I'm rather jaded with it.

---

### Post by user 76 on 2010-02-09
Hopefully someone can help,

I have installed this on a freshly installed Ubuntu server 8.10.

Whenever I try to add a torrent file it gives the error '
                               
     
         'This is not a torrent file'

Adding .torrent files by ftp to the watch filder works no problem.

Thanks in advance, I'm fairly new to all this;)

[B]Edit:

I have tried also manually adding a .torrent file to the '/var/www/torrents' folder and that isn't getting picked up. Anyone have any ideas?[/B]

---

### Post by devinw on 2010-02-15
@user 76
Sorry I didn't get back to you sooner. Does this help?
[http://www.wtorrent-project.org/trac/ticket/377](http://www.wtorrent-project.org/trac/ticket/377)

---

### Post by user 76 on 2010-02-17
> **devinw said:**
> @user 76
Sorry I didn't get back to you sooner. Does this help?
[http://www.wtorrent-project.org/trac/ticket/377](http://www.wtorrent-project.org/trac/ticket/377)

devinw, I ended up going with rutorrent in the end :)

Thanks for a excellent script though.

---

### Post by devinw on 2010-02-17
> **user 76 said:**
> devinw, I ended up going with rutorrent in the end :)

Thanks for a excellent script though.
I just set up ruTorrent on my box too, it's great.
If anyone else is interested, the github version of the script works with ruTorrent: [http://github.com/daymun/rtorrent-webui-installer](http://github.com/daymun/rtorrent-webui-installer)

---

### Post by user 76 on 2010-02-18
> **devinw said:**
> I just set up ruTorrent on my box too, it's great.
If anyone else is interested, the github version of the script works with ruTorrent: [http://github.com/daymun/rtorrent-webui-installer](http://github.com/daymun/rtorrent-webui-installer)


Do you know how I go about upgrading to verion 3.0 of rutorrent?

---

### Post by devinw on 2010-02-18
> **user 76 said:**
> Do you know how I go about upgrading to verion 3.0 of rutorrent?

You can download the 3.0 branch with svn like this:
```
svn checkout http://rutorrent.googlecode.com/svn/branches/3.0/rutorrent/
```

---

### Post by l3lackEyedAngels on 2010-02-18
When I ran ```
wtorrent-installer/install.sh
```, all I got was ```
Unpacking mc (from .../mc_2%3a4.6.2-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mc_2%3a4.6.2-2ubuntu1_i386.deb (--unpack):
trying to overwrite '/usr/share/locale/pt_BR', which is also in package apt 0:0.7.23.1ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mc_2%3a4.6.2-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Halp!, please.

I should also mention that I tried using [this guide]("http://www.wtorrent-project.org/trac/wiki/wTorrentInstall") first, but ran into some issues with ```
./configure --disable-cplusplus
``` and ```
./configure --with-xmlrpc-c
```.

Thanks in advance!

PS, I'm running 9.10.

---

### Post by user 76 on 2010-02-19
> **devinw said:**
> You can download the 3.0 branch with svn like this:
```
svn checkout http://rutorrent.googlecode.com/svn/branches/3.0/rutorrent/
```

Cheers devinw I'll give that a go

---

### Post by MeRodent on 2010-04-01
Bugger. Had wtorrent working, changed my network settings and now can't connect to rtorrent.

Any idea of where I should be looking?

basically changed server.host.net to server.host.lan 

All the settings I can find point to localhost rather than a domain so it's not making much sense to me.




After lots of stuffing around it appears the problem was running bind9 without a localhost.host.lan designation and a lock file on the rtorrent session.

---

### Post by miki_x on 2010-04-15
Hi,

First of all thanks for these great scripts!
I'm running into a small problem; you might be able to help:
-I installed rtorrent+wtorrent from the scripts. No problem, everything worked.
-Then I tried the rtorrent-svn-upgrade script, agin everything is still running; but I ran into the following problems:

-When I try to add a torrent with its URL I get "error adding torrent".
The "watch" directory permissions are as follows
```
drwxr-xr-x 2 rt rt 4096 2010-04-15 18:00 watch

``` 

-The upload rate I've set is not respected. The .rtorrent.rc file is located in /home/rt/ as it should and I used upload_rate = 60
Still rtorrent is uploading at 150.
Actually quite a few parameters are not respected in the .rtorrent.rc:
- upload_rate
- dht_port (gives me an "dht_port does not exist" on launch"
- use_udp_tracker (gives me an "use_udp_tracker does not exist" on launch"
- max_peers

In case it helps, here's my .rtorrent.rc:
```
#SCGI port
scgi_port = localhost:5000

# Peer limits configuration
min_peers = 40
max_peers = 120
min_peers_seed = 10
max_peers_seed = 50
max_uploads = 15

# Maximum upload rate
upload_rate = 60

directory = /home/rt/torrents/doing
session = /home/rt/.rtsession
schedule = watch_directory,5,5,load_start=/home/rt/torrents/watch/*.torrent
schedule = tied_directory,5,5,start_tied=
schedule = untied_directory,5,5,close_untied=
system.method.set_key = event.download.finished,move_complete,"d.set_directory=~/torrents/done/ ;execute=mv,-u,$d.get_base_path=,~/torrents/done/"

port_range = 51320-51329
port_random = no
check_hash = yes
use_udp_trackers = yes
encryption = allow_incoming,try_outgoing,enable_retry
dht = auto
dht_port = 51330
peer_exchange = yes

```

---

### Post by wisie on 2010-05-01
I had some minor issues upgrading to 10.04 which might have affected my wtorrent/rtorrent setup and I'm a little stuck on how to fix it. 

My wTorrent was giving the error "Unable to connect to rtorrent" so I uninstalled wtorrent and hoped through reinstalling it would all magically work again. Unfortunately now when trying to load the wtorrent page I just get a blank directory with a 	index.lighttpd.html file. I'm really quite stuck on how to fix this, any suggestions would be appreciated.

---

### Post by ssingleton on 2010-05-20
on the new script on git. There is no mention of the arguments used to either install rutorrent or wtorrent. Or does it ask?


possibly a silly question

---

### Post by devinw on 2010-05-22
> **ssingleton said:**
> on the new script on git. There is no mention of the arguments used to either install rutorrent or wtorrent. Or does it ask?


possibly a silly question

Run the github version like this: ./install.sh [wTorrent/ruTorrent] [apt/svn]
So if you want to use ruTorrent and install the SVN versions of rTorrent and XMLRPC-C, run: ./install.sh ruTorrent svn
There's an issue open for adding dialog boxes that would replace the command line arguments, but for now that is the only way to specify which webui to use.

To anyone having problems with the version of the script posted in this thread, please use the github version instead - it's up to date. I will update the original post at some point.

I will probably try to make some updates to the script in the next few weeks. Here are some things I have in mind: [http://github.com/daymun/rtorrent-webui-installer/issues](http://github.com/daymun/rtorrent-webui-installer/issues)
Suggestions are welcome. If anyone is interested in helping with changes, testing, creating a github project page, etc. just contact me through github or ubuntuforums.

---

### Post by ssingleton on 2010-05-23
So i tried the version from github. I start the script off for rutorrent either the apt or svn version and i get a failed to download it is trying to download rutorrent from this location which is wrong/failing http:rutorrent.googlecode.com/svn/trunk/rtorrent/

---

### Post by testme26 on 2010-07-18
I try install wtorrent from SVN and my server say: Failed to check out  the latest wTorrent release from '[ svn://wtorrent-project.org/repos/trunk/wtorrent/]("svn://wtorrent-project.org/repos/trunk/wtorrent/")'. 
 

Someone can help me? 
 

Thanks.

---

### Post by dcorwin822 on 2010-07-18
The script seems out of date. too bad life gets in the way of projects like these.

---

### Post by olragon on 2010-07-18
wtorrent svn repository changed, you need to edit install.sh
[http://www.wtorrent-project.org/trac/](http://www.wtorrent-project.org/trac/)

---

### Post by dcorwin822 on 2010-07-20
any one want to explain to me how to upload a fork to github?

---

### Post by Fredrik_b on 2010-08-01
Hi I have modified the install script to try to make it work again.
This script is now for a 64bit (32bit will not work at the moment)n Ubuntu 9.10.It also uses rutorrent instead of wtorrent


I have some problems that is
some parts have to run as ROOT for some reason
It does not seem to autostart.
webinterface will not connect to rtorrent (loads forever)


The script is based on the original script but i took most commands from [http://blog.unixguru.se/?p=5](http://blog.unixguru.se/?p=5)

here are the files:
install.sh: [http://pastebin.com/atYHZWcn](http://pastebin.com/atYHZWcn)
default: [http://pastebin.com/0Rxirz43](http://pastebin.com/0Rxirz43) (new used with apache)
rtorrent: [http://pastebin.com/y3QDiBc4](http://pastebin.com/y3QDiBc4)
rtorrent.rc: [http://pastebin.com/i50UpcpM](http://pastebin.com/i50UpcpM)

Will look in to it more later today, but would appreciate some input.

---

### Post by tkhobbes on 2010-08-06
Hi all

I have a small problem, still: Downloaded torrents are owned by rt:rt, but the permissions are rwxr-x. This means that only rt can actually write / delete downloaded torrents.
So I am looking to change the GROUP permissions of downloaded torrents to rwx OR user ownership to another user. How to achieve this?

Cheers

---

### Post by Lerxst2112 on 2010-08-08
> **Fredrik_b said:**
> Hi I have modified the install script to try to make it work again.
This script is now for a 64bit (32bit will not work at the moment)n Ubuntu 9.10.It also uses rutorrent instead of wtorrent
 
 
I have some problems that is
some parts have to run as ROOT for some reason
It does not seem to autostart.
webinterface will not connect to rtorrent (loads forever)
 
 
The script is based on the original script but i took most commands from [http://blog.unixguru.se/?p=5](http://blog.unixguru.se/?p=5)
 
here are the files:
install.sh: [http://pastebin.com/atYHZWcn](http://pastebin.com/atYHZWcn)
default: [http://pastebin.com/0Rxirz43](http://pastebin.com/0Rxirz43) (new used with apache)
rtorrent: [http://pastebin.com/y3QDiBc4](http://pastebin.com/y3QDiBc4)
rtorrent.rc: [http://pastebin.com/i50UpcpM](http://pastebin.com/i50UpcpM)
 
Will look in to it more later today, but would appreciate some input.
 
I've recently gone the whole hog of compiling/installing/persuading to work rutorrent & rtorrent so some of this is still fresh in my memory. I'll have a look at your code and make some corrections I've spotted. I can't do much with the apache side as I'm using lighthttpd on my install.
 
I noticed that you are using ruTorrent 2.8. Is there any particular reason for this? I'm using 3.1 from SVN as it is now stable but does make changes to the folder structure.
 
Cheers,
 
Lerxst2112

---

### Post by Fredrik_b on 2010-08-10
Updated install.sh a bit new file: [http://pastebin.com/SKR2GXug](http://pastebin.com/SKR2GXug)

Lerxst2112: all you updates went missing sins a new link is created when you edit (learnd that just now)

If you could have a look again that would be nice.

---

### Post by Fredrik_b on 2010-08-11
I now have a script that seems to work for 9.10 will update and try to get it to work on 10.04 jeos and make a virtual appliance of it.

Will post it this evening CET

Ps, anyone know of a good free permanent place where i can put the files and have http/wget access?

---

### Post by devinw on 2010-09-01
Sorry I have been absent from the forums. It's cool to see that this hasn't completely died. If anyone is interested in collaborating on GitHub to get the script in a functional state, create a project page, etc. please shoot me a PM.

---

### Post by Japsser on 2010-09-08
I've found it impossible to install rtorrent+wtorrent using lighttpd on ubuntu 10.04 server.

 I've got it running now using only apache2 though, after checking a bunch of tutorials and finally configuring it with apache as described here:

[http://www.transdroid.org/download/using-rtorrent-on-ubuntu/](http://www.transdroid.org/download/using-rtorrent-on-ubuntu/)

---

### Post by bustaqigdh8 on 2011-01-12
> ** said:**
> Anybody can answer it? I have the issue [[COLOR=#000000]which[/COLOR]](http://www.violetin.net/es/sales/wonderful-7-star-replica-hublot-big-bang-lefty-all.html) is similar to what you have faced.

---

### Post by testme26 on 2012-07-01
svn://wtorrent-project.org/repos/trunk/wtorrent/  don't work. What is new svn of wtorrent?

---

### Post by oldos2er on 2012-07-01
"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

