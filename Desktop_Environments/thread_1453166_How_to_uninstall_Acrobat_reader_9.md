---
title: "How to uninstall Acrobat reader 9 ?"
date: 2010-04-12
forum: Desktop Environments
---

### Post by ujjwalkp on 2010-04-12
Hi,

I installed Acrobat reader 9 from adobe website on my amd64 laptop. This is 32 bit version which i forcefully installed. I could not find a way to uninstall the same.

If I do apt-get remove acroread, it does not find a package because i did not install it from repositories. Did not find any uninstall script in Adobe installation directory. Any idea how do i completely remove the package and its traces ? 

If I want to install amd64 bit version, what repository I should add in my sources?

Thanks
Ujjwal

---

### Post by crichard on 2010-04-13
There is no 64 bit adobe reader for linux right now. You can use 32 bit apps in 64 bit OS without any problem. I don't know how you installed Adobe reader but if you want to uninstall it try these two keywords on the search box of Synaptic Package Manager, > acroread  or > adobereader  The installed versions will be listed there, then you can uninstall there. Let me know the result.

---

### Post by ujjwalkp on 2010-04-14
I installed from [http://get.adobe.com/reader/](http://get.adobe.com/reader/) . I am running 32 bit version. Since I directly installed from downloaded file, I am not sure if it made entry in apt cache because

apt-cache search <acroread/adobereader> gives me nothing.

Well, this version has been running fine except gnome global menu because of 32 bit version, So i was wondering if i get 64bit version, things would run smooth, also read out loud does not work with this version.

---

### Post by crichard on 2010-04-14
What's the output of the following command
> locate adobereader

[U]My suggestion:
[/U]Next time if you want to install adobe reader, install it from Synaptic Package Manager or download .deb package from [http://get.adobe.com/reader/](http://get.adobe.com/reader/)
It's under *Different language or operating system?* link,
then pick* Linux x86(.deb*) package to download.

---

### Post by Rendsvig on 2012-02-09
Sorry to revive, but I did something similar, but in 12.04 64 bit: downloaded Adobe Reader from Adobe's website, ran it which opened software center where I chose to install it.

To remove it I used
```
sudo apt-get purge adobereader-enu 
```
which did the trick.
I then ran
```
sudo apt-get autoremove
```
to clean up, and now it's gone.

---

### Post by Pilot6 on 2012-02-09
Now there is 64-bit acroread in Ubuntu Partners repository.
Just add it and install acroread.

---

### Post by panvag on 2013-01-05
> **Rendsvig said:**
> Sorry to revive, but I did something similar, but in 12.04 64 bit: downloaded Adobe Reader from Adobe's website, ran it which opened software center where I chose to install it.

To remove it I used
```
sudo apt-get purge adobereader-enu 
```which did the trick.
I then ran
```
sudo apt-get autoremove
```to clean up, and now it's gone.


Nice !

---

