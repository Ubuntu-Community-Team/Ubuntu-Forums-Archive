---
title: "Running clamav (tk)"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-24
Hello,
I figured out how to install clamav (tk), and I cannot get the updates as I need to be root?  So, I typed in:  sudo freshclam -v and it does not work.  It says: 

WARNING: Incremental update failed, trying to download daily.cvd
Retrieving [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
Ignoring mirror 65.120.238.5 (too often connections with outdated version)
Ignoring mirror 128.121.60.235 (too often connections with outdated version)
Ignoring mirror 194.47.250.218 (too often connections with outdated version)
Ignoring mirror 205.139.192.213 (too often connections with outdated version)
Ignoring mirror 206.154.203.13 (too often connections with outdated version)
Ignoring mirror 208.67.80.27 (too often connections with outdated version)
Ignoring mirror 209.8.40.140 (too often connections with outdated version)
Ignoring mirror 64.142.100.50 (too often connections with outdated version)
Ignoring mirror 64.246.44.108 (too often connections with outdated version)
ERROR: Can't download daily.cvd from database.clamav.net
Restoring incremental directory daily.inc from backup
Giving up on database.clamav.net...
Update failed. Your network may be down or none of the mirrors listed in freshclam.conf is working. Check [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem) for possible reasons.

I am a newbie.  Thanks.

---

### Post by delacr_a on 2007-08-24
su -c 'freshclam -v' 
(and then the password).

---

### Post by poe503 on 2007-08-24
*sudo clamtk* will unlock the update function in clamtk.  I'm not sure the latest version will update for you.  It doesn't for me.  They update clamav and then clamtk doesn't work, eventually they update clamtk to work properly and then they update clamav and the cycle starts again, ad nauseum.

---

### Post by arvadawest on 2007-08-24
> **delacr_a said:**
> su -c 'freshclam -v' 
(and then the password).

Hi, thanks for this.  But it is giving me an authentication failure, yet I am logged on as a user who has su access.  I understand that ubuntu doesn't allow su access just sudo.  What do I need to do?  Thanks for your help.  -aw

---

### Post by saru411 on 2007-08-24
i believe you are trying to do this. type this first then do your installation/command in terminal

> sudo -i

notice it chances your name to root@arvadawest...

---

### Post by arvadawest on 2007-08-24
> **saru411 said:**
> i believe you are trying to do this. type this first then do your installation/command in terminal



notice it chances your name to root@arvadawest...

Hi Saru!  Thanks.  I did type sudo -i and it did take my password this time.  Then I ran:  su -c 'freshclam -v' and this is what I got--

Retrieving [http://database.clamav.net/daily-4036.cdiff](http://database.clamav.net/daily-4036.cdiff)
Ignoring mirror 129.64.99.170 (too often connections with outdated version)
Ignoring mirror 199.239.233.95 (too often connections with outdated version)
Ignoring mirror 206.154.202.13 (too often connections with outdated version)
Ignoring mirror 206.154.203.213 (too often connections with outdated version)
Ignoring mirror 209.170.150.7 (too often connections with outdated version)
Ignoring mirror 216.24.174.245 (too often connections with outdated version)
Ignoring mirror 64.186.240.114 (too often connections with outdated version)
Ignoring mirror 65.110.48.11 (too often connections with outdated version)
Ignoring mirror 66.111.55.10 (too often connections with outdated version)
ERROR: getpatch: Can't download daily-4036.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd

---

### Post by ArrantSquid on 2007-08-27
I had a similar problem recently. I wrote a post on [my site]("http://lotekbrigade.doesntexist.com/2007/08/27/clam-av/") about how to go about fixing it. Here's the gist of what I wrote there:

add &#8220;deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free&#8221; to your /etc/apt/sources.list . Now if you run &#8220;sudo apt-get update&#8221; now, you&#8217;ll get a gpg error. No worries right. Just grab the key from the[ volatile site]("http://www.debian.org/volatile/"). Except when you grab the etch-volatile.asc and attempt to add it with &#8220;sudo apt-key add etch-volatile.asc&#8221; it doesn&#8217;t work. Well here&#8217;s the fix. Simply change the file extension of .asc to .gpg and run &#8220;sudo apt-key add etch-volatile.gpg&#8220;. Now you can run &#8220;apt-get update&#8221; and then run &#8220;apt-get install clamav clamtk&#8220;.

HTH.

[edit]I'd suggest removing the previous installs just for clarity before you add this[/edit]

---

