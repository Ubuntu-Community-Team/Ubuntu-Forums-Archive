---
title: "Dell Mini 9: Firefox won't start for one user - will for other"
date: 2009-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JRSinOK on 2009-01-26
I am having a similar problem with Firefox on my Dell Mini.  I am running factory 8.04.

There is a slight difference.  When I log on I can run Firefox just fine, but when I log out and my wife logs in under her user name, Firefox won't open. I have tired running it from the terminal and from the desktop and menus, but I get the same thing.  It looks like the window is going to open, then nothing.  

 Don't know if that's related to your issue or not, but I can't figure out what is going on with mine.

---

### Post by ugm6hr on 2009-01-27
> **JRSinOK said:**
> Don't know if that's related to your issue or not, but I can't figure out what is going on with mine.

Moved to a new thread.

What does Terminal put out when you try and run it from there?

---

### Post by JRSinOK on 2009-01-27
Thanks for the new thread. 


Nothings happens when I go to the terminal and try to execute the program.

```
abbey@jimmy:~$ firefox
abbey@jimmy:~$ 


```

I've checked the hard drive memory and that's not the problem.  Any suggestions?

---

### Post by ugm6hr on 2009-01-27
Try and work out whether it is your wife's login that is the problem, or whether it is the logging out as one user and logging back in as another that is the issue.

If the former, we can dig around to work out why.  If the latter, I'm afraid I can't think of any reason why logging out and then logging back in would be an issue for firefox.

---

### Post by armandh on 2009-01-27
has the new users wireless established a connection????
[different setup required for each?]
if not, it is likely waiting for the connection.

---

### Post by JRSinOK on 2009-01-27
I  believe it may have something to do with her log in.  I set her up as a full administrator and Firefox originally worked with her profile.  I'm thinking I need to create a third account and see if there is any problem with it.  

I reach my conclusion based on the fact that I can boot up and log in as me and have no problem.  I can shut down, and boot up again and log in as her and Firefox won't start.  

I can log in as her and not get to Firefox, I can log out and log back in under my name and get Firefox to work without re-booting.

I have noticed that if I use the "switch user" function my computer slows way down.  I'm guessing with only 512Mb of Ram that with the other user logged on it's just dragging down my system resources.  For that reason I will log out of one account and log back in with another.  

Does any of this make sense or should I provide a flow chart and/or diagram....Kidding....

---

### Post by JRSinOK on 2009-01-27
> **armandh said:**
> has the new users wireless established a connection????
[different setup required for each?]
if not, it is likely waiting for the connection.

Yes.  The wireless icon shows connectivity already established prior to my trying to open Firefox.

---

### Post by ugm6hr on 2009-01-27
OK. So there is a problem with her Firefox.  Hopefully we can work out what.

Did you make any changes to her Firefox profile after any of the updates?

First, make sure you have updated everything (post output from these commands):
```
sudo apt-get update
sudo apt-get upgrade
```

Then, give the output (when logged in as your wife) from:
```
ls -l ~/.mozilla
```

---

### Post by JRSinOK on 2009-01-27
Out-put, as requested:

apt-get

```
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Hit http://archive.ubuntu.com hardy Release.gpg                      
Ign http://archive.ubuntu.com hardy/main Translation-en_US           
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Get:2 http://security.ubuntu.com hardy-security Release [58.5kB]     
Ign http://archive.ubuntu.com hardy/universe Translation-en_US           
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US         
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US         
Get:3 http://archive.ubuntu.com hardy-updates Release.gpg [189B]         
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US   
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US 
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US 
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Hit http://archive.ubuntu.com hardy Release                              
Get:4 http://archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg         
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release     
Hit http://dell-mini.archive.canonical.com hardy-updates Release               
Hit http://dell-mini.archive.canonical.com hardy-security Release              
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release          
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release             
Hit http://dell-mini.archive.canonical.com hardy/main Packages                 
Hit http://dell-mini.archive.canonical.com hardy/universe Packages             
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages           
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages           
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources         
Ign http://security.ubuntu.com hardy-security/universe Packages             
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages         
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages     
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages   
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages   
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources          
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources      
Ign http://security.ubuntu.com hardy-security/main Packages          
Ign http://security.ubuntu.com hardy-security/multiverse Packages    
Ign http://security.ubuntu.com hardy-security/restricted Packages    
Get:5 http://security.ubuntu.com hardy-security/universe Sources [8903B]
Ign http://archive.ubuntu.com hardy/main Packages                         
Ign http://archive.ubuntu.com hardy/universe Packages                
Ign http://archive.ubuntu.com hardy/restricted Packages              
Ign http://archive.ubuntu.com hardy/multiverse Packages              
Hit http://archive.ubuntu.com hardy/main Sources                     
Hit http://archive.ubuntu.com hardy/universe Sources                 
Hit http://archive.ubuntu.com hardy/restricted Sources               
Hit http://archive.ubuntu.com hardy/multiverse Sources               
Get:6 http://security.ubuntu.com hardy-security/main Sources [21.9kB]
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages   
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages    
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages  
Get:7 http://security.ubuntu.com hardy-security/multiverse Sources [1107B]     
Get:8 http://security.ubuntu.com hardy-security/restricted Sources [892B]      
Err http://security.ubuntu.com hardy-security/universe Packages                
  404 Not Found
Err http://security.ubuntu.com hardy-security/main Packages        
  404 Not Found
Err http://security.ubuntu.com hardy-security/multiverse Packages  
  404 Not Found
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages  
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources         
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources     
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources   
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources   
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages    
Ign http://archive.ubuntu.com hardy-updates/universe Packages                  
Ign http://archive.ubuntu.com hardy-updates/main Packages                      
Ign http://archive.ubuntu.com hardy-updates/multiverse Packages                
Ign http://archive.ubuntu.com hardy-updates/restricted Packages      
Get:9 http://archive.ubuntu.com hardy-updates/universe Sources [35.6kB]
Err http://security.ubuntu.com hardy-security/restricted Packages          
  404 Not Found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Get:10 http://archive.ubuntu.com hardy-updates/main Sources [106kB]
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources        
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Get:11 http://archive.ubuntu.com hardy-updates/multiverse Sources [4601B]
Get:12 http://archive.ubuntu.com hardy-updates/restricted Sources [903B] 
Err http://archive.ubuntu.com hardy/main Packages                        
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy/universe Packages                    
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy/restricted Packages             
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy/multiverse Packages             
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy-updates/universe Packages       
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy-updates/main Packages           
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy-updates/multiverse Packages     
  404 Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com hardy-updates/restricted Packages     
  404 Not Found [IP: 91.189.88.31 80]
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 298kB in 2s (132kB/s)                     
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

```
bbey@jimmy:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
abbey@jimmy:~$ 

```

```
abbey@jimmy:~$ ls -l ~/.mozilla
total 8
drwx------ 3 abbey abbey 4096 2009-01-19 11:51 extensions
lrwxrwxrwx 1 abbey abbey   28 2009-01-24 07:52 web browser -> /home/abbey/.mozilla/firefox
drwx------ 3 abbey abbey 4096 2009-01-19 11:51 web browser.bak
abbey@jimmy:~$ 

```

---

### Post by ugm6hr on 2009-01-28
OK. I think I know the problem.

Your wife renamed the ~/.mozilla/firefox folder to ~/.mozilla/"web browser" (presumably after the original update that messed things up).

You need to change that back.

So - logged in as your wife (abbey):
```
mv ~/.mozilla/"web browser.bak" ~/.mozilla/firefox
```

Then log out and back in again - it should now work OK.

Reason:
The original update started a new profile in "web browser" instead of "firefox" - thereby deleting all bookmarks etc.  Your wife renamed "firefox" to "web browser" in order to reinstate the old profile (or perhaps the first time she used Firefox was after the 1st update, but before the 2nd?)  The most recent update was designed to correct the original error, and renamed "web browser" to "web browser.bak", and created a symlink (shortcut) from "web browser" to "firefox".  Unfortunately, given your wife no longer has a "firefox" folder, that shortcut leads to no where, thereby confusing Firefox into not starting.  So, by changing back to "firefox" everything should be as Dell intended.

Basically - blame Dell for their stupidity.

Also - I hope you realise that you have the standard Ubuntu repositories enabled in addition to the Dell ones.  That is not the issue here, and I suspect that it won't cause any problems, but if you want to use Canonical repositories, you are better of using the Canonicla netbook repo than standard ones.

---

### Post by JRSinOK on 2009-01-28
Sorry, you may have to 'spoon feed' me on how to do this....here is what I get when I try and move the folders that you suggested above

```

abbey@jimmy:~$ mv ~/.mozilla/"web browser.bak" ~./mozilla/firefox
mv: cannot move `/home/abbey/.mozilla/web browser.bak' to `~./mozilla/firefox': No such file or directory
abbey@jimmy:~$ 
```

Do I just need to create that file?

---

### Post by ugm6hr on 2009-01-29
Sorry - my advice had the "." in the wrong place.  Should be after the "/" not before.

Copy and paste from the previous post again - I have edited it.

---

### Post by JRSinOK on 2009-02-05
Sorry.  I should have responded sooner.  This did fix it, thanks for the help!

---

### Post by JRSinOK on 2009-02-05
I know there is a way to mark this thread as "solved" but I don't know how.  Any help?

---

### Post by ugm6hr on 2009-02-06
> **JRSinOK said:**
> I know there is a way to mark this thread as "solved" but I don't know how.  Any help?

It used to be in the Thread tools menu at the top.

Unfortunately, some of the forum features have been disabled since the database errors a few weeks ago.  It will hopefully return soon.

---

