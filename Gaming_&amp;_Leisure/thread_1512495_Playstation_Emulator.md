---
title: "Playstation Emulator?"
date: 2010-06-18
forum: Gaming &amp; Leisure
---

### Post by EvCrock on 2010-06-18
I was wondering if anyone was able to find/download/make work a PS emulator for 10.04 that works.  All the ones I've found recently have seemed to either not or were made for older versions of Ubuntu.  As for owning the system, I own two, actually, but it would be great to be able to play some of the games I own on the go.

Anyone got either a link or the time to explain to me how it all works?  I've heard of PSCX (sp?) but haven't found it for 10.04.

---

### Post by Grishka on 2010-06-18
> **EvCrock said:**
> Anyone got either a link or the time to explain to me how it all works?  I've heard of PSCX (sp?) but haven't found it for 10.04.

[here](http://www.playdeb.net/updates/ubuntu/10.04/?q=pcsxr).

---

### Post by Chame_Wizard on 2010-06-18
> **Grishka said:**
> [here](http://www.playdeb.net/updates/ubuntu/10.04/?q=pcsxr).

Going to need it soon.

---

### Post by Rainstride on 2010-06-18
[http://pcsxr.codeplex.com/releases/view/37759](http://pcsxr.codeplex.com/releases/view/37759)

---

### Post by EvCrock on 2010-06-18
alright, now I've downloaded pcsxr, and now all I need to know is what are these BIOS things about, and how to extract files marked .7z

[http://www.7-zip.org/](http://www.7-zip.org/)

Anyone know if this program will work for Linux as well as Windows?

---

### Post by hikaricore on 2010-06-18
> **EvCrock said:**
> alright, now I've downloaded pcsxr, and now all I need to know is what are these BIOS things about, and how to extract files marked .7z

[http://www.7-zip.org/](http://www.7-zip.org/)

Anyone know if this program will work for Linux as well as Windows?

In the future do not discuss system bios and other grey legal areas here.

```
sudo apt-get install 7z
```

---

### Post by EvCrock on 2010-06-18
```
sudo apt-get install 7z
```[/QUOTE]

Didn't work, for whatever reason?

and woops about the BIOS thing!  Like I said, I own two of the darn things, so I don't really feel like I'm breaking the law.

---

### Post by hikaricore on 2010-06-18
Mind posting the terminal output?

"Didn't work for whatever reason" tells us nothing.

---

### Post by Tombgeek on 2010-06-19
> **EvCrock said:**
> ```
sudo apt-get install 7z
```

Didn't work, for whatever reason?

and woops about the BIOS thing!  Like I said, I own two of the darn things, so I don't really feel like I'm breaking the law.[/QUOTE]

Just use the Software Centre.

---

### Post by imperialyell on 2010-06-19
I get this message when trying the download on the  link from Grishka:

Failed to fetch [http://packages.dfreer.org/dists/gutsy/Release.gpg](http://packages.dfreer.org/dists/gutsy/Release.gpg)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2](http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/Release.gpg](http://packages.dfreer.org/dists/feisty/Release.gpg)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/i18n/Translation-en_US.bz2](http://packages.dfreer.org/dists/feisty/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

I also could not find it on the software center as someone else suggested? I am an absolute linux noob so please be kind =)

---

### Post by hikaricore on 2010-06-19
Getdeb has been a bit flakey lately and it looks like their mirrors aren't up to par.
Here's a ppa with pcsxr: [https://launchpad.net/~falk-t-j/+archive/games](https://launchpad.net/~falk-t-j/+archive/games)

---

### Post by Tombgeek on 2010-06-20
> **imperialyell said:**
> 

I also could not find it on the software center as someone else suggested? I am an absolute linux noob so please be kind =)

It is in the Accessories category.

---

### Post by EvCrock on 2010-06-21
Wow, that all worked really well!!  Thank you guys for your patience.  This isn't even really an issue, because I'll probably keep the audio off, but is there any way to make the audio not quite so.... choppy?  It might just be FF7, I'll have to try some more.

---

### Post by dfreer on 2010-06-21
> **imperialyell said:**
> I get this message when trying the download on the  link from Grishka:

Failed to fetch [http://packages.dfreer.org/dists/gutsy/Release.gpg](http://packages.dfreer.org/dists/gutsy/Release.gpg)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2](http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/Release.gpg](http://packages.dfreer.org/dists/feisty/Release.gpg)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/i18n/Translation-en_US.bz2](http://packages.dfreer.org/dists/feisty/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

I also could not find it on the software center as someone else suggested? I am an absolute linux noob so please be kind =)

That is my old repository that is currently offline. Sorry about that :/ If you continue to see these errors when updating your package manager, you'll want to remove the relevant lines in your /etc/apt/sources.list

---

### Post by kirijin on 2011-01-15
maybe too late, but to extract .7z type:

sudo apt-get install p7z-full

and for .rar:

sudo apt-get install p7z-rar

---

