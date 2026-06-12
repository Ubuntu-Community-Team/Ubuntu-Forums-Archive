---
title: "No Tor in Jaunty?"
date: 2009-04-25
forum: General Help
---

### Post by whitefort on 2009-04-25
Hi - sorry if this is a dumb question.

In previous Ubuntus, I've always installed tor without any problems.

This time around, it's not in the repositories, and trying to apt-get it
gives me the message:

"Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

I even followed another tutorial telling me how to build it from source (which is scary for me!), but the process needed another package, and when I tried to install THAT, I got the exact same message.

Is there a way to 'do' tor in Jaunty at present, or is the problem that some packages are still catching up with the new Ubuntu?

Any help would be mucho appreciated!

---

### Post by oldos2er on 2009-04-25
Do you have all repositories enabled?

---

### Post by whitefort on 2009-04-25
Hi,

Yes, everything that's in Synaptic 'out of the box' is enabled.  I haven't added any other repositories - I'm pretty sure I haven't had to do that in the past.

My googling found a few things that sounded a bit like a disagreement between the Ubuntu people and the Tor people, and I'm wondering if that's why Tor seems to have vanished... but I might be barking up the wrong tree.  It's possible that I'm just being stupid, and forgetting something that I normally do as part of a new Ubuntu setup.

---

### Post by paradigm2 on 2009-04-25
> **whitefort said:**
> Hi - sorry if this is a dumb question.

In previous Ubuntus, I've always installed tor without any problems.

This time around, it's not in the repositories, and trying to apt-get it
gives me the message:

"Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

I even followed another tutorial telling me how to build it from source (which is scary for me!), but the process needed another package, and when I tried to install THAT, I got the exact same message.

Is there a way to 'do' tor in Jaunty at present, or is the problem that some packages are still catching up with the new Ubuntu?

Any help would be mucho appreciated!

I have Jaunty and Tor running just fine.  I did install when it was in beta though.

It should be in there. Go to the Synaptic Package Manager and do a search for tor (it is simply called "tor").  Try to install.  If it does not work, give us the exact error message please.

---

### Post by paradigm2 on 2009-04-25
Hmm In investigating this matter a bit,

I found:

[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

This gives their own respository and they state:

> 
Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes.


Currently in synaptic I see that the version in the default Ubuntu repository is Tor 0.2.0.34.  However, the stable version listed on the website still appears to be 2.0.34.

It looks like it (the default Ubunutu) is updated now., however, it must have been out of date in the past.  I agree with the tor developers that tor is the type of software which must be timely updated to the latest stable absent very good reasons not to do so.

---

### Post by paradigm2 on 2009-04-25
More information on the "dispute" :

[https://bugs.launchpad.net/ubuntu/intrepid/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/intrepid/+source/tor/+bug/328442)

---

### Post by whitefort on 2009-04-25
> **paradigm2 said:**
> Go to the Synaptic Package Manager and do a search for tor (it is simply called "tor"). 


That was the first thing I tried.  It's not there, in a freshly downloaded and installed 'official' Jaunty.

If anybody downloaded Jaunty when it was released, and has tor in Synaptic, I'd be grateful if they'd let me know.

---

### Post by codeseer on 2009-04-25
> **paradigm2 said:**
> More information on the "dispute" :

[https://bugs.launchpad.net/ubuntu/intrepid/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/intrepid/+source/tor/+bug/328442)

Humm...

---

### Post by stlsaint on 2009-04-25
i too have had a problem installing torK in jaunty...after its all said and done...synaptics updated and tork intalled i still get a error saying that jaunty cannot find my tor insallation!!!:confused:

---

### Post by McQuaid on 2009-04-26
It's because it's not there:

[http://packages.ubuntu.com/search?searchon=names&keywords=tor](http://packages.ubuntu.com/search?searchon=names&keywords=tor)

As to why? I don't know.

---

### Post by darkstaar on 2009-04-26
I'm under the impression that Tor 2.0.34 should be out for 9.04 soon but you can certainly use 2.0.31-1 in the meantime.

Grab the **i386** .deb (meant for 8.10) at any one of the mirrors listed at:
[http://packages.ubuntu.com/intrepid/i386/tor/download]("http://packages.ubuntu.com/intrepid/i386/tor/download")

...or the **amd64** .deb at:
[http://packages.ubuntu.com/intrepid/amd64/tor/download]("http://packages.ubuntu.com/intrepid/amd64/tor/download")

---

### Post by whitefort on 2009-04-26
Darkstaar,

Many thanks for that helpful post.  I've got tor again!

---

### Post by grendel_khan on 2009-04-29
> **darkstaar said:**
> I'm under the impression that Tor 2.0.34 should be out for 9.04 soon but you can certainly use 2.0.31-1 in the meantime.

Grab the **i386** .deb (meant for 8.10) at any one of the mirrors listed at:
[http://packages.ubuntu.com/intrepid/i386/tor/download]("http://packages.ubuntu.com/intrepid/i386/tor/download")

...or the **amd64** .deb at:
[http://packages.ubuntu.com/intrepid/amd64/tor/download]("http://packages.ubuntu.com/intrepid/amd64/tor/download")

That may be a bad idea, if the package doesn't get included in Jaunty. (From the current status of the bug report, it's not obvious exactly what will happen.) Additionally, the version from Intrepid is no longer recommended for use.

```
Apr 29 08:08:39.747 [notice] Tor 0.2.0.31 (r16744) opening new log file.
Apr 29 08:45:09.116 [warn] Please upgrade! This version of Tor (0.2.0.31) is obsolete, according to the directory authorities. Recommended versions are: 0.2.0.33,0.2.0.34,0.2.1.11-alpha,0.2.1.12-alpha,0.2.1.13-alpha,0.2.1.14-rc
```

If you want to run tor, add the upstream repositories ( [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian) ); I'm using the Intrepid version without issue currently; they should come out with a Jaunty one at some point.

---

### Post by aNaRcHiSt on 2009-05-01
Just add

```
deb http://mirror.noreply.org/pub/tor jaunty main
deb-src http://mirror.noreply.org/pub/tor jaunty main

```

to /etc/apt/sources.list

then

apt-get update
apt-get install tor

---

### Post by burntresistor on 2009-09-05
I'm getting these two error messages after I edited the 
file and tried to download


 Failed to fetch [http://mirror.noreply.org/pub/tor/dists/Jaunty/main/binary-amd64/Packages](http://mirror.noreply.org/pub/tor/dists/Jaunty/main/binary-amd64/Packages)  404 Not Found




 tor Package tor is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or is only available from another source

---

### Post by ToshibaLaptoplinux on 2009-09-23
I am also installing tor on Jaunty from [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

I am able to add the repesitory to my sources file but I am having difficulty when it comes to getting the key:

[gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
apt-get update
apt-get install tor tor-geoipdb]

returns

[gpg: WARNING: unsafe ownership on configuration file `/home/****/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error]

Is there something obvious that I am missing? I went ahead and installed tor anyway but am conncerened that it is unsafe.

---

