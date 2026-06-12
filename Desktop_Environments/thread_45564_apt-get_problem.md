---
title: "apt-get problem"
date: 2005-06-30
forum: Desktop Environments
---

### Post by 5horizons on 2005-06-30
Hello all,


I'm having some problems with apt-get (and synaptic) lately.  Attempting to do an 'apt-get update' (a reload in synaptic), I get the error 'gzip: stdin: not in gzip format ....   Sub-process gzip returned an error code (1)'.  What is going on here?

I've ssh'ed into another nearly identical ubuntu box that fetches everything correctly, and copied the /etc/apt/source.list file to my machine, performed an 'apt-get clean' and 'apt-get update' and I still get the same error.  Ubuntu has been working fine for months, this is the first problem like this I have seen.  I've got lots of space left on my drive too.

There is a similar thread on a debian list about this problem, [http://www.linuxarkivet.se/mlists/debian-user/0307/msg00734.html ](http://www.linuxarkivet.se/mlists/debian-user/0307/msg00734.html ).  I'm not sure if this is the same problem or not.

Any advice for this problem?

---

### Post by 5horizons on 2005-06-30
Oh yes, here is the detailed error and the sources.list I am using.


error:
```
chris@vector:~/junk$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable Release.gpg
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable Release
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Get:3 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Get:4 http://security.ubuntu.com hoary-security/main Sources [8074B]
99% [4 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com hoary-security/main Sources
  Sub-process gzip returned an error code (1)
Fetched 17.0kB in 1s (15.7kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here is the sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb http://archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse   
# deb-src http://archive.ubuntu.com/ubuntu/ hoary universe    

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted   
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted  
```

---

### Post by davahmet on 2005-06-30
[QUOTE=5horizons]Oh yes, here is the detailed error and the sources.list I am using.


error:
```
chris@vector:~/junk$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable Release.gpg
Ign cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020) unstable Release
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Get:3 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Get:4 http://security.ubuntu.com hoary-security/main Sources [8074B]
99% [4 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com hoary-security/main Sources
  Sub-process gzip returned an error code (1)
Fetched 17.0kB in 1s (15.7kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here is the sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb http://archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse   
# deb-src http://archive.ubuntu.com/ubuntu/ hoary universe    

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted   
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted  
```[/QUOTE]
 In your sources.list, remove the line that begins with "deb cdrom".  That was needed in the initial installation of Warty only.  It will definitely confuse apt-get.

Also uncomment the line: 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

Run apt-get update

That should get you going, I think.

---

### Post by 5horizons on 2005-06-30
Thanks for the speedy reply,

I tried the two suggestions you mentioned, both of which make sense.  I'm getting the exact same error with apt-get as before.  Funny how its only with this machine, and only within the last couple days.   This is an office computer at a University, so its possible that the network people have changed some things around on me (its pretty hard to tell at this point).

Downloading the file manually (with wget) does give a gzipped file, so I'm not sure why apt-get is complaining.

the debian mailing list thread makes me think its a mime type problem.  I'll try a different mirror later, and see if that makes a difference.  There is also an ubuntu thread on this same topic: [http://ubuntuforums.org/archive/index.php/t-9944.html](http://ubuntuforums.org/archive/index.php/t-9944.html) 

Thanks

---

