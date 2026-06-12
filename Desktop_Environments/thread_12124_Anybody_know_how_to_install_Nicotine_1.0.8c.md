---
title: "Anybody know how to install Nicotine 1.0.8c?"
date: 2005-01-22
forum: Desktop Environments
---

### Post by clparker on 2005-01-22
Anybody know how to install Nicotine 1.0.8c?
 That's the latest version of the Soulseek Client for Linux. Anybody know how to install it on Ubuntu? I downloaded the .deb file and would love to know how to use it.

---

### Post by Error1312 on 2005-01-22
Doesn't 'sudo apt-get install nicotine' work? It did for me.

---

### Post by eNiNjA on 2005-01-22
[QUOTE=clparker]Anybody know how to install Nicotine 1.0.8c?
 That's the latest version of the Soulseek Client for Linux. Anybody know how to install it on Ubuntu? I downloaded the .deb file and would love to know how to use it.[/QUOTE]
 did ya try sudo dpkg -i ?

---

### Post by barbarian on 2005-01-22
What nikotin has, that limewire hasn't?

---

### Post by clparker on 2005-01-22
> user@UBUNTU:~ $ sudo apt-get install nicotine
Reading Package Lists... Done
Building Dependency Tree... Done
nicotine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
 
 
 See, it does that wheh i try to install it. I have 1.0.7 and I wont use Limewire because It's not a soulseek client. If you've never used the network, then you dont know what your missing.
 
 now as of that 
  > user@UBUNTU:~ $ sudo dpkg -i
dpkg: --install needs at least one package archive file argument
 please help, because when i figure this out, I'm gonna write a bad ass how to that's gonna change the world.

---

### Post by barbarian on 2005-01-22
> If you've never used the network, then you dont know what your missing. 

Ha ha ha, I have never used network, say it to somebody else =D> 

What's wrong about LimeWire? For my mp3's library it's fit perfectly, for the movies I use azareus;)

---

### Post by DJ_Max on 2005-01-22
[QUOTE=clparker]See, it does that wheh i try to install it. I have 1.0.7 and I wont use Limewire because It's not a soulseek client. If you've never used the network, then you dont know what your missing.
 
 now as of that 
  
 please help, because when i figure this out, I'm gonna write a bad ass how to that's gonna change the world.[/QUOTE]

You have to tell the program what package to install.

You need to move to the directory the file is in, and issue
```
sudo dpkg -i PACKAGE-xx.deb
``` 
Replace PACKAGE-xx.deb with the correct filename.

---

### Post by clparker on 2005-01-23
Bear with me, I'm still learning...
 
 > 
user@UBUNTU:~ $ sudo dpkg -i nicotine_1.0.8rc1-1.1_all.deb
(Reading database ... 78930 files and directories currently installed.)
Preparing to replace nicotine 1.0.7-1 (using nicotine_1.0.8rc1-1.1_all.deb) ...
Unpacking replacement nicotine ...
dpkg: dependency problems prevent configuration of nicotine:
 nicotine depends on python (>= 2.4); however:
  Version of python on system is 2.3.4-1ubuntu1.
dpkg: error processing nicotine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nicotine
 
 
 So now i have to upgrade python?

---

### Post by az on 2005-01-23
Go here:
[http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/](http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/)

Download the three source files.  (orig.tar.gz, diff.gz and dsc)

cd to the directory
dpkg-source -x nicotine_1.0.8rc1-1.1.dsc
cd nicotin*
sudo dpkg-buildpackage -d
cd ..
dpkg -i nicotine*.deb

It depends on python 2.4, but you are forcing it to use 2.3.  This may or may not be a problem.  Please let me know.  It runs, but I do not know if everything (anything) works.

Yes, I should use fakeroot, but I am lazy.

---

### Post by clparker on 2005-01-24
that did it boss, E-mail me, and we can work out the details of the how-to guide we can throw together.

---

### Post by az on 2005-01-24
How about you write what you did to get it to work and you add what you need to do to make it work behind a firewall?


And while you are at it, check with the backports people if they want it.  (there is a backports cheatsheet thread...)

---

### Post by clparker on 2005-01-24
**N**icotine is a Linux P2P file sharing client that logs into the soulseek network. It's ability to 'Download Containing Folder(s)' is amazing as the program with simple ease allows you to download entire albums, or even an artist's complete discography. It's features are geared towards music, and it lets you set up a buddy list so you can begin trading your favorite music who share your interests. It's fair to say that the soulseek network with it's privlidged user status makes the Napster of days ago look like a baby's toy. 
   Now many have used:
   ```
	sudo apt-get install nicotine
``` 
   to get the 1.0.7 version default with Ubuntu 4.10 'Warty Warthog'
    However if you follow these steps you *should *be able to get the latest version running on your system.
    (right click > copy link locataion)
      ```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.diff.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.diff.gz") 
   
``` 
   (right click > copy link locataion)
    ```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.dsc]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.dsc") 
   
``` 
   (right click > copy link locataion)
    ```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1.orig.tar.gz") 
   
```  
   ```
	dpkg-source -x nicotine_1.0.8rc1-1.1.dsc
``` 
   ```
	cd nicotin*
``` 
   ```
	sudo dpkg-buildpackage -d
``` 
   ```
	cd ..
``` 
   ```
	sudo dpkg -i nicotine*.deb
``` 
 You should see Nicotine in your Applications > Internet. If not reboot. Your gonna need to simply just make up a user name and password under File > Settings.
 Once you run a search and find something you like, download the whole album, and once you get a good reputation on the network, you can download whole discographies.
    For more information see [http://nicotine.thegraveyard.org/]("http://nicotine.thegraveyard.org/")

---

### Post by clparker on 2005-01-24
Somebody look at that, if that looks good, i'm gonna post something like that in a how-to.

---

