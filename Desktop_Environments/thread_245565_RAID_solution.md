---
title: "RAID solution"
date: 2006-08-28
forum: Desktop Environments
---

### Post by pwrstick on 2006-08-28
Hello, hope this finds everyone well!

I'm hoping to get some advice from anyone about a RAID configuration.  Here's the scenario:

Slow (~400MHz w/ 256MB Ram) computer with Ubuntu Server running simply as a file server with SMBA support for the Windows users (aka "Parents").  This server will be doing nothing other than filesharing and rSync'ing nightly to another server (for fire tolerance.  High fire area here).

So I'm trying to set this RAID solution up for my folks, and here's a few ideas I've run into:

[LIST=1]
[*]***Software raid is OK for a server that isn't doing anything else or needed for performance.***  You think that still applies to a slower system?  Also, my mom is going to want to pull pictures (2 MB) off the server fairly quickly.
[*]***If you do go hardware, get a 3ware card; it has the best Linux support.***  I've found one at Newegg for just over 100 bucks.  I can get a cheaper card and turn the box into a Win2K machine, but I'd rather not.  Honestly I don't want to have to worry about the security as much even though they're not getting internet access.[/LIST]

My plan is to go mirror two 300GB drives (so just Raid 1) and maybe have a hot stand-by.  But my biggest concern is making sure the server actually runs and serves and writes files somewhat quickly, and is compatible with Dapper.  Smooth is the word!

Input is greatly appreciated!  No matter how small -- please, any experience you have would be happily received since I have never worked with RAID and gnu/linux before.

Cheers! :beer:

---

### Post by TSMJ on 2006-08-29
I need to know how to set up RAID with Ubuntu server too - I looked around for distro-unspecific HowTo's and they mentioned things like raidtools, mdadm and EVMS, the latter of which (+ RAID monitoring tools) are listed during boot. Is installing RAID or similar straight-forward with ubuntu server? I can't find any documentation on it.

Cheers.

TJ

---

### Post by cleentrax on 2006-08-30
[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)
[http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/](http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/)

Check out the above guides. mdadm is fairly straightforward, but I've had a hell of a time getting my server fully functional with a software RAID 5. I may end up going with two raid 1's.

---

