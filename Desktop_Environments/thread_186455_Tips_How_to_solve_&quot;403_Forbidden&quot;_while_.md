---
title: "Tips: How to solve &quot;403 Forbidden&quot; while apt-get update"
date: 2006-06-02
forum: Desktop Environments
---

### Post by swamytk on 2006-06-02
When I run apt-get update, I was thrown with "403 Forbidden [IP: xx.xx.xx.xx 80]" message. It is due to HTTP stream related restriction by the corporate firewall. To solve this issue, I changed all http repositories with ftp repository in /etc/apt/sources.lst (command in vi is :1,$s/http/ftp/g). Then it worked like charm.

---

### Post by Mart on 2006-06-12
I followed this example as well.  Instead of changing /etc/apt/sources.list I went through

System > Administration > Software Properties > (enter password) > Select Repository on left side > Choose Edit > Replace http:// with ftp://  > OK > Close > Reload.

I did this for each of the repositories I had listed and everything worked properly.


Is this a common problem?  If I browse to the repository in firefox I have no problem but I can't see it in the software update manager.

Nothing is blocked going out, and there is no proxy involved.

Thanks

---

### Post by MTZeon on 2006-06-18
I'm also having problems getting the repositories to work with http... is there a problem with apt-get ?

---

### Post by hawkbane on 2006-06-18
This solved my problems perfectly!  Many thanx!

---

### Post by Doughsay on 2006-06-18
[QUOTE=swamytk]It is due to HTTP stream related restriction by the corporate firewall.[/QUOTE]

I'm not quite sure what you mean by this.  I have a very similar problem that I have posted about, and am getting no answers. [My other post.]("http://ubuntuforums.org/showthread.php?t=191039")

My problem is not with the official repos, therefore I can't use ftp instead of http because the repo in question doesn't have an ftp server set up.  But even so, this "corporate firewall" explanation doesn't make sense in my case.  I have two computers running dapper, both on the same connection, both behind the same switch/same router/same modem.  One will update perfectly with this repo and the other will not.  Therefore, the problem MUST be on my end.  And I have no firewall problems obviously because one of them works.

Apart from this one solution, I see many people asking about this same problem and not getting any good answers.  What's going on here?  Doesn't anyone have a clue at all as to what's going on here?

---

### Post by MTZeon on 2006-06-19
Replacing the http/ftp did resolve the problem, but as Doughsay mentioned, if there aren't any ftp set up for the repository? :( Weird thing is, on Breazy, I don't have any problems updating via HTTP :\ I'll see if it is somewhat related to my router or the language selected for the repositories!

---

### Post by mega on 2006-06-21
This does not fix it for me

with drake I get 403 errors
with another box right next to it I dont
do not get this error with another box next to it running breezy

anyone have any idea what the real cause for this error is?

---

### Post by clparker on 2006-06-21
Yeah, What gives? It wasn't doing this last night? Only thing that i can think of that's causing this is the new ethernet card?

---

### Post by elusivespoon on 2006-06-21
I just started getting the 403 errors today and I made no changes to my system. If I change from http to ftp I get one of two new errors:
"Unable to fetch file, server said 'Failed to open file."
 or
"The server refused the connection and said: OOPS: vsftpd: cannot locate user specified in 'ftp_username':ftp"

---

### Post by schlupper on 2006-06-21
My Dapper install was updating fine, and now I get this "403 Forbidden" error.  I tried changing all the http references to ftp in the /etc/apt/sources.list file, but then I get the following:
Get:1 [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) dapper/main tex-common 0.15build1 [241kB]
Err [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) dapper/main tex-common 0.15build1
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 146.137.96.15 21]


All of this came about because tetex was broken after upgrading from Breezy.

---

### Post by llimllib on 2006-06-21
Neither FTP nor HTTP works for me right now. The error I get with HTTP is a 403, and this is what I get with FTP:

> Err [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) dapper/universe wifi-radar 1.9.6-0ubuntu4
  The server refused the connection and said: OOPS: vsftpd: cannot locate user specified in 'ftp_username':ftp   [IP: 146.137.96.15 21]


Everything worked until about a half hour ago, right in the middle of a system update. Weird. (Is everyone who has a problem using the us.archive.ubuntu repository?)

---

### Post by capkanada on 2006-06-21
[FONT="Lucida Sans Unicode"]Hmmmm... not sure quite what is going on here....  My apt-get was working fine about 15 minutes ago, now when I try to install **ANYTHING** I get the lovely "403 Forbidden [IP: xxx.xxx.xx.xx 80]" error.  What gives?!  :mad: [/FONT]

---

### Post by bugman on 2006-06-21
[QUOTE=capkanada][FONT="Lucida Sans Unicode"]Hmmmm... not sure quite what is going on here....  My apt-get was working fine about 15 minutes ago, now when I try to install **ANYTHING** I get the lovely "403 Forbidden [IP: xxx.xxx.xx.xx 80]" error.  What gives?!  :mad: [/FONT][/QUOTE]
I just heard on the IRC channel that the US mirror is down

---

### Post by capkanada on 2006-06-21
[QUOTE=bugman]I just heard on the IRC channel that the US mirror is down[/QUOTE]
Loovely...  :-p  Hopefully it'll be back up soon....  What can I use in the meantime?

---

### Post by llimllib on 2006-06-21
[QUOTE=capkanada]Loovely...  :-p  Hopefully it'll be back up soon....  What can I use in the meantime?[/QUOTE]

I just changed my sources.list to use archive.ubuntu.com instead of us.archive.ubuntu.com in every instance.

In vim, this command is ```
:%s/\/us.archive.ubuntu.com/\/archive.ubuntu.com/g
```

---

### Post by Owdy on 2006-07-01
[quote=elusivespoon]I just started getting the 403 errors today and I made no changes to my system. [/quote] Same here. Whats going on?

---

### Post by Owdy on 2006-07-02
[URL="https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/51588"]
[/URL]edit:
This was proxy server issue. I turn it off and everything is fine. I have no idea how it was turned on :\

---

### Post by Doughsay on 2006-07-03
Ok, I'm still having this problem and nobody has anything helpful to say at all.  I'm NOT the only person having this problem!

Can anyone answer this:  What causes a "403 Forbidden" error when apt is updating the indexes?

I have one answer:  The repository being accessed doesn't exist.

There must be some other situations where this occurs and I don't know what they are...please help.  The repository that I'm using DOES EXIST!  My other PC accesses it just fine!  And I can browse it in a browser!  What's going on here!?!?!?

---

### Post by Owdy on 2006-07-03
[quote=Doughsay]Ok, I'm still having this problem and nobody has anything helpful to say at all.  I'm NOT the only person having this problem!

Can anyone answer this:  What causes a "403 Forbidden" error when apt is updating the indexes?

I have one answer:  The repository being accessed doesn't exist.

There must be some other situations where this occurs and I don't know what they are...please help.  The repository that I'm using DOES EXIST!  My other PC accesses it just fine!  And I can browse it in a browser!  What's going on here!?!?!?[/quote] Check your proxy settings.

---

### Post by Doughsay on 2006-07-03
Thanks for the reply.  Yes I did check my proxy settings, it's all turned off.

So this is a second answer:  Proxy settings are wrong.

Still no solution to my problem...

---

### Post by Doughsay on 2006-07-03
I finally solved it!

It WAS a proxy issue.  But I didn't set this up like this.  I don't know how this happened.  I said before that I didn't have proxy turned on, and this is true:

In my gnome settings (System > Preferences > Network Proxy)  it was turned off.

I checked the file "/etc/apt/apt.conf" and this is what it contained:
```
APT::Authentication::TrustCDROM "true";
Acquire::HTTP::Proxy "false";
```

So naturally I assumed that meant the proxy was turned off.  I'm not exactly sure what it means really.  Because when I checked the same file on my other computer it contained this:
```
APT::Authentication::TrustCDROM "true";
Acquire::::Proxy "false";
```

It took me a while to notice the difference.  But after I noticed, I removed the "HTTP" from my other config file and, magically, it works.

Now can anyone explain why?  And how this happened?

---

### Post by mega on 2006-07-05
Doughsay rocks

mine is fixed now too, at last!

---

### Post by cefola on 2006-07-07
Doughsay is correct.
Removed http from the apt.conf file and all is well.
Thanks !

---

### Post by jfdill_2 on 2006-07-07
2 things that have helped me:

Comment out proxy line in /etc/apt/apt.conf
// Acquire::http::Proxy "false";

Create a file /etc/apt/apt.conf.d/80http containing:
// /etc/apt/apt.conf.d/80http
Acquire::http::Pipeline-Depth "0";

2nd one seems to fix a problem I was having due to SonicWALL, which affected Debian Sarge also.

---

### Post by soft@cbov.org on 2006-07-07
hi ... i solve this problem with edition of file /etc/apt/apt.conf and remove "http" from line 
Adquire::http::Proxy "false";
or removing the original /etc/apt/apt.conf
 
[]os
Cristofer

---

### Post by stonefeet on 2006-07-07
i will try this as soon as i get home and see if this fixes the never ending "101 network unreachable without an nslookup of the address first" problem

@home
nope still didn't fix anything
the search continues

---

### Post by MTZeon on 2006-07-08
> **Doughsay said:**
> I finally solved it!

It WAS a proxy issue.  But I didn't set this up like this.  I don't know how this happened.  I said before that I didn't have proxy turned on, and this is true:

In my gnome settings (System > Preferences > Network Proxy)  it was turned off.

I checked the file "/etc/apt/apt.conf" and this is what it contained:
```
APT::Authentication::TrustCDROM "true";
Acquire::HTTP::Proxy "false";
```

So naturally I assumed that meant the proxy was turned off.  I'm not exactly sure what it means really.  Because when I checked the same file on my other computer it contained this:
```
APT::Authentication::TrustCDROM "true";
Acquire::::Proxy "false";
```

It took me a while to notice the difference.  But after I noticed, I removed the "HTTP" from my other config file and, magically, it works.

Now can anyone explain why?  And how this happened?

YESSSSS! It's working now! :D no more "forbidden 403" :) Tks!

Maybe something got wrong when Ubuntu Dapper packaged :\ Either way, working again!

This thread should be sticky!

---

### Post by DiGiTaLFX on 2006-07-09
Wow thanks it works! I just removed the apt.conf file (as all it had was the proxy line and i never used to have it). Now I can get some xmms2 goodness :D

---

### Post by Sefianix on 2006-07-21
jfdill_2, thanks!
We've got a sonicWall and your post helped!
It all works now.  :D

---

### Post by GreyDuck on 2006-08-10
> **jfdill_2 said:**
> Create a file /etc/apt/apt.conf.d/80http containing:
// /etc/apt/apt.conf.d/80http
Acquire::http::Pipeline-Depth "0";

2nd one seems to fix a problem I was having due to SonicWALL, which affected Debian Sarge also.
Ah, SonicWALL. *grumble* I should've known.

This fix did the trick for me, thank you!

---

### Post by Robor on 2007-01-24
I know this thread is like 6 months old but it came up in a Google search for errors with apt and 403 Forbidden errors.

I tried editing my apt.conf file as specified here and I tried renaming it completely and neither solved my problem.  Here's my situation:

I still have 'net access - only apt is broken
Everything was working before
I'm not blocked outbound in any way
apt-get update and apt-get upgrade worked fine in the past

---

### Post by digTro on 2007-01-24
I'm also facing the same problem. This is the error message I'm getting:
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb
  403 Forbidden [IP: 195.248.90.38 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb
  403 Forbidden [IP: 195.248.90.38 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb
  403 Forbidden [IP: 195.248.90.38 80]

```

There were a bunch of other updates which went fine. Only these three are failing.

---

### Post by jerremy-tamlin on 2007-02-18
Hi, I'm wondering if I should start a new thread as this one is really old.

I am having the same problem.

```
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Sources
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas/all Packages
  403 Forbidden
Err [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas/all Sources
  403 Forbidden
```

Does *Ign* mean that it is being ignored (posibly because I have already downloaded it?).

I changed the *http://* to *ftp://* in *sources.list* and this sort of fixed the problem - I was able to download the repositories and install the software that I wanted but it went very slow for some reason and for each repository stated '[Logging In]' then '[Query]' I gues this is because the ftp server requires it.

When I change the repositories back to *http://* I get the 403 errors. But I can go there with my browser and download the *Packages.gz* no problem.

apt-get is now also refusing to install packages:
```
jesse@windwanderer:~$ sudo apt-get install -f  mysql-server-5.0
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
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.22-0ubuntu6.06.2) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
E: Broken packages
```

I am now downloading the .deb packages manually.

This is a real problem, and I would have thought that it had been fixed by now.
Obviously it's one of those horrible subtle errors that don't have clear causes.

If anyone has any idea's on the cause of this error, Please post it here.
Thanks

**I did a *sudo apt-get clean* and it now works perfectly again even with *http://* Weired!!!**

---

### Post by itzpapalotl on 2007-03-27
Man... like a light at the end of a long dark tunnel. the words sonicwall, ubunutu 403 finally hit home. If this doesn't solve it......

---

### Post by Foaming Draught on 2007-04-13
This morning's Linux kernel update threw up the old 403 "permission denied" message.  sudo apt-get clean didn't fix it.

I used Synaptic (wonderful as the command line is, if you like that sort of thing, I don't want to go back to CP/M in the 21st century) Settings/Repositories, clicked on 'Other', found an ftp server for Australia, selected it, closed the dialogue, hit 'Reload', then 'Mark all updates', then 'Apply' and hey presto, it worked fine, no 403.

I've switched back to the usual server for Australia, so we'll see if the problem recurs.  But if it does, it's a cinch to fix via Synaptic pointing & clicking, with nary a terminal screen or command line to be seen.

---

### Post by Karnex420 on 2007-04-14
So here is my /etc/apt/sources.lst   .     Where would I change this?




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by g_pyle on 2007-05-23
This worked for me too.  Thanks for the help!

---

### Post by jfdill_2 on 2007-05-24
> **Karnex420 said:**
> So here is my /etc/apt/sources.lst   .     Where would I change this?

Just comment out all of the lines with a "#" and the error will disappear #-o  **But seriously** read the thread, you have to make changes to other files not sources.list.  I did it by creating a new file called /etc/apt/apt.conf.d/80http with this line in it:

```
Acquire::http::Pipeline-Depth "0";
```

If you have upgraded from a previous OS it's possible you could also have settings in /etc/apt/apt.conf which would be similar.

Note this only fixes a specific type of problem where the pipelining is tripping a rule in an Intrusion Prevention System (IPS) such as SonicWALL where the activity is incorrectly being detected as a "port scan" or some other type of attack.  It looks like some of the recent reports could be a different type of problem, either a problem with the particular apt source, or maybe the IP address had been blacklisted for some reason.

If you are having a problem due to an intrusion prevention system, there should be some telltale errors in the firewall logs.  If you don't have access to the firewall logs, but can run a packet sniffer such as wireshark, you may see the firewall sending back RST packets to your workstation with the IP address of the apt source.  Basically, this is the firewall's way of duping the client (apt-get) into thinking that the server has dropped the connection, the idea being that the client will immediately drop the connection and try to recover gracefully.  Unfortunately, this can sometimes lead to some confusing symptoms if you are not aware that the firewall could do that, and you could find yourself charging off to try and fix software or hardware and replace network cables, not that I've ever done anything like that :rolleyes:

---

