---
title: "[SOLVED] Octave installation doesn't work"
date: 2008-04-08
forum: Education &amp; Science
---

### Post by steak-sandwich on 2008-04-08
Hey,

I am trying to install octave with synaptic package manager.
During the installation I get the following error

E: /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb: trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4

What should I do now? I don't know how to handle this.

Thx

---

### Post by thisismalhotra on 2008-04-09
> **steak-sandwich said:**
> Hey,

I am trying to install octave with synaptic package manager.
During the installation I get the following error

E: /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb: trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4

What should I do now? I don't know how to handle this.

Thx

First of all make sure you have all the repositories enabled in Synaptic. If, no enable all the repos, hit reload and then try to install it again.

IF it still does not work, go to terminal and run these commands

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get build-dep octave
sudo apt-get install octave
```

If this does not work either, post back I will give you instructions to compile it from source. I am saying this because I recently helped somebody with almost similar issue and the only way we could fix it was to build from the source.

Are you running ubuntu or xubuntu and what version??

LOL .. on the user name I love steaks:lolflag:

---

### Post by steak-sandwich on 2008-04-09
when I use
```
sudo apt-get update
```
I get the following message 
[B]Failed to fetch [http://ubuntu.mirrors.tds.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  302 FoundReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_feisty_free_source_Sources - open (2 No such file or directory)

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]

when I use 
```
sudo apt-get build-dep octave
```
I get the the following 
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_feisty_free_source_Sources - open (2 No such file or directory)
[/B]


where can I enable all the repos in synaptic. sorry, I don't use this program very often. 

I have ubuntu 7.10



Yeah, the user name is really unique.

Thanks

---

### Post by thisismalhotra on 2008-04-09
Well I see the issue, your problem most likely is you dont have all the repos enabled.

Assuming you are connected to a high speed internet, Open Synaptic (I think in System -> Administration). Go Settings -> Repositories and than make sure you check all the repositories(main, universe, restricted, multiverse). Also, if you are in US, replace the 'main server' to 'Server for United States'. Uncheck the Cdrom too. Close it and Press Reload and then find Octave in synaptic and install it.

Alternatively to Enable repos you have to go in System -> Administration -> Software Sources and do the same steps.

Hope that works or else post back.

TC

---

### Post by steak-sandwich on 2008-04-09
okay, everything was already enabled, the only thing I did, I changed to  "Server for US". But when I reloaded I got the same message:
[B][http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found
[/B]

What does that mean? 

But anyway, the octave installation worked out. I installed 2.9.
Actually, I tried to install 3.0 from source but it did not work. Then I changed to synaptic. 
Is there a big difference between 2.9 and 3.0? 

Thanks a lot for your help.

Ben

---

### Post by steak-sandwich on 2008-04-09
for some reasons, it shows me that I installed 2.1 but I enabled 2.9
that's really strange.

---

### Post by thisismalhotra on 2008-04-09
> **steak-sandwich said:**
> okay, everything was already enabled, the only thing I did, I changed to  "Server for US". But when I reloaded I got the same message:
[B][http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found
[/B]

What does that mean? 

But anyway, the octave installation worked out. I installed 2.9.
Actually, I tried to install 3.0 from source but it did not work. Then I changed to synaptic. 
Is there a big difference between 2.9 and 3.0? 

Thanks a lot for your help.

Ben

Ben,

I dont know why those medibuntu sources are there in your sources.list file but they donot come with default ubuntu installation.You must have added them or maybe some app did anyways. You can take it out if you need to and I can help yuou with that.

There is a REAL BIG diffrence with 2.X versions of octave and 3.0 so I recommend using #.0. It will be included by default in hardy but is not in Gutsy at the moment.

I hae other 2 threads where I have helped people in installing 3.0 or compiling it from source.

I would say download the .deb file from this thread

[http://ubuntuforums.org/showthread.php?t=713880](http://ubuntuforums.org/showthread.php?t=713880)

and use instruction from Post #2 on this thread to install it

[http://ubuntuforums.org/showthread.php?t=680690](http://ubuntuforums.org/showthread.php?t=680690)

Should be easy ... cheesy

TC

---

### Post by steak-sandwich on 2008-04-09
oh I remember this thread, I tried that but I got an error message, but it worked out now.
Thanks.

---

### Post by steak-sandwich on 2008-04-09
the only thing which is weird is that the update manager wants to update from 3.0 to 2.9?!

---

### Post by thisismalhotra on 2008-04-09
You will have to bear with it, I have a solution for that, but I will have to make a new .deb file for it ... unfortunately I dont have time right for it ... anyways you can neglect that and just keep working ...

If you are willing to help I can give you instructions and probabaly you can mek the deb for me ... entirely up to you 

Also Can you please mark the thread solved so that other people may find good use of it.

Appreciate it Ben

---

