---
title: "GPG Ubuntu Jaunty Archive Error"
date: 2009-05-08
forum: General Help
---

### Post by Laibcoms on 2009-05-08
Error:
> 
GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


What I have tried so far:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
sudo apt-get update

```

```

sudo apt-get update -o Acquire::http::No-Cache=True

```

```

sudo apt-get update -o Acquire::BrokenProxy=true

```

Any help much appreciated, thank you!! ^_^

---

### Post by maw140 on 2009-05-19
I have the same problem...
bumped

---

### Post by rasteenb on 2009-05-19
Same problem here.

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by nqminh on 2009-05-27
> **Laibcoms said:**
> Error:


What I have tried so far:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
sudo apt-get update

``````

sudo apt-get update -o Acquire::http::No-Cache=True

``````

sudo apt-get update -o Acquire::BrokenProxy=true

```Any help much appreciated, thank you!! ^_^

It seams you missed the command 

```
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add 
```
I have the same problem, no more errors after i tried the following commands 

```

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

Sources: [http://ohioloco.ubuntuforums.org/showthread.php?t=803585](http://ohioloco.ubuntuforums.org/showthread.php?t=803585)

---

### Post by ironstone146 on 2009-07-29
yip, the above worked for me to (though had to sudo them...)
[INDENT]apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

[/INDENT]many thanks !

---

### Post by ironstone146 on 2009-07-29
aarg ! spoke too soon...
once the above ran through, still got error (in synaptic and cl)

[INDENT]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com
[/INDENT]

---

### Post by ironstone146 on 2009-07-30
the next day (following overnight shutdown etc)... refreshing / updating the repository ran through OK. maybe i needed a restart following the commends entered 2 posts back ? something has worked.

---

### Post by Brokerjoe24 on 2009-08-11
I tried the above command 'mv lists lists.old', but it said 'mv: cannot move `lists' to `lists.old': Permission denied'.  I am a new user, obviously, so any advice you might have would be greatly appreciated.

Thanks.

---

### Post by greg_ory on 2009-09-17
sudo in front of the command and it should work

---

### Post by refrishx on 2010-05-04
i did everything but i got the following errors on the terminal:

terminal:
________________________________________________

...
Fetched 11.1MB in 1min 45s (105kB/s)                                           
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2)
Hash Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
khaled@ubuntu:/var/lib/apt$ _
________________________________________________

what is the solution ..?

---

### Post by amjjawad on 2011-03-01
This is a very helpful thread even though it does not explain the real reason behind this kind of problems/errors.

I have got the same issue with:

antiX 8.5
Lubuntu 10.04
Linux Mint LXDE and Fluxbox
Ubuntu 10.04
and some other distributions which are based on Debian/Ubuntu.


```
Hit http://www-ftp.lip6.fr lucid Release.gpg
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid/universe Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid/multiverse Translation-en_US
Get:1 http://www-ftp.lip6.fr lucid-updates Release.gpg [198B]
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-updates/main Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-updates/restricted Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-updates/universe Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-updates/multiverse Translation-en_US
Get:2 http://www-ftp.lip6.fr lucid-security Release.gpg [198B]
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-security/main Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-security/restricted Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-security/universe Translation-en_US
Ign http://www-ftp.lip6.fr/pub/linux/distributions/Ubuntu/archive/ lucid-security/multiverse Translation-en_US
Hit http://www-ftp.lip6.fr lucid Release
Get:3 http://www-ftp.lip6.fr lucid-updates Release [44.7kB]             
Ign http://www-ftp.lip6.fr lucid-updates Release  
Get:4 http://www-ftp.lip6.fr lucid-security Release [44.7kB]
Ign http://www-ftp.lip6.fr lucid-security Release
Hit http://www-ftp.lip6.fr lucid/main Packages
Hit http://www-ftp.lip6.fr lucid/restricted Packages
Hit http://www-ftp.lip6.fr lucid/main Sources
Hit http://www-ftp.lip6.fr lucid/restricted Sources
Hit http://www-ftp.lip6.fr lucid/universe Packages
Hit http://www-ftp.lip6.fr lucid/universe Sources
Hit http://www-ftp.lip6.fr lucid/multiverse Packages
Hit http://www-ftp.lip6.fr lucid/multiverse Sources
Hit http://www-ftp.lip6.fr lucid-updates/main Packages                         
Hit http://www-ftp.lip6.fr lucid-updates/restricted Packages                   
Hit http://www-ftp.lip6.fr lucid-updates/main Sources                          
Hit http://www-ftp.lip6.fr lucid-updates/restricted Sources                    
Hit http://www-ftp.lip6.fr lucid-updates/universe Packages                     
Hit http://www-ftp.lip6.fr lucid-updates/universe Sources                      
Hit http://www-ftp.lip6.fr lucid-updates/multiverse Packages                   
Get:5 http://www-ftp.lip6.fr lucid-updates/multiverse Sources [4,369B]         
Get:6 http://www-ftp.lip6.fr lucid-security/main Packages [143kB]
Hit http://www-ftp.lip6.fr lucid-security/restricted Packages                  
Hit http://www-ftp.lip6.fr lucid-security/main Sources                         
Hit http://www-ftp.lip6.fr lucid-security/restricted Sources                   
Hit http://www-ftp.lip6.fr lucid-security/universe Packages                    
Hit http://www-ftp.lip6.fr lucid-security/universe Sources                     
Hit http://www-ftp.lip6.fr lucid-security/multiverse Packages                  
Get:7 http://www-ftp.lip6.fr lucid-security/multiverse Sources [651B]          
Fetched 148kB in 20s (7,101B/s)                                                
Reading package lists... Done
W: GPG error: http://www-ftp.lip6.fr lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://www-ftp.lip6.fr lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Changing the server was NOT helpful so the real fix was one of these two commands:

```

sudo apt-get update -o Acquire::http::No-Cache=True

```

if the first one then:

```

sudo apt-get update -o Acquire::BrokenProxy=true

```


90-95% the above two commands worked perfectly ... very few times did not work.
 
I have searched a lot about this error and can't remember what did I find exactly.
It's also worth to mention that the above two commands work but not for a long time. Sometimes, I got the same problem after one or two days when I restart/shutdown my PC and turn it on again. So, have to run the first command, if did not work then the 2nd one.


Just thought to share this in here!

P.S
It's been ages I did not post in this forum :P

---

### Post by glen-shennan on 2011-04-01
I'm running Ubuntu 10.10 and the

```

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```system has worked for me so far. 

I agree I think this is still a relevant thread given that I don't know what is causing this or really why this fix has worked for me so far.

---

### Post by Francus on 2011-04-05
I'm running Ubuntu 10.10 64bit and after changing various servers with no result, tried this

```

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

But I am still getting errors with apt-get update and also System/ Update manager fails to install updates.

This is the output of my apt-get update


```

f@Toshiba:/var/lib/apt$ sudo apt-get clean
f@Toshiba:/var/lib/apt$ sudo apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Get:2 http://archive.canonical.com maverick Release.gpg [198B]                 
Get:3 http://it.archive.ubuntu.com maverick Release.gpg [198B]                 
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-it              
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-it
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-it       
Get:5 http://extras.ubuntu.com maverick Release [9762B]                        
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Get:7 http://archive.canonical.com maverick Release [5925B]                    
Get:8 http://it.archive.ubuntu.com/ubuntu/ maverick/main Translation-it [322kB]
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Get:9 http://archive.canonical.com maverick/partner amd64 Packages [6694B]     
Get:10 http://extras.ubuntu.com maverick/main Sources [1073B]                  
Get:11 http://extras.ubuntu.com maverick/main amd64 Packages [1201B]           
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-it
Get:12 http://ppa.launchpad.net maverick Release [9755B]                       
Get:13 http://ppa.launchpad.net maverick Release [9753B]                       
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Get:14 http://it.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-it [32,4kB]
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Get:15 http://it.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-it [2446B]
Get:16 http://ppa.launchpad.net maverick/main Sources [1503B]                  
Ign http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Get:17 http://ppa.launchpad.net maverick/main amd64 Packages [3541B]           
Get:18 http://it.archive.ubuntu.com/ubuntu/ maverick/universe Translation-it [1259kB]
Get:19 http://it.archive.ubuntu.com maverick-updates Release.gpg [198B]        
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-it  
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-it
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-it
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-it
Get:20 http://it.archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-it
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-it
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-it
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://it.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-it
Get:21 http://it.archive.ubuntu.com maverick Release [39,8kB]
Get:22 http://ppa.launchpad.net maverick/main Sources [2457B]                  
Get:23 http://ppa.launchpad.net maverick/main amd64 Packages [4412B]           
Get:24 http://it.archive.ubuntu.com maverick-updates Release [31,4kB]          
Get:25 http://it.archive.ubuntu.com maverick-security Release [31,4kB]         
Get:26 http://it.archive.ubuntu.com maverick/main Sources [829kB]              
Get:27 http://it.archive.ubuntu.com maverick/restricted Sources [4370B]        
Get:28 http://it.archive.ubuntu.com maverick/universe Sources [4179kB]         
Ign http://it.archive.ubuntu.com maverick/universe Sources                     
Ign http://it.archive.ubuntu.com maverick/multiverse Sources                   
Ign http://it.archive.ubuntu.com maverick/main amd64 Packages                  
Ign http://it.archive.ubuntu.com maverick/restricted amd64 Packages            
Ign http://it.archive.ubuntu.com maverick/universe amd64 Packages              
Ign http://it.archive.ubuntu.com maverick/multiverse amd64 Packages            
Ign http://it.archive.ubuntu.com maverick-updates/main Sources                 
Ign http://it.archive.ubuntu.com maverick-updates/restricted Sources           
Ign http://it.archive.ubuntu.com maverick-updates/universe Sources             
Ign http://it.archive.ubuntu.com maverick-updates/multiverse Sources           
Ign http://it.archive.ubuntu.com maverick-updates/main amd64 Packages          
Ign http://it.archive.ubuntu.com maverick-updates/restricted amd64 Packages    
Ign http://it.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Ign http://it.archive.ubuntu.com maverick-updates/multiverse amd64 Packages    
Ign http://it.archive.ubuntu.com maverick-security/main Sources                
Ign http://it.archive.ubuntu.com maverick-security/restricted Sources          
Ign http://it.archive.ubuntu.com maverick-security/universe Sources            
Ign http://it.archive.ubuntu.com maverick-security/multiverse Sources
Ign http://it.archive.ubuntu.com maverick-security/main amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/restricted amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/universe amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/multiverse amd64 Packages
Ign http://it.archive.ubuntu.com maverick/universe Sources
Ign http://it.archive.ubuntu.com maverick/multiverse Sources
Ign http://it.archive.ubuntu.com maverick/main amd64 Packages
Ign http://it.archive.ubuntu.com maverick/restricted amd64 Packages
Ign http://it.archive.ubuntu.com maverick/universe amd64 Packages
Ign http://it.archive.ubuntu.com maverick/multiverse amd64 Packages
Ign http://it.archive.ubuntu.com maverick-updates/main Sources
Ign http://it.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://it.archive.ubuntu.com maverick-updates/universe Sources
Ign http://it.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://it.archive.ubuntu.com maverick-updates/main amd64 Packages
Ign http://it.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Ign http://it.archive.ubuntu.com maverick-updates/universe amd64 Packages
Ign http://it.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/main Sources
Ign http://it.archive.ubuntu.com maverick-security/restricted Sources
Ign http://it.archive.ubuntu.com maverick-security/universe Sources
Ign http://it.archive.ubuntu.com maverick-security/multiverse Sources
Ign http://it.archive.ubuntu.com maverick-security/main amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/restricted amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/universe amd64 Packages
Ign http://it.archive.ubuntu.com maverick-security/multiverse amd64 Packages
Get:29 http://it.archive.ubuntu.com maverick/universe Sources [5185kB]
Err http://it.archive.ubuntu.com maverick/universe Sources                     
  Connection failed
Err http://it.archive.ubuntu.com maverick/multiverse Sources                   
  400  Bad Request
Err http://it.archive.ubuntu.com maverick/main amd64 Packages                  
  400  Bad Request
Err http://it.archive.ubuntu.com maverick/restricted amd64 Packages            
  400  Bad Request
Err http://it.archive.ubuntu.com maverick/universe amd64 Packages              
  400  Bad Request
Err http://it.archive.ubuntu.com maverick/multiverse amd64 Packages            
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/main Sources                 
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/restricted Sources           
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/universe Sources             
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/multiverse Sources           
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/main amd64 Packages          
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/restricted amd64 Packages    
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/universe amd64 Packages      
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-updates/multiverse amd64 Packages    
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/main Sources                
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/restricted Sources          
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/universe Sources
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/multiverse Sources
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/main amd64 Packages
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/restricted amd64 Packages
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/universe amd64 Packages
  400  Bad Request
Err http://it.archive.ubuntu.com maverick-security/multiverse amd64 Packages
  400  Bad Request
Fetched 2610kB in 2min 26s (17,8kB/s)
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  Connection failed

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz  400  Bad Request

W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz  400  Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.
f@Toshiba:/var/lib/apt$ 


```

---

