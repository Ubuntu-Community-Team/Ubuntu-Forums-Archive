---
title: "Help With Installing Java"
date: 2009-03-10
forum: General Help
---

### Post by tigshadorakie on 2009-03-10
Some websites are not working correctly because I believe I do not have the most up to date JAVA software. I went to the JAVA website and it detected that I was running an older version. I clicked the link to download the newest LINUX version. It is a BIN file and the website said it was self extracting? How do I install this?

---

### Post by taurus on 2009-03-10
Which version do you have on your computer right now?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Which version do you have on your computer right now?

Applications -> Accessories -> Terminal
```
java -version
```

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

I have 3 of them which confuses me.

---

### Post by taurus on 2009-03-10
Which version of plugin (java) do you use if you type this in the address bar?

```
about:plugins
```

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Which version of plugin (java) do you use if you type this in the address bar?

```
about:plugins
```

I see a lot of ICED TEA plugins and then a bunch of other ones for shockwave, ext

---

### Post by taurus on 2009-03-10
Are you running x86 (i686) or x86_64?

```
uname -m
```

---

### Post by Neo_The_User on 2009-03-10
Use the Java Sun Download Manager. It does it all for you.

---

### Post by jreiner3 on 2009-03-10
```
sudo update-alternatives --config java
```

shows all the installed versions and which is currently selected as the default, you may want to verify that 1.6.0 is the default.

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> Use the Java Sun Download Manager. It does it all for you.

Where is this download manager? They don't seem to have anything specific for Ubuntu. I am very good with computer hardware and Windows OS's but Linux is like learning a whole new language LOL. I like it though :)

---

### Post by tigshadorakie on 2009-03-10
> **jreiner3 said:**
> ```
sudo update-alternatives --config java
```

shows all the installed versions and which is currently selected as the default, you may want to verify that 1.6.0 is the default.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-6-cacao/jre/bin/jav

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Are you running x86 (i686) or x86_64?

```
uname -m
```

It is 32bit. 686

---

### Post by taurus on 2009-03-10
Did you remember to install the plugin when you installed java?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> Where is this download manager? They don't seem to have anything specific for Ubuntu. I am very good with computer hardware and Windows OS's but Linux is like learning a whole new language LOL. I like it though :)

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_us/-/USD/ViewProductDetail-Start?ProductRef=sdm-2.0-oth-g-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_us/-/USD/ViewProductDetail-Start?ProductRef=sdm-2.0-oth-g-F@CDS-CDS_SMI)

There are no dependencies so just use Alien and convert it to .deb and unpack via gdebi.

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Did you remember to install the plugin when you installed java?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```


Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_us/-/USD/ViewProductDetail-Start?ProductRef=sdm-2.0-oth-g-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_us/-/USD/ViewProductDetail-Start?ProductRef=sdm-2.0-oth-g-F@CDS-CDS_SMI)

There are no dependencies so just use Alien and convert it to .deb and unpack via gdebi.

I downloaded the file but it doesn't do anything. It is on the desktop right now.

---

### Post by taurus on 2009-03-10
Wow!  How come you have edgy in your repos? 

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the repos that have edgy in them or at least put a # in front of them (before the **deb**) to comment them out.  Then save it.

Now run

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

p.s.  If you want to add a repo for wine, there is an intrepid version.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> I downloaded the file but it doesn't do anything. It is on the desktop right now.

Yeah it takes awhile for me to explain on how to do all that if your new to linux. Upgrade to intrepid or Jaunty then do sudo apt-get install sun-java6-plugin sun-java6-bin sun-java6-jdk sun-java6-jre

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Wow!  How come you have edgy in your repos? 

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the repos that have edgy in them or at least put a # in front of them (before the **deb**) to comment them out.  Then save it.

Now run

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

p.s.  If you want to add a repo for wine, there is an intrepid version.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
chris@ChrisUbuntu:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1962B of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse sun-java6-plugin 6-10-0ubuntu2 [1962B]
Fetched 1962B in 0s (10.3kB/s)
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 153683 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-10-0ubuntu2_i386.deb) ...
Setting up sun-java6-plugin (6-10-0ubuntu2) ...
---------------------------------------------
Then it sits at the prompt. Is it done?

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> Yeah it takes awhile for me to explain on how to do all that if your new to linux. Upgrade to intrepid or Jaunty then do sudo apt-get install sun-java6-plugin sun-java6-bin sun-java6-jdk sun-java6-jre

Is there any tutorials on how to use Alien or how to convert and upack different linux files? This is where I get stuck with things. Perhaps I need a good beginners book or something.

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> Is there any tutorials on how to use Alien or how to convert and upack different linux files? This is where I get stuck with things. Perhaps I need a good beginners book or something.

Yes. Consult the documentation for Alien and from Sun Java and look into the READMEs and stuff if you're still stuck. If that doesn't help, [http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

---

### Post by taurus on 2009-03-10
> **tigshadorakie said:**
> 
chris@ChrisUbuntu:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1962B of archives.
After this operation, 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse sun-java6-plugin 6-10-0ubuntu2 [1962B]
Fetched 1962B in 0s (10.3kB/s)
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 153683 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-10-0ubuntu2_i386.deb) ...
Setting up sun-java6-plugin (6-10-0ubuntu2) ...
---------------------------------------------
Then it sits at the prompt. Is it done?

You mean like this prompt, **chris@ChrisUbuntu:~$**?

---

### Post by tigshadorakie on 2009-03-10
Yes. I closed Firefox down and then rechecked the about:plugins. I still see Icedtea but now I also see the Sun version of the plugins in there as well. It still isn't up to date though. Should I still try to get the newest version? I guess what you were saying is that I forgot to do the command for installing the plugins?

---

### Post by Neo_The_User on 2009-03-10
Java in the repos are old. If you want the latest one, you have to go to the java site and download. I never use anything in the Ubuntu repos anymore. Only when a new version just comes out.

---

### Post by taurus on 2009-03-10
> **tigshadorakie said:**
> Yes. I closed Firefox down and then rechecked the about:plugins. I still see Icedtea but now I also see the Sun version of the plugins in there as well. It still isn't up to date though. Should I still try to get the newest version? I guess what you were saying is that I forgot to do the command for installing the plugins?

Reboot.

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> Java in the repos are old. If you want the latest one, you have to go to the java site and download. I never use anything in the Ubuntu repos anymore. Only when a new version just comes out.

I really don't know much about repos and such. I have the bin file that I mentioned earlier. I just need to work on installing it. I have .10 right now and it says there is a .12.

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> I really don't know much about repos and such. I have the bin file that I mentioned earlier. I just need to work on installing it. I have .10 right now and it says there is a .12.

Since your new to Ubuntu, don't do everything against it. I personally do everything against the ubuntu way because its all legacy.

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> Since your new to Ubuntu, don't do everything against it. I personally do everything against the ubuntu way because its all legacy.

alien doesn't seem to be working. It says it is an unknown type of package.

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> alien doesn't seem to be working. It says it is an unknown type of package.

I take back my advice. Pretend I didn't say anything. Sorry for wasting your time.

---

### Post by tigshadorakie on 2009-03-10
> **Neo_The_User said:**
> I take back my advice. Pretend I didn't say anything. Sorry for wasting your time.

You didn't waste my time I got some other stuff working by what you said. Are you saying you were wrong about using Alien to convert?

---

### Post by Neo_The_User on 2009-03-10
> **tigshadorakie said:**
> You didn't waste my time I got some other stuff working by what you said. Are you saying you were wrong about using Alien to convert?

No I'm just saying that if you don't know what you're doing, just stop doing stuff with alien and do things the "Ubuntu way" because its simple.

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> Reboot.

Ok so now I still do not know how to update Java. The repositories don't have the latest Java and the only file I have is a bin and still don't know what to do with it.

---

### Post by taurus on 2009-03-10
If you _really_ want to install that .bin file, you need to move it somewhere and unpack it.  Then, you need to link/configure it so the system would use that new version.  And before you do all that, better to remove the older version from the repos so there won't be a conflict later.

---

### Post by tigshadorakie on 2009-03-10
> **taurus said:**
> If you _really_ want to install that .bin file, you need to move it somewhere and unpack it.  Then, you need to link/configure it so the system would use that new version.  And before you do all that, better to remove the older version from the repos so there won't be a conflict later.

As an update, I followed the directions on the Java website and managed to extract the bin file and it created a java folder. I then found my firefox folder and created a symbolic link in the firefox plugins folder. In the about:plugins page in firefox it now shows the version 12 in there, but has all the other versions still.  

Also, the system is still showing me that I have version 10 installed. The Java website version verification also still tells me that I am running the older version. Is there something I should do next?

---

