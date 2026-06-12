---
title: "Problems installing BitTorrent 4.1.6"
date: 2005-10-22
forum: Desktop Environments
---

### Post by thumbsoup on 2005-10-22
Prior to install I used Synaptic to remove BitTornado and Azureus from my computer (Ubuntu 5.10 on AMD Athlon).   I was having problems with Azureus not connecting sometimes.

I downloaded BitTorrent 4.1.6 for Debian, Python 2.4 version.  Install seemed to go okay:

sudo dpkg -i bittorrent-4.1.6.linux_i686-2_all_python2.4.deb


But I don't know how to start the program.  I use Firefox 1.07 as my browser, and clicking on torrents does not launch BitTorrent.  There is no MIME application/x-torrent file association in Firefox Preferences, which I think should be there, right? I tried googling for instructions on how to manually set the MIME type in Firefox, but didn't find anything.  I restarted the browser a couple times, but no luck.

I have tried installing BitTorrent again, and again seemed to go okay but it doesn't work.

Any ideas on what is going on here?

I would like to give this torrent client a try before moving on.

Thanks.

---

### Post by bored2k on 2005-10-22
1. You want to download the .tar.gz source package.
2. ```
sudo apt-get install python-wxgtk2.6
```
3. ```
sudo apt-get install libwxgtk2.6-0
```
4. Extract the .tar.gz package and create a shortcut to bittorrent.py (using the menu editor) or run it from a terminal (python bittorrent.py)

How to add that to Firefox? When prompted, point Firefox to the bittorrent.py.

---

### Post by landotter on 2005-10-22
Any reason you can't use the native Gnome bittorrent client? It's resource light and I've never had it bork a download.

---

### Post by bored2k on 2005-10-22
BT Official is even lighter. More updated. DHT support. Much better GUI. Queue manager, et al.

---

### Post by thumbsoup on 2005-10-22
Thanks for all the help.  I will try installing from the .tar.gz now, and fall back on Gnome client if I can't get it to work.

Cheers!

---

### Post by thumbsoup on 2005-10-22
Installing from the source worked like a charm.  BitTorrent 4.1.6 works, including the file association for torrents. 

Thanks,
Thumbsoup

---

### Post by stoeptegel on 2005-10-25
Slightly offtopic:
This DHT support in the new beta, is that configurable to disable in options?

---

### Post by bored2k on 2005-10-25
No.

---

### Post by stoeptegel on 2005-10-25
Bummer, that might got me using 4.1.x

---

### Post by bionnaki on 2005-10-28
just installed.
I really like this client.

---

### Post by Cr4z33 on 2005-11-01
[quote=bored2k]1. You want to download the .tar.gz source package.
2. ```
sudo apt-get install python-wxgtk2.6
``` 3. ```
sudo apt-get install libwxgtk2.6-0
```[/quote]
For both commands I get an 'obsolete package blah blah' error.
BTW do I have to add extra repositories to my sources.list? Are they already out for Ubuntu 5.10?

---

### Post by bored2k on 2005-11-01
[QUOTE=Cr4z33]For both commands I get an 'obsolete package blah blah' error.
BTW do I have to add extra repositories to my sources.list? Are they already out for Ubuntu 5.10?[/QUOTE]
```
sudo nano /etc/apt/sources.list
``````


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

``````
sudo apt-get update
```

---

### Post by pickarooney on 2005-11-01
Anyone got a direct link to the source tarball? I can only see Windows versions on the BitTorrent homepage (possibly because I'm on a Windows machine at the moment).
Also, does it need to be compiled or simply extracted? Where is a good place to extract it?

---

### Post by stoeptegel on 2005-11-01
[http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125)
AFAIK there is no compiling needed as it comes with his own 'python setup.py' installation. Any temp directory will do, most of the time i use /home/user/.used.soft/appname myself where i keep the tarballs in ~/.used.soft.

---

### Post by pickarooney on 2005-11-01
<embarassing question>
Ok, I installed it, but I can't find the name of the runnable file.
Actually, this happens a lot with me and linux, I install something and then have no idea what the executable is called. Is this common or is there some easy way of knowing?
</embarassing question>

---

### Post by wjp.reg on 2005-11-01
[QUOTE=pickarooney]<embarassing question>
Ok, I installed it, but I can't find the name of the runnable file.
Actually, this happens a lot with me and linux, I install something and then have no idea what the executable is called. Is this common or is there some easy way of knowing?
</embarassing question>[/QUOTE

bored2k suggested a way to put it in the menu using the gnome menu editor on the first page of this thread.

the menu editor is under Applications | System Tools; cruise down the left panel to Internet, and on the right side, make a new entry, browsing down to /user/bin and select bittorrent.py (you won't see the (.py extension).

hope this helps

---

### Post by pickarooney on 2005-11-01
cheers :) My embarassment is complete by the discovery that in order to run the bittorrent client I had to execute the arcane command of [b]bittorrent] :D
Now... I started a torrent, opened a second one, and it's queued instead of downloading simultaneously (greedy, moi?) Can't find an option in the settings of 4.1.6 Beta

And how to make opera my default browser in gnome... :) SMEG is a bit rubbish, no?

---

### Post by wjp.reg on 2005-11-01
[QUOTE=pickarooney]cheers :) My embarassment is complete by the discovery that in order to run the bittorrent client I had to execute the arcane command of [b]bittorrent] :D
Now... I started a torrent, opened a second one, and it's queued instead of downloading simultaneously (greedy, moi?) Can't find an option in the settings of 4.1.6 Beta

And how to make opera my default browser in gnome... :) SMEG is a bit rubbish, no?[/QUOTE]

lol, I'm afraid SMEG is all we got :rolleyes:

To change the default browser gto to System | Preferences | Preferred Apps; hope you like this one better ;)

---

### Post by Cr4z33 on 2005-11-02
[quote=bored2k]```
sudo nano /etc/apt/sources.list
``````


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

``````
sudo apt-get update
```[/quote]
Thanks it worked great!

---

### Post by dezier on 2005-11-25
I have followed the instructions above, but i get an error when trying to execute the package. My terminal only speaks Swedish, but i will try to translate... :)

```

andreas@dezier:~$ sudo dpkg -i bittorrent-4.2.0.linux_i686-2_all_python2.4.deb
(Reading database ... 81590 directories and files installed.)
Unpack bittorrent-4.2.0.linux (from bittorrent-4.2.0.linux_i686-2_all_python2.4.deb) ...
dpkg: error in managing of bittorrent-4.2.0.linux_i686-2_all_python2.4.deb (--install):
 try to write over "/usr/lib/python2.4/site-packages/BitTorrent/DownloaderFeedback.py" which also is in the package bittorrent
dpkg-deb: subprocess paste killed by signal (Brooken pipe)
Error in managing:
 bittorrent-4.2.0.linux_i686-2_all_python2.4.deb

```

Any clues of what may be wrong?

---

### Post by ferox on 2005-12-01
[QUOTE=dezier]I have followed the instructions above, but i get an error when trying to execute the package. My terminal only speaks Swedish, but i will try to translate... :)

```

andreas@dezier:~$ sudo dpkg -i bittorrent-4.2.0.linux_i686-2_all_python2.4.deb
(Reading database ... 81590 directories and files installed.)
Unpack bittorrent-4.2.0.linux (from bittorrent-4.2.0.linux_i686-2_all_python2.4.deb) ...
dpkg: error in managing of bittorrent-4.2.0.linux_i686-2_all_python2.4.deb (--install):
 try to write over "/usr/lib/python2.4/site-packages/BitTorrent/DownloaderFeedback.py" which also is in the package bittorrent
dpkg-deb: subprocess paste killed by signal (Brooken pipe)
Error in managing:
 bittorrent-4.2.0.linux_i686-2_all_python2.4.deb

```

Any clues of what may be wrong?[/QUOTE]

Download the 2.3 python version instead.
bittorrent-4.2.0.linux_i686-2_all_**python2.3**.deb

---

### Post by dezier on 2005-12-03
Thanks, now the package seems to install correctly. But when i write "bittorrent" in the terminal it says:

```

andreas@dezier:~$ bittorrent
Traceback (most recent call last):
  File "/usr/bin/bittorrent", line 17, in ?
    from BitTorrent.platform import install_translation
ImportError: No module named platform

```

And this gives:

```

andreas@dezier:~$ python bittorrent
python: can't open file 'bittorrent': [Errno 2] No such file or directory


```

"python bittorrent.py" gives the same as above.

---

### Post by Mosey on 2005-12-23
I have the same issue as the above poster...

Was this ever resolved?

---

### Post by ravpaul on 2006-05-15
Hi guys new so do not know what you mean when you say "4. Extract the .tar.gz package and create a shortcut to bittorrent.py (using the menu editor) or run it from a terminal (python bittorrent.py)"

I am having same problem where I cannot install bittorrent but as I am starting my Linux experience from scratch some of the basics seem like technical jargon. So if you could could you please explain how to do the above.

Thanks

---

