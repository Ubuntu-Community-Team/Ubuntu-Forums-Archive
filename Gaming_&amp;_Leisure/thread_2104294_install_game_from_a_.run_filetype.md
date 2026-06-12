---
title: "install game from a .run filetype?"
date: 2013-01-12
forum: Gaming &amp; Leisure
---

### Post by goodbye-windows(tm) on 2013-01-12
I'm trying to install a program into my 12.10 Xubuntu system. I currently have ver .9x installed, but need to install ver 1.x to access the server.

The software center and synaptic do not list the newer version and the software won't allow me to access the server unless I'm running the newer (ver 1.x) version. 

Sourceforge shows an available 1.x version, but only with a .run extension.

I downloaded the newest version in the available .run filetype and it is on my desktop. I enabled it to run as an executable. There is no typo in the filename, I used copy and paste to get the filename into the terminal command as shown below.

artie@superuser:~/Desktop$ ./PokerTH-1.0-linux-installer.run
artie@superuser:~/Desktop$ 

When the above is run in terminal, it completes instantaneously and doesn't produce an error message. I didn't notice any harddrive activity. But, ver 1.x isn't installed.........

Any idea why I can't install it?

---

### Post by Jakin on 2013-01-12
Nevermind.

---

### Post by holastickboy on 2013-01-12
> **goodbye-windows(tm) said:**
> I'm trying to install a program into my 12.10 Xubuntu system. I currently have ver .9x installed, but need to install ver 1.x to access the server.

The software center and synaptic do not list the newer version and the software won't allow me to access the server unless I'm running the newer (ver 1.x) version. 

Sourceforge shows an available 1.x version, but only with a .run extension.

I downloaded the newest version in the available .run filetype and it is on my desktop. I enabled it to run as an executable. There is no typo in the filename, I used copy and paste to get the filename into the terminal command as shown below.

artie@superuser:~/Desktop$ ./PokerTH-1.0-linux-installer.run
artie@superuser:~/Desktop$ 

When the above is run in terminal, it completes instantaneously and doesn't produce an error message. I didn't notice any harddrive activity. But, ver 1.x isn't installed.........

Any idea why I can't install it?

When I saw the post title, first thing I thought of was ensuring you had it marked as executable, and running it from the terminal... which you already seemed to have  done.

I'm out of ideas, but just letting you know that the basics have been covered, and you aren't making a simple mistake.  Perhaps the download is broken?

---

### Post by DoktorSeven on 2013-01-12
1.0 is available from the Debian/Ubuntu Games Team [PPA](https://launchpad.net/~pkg-games/+archive/ppa).

If you still want to use the .run, note that it's a 32bit binary, so if you have 64bit Xubuntu installed you may need 32bit libraries on your system.

---

### Post by goodbye-windows(tm) on 2013-01-12
Thanks Doktor

I do indeed have a 64 bit machine, but have many 32 bit programs already installed. SO, I never suspected this was an issue.

Do I need to search out and install 32 bit libraries even though they should be present already? If I need to install the 32 bit libraries, is symantic the best way to install them??

I did look at the directions for adding the  Debian/Ubuntu Games Team [PPA]("https://launchpad.net/%7Epkg-games/+archive/ppa").

After selecting my version (12.10) from the dropdown box, I am told to enter these 2 lines into the terminal in order to add the Debian/Games Team PPA:

 ```
deb [http://ppa.launchpad.net/pkg-games/ppa/ubuntu](http://ppa.launchpad.net/pkg-games/ppa/ubuntu) quantal main  
deb-src [http://ppa.launchpad.net/pkg-games/ppa/ubuntu](http://ppa.launchpad.net/pkg-games/ppa/ubuntu) quantal main
```

I get the following error:

```
artie@superuser:~$ deb http://ppa.launchpad.net/pkg-games/ppa/ubuntu quantal main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'dwb' from package 'dwb' (universe)
deb: command not found
artie@superuser:~$
```There are changes made in 12.10, is it possible the deb command has changed???

I did look in the software sources>other software, it doesn't indicate the ppa is present, so this is likely the problem???

TY.

Art

---

### Post by holastickboy on 2013-01-13
sudo apt-get install ia32-libs

This will give you the 32 bit libraries, and doesn't require any special repository!

---

### Post by goodbye-windows(tm) on 2013-01-13
I installed the 32 bit libraries, without errors. I restarted the  computer, and tried to execute the pokerth.run file that's saved on my  desktop. 

I right click on the .run file and select 'execute' from the window that pops up.....but nothing happens. 

So, I'm stuck.

Art

---

### Post by steeldriver on 2013-01-13
I'm not saying it's necessarily the right way to go but fyi to add a ppa the

```
deb http://ppa.launchpad.net/pkg-games/ppa/ubuntu quantal main  
deb-src http://ppa.launchpad.net/pkg-games/ppa/ubuntu quantal main
```lines would NOT go in a terminal they would need to go in a FILE - either your /etc/apt/sources.list file or a custom file in /etc/apt/sources.list.d

Or you could add them via the Software Center --> Edit --> Software Sources... --> Other Software --> Add...

---

### Post by mastablasta on 2013-01-14
> **steeldriver said:**
> Or you could add them via the Software Center --> Edit --> Software Sources... --> Other Software --> Add...
 
this i find convenient. then you refresh/reload the software and search for the game in the software center. new version should appear.

---

### Post by goodbye-windows(tm) on 2013-01-15
> **mastablasta said:**
> this i find convenient. then you refresh/reload the software and search for the game in the software center. new version should appear.


Hi Masta,

I installed the games ppa by adding new entries to the software sources. I have attached a screen capture showing my software sources.

When you say I should 'refresh/reload', does this mean I have to delete the old pokerth program (ver .9x) and then the newer version (ver 1.x) will appear in the software center????

I do have the .run file (latest 1.x ver) on my desktop, but nothing happens when I attempt to execute it or double click on it.

How do I install the new ver 1 software?

TY.

Art

---

### Post by mastablasta on 2013-01-15
> **goodbye-windows(tm) said:**
> When you say I should 'refresh/reload', does this mean I have to delete the old pokerth program (ver .9x) and then the newer version (ver 1.x) will appear in the software center????

 
that might be a good idea. as having different versions of same software in linux is not a trivial thing to do.
 
> 
I do have the .run file (latest 1.x ver) on my desktop, but nothing happens when I attempt to execute it or double click on it.

 
you need to mark it as executable in order to be able to run it. if you mark the file as executable (for example in file properties) and then run it from terminal - that should give any errors if there are any...

---

### Post by goodbye-windows(tm) on 2013-01-15
see message below:

---

### Post by goodbye-windows(tm) on 2013-01-15
> you need to mark it as executable in order to be able to run it.

I marked it as executable long ago and checked again just a few moments ago. It is still marked as executable.

It seems I needed to delete the old version. After that, the software center showed ver 1.0 as now being available. 

After that, I installed it from the software center. Will mark this one 'solved' I sure learned allot::> TY to all who commented.[/QUOTE]

---

