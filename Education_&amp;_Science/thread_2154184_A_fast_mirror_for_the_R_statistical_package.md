---
title: "A fast mirror for the R statistical package"
date: 2013-06-13
forum: Education &amp; Science
---

### Post by rewyllys on 2013-06-13
[SIZE=2]The vendor of my favorite GUI for R, viz., [/SIZE][[SIZE=2]RStudio.com[/SIZE]]("http://RStudio.com")[SIZE=2], has recently started maintaining its own mirror of the Comprehensive R Archive Network (CRAN), the primary server for which is maintained by the [Institute for Statistics and Mathematics]("http://statmath.wu.ac.at/") of [WU (Wirtschaftsuniversität Wien)]("http://www.wu.ac.at/"). [/SIZE] 

 [SIZE=2]The RStudio.com mirror offers an interesting potential advantage for users.  Explaining this is the following excerpt from the RStudio Blog:
  [/SIZE][INDENT][SIZE=2]
"RStudio maintains its own CRAN mirror, [http://cran.rstudio.com](http://cran.rstudio.com). The server itself is a virtual machine run by Amazon’s EC2 service, and it syncs with the main CRAN mirror in Austria once per day. When you contact [http://cran.rstudio.com](http://cran.rstudio.com), however, you’re probably not talking to our CRAN mirror directly. That’s because we use Amazon CloudFront, a content delivery network, which automatically distributes the content to locations all over the world. When you try to download a package from the RStudio cloud mirror, it’ll be retrieved from a local CloudFront cache instead of the CRAN mirror itself. That means that, no matter where you are in the world, the data [don’t] need to travel very far, and so [are] fast to download."[/SIZE]
[/INDENT]
 
[SIZE=2]I've tried out the RStudio.com mirror myself, and I have the impression (admittedly, merely a subjective one) that this mirror is indeed fast.  In my case, I have for some time been using the CRAN mirror maintained by the University of California, [/SIZE][SIZE=2]Berkeley (UCB)[/SIZE][SIZE=2]; its service has been generally good, but occasionally slow[/SIZE][SIZE=2].  (I need to acknowledge that I haven't tried to ascertain whether the occasional slownesses were due to that mirror itself or to network delays.)[/SIZE]
 
 [SIZE=2]In any case, my experience with the RStudio.com mirror has been satisfactory enough that today I changed my desktop's repository for R from UCB to RStudio.com.  In case you would like to try this yourself, here is the APT line to be added to the "Other Software" tab of the " Software Sources" window in the Synaptic Package Manager:

[/SIZE]```
[INDENT][SIZE=2]deb[/SIZE] http://cran.rstudio.com/bin/linux/ubuntu precise/
[/INDENT]

```  [SIZE=2]Of course, if you are not using Precise Pangolin, then replace "precise" by the name of your version of Ubuntu.[/SIZE]

---

### Post by monkeybrain2012 on 2013-06-15
```
[SIZE=2]W: GPG error: [http://cran.rstudio.com](http://cran.rstudio.com) raring/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9[/SIZE]
```

To fix this run

```
gpg --keyserver pgpkeys.mit.edu --recv-key 51716619E084DAB9

gpg -a --export 51716619E084DAB9 | sudo apt-key add -
```

---

### Post by rewyllys on 2013-06-16
Thanks for your help.:D

---

### Post by monkeybrain2012 on 2013-06-16
Hi,

I installed R and a few packages using Michael Rutter's ppa [https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)  After adding this repository something strange has happened. All the packages I have installed under Michael's ppa appear instead under the entry raring/main/([cran.rstudio.com]("http://cran.rstudio.com")) when I searched for them  in synaptic, normally that only happens when a newly added repository has more up to date versions but the version numbers have not changed for these packages and there was no update available. Also the entries for all packages in  raring/main/cran.rstudio.com and raring/universe/(cran.rstudio.com) appear twice in synaptic.

I asked Michael and here is his reply
> 1.  All the packages are built at the RRutter PPA.
2.  The packages found at any CRAN mirror are copies of the packages at the RRutter PPA.
3.  In fact, it is only a subset, so if you want all of the packages at RRutter, just install that.
4.  Even more packages can be found at the c2d4u PPA ([https://launchpad.net/~marutter/+archive/c2d4u]("https://launchpad.net/%7Emarutter/+archive/c2d4u")).

My advice is to install only the RRutter PPA and the c2d4u PPA.  The  only reason to use a CRAN mirror in /etc/apt/sources.list is if you want  to use an older version of R.

I have since removed the rstudio repository from my sources and everything is now back to normal.

Hope this will help if someone experiences something like that in the future.

---

### Post by rewyllys on 2013-06-17
> **monkeybrain2012 said:**
> . . . . Hope this will help if someone experiences something like that in the future.
   Thanks again, MonkeyBrain.
 
 From looking at Michael Rutter's RutterR Webpage, I get the impression that it's an interesting source of R packages, provided that one is willing to accept the risks associated with what Mr. Rutter styles as “unsupported packages from this untrusted PPA”.

---

### Post by monkeybrain2012 on 2013-06-17
> **rewyllys said:**
>  I get the impression that it's an interesting source of R packages, provided that one is willing to accept the risks associated with what Mr. Rutter styles as “unsupported packages from this untrusted PPA”.
Never mind that, it is a standard disclaimer on launchpad's ppas, "untrusted" just means that Canonical is not responsible for maintaining it. There is no risk whatsoever.

---

### Post by rewyllys on 2013-07-12
@MonkeyBrain2012,

It being the case that I'm both stubborn and slow, it's taken me the past three weeks to come round to your suggestions, but I've now done so.

I've removed the RStudio mirror of the CRAN Website from my desktop and replaced it by Michael Rutter's PPA.

Thank you again for your help and suggestions.

---

### Post by RichardET on 2013-08-18
I know i came to this thread late in the game, but I prefer installing packages directly from the terminal window.  If one mirror is slow, pick another.

---

### Post by rewyllys on 2013-08-18
> **RichardET said:**
> I know i came to this thread late in the game, but I prefer installing packages directly from the terminal window.  If one mirror is slow, pick another.
@RichardET: À chacun son goût.

---

