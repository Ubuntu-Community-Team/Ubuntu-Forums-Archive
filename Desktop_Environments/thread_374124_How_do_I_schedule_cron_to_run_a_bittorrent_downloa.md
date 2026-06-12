---
title: "How do I schedule cron to run a bittorrent download?"
date: 2007-03-02
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-03-02
Hi guys,
Im trying to figure out how to schedule a task in Cron.
Im on an ADSL account that counts my traffic between the hours of 16:00 - 00:00 weekdays and all weekends. 
I want to schedule a bittorrent download to start at 00:05 and finish at 17:55 weekdays. Im not at all sure how to use crontab, Ive had a look but Im a bit wary of messing things up. 

I tried adding the torrent file to the system startup, but it didnt work, so I guess cron is the way to go. Can some wise soul help me?
Steve

---

### Post by scxtt on 2007-03-02
i use "btdownloadcurses" for CLI bittorrent downloads ... you could do (in /etc/crontab) as root:

```
[font=courier]05 00    * * 1,2,3,4,5 <username>   /usr/bin/btdownloadcurses <path to torrent file> &
55 17    * * 1,2,3,4,5 <username>   /usr/bin/killall btdownloadcurses[/font]
```

or use "crontab -e" as the user you want to run this as and add similar entries ...

AFAIK, "vixiecron" should be installed on 99% of ubuntu systems ... make sure it's running w/ "ps -ef | grep cron" ...

---

### Post by samir85 on 2007-03-02
It would be much easier, if you use a bittorrent client, which supports scheduling. For example Azureus has a very neat plugin for that. :D

---

### Post by scxtt on 2007-03-02
> **samir85 said:**
> It would be much easier, if you use a bittorrent client, which supports scheduling. For example Azureus has a very neat plugin for that. :Dthat's quite a bit of overhead (esp. as far as Azureus is concerned) compared to a simple cron task ... to each his own tho :D

---

### Post by mister_p_1998 on 2007-03-02
> **scxtt said:**
> i use "btdownloadcurses" for CLI bittorrent downloads ... you could do (in /etc/crontab) as root:

```
[font=courier]05 00    * * 1,2,3,4,5 <username>   /usr/bin/btdownloadcurses <path to torrent file> &
55 17    * * 1,2,3,4,5 <username>   /usr/bin/killall btdownloadcurses[/font]
```

or use "crontab -e" as the user you want to run this as and add similar entries ...

AFAIK, "vixiecron" should be installed on 99% of ubuntu systems ... make sure it's running w/ "ps -ef | grep cron" ...

Exactly HOW do I enter the start/end time exactly?
is 05 00 five past midnight? why isnt it 00 05?

---

### Post by scxtt on 2007-03-02
you don't see "# m h dom mon dow user  command" at the top of /etc/crontab?  i think that even "crontab -e" gives you a little hint ...

m=minute
h=hour
dom=day of month
dow=day of week
user=user to run as
command=command to run (best to use full path)

---

### Post by mister_p_1998 on 2007-03-03
Ah!
sorry, to be honest, I didnt even look!
thats what 20 years of windows use does to you!
its a shame you cant do it as easy as windows scheduler though, 
although that would probably have security issues would it?
Thanks for your help,
Steve

---

### Post by scxtt on 2007-03-03
i'm sure there are some GUI cron schedulers that "dumb it down" ( no offense to anyone :) ) ... i  think KCron would be one, not sure - i pretty much always just edit /etc/crontab ...

---

### Post by n.a.b.s.t.e.r on 2008-03-13
I had no luck with btdownloadcurses or btdownloadheadless, but ctorrent eventually worked for me in cron.

---

### Post by simon_ives on 2008-07-06
I had the same issue so I'll explain how I got this working.  I use the standard cmd line bittorrent client from the Ubuntu Repos.  Also, I've got this running on my headless file server so you'll have no worries running it on your standard Gnome desktop.  This process is slightly complicated but very worth while :)

To begin with, make sure you have the bittorrent client:
[INDENT]```
sudo apt-get install bittorrent
```[/INDENT]

Now create a folder (directory) in your home folder called something like 'torrents'.
[INDENT]```
username@hostname:~$ mkdir torrents
```[/INDENT]

That's the easy stuff out of the way.  What we will do next is create two bash scripts; one to start your downloads and one to stop your downloads.

Create a new file in your home directory called btdownloadstart.sh
[INDENT]```
username@hostname:~$ nano btdownloadstart.sh
```[/INDENT]

Add the following text and then save and close the file (ctrl+x, y, enter)

[INDENT]```
#!/bin/sh
# Start Downloading Torrent Files!
cd
nohup btlaunchmany /home/simon/torrents/ > torrent.log & 
tail -f torrent.log
```[/INDENT]

Create a new file in your home directory called btdownloadstopt.sh
[INDENT]```
username@hostname:~$ nano btdownloadstop.sh
```[/INDENT]

Add the following text and then save and close the file (ctrl+x, y, enter)

```
[INDENT]#!/bin/bash
# Stop Downloading ALL Torrent Files!
killall btlaunchmany[/INDENT]
```

What the first script will do is to start up the bittorrent client, scan the torrents directory for torrent files, and start as many instances of itself as required to download them.  It will also create a log file in your home folder so you can monitor what's going on.

The second script will stop all instances of the torrent downloads.

So now we need to tell Ubuntu to start downloading at a given time and to stop downloading at a given time.  To start your downloading at 12:05am and stop at 5:55pm on weekdays you need to add an entry to cron.  The easiest way to do this is to create a text file that we'll add the cron entries in and then append this to crontab.  This way you can edit your cron entries in gedit (or something similar) without having to edit within the terminal.

Create a text file in your home directory called cron.txt
[INDENT]```
username@hostname:~$ nano cron.txt
```[/INDENT]

Add the following text and then save and close the file (ctrl+x, y, enter)

```
[INDENT]# Start BitTorrent Download Script
05 0 * * 1-5 sh /home/your_username/bittorrentstart.sh

# Stop ALL BitTorrent Downloads Script
55 17 * * 1-5 sh /home/your_username/bittorrentstop.sh[/INDENT]
```

> Just a note if you want different times for your cron entry.  The cron date format is:
* * * * *
which correspond to:
minute           0-59
hour		 0-23
day of month	 1-31
month	         1-12 (or the month names)
day of week	 0-7 (0 or 7 is Sun, or use the weekday names)

Now we append this to crontab.
[INDENT]```
username@hostname:~$ crontab cron.txt
```[/INDENT]

To check that it was added to crontab enter.
[INDENT]```
username@hostname:~$ crontab -l
```[/INDENT]

You should be presented with your cron entries.

All you need to do now is save all of your torrent entries into your /torrents folder.  Bittorrent will begin downloading them all into their own sub-directories between 12:05am and 5:55pm on weekdays; you no longer need to think about it and you don't need to update cron with the details of each new torrent file.

---

