---
title: "CGWD/Gcompizthemer replacement woes."
date: 2006-08-06
forum: Desktop Environments
---

### Post by Sanjay on 2006-08-06
Having recently ran an 'apt-get dist-upgrade' synaptic saw fit to uninstall gcompizthemer & gcompizthemer-themes and replace them with the new version of CGWD, which supposedly now encompasses Gcompizthemer.

The problem i have is that i was using one of the custom Gcompizthemer themes. Now that CGWD has taken over all that has dissapeared...and i liked my fancy window decorations :oops: :sad: . Now i only have a standard looking window decoration. And if i run 'gcompizthemer' i get the old looking gcompizthemer, just no themes. I presume what i get upon running gcompizthemer is the CGWD integrated new gcompizthemer?

So i am looking for a way of either using the previous theme with the new CGWD, which i'm not sure is possible as i'm sure i heard quinn himself say that they wouldnt be. OR: A way to uninstall the newer CGWD, and install the older ones along with Gcompizthemer + Themes.

Many thanks for any help in advance. Sanjay

---

### Post by yossman on 2006-08-06
i've been fighting with cgwd and gcompizthemer for a couple days now.  i'm getting a bizarre version conflict i was not getting last week with cgwd and gcompizthemer.  synaptic gives me some cryptic messages about dependencies not met, and then just dies and doesn't install anything.  

we have a desktop running latest nvidia + Xgl + compiz.  the desktop has this mysterious 0.9 version of cgwd; the latest available version i can see in synaptic with the laptop is 0.40.  the desktop has working cgwd theme editor with themes, the whole nine yards, it works great.  we're trying to get the laptop up to the same level as the desktop.

how did the desktop get cgwd 0.9 last week, when the latest version we can see this week is 0.40?  why is 0.9 no longer available?  i saw the latest version for cgwd changed from 0.38 to 0.40 in the last 18 hours -- did we go through some sort of timewarp into the past this weekend compared to last, and so we have to wait now until we catch up to v0.9 again? ;-)

trying from the terminal instead of synaptic:

```

root@laptop:/etc/apt# apt-get install gcompizthemer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcompizthemer: Depends: cgwd (>= 0.9) but it is not going to be installed
E: Broken packages

```

the crazy thing is, using the synaptic manager on the desktop, we can see the latest downloadable version appears to be 0.40, but it says 0.9 is installed.  wtf?

here's the condensed list of repositories we have in the laptop's sources.list file, which has now been matched with the desktop's sources.list file exactly:

```

deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

there may be a couple of repeats, i'm still wrapping my head around why there's so many channel choices in the synaptic repositories editor.

any hints as to how this got so broken? ;)  should i just be patient and wait for ALL the version numbers to increment on the packages to they'll be happy and install again?

thanks for any help.

yossman

EDIT: i got it working, see this page in one of the other xgl threads:

[http://www.ubuntuforums.org/showthread.php?t=148351&page=37]("http://www.ubuntuforums.org/showthread.php?t=148351&page=37")

---

### Post by Saibot on 2006-08-06
If you haven't already - use Synaptic to get cgwd-themes.

---

### Post by Sanjay on 2006-08-06
> **Saibot said:**
> If you haven't already - use Synaptic to get cgwd-themes.

Thankyou! Worked perfectly Loads of kool new themes too! :D :D :D 
I have to say, Ubuntu community is awesome, one of the main reasons why i ditched windoze.

Many many Thanks Sanjay.

---

