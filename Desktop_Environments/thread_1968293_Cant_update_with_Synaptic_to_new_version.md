---
title: "Cant update with Synaptic to new version"
date: 2012-04-28
forum: Desktop Environments
---

### Post by tdlam on 2012-04-28
Hi folks...I dont know if this is an error with my system or not. I am running Xubuntu 11.04 and would like to upgrade to the newest release. When I try to have Synaptic Package manger look for updates I get these errors:

GPG error: [http://code.iki.fi](http://code.iki.fi) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BACCFCFB98DB2EDCFailed to fetch [http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

is this because the new version is not yet available for synaptic or is maybe something else going on?

Also, would you say it is safe to update if I can get it working or will it bonk my system?

Thanks in advance for your time and help.

All the best

---

### Post by cortman on 2012-04-28
Hi, it looks like you are missing some security keys for a couple repositories and have entries for repos that no longer exist. These are both correctable, but if I can I would advise you to back up all your data, make a list of programs you want, and do a clean re-installation. You'll probably save yourself a LOT of headaches by doing a fresh installation of 12.04 rather than an upgrade.
If you elect not to do this for whatever reason, we can help you with the GPG and 404 errors.

---

### Post by tdlam on 2012-04-28
I was afraid you would say something like that lol...
you see...it took me days to get this laptop configured to recognise my printer scanner for work...I'm not even sure how the heck I did it at this point. Not sure i want to go through with that again.

maybe I should just stay with this version and be happy.
But if you say the errors are correctable I would welcome any help you may offer...thanks!

---

### Post by cortman on 2012-04-28
We would all be glad, given the machine information, to step you through setting your printer back up again, if you would like. 
With 12.04 you'll have an LTS, and will be supported for 3 years. Your 11.04 will only be supported until 12.10, or October of this year.
While you can continue running 11.04, it's probably in your best interest to upgrade at some point.
I'm sorry to hear that your printer was a challenge, but like was said- given the info, we'll be glad to help.

---

### Post by tdlam on 2012-04-29
You are a nice person and I appreciate your kindness. I have an Epson workforce 520...and it was a ROYAL pain to get it working...and that's no lie...every other Epson was supported but not that one...so I had to REALLY dig to get it working with XSane..
the other bundled scanning prog wouldnt even work with it.
Also getting my windows 7 network shared printer to work was not easy...

I had to manually install SAMBA and dont remember how i got that to work too

Thats bad news about this version not being supported ...does not make me feel comfortable...

---

### Post by cortman on 2012-04-29
It's your choice. Non LTS releases are supported for 18 months. LTS releases of Xubuntu are supported for 3 years, standard Ubuntu LTS is supported for five years.

---

### Post by tdlam on 2012-04-29
Well if you could talk me through how to get rid of those errors...that would be greatly appreciated.
Thanks in advance

---

### Post by cortman on 2012-04-30
Can do!

For the GPG error (no PUBKEY, etc) follow the instructions given [here.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")
To fix the "404 not found" error, you should comment out that repository in sources.list. In a terminal, run

```
gksu gedit /etc/apt/sources.list
```

Find the line that corresponds to the one that gave the error (something about "danial moral...") and put a hash mark (#) at the start of the line. Save and exit.
When these are done, run

```
sudo apt-get update
```

And if you get any errors, post them back between [CODE] tags- Just click the hash mark button in the editing toolbar of your reply to generate code tags.
Good luck!

---

### Post by tdlam on 2012-05-01
well no go I'm afraid to say...I tried fetching the key through the info at the site and I get this in terminal
```
tdlam@tdlam-Inspiron-6000:~$ sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys BACCFCFB98DB2EDC
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.886oV9d0LK --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys BACCFCFB98DB2EDC
usage: gpg [options] [filename]
```

then when I do a sudo apt-get update i get these errors:
```
W: GPG error: http://code.iki.fi stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BACCFCFB98DB2EDC
W: Failed to fetch http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/danielmorales/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I looked in sources list like you said but cant find the lines relating to the 404 errors as well...so am a bit stumped ATM

---

### Post by cortman on 2012-05-01
Hi, for the GPG try this command instead-

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com BACCFCFB98DB2EDC
```

For the 404 repositories, run

```
gksu thunar /etc/apt/sources.list.d/
```

Find and delete any files that include "daniel morales". Close the thunar file manager window.
Now run sudo apt-get update.
Good luck!

---

### Post by tdlam on 2012-05-01
well daniel morales is gone Thank you very much!!! It worked...

however the key is still an issue when I tried what you said in terminal I got this error:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.trQX5bne13 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com BACCFCFB98DB2EDC
gpg: requesting key 98DB2EDC from hkp server keyserver.ubuntu.com
gpgkeys: key BACCFCFB98DB2EDC not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

thanks

---

### Post by cortman on 2012-05-01
It looks as though the other repository is defunct as well, so we'll remove its entry as well. I've shown you the two methods; first run

```
gksu gedit /etc/apt/sources.list
```

If you see a line referring to the iki.fi repository, delete it. If you see nothing there, then go to sources.d and delete it there.
Good luck!

---

### Post by tdlam on 2012-05-02
noyhing in sources.list or sources.d

here's my sources.list readout:

```
  GNU nano 2.2.6                         File: /etc/apt/sources.list                                                Modified  

# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free
```

---

### Post by cortman on 2012-05-02
Hm, copy/paste this code into the terminal and run it

```
sudo rm -r /var/lib/apt/lists/*
```

Then run

```
sudo apt-get update
```

See if that fixes it.

---

### Post by tdlam on 2012-05-02
well something has changed because now after I sudo apt-get update I just get this error about that key again:

```
W: GPG error: http://code.iki.fi stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BACCFCFB98DB2EDC

```

so at least the other errors are gone but this one still hangs on
:(
also. I know we talked about this at the beginning of this post but I would like to try an upgrade. What my plan is to image this current installation with clonezilla after this error is ironed out and BEFORE upgrading. That way if anything bonks I can restore the installation. I cant go for a clean install because I cant get my scanner to work with Xsane no matter what I do again on a clean install. I already tried it and I need it for work. So I figure a full system back up is the safest thing to do Before I try an upgrade. Downlaod manager tells me a new version of UBUNTU is available to upgrade with but is that valid for XUBUNTU?

I just want that LTS but don't want to buy a new printer scanner...

thanks for the advice and help in advance my friend. You are a good person.

---

### Post by cortman on 2012-05-02
Very odd. This may have something to do with your server mirrors. You can change them in Synaptic- go to Settings>Repositories> and select the "Download from" dropdown. Change the server to a different one near you, and try the update again. If the first one doesn't work, try one or two more. 
Sorry it's still giving trouble!

---

### Post by tdlam on 2012-05-02
Sorry my good friend...the error is still there and I have tried 5 different servers...

also...could you please tell me how I would do an upgrade? as I said I am imaging the install prior just in case

Thank you very much and thank you for your time and patience.

---

### Post by cortman on 2012-05-02
That is really strange. Try one last thing: the only non-standard thing I noticed in the sources.list file was the two lines near the end-

```
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb-src http://download.bitdefender.com/repos/deb/ bitdefender non-free
```

Try commenting out these two lines. If it fixes the problem, delete them from sources.list. If the problem persists, uncomment them.

To upgrade, the easiest way is probably through the update manager. It's in Applications>System. Click "Check", and it should say at the top "New Ubuntu release available", etc.
Good luck! Always a pleasure to be of help.

---

### Post by tdlam on 2012-05-03
Ok good news...I upgraded to xubuntu 12.04 and hey boy! those errors are now gone. But when I checked on my printer scanner it wouldn't work. I then stumbled upon the software for it just by chance.

So I wanted to thank you for your kind help. The upgrade seems ok so far. So I am happy...
I would like to post in the UBUNTU forums how and where I got the software for my printer scanner because it was very very difficult to find and a lot of folks out there are suffering like I did who have the same model I do. So if you would be so kind as to tell me what area would be appropriate to post the info i would appreciate it as I would like to help folks out by posting the info.

I am getting a missing drive mounting error on boot up but it doesn't seem to be affecting the install...still it does slow boot up down a bit. 

Would I need to open another post to deal with that error?

anyway thanks again in advance and I await your reply.

All the best.

---

### Post by mips on 2012-05-03
> **tdlam said:**
> 
I would like to post in the UBUNTU forums how and where I got the software for my printer scanner because it was very very difficult to find and a lot of folks out there are suffering like I did who have the same model I do. So if you would be so kind as to tell me what area would be appropriate to post the info i would appreciate it as I would like to help folks out by posting the info.

Here [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

Make the title something like "*Brand* *Model* Printer Driver"

---

### Post by cortman on 2012-05-03
> **tdlam said:**
> Ok good news...I upgraded to xubuntu 12.04 and hey boy! those errors are now gone. But when I checked on my printer scanner it wouldn't work. I then stumbled upon the software for it just by chance.

So I wanted to thank you for your kind help. The upgrade seems ok so far. So I am happy...
I would like to post in the UBUNTU forums how and where I got the software for my printer scanner because it was very very difficult to find and a lot of folks out there are suffering like I did who have the same model I do. So if you would be so kind as to tell me what area would be appropriate to post the info i would appreciate it as I would like to help folks out by posting the info.

I am getting a missing drive mounting error on boot up but it doesn't seem to be affecting the install...still it does slow boot up down a bit. 

Would I need to open another post to deal with that error?

anyway thanks again in advance and I await your reply.

All the best.

Good to know the upgrade went well. The drive mounting error sounds like something that could be fixed in fstab, and it would be a good idea to start another thread on that issue.
The Hardware forum may be a good place for your how-to, as mips pointed out, or you might try the Tutorials and Tips section, which is in the process of being converted to the wiki, but you can still post there.

All the best, and have fun with Xubuntu!

---

### Post by tdlam on 2012-05-03
I posted the prinetr info in the link you gave me thanks. I am opening a new thread for the boot up error.

Thanks again for the help folks. You are all too very nice!

---

