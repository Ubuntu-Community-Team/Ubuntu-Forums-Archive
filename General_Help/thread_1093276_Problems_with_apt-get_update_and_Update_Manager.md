---
title: "Problems with apt-get update and Update Manager"
date: 2009-03-11
forum: General Help
---

### Post by niallporter on 2009-03-11
Hi all,

When Update Manager checks for updates, I get error messages like this one:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2  Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2  Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2  Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
```

If I do "sudo apt-get update" in a terminal I get errors like this:

```


...

Hit http://gb.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-security/multiverse Sources            
Fetched 5B in 3s (2B/s)                                   
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

After some reading on google, launchpad and these forums I learned if I do "sudo apt-get update -o Acquire::http::No-Cache=True" in a terminal then it will work, and it does.  That's great but I don't want to have to do that every time.  A little more reading and it turns out I can add such options to /etc/apt/apt.conf.  The man page for apt.conf suggests that *all* apt based tools use this.  "Great," I think, "that should fix Update Manager."  So I edit my apt.conf file thus:

```
APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}
```

Problem is, Update Manager still returns the errors above.  If I copy one of the URLs that Update Manager claims it can't get, then paste it into the address bar in FireFox (or try and get it with wget) it works just fine.

This is driving me to distraction.  I am behind some proxy or similar in my workplace LAN that I have no control over.  Can anyone tell me why Update Manager isn't obeying the options in apt.conf and suggest how I can fix it properly?

Many thanks,
Niall

---

### Post by taurus on 2009-03-11
Go into either System -> Administration -> Synaptic Package Manager -> Settings -> Repositories or System -> Administration -> Software Sources and try another server.

p.s.  Don't forget to clean out the old cache first.

```
sudo apt-get clean
```

---

### Post by niallporter on 2009-03-11
> **taurus said:**
> Go into either System -> Administration -> Synaptic Package Manager -> Settings -> Repositories or System -> Administration -> Software Sources and try another server.

Sorry, should have mentioned that.  Tried that too - errors on different files but essentially the same problem on either the UK mirror or the main server.

---

### Post by thtrgremlin on 2009-03-11
You got me stumped. Your config looks right from reviewing [http://fts.ifac.cnr.it/cgi-bin/dwww/usr/share/doc/apt/examples/configure-index.gz](http://fts.ifac.cnr.it/cgi-bin/dwww/usr/share/doc/apt/examples/configure-index.gz)

Another way to set a default would be to use an alias. Double check, but I think this would fix your issue:

```
sudo alias apt-get='apt-get -o Acquire::http::No-Cache=True'
```

Then, when you run apt-get, it will always add the option. Unfortunately, I am not on a machine to test it. While it is not the ideal solution, it would keep you from having to type the tedious part.

Hope this helps.

---

### Post by niallporter on 2009-03-12
OK today things are a little different.  Doing a regular "sudo apt-get update" on the Main server gives:

```

...

Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Fetched 62.2kB in 4s (14.1kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

And doing the same on the UK server gives:

```

...

Get: 33 http://gb.archive.ubuntu.com hardy-security/multiverse Packages [11.0kB]
Get: 34 http://gb.archive.ubuntu.com hardy-security/multiverse Sources [1105B] 
Fetched 8582kB in 2min1s (70.8kB/s)                                            
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

On either server, using "sudo apt-get update -o Acquire::http::No-Cache=True" works fine, returns no errors.  Anyone got any better ideas?  I'd rather not have to use the alias trick (thanks anyway for that) since to my mind, having the apt options in /etc/apt/apt.conf *should* work...

---

### Post by thtrgremlin on 2009-03-12
GPG error means that the servers are not authenticated. They will still work, it will just keep warning you that the software isn't from a trusted source. Sounds like the US servers are working well for you.

---

### Post by niallporter on 2009-04-07
> **thtrgremlin said:**
> GPG error means that the servers are not authenticated. They will still work, it will just keep warning you that the software isn't from a trusted source. Sounds like the US servers are working well for you.

It was working for a couple of weeks or so, now I'm back to getting the following (from Update Manager or from a regular "sudo apt-get update"):

```
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

Switching to the UK server and doing a "sudo apt-get update" takes a *VERY* long time (compared to using the US server) but didn't generate any errors in the terminal window.  However, once it was finished I got the Information icon in the system notification area which gave the following message:

> Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

Clicking the "Run this action now" button as advised, did a graphical package refresh which generated no errors.  Now I appear to have 6 updates including a new kernel and associated gubbins.

So it seems switching from the US back to UK servers got a fresh package list from an authentic source.  This begs the question as to why - I have the same Ubuntu release at home (8.04 LTS on x64) and I never see messages like this.  I don't think I've ever switched mirrors for apt there.  Any ideas?

Thanks,
Niall

---

### Post by fortknox on 2009-12-09
Sorry to bring up an ancient thread, but I've been playing with this issue myself because it comes up with work routinely.

If you are still having the issue (or someone else stumbles in it googling around), I thought I'd post my solution and hopefully help a person or two.

From the first thread:
> **niallporter said:**
> Hi all,
```
APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}
```

"Aquire" isn't nested inside "APT".  Here is my conf:
```

Acquire
{
  http
  {
    No-Cache "true";
  };
// unsure if this is a valid line
//  BrokenProxy "true";
};

```You'll need to 'sudo apt-get clean' and probably even [clean out the /lib/apt/lists directory]("http://www.drewwithers.com/content/how-fix-ubuntu-gpg-error-badsig") as well after setting the conf the first time.  I don't know if it was necessary, but I did it, regardless.

Hope that helps.

---

### Post by niallporter on 2009-12-11
Thanks for the post, it is still a problem for me.  I tried your steps, I didn't have an apt.conf in /etc/apt/ as I've done a reinstall and hadn't put that back in so I created the file and pasted in what you posted.  I followed your link and performed the steps in there.

The output from the last apt-get update had the following at the end:

```
W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://packages.medibuntu.org/dists/jaunty/non-free/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I thought that was all I was going to get, but then the Update Manager popped up with some updates.  It did say at the top, however, that "The package information was last updated 3 days ago".  I had it download and apply the updates, then I got an information box with the following text in it:

```
Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
```

I did the "Run this action now" thing but got an error:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://packages.medibuntu.org/dists/jaunty/free/binary-amd64/Packages.bz2  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.
```

I don't know enough about the whole apt process and setup to be able to work out what this all means but I do know this; if I do "sudo apt-get update -o Acquire::http::No-Cache=True" it seems to work fine, but with that same option in /etc/apt/apt.conf it's no different.  I still think that /etc/apt/apt.conf file is being ignored by apt-get.

There is an apt.conf.d directory in /etc/apt :

```
niall@abehws02:~$ ls -al /etc/apt/apt.conf.d/
total 52
drwxr-xr-x 2 root root 4096 2009-10-01 10:37 .
drwxr-xr-x 4 root root 4096 2009-12-11 11:52 ..
-rw-r--r-- 1 root root   40 2009-09-30 19:35 00trustcdrom
-rw-r--r-- 1 root root  305 2009-04-17 05:26 01autoremove
-rw-r--r-- 1 root root    9 2009-04-17 05:26 01ubuntu
-rw-r--r-- 1 root root  157 2009-02-10 17:00 05aptitude
-rw-r--r-- 1 root root  129 2009-03-26 13:35 10periodic
-rw-r--r-- 1 root root  108 2009-03-26 13:35 15update-stamp
-rw-r--r-- 1 root root   85 2009-03-26 13:35 20archive
-rw-r--r-- 1 root root  228 2009-04-23 12:18 20packagekit
-rw-r--r-- 1 root root  598 2009-03-02 10:03 50unattended-upgrades
-rw-r--r-- 1 root root  182 2009-03-24 05:30 70debconf
-rw-r--r-- 1 root root  197 2009-03-26 13:35 99update-notifier
niall@abehws02:~$
```

Do I need to put the stuff i put in the (newly created) apt.conf file into one of the above, or create a new one or something?

---

### Post by daaussie on 2009-12-16
I fixed this problem by configuring ubuntu to get updates from main server (i was previously having this same problem with the Australian server).

I did it for 3 workstations, and I never have the problem again. 

HELP? >> Only thing is, I don't have a GUI for server, and don't know the terminal terminology to switch where it gets the updates from.

can anyone help by providing word for word the entries for terminal to switch to main server?

thanks

---

### Post by AlexanderDGreat on 2009-12-26
Hi I'm behind a firewall, I can't apt-get update. I've already tried ALL suggestions here: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy")

But they're NOT working for me! I'm using Karmic Koala on server and client. Pls. Help!

---

### Post by ant2ne on 2010-01-15
> **daaussie said:**
> I fixed this problem by configuring ubuntu to get updates from main server (i was previously having this same problem with the Australian server).

I did it for 3 workstations, and I never have the problem again. 

HELP? >> Only thing is, I don't have a GUI for server, and don't know the terminal terminology to switch where it gets the updates from.I too am having this issue with an ubuntu server. No GUI? how do I pick the server location?

---

### Post by Dark Angel on 2010-05-04
You need to edit your sources file.

I think it's:

sudo nano /etc/apt/sources.list

(nano is a text editor)

just edit the country code in the links (au or uk or whatever) to the one you want to use.  Use none for the main server.
eg
Change this line:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
 to read:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
 to switch from the Australian to the main server.

hth

I'm still getting the same issue though, changing the sources hasn't helped me.

---

### Post by DroBuddy on 2011-04-25
I removed "us." from the /etc/apt/sources.list from the maverick meerkat multiverse repos and am now able to get updates again! Yeah... Thanks guys.

I have no clue why I can download from the rest of the US repositories, but the multiverse repos quit working for me a week ago. After removing us from the repos path, I ran the following:

```

sudo apt-get clean; sudo apt-get update

```

And, it works. Hope this helps someone else out, as well. And, sorry for reviving a dead thread, but it was useful. ;-)

---

