---
title: "Could not download all repository indexes"
date: 2009-05-22
forum: General Help
---

### Post by desic on 2009-05-22
Hi

I'm running Ubuntu 7.10 Gutsy Gibbon

When going to install a library from synaptic recently I encountered a problem:

```

An error occured

The following details are provided:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/boost/libboost-dev_1.34.1-2ubuntu1.1_i386.deb
  404 Not Found [IP: 91.189.88.46 80]

```

Upon reloading the repositories I get the following:

```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]

```

I click "Close" on the bottom of this and then get:

```

An error occured

The following details are provided:

W: GPG error: http://ppa.launchpad.net gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

```

My internet connection is fine, and I'm using the Ubuntu Main Server for repositories.

I do intend to upgrade to Ubuntu 9 in a few months time, but I need to stay stable right now. I would appreciate any help or suggestions.

Thanks

---

### Post by chriskin on 2009-05-22
it is not a problem of your internet service

you can either use these commands , changing the numbers for the last 8 numbers of your error message
> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
``````
gpg --export --armor 0c713da6 | sudo apt-key add -
```Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa? 

or use the easier method of a script that does it for you :

[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by desic on 2009-05-22
Ok so I went via the script route, it has removed the last error I reported in my original post (Thanks for that chriskin!).

But I still get the same error when trying to get the library, and I still get the "repositories not found" error on reloading the repositories.

---

### Post by chriskin on 2009-05-22
there is always the chance that the servers that host the repositories might be down, and then all you have to do is to wait for the repository owner to fix them - i don't know of any other reason why this error appears

all credit goes to the two users i quoted, all i did was tell you what i found some time ago :)

---

### Post by x33a on 2009-05-22
gutsy was discontinued last month:

[http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml](http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml)

---

### Post by desic on 2009-05-22
> **chriskin said:**
> there is always the chance that the servers that host the repositories might be down, and then all you have to do is to wait for the repository owner to fix them - i don't know of any other reason why this error appears

Ok. The first time I got this problem was yesterday [22/05/09] morning, so I'll be patient and wait a few more days!

Thanks for your help

---

### Post by chriskin on 2009-05-22
> **x33a said:**
> gutsy was discontinued last month:

[http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml](http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml)


true, gutsy is discontinued, why don't you just move to a newer version? 
even if it wasn't discontinued, it is really old :P

---

### Post by desic on 2009-05-22
> **x33a said:**
> gutsy was discontinued last month:

[http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml](http://news.softpedia.com/news/Goodbye-Ubuntu-7-10-107519.shtml)

Ah, so patience won't help me!

Ok I guess I'll just have to wait until I have time to make the move to Ubuntu 9 then.

---

### Post by desic on 2009-05-22
> **chriskin said:**
> true, gutsy if discontinued, why don't you just move to a newer version? 
even if it wasn't discontinued, it is really old :P

Yeah, I'm just in the middle of exams at the minute so I'm short on time.
As soon as I'm out the other side i'll make the upgrade.

---

### Post by chriskin on 2009-05-22
> **desic said:**
> Yeah, I'm just in the middle of exams at the minute so I'm short on time.
As soon as I'm out the other side i'll make the upgrade.
oh, exams are this time of the year over at the uk as well? i finish mine the next week 
and then..Summer Time :) :popcorn::popcorn::popcorn:
[U][B]
edit : to the next post , no reason to fill the whole forum with offtopics - I already overdid it  : good luck to you too :) [/B][/U]

---

### Post by desic on 2009-05-22
Yeah I can't wait :)

Good luck!!

---

