---
title: "!!HELP!! How to Install Programs !!HELP!!"
date: 2009-06-07
forum: General Help
---

### Post by Kaaku on 2009-06-07
[CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE]
[/CENTER]

Ok so I know how to get games/Programs off of "synaptic" But! when it comes to downloading [SIZE=1]**_"Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"   _**Off of a Linux Download on the site I cant do it! OK heres exactly what i do..

(I have never used Linux) Also I am running on Ubuntu the newest version!

1. I go to the game I want to download.. as in this example it is "[/SIZE][SIZE=1]**_Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"  _**So now.. I go to download select the LINUX download then it downloads no problem...

2. I select the file I downloaded.. I click on it and there are 2 files... (a Read ME File) and "CounterStrike2D" witch is the game! When I double click on it a box pops up like this..
[IMG]http://i41.tinypic.com/11ta04g.png[/IMG]

So i dont know if i need to get something from [/SIZE]"synaptic" or what to be able to read these files..

REMEMBER: I have never used Linux!
Please help![SIZE=1][B][U][IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]


[/U][/B][/SIZE][CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][/CENTER]

---

### Post by sahabcse on 2009-06-07
Try command line package installation for more info follow below url 

[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by colau on 2009-06-07
> **Kaaku said:**
> [CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE]
[/CENTER]

Ok so I know how to get games/Programs off of "synaptic" But! when it comes to downloading [SIZE=1]**_"Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"   _**Off of a Linux Download on the site I cant do it! OK heres exactly what i do..

(I have never used Linux) Also I am running on Ubuntu the newest version!

1. I go to the game I want to download.. as in this example it is "[/SIZE][SIZE=1]**_Counter-Strike 2D for [IMG]http://www.cs2d.com/img/os_linux.gif[/IMG] Linux"  _**So now.. I go to download select the LINUX download then it downloads no problem...

2. I select the file I downloaded.. I click on it and there are 2 files... (a Read ME File) and "CounterStrike2D" witch is the game! When I double click on it a box pops up like this..
[IMG]http://i41.tinypic.com/11ta04g.png[/IMG]

So i dont know if i need to get something from [/SIZE]"synaptic" or what to be able to read these files..

REMEMBER: I have never used Linux!
Please help![SIZE=1][B][U][IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]


[/U][/B][/SIZE][CENTER][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][SIZE=1]**_[IMG]http://www.cs2d.com/img/os_linux.gif[/IMG]_**[/SIZE][/CENTER]

To install a package.
```

sudo apt-get install <packagename>

```

---

### Post by Kaaku on 2009-06-07
> **colau said:**
> To install a package.
```

sudo apt-get install <packagename>

```


How do I find the packageName?

---

### Post by chronographer on 2009-06-07
To run it (from the readme) you need to (in a terminal):

```
sudo apt-get install libstdc++5
```

to install a required library. Then change the permissions of the file to make it executable:
chmod 777 (path/to/file) (or drag and drop the counter strike file into terminal)

now just run it, either by double clicking, or by drag and drop into a terminal and press enter.

Problem, it doesn't work for me... says: 

```
Error: Failed to load image
gfx/player/t1.bmp
```

you need to download the zip file too: [http://www.unrealsoftware.de/get.php?cid=1073744165&get=cs2d_0114_linux.zip&p=1](http://www.unrealsoftware.de/get.php?cid=1073744165&get=cs2d_0114_linux.zip&p=1)

---

### Post by chronographer on 2009-06-07
Now we have it all down. We can 'install' it. Unzip the folder I mentioned above onto your desktop. Drop the CounterStrike2D file into it. Now at the terminal type:
```
sudo cp -r /home/alex/Desktop/CS2D /opt/
```

this places it somewhere good. Now we can sym link it into the place where Ubuntu looks for executables:

```
sudo ln -s /opt/CS2D/CounterStrike2D /usr/bin/
```

now you can run it from the command line.

To add it to your menu right click the applications menu and add an entry into games with the command "/usr/bin/CounterStrike2D"

---

### Post by Kaaku on 2009-06-07
> **chronographer said:**
> Now we have it all down. We can 'install' it. Unzip the folder I mentioned above onto your desktop. Drop the CounterStrike2D file into it. Now at the terminal type:
```
sudo cp -r /home/alex/Desktop/CS2D /opt/
```this places it somewhere good. Now we can sym link it into the place where Ubuntu looks for executables:

```
sudo ln -s /opt/CS2D/CounterStrike2D /usr/bin/
```now you can run it from the command line.

To add it to your menu right click the applications menu and add an entry into games with the command "/usr/bin/CounterStrike2D"

This is what I get when I try to do that command in the termanal:

```
jake@Jake-Computer:~$ sudo apt-get install libstdc++5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jake@Jake-Computer:~$ 
```

hmm...?

---

### Post by colau on 2009-06-07
> **Kaaku said:**
> This is what I get when I try to do that command in the termanal:

```
jake@Jake-Computer:~$ sudo apt-get install libstdc++5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jake@Jake-Computer:~$ 
```

hmm...?
Close the Synaptic window if you are running the Synaptic.
Or being root 
```

gedit /var/lib/dpkg/lock 

```
delete everything there and saving this file close the window.

---

### Post by Kaaku on 2009-06-07
> **colau said:**
> Close the Synaptic window if you are running the Synaptic.
Or being root 
```

gedit /var/lib/dpkg/lock 

```delete everything there and saving this file close the window.
Ok.. Colau, I did that and I received this:
[IMG]http://i40.tinypic.com/30xgyh1.png[/IMG]

---

### Post by Kaaku on 2009-06-07
This is very confusing is it just Counter-Strike? because I got a file called

"TileRacer0.702_Setup.sh" the ".sh" isint that a linux thing?

Well if I have "TileRacer0.702_Setup.sh" on my desktop can I just like Install it?

Well I click on it and NOTHING happens... This is very annoying... 

Why is this so hard..?

Also, When i downloaded "TileRacer0.702_Setup.sh" I downloaded it for "LINUX" so it should be for Linux!

---

### Post by colau on 2009-06-07
> **Kaaku said:**
> Ok.. Colau, I did that and I received this:
[IMG]http://i40.tinypic.com/30xgyh1.png[/IMG]
```

sudo gedit /var/lib/dpkg/lock

```

---

### Post by 3rdalbum on 2009-06-07
> **Kaaku said:**
> Well I click on it and NOTHING happens... This is very annoying... 

Why is this so hard..?

It's not hard, you're just getting a lot of general suggestions because:

1. Nobody is familiar with what you're trying to install (please post a link to the file you downloaded)
2. You're trying to apply Windows-user knowledge to Ubuntu.

Generally you should be trying to find your Ubuntu software in the package manager (Synaptic Package Manager). If there is nothing there that will do, you should be looking for a third-party repository to add to your package manager. If there's no repository for the program, then you should look for a Debian package (.deb). If there isn't one, then you should look for a binary installer, assuming you know how to use one.

If all that is available is source code, then you'd have to compile it. But you see, don't make more work for yourself than necessary: When looking for software, follow my procedure! You don't want to be compiling everything when it's all available to install in two clicks.

For Tile Racer, I know that there is a Debian package from [www.getdeb.net](www.getdeb.net). I've got it installed.

If you must run one of those binary installers (that end in .sh or .bin or .run), then you need to make them executable by root in the terminal:

```
sudo chmod a+x <after the "x", press the space bar and then drag the file into the terminal, then run the command>
```
```
sudo <after the "o", press the space bar and then drag the file into the terminal, then run the command>
```

The first command makes the program executable (it's part of the Linux security system, it can be done graphically but it's quicker on command-line). The second command will run the program. Both commands run as root - that's because only root can install software into system-wide locations.

If you could post a link to the page where you downloaded the software, we can give more precise help.

EDIT: Why on earth did someone tell you to edit the lock file? There's no need for that, so don't worry about it. Just make sure you're not running multiple package managers at the same time.

---

### Post by Kaaku on 2009-06-07
> **3rdalbum said:**
> It's not hard, you're just getting a lot of general suggestions because:

1. Nobody is familiar with what you're trying to install (please post a link to the file you downloaded)
2. You're trying to apply Windows-user knowledge to Ubuntu.

Generally you should be trying to find your Ubuntu software in the package manager (Synaptic Package Manager). If there is nothing there that will do, you should be looking for a third-party repository to add to your package manager. If there's no repository for the program, then you should look for a Debian package (.deb). If there isn't one, then you should look for a binary installer, assuming you know how to use one.

If all that is available is source code, then you'd have to compile it. But you see, don't make more work for yourself than necessary: When looking for software, follow my procedure! You don't want to be compiling everything when it's all available to install in two clicks.

For Tile Racer, I know that there is a Debian package from [www.getdeb.net]("http://www.getdeb.net"). I've got it installed.

If you must run one of those binary installers (that end in .sh or .bin or .run), then you need to make them executable by root in the terminal:

```
sudo chmod a+x <after the "x", press the space bar and then drag the file into the terminal, then run the command>
``````
sudo <after the "o", press the space bar and then drag the file into the terminal, then run the command>
```The first command makes the program executable (it's part of the Linux security system, it can be done graphically but it's quicker on command-line). The second command will run the program. Both commands run as root - that's because only root can install software into system-wide locations.

If you could post a link to the page where you downloaded the software, we can give more precise help.

EDIT: Why on earth did someone tell you to edit the lock file? There's no need for that, so don't worry about it. Just make sure you're not running multiple package managers at the same time.

OK, So far I got the "Tile Racer" To be executable, Then I ran it... 
It installed then I don't know were it saved... I want it to be in  "Games"

OK now for the counterstrike info..
Site: [http://www.cs2d.com/](http://www.cs2d.com/)
Download page: [http://www.cs2d.com/download.php](http://www.cs2d.com/download.php)
Download Link: [http://www.unrealsoftware.de/get.php?get=cs2d_0114_linux.zip](http://www.unrealsoftware.de/get.php?get=cs2d_0114_linux.zip)

There, I don't understand why this is so confusing? Like I mean I was told "Linux" Operating system is AMAZING! for games...

Also I don't get why this is bringing me trouble.. I clicked the "Linux" Download..

I'm using Ubuntu.

Thanks!

---

### Post by Kaaku on 2009-06-07
> **3rdalbum said:**
> It's not hard, you're just getting a lot of general suggestions because:

1. Nobody is familiar with what you're trying to install (please post a link to the file you downloaded)
2. You're trying to apply Windows-user knowledge to Ubuntu.

Generally you should be trying to find your Ubuntu software in the package manager (Synaptic Package Manager). If there is nothing there that will do, you should be looking for a third-party repository to add to your package manager. If there's no repository for the program, then you should look for a Debian package (.deb). If there isn't one, then you should look for a binary installer, assuming you know how to use one.

If all that is available is source code, then you'd have to compile it. But you see, don't make more work for yourself than necessary: When looking for software, follow my procedure! You don't want to be compiling everything when it's all available to install in two clicks.

For Tile Racer, I know that there is a Debian package from [www.getdeb.net]("http://www.getdeb.net"). I've got it installed.

If you must run one of those binary installers (that end in .sh or .bin or .run), then you need to make them executable by root in the terminal:

```
sudo chmod a+x <after the "x", press the space bar and then drag the file into the terminal, then run the command>
``````
sudo <after the "o", press the space bar and then drag the file into the terminal, then run the command>
```The first command makes the program executable (it's part of the Linux security system, it can be done graphically but it's quicker on command-line). The second command will run the program. Both commands run as root - that's because only root can install software into system-wide locations.

If you could post a link to the page where you downloaded the software, we can give more precise help.

EDIT: Why on earth did someone tell you to edit the lock file? There's no need for that, so don't worry about it. Just make sure you're not running multiple package managers at the same time.

Ok, Well I Found the Tiles Race "Game" file!
Its was in "usr/local/games/game-was-here/" 
It is VERY! VERY! laggy! Why?

Thanks..

Read my Post above!

---

### Post by Kaaku on 2009-06-07
bump

with

umm..

cheese"?

---

### Post by chronographer on 2009-06-07
I suggest you spend some time becoming familiar with the operating syustem. Read this for info on installing software on Linux (Ubuntu in particular): [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Now, as for games. Try some of the packaged games which come with Linux first: Go to Applications, Add/Remove software, then click 'games' and in here rearrange so that the 5 star games are at the top, look through here for games you find interesting. I would recommend:
[LIST=1]
[*]Widelands
[*]Open arena
[*]Alien arena
[*]scorched 3D
[*]tremulous
[*]blob wars
[/LIST]

Another great game is Astromenace. Hours of fun: [http://www.viewizard.com](http://www.viewizard.com)

There is a ppa here with it in it: [https://launchpad.net/~rzr-team/+archive/ppa]("https://launchpad.net/~rzr-team/+archive/ppa")

You need to add it to your sources list, along with a key, follow instructions on the web site.

---

### Post by chronographer on 2009-06-07
Ah yes, check my previous posts for the counterstrike2D install. The reason you had that problem running apt-get install is that you had another package manager running at the same time. This would be either synaptic, add/remove software or the updater.

---

### Post by Kaaku on 2009-06-08
> **chronographer said:**
> I suggest you spend some time becoming familiar with the operating syustem. Read this for info on installing software on Linux (Ubuntu in particular): [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Now, as for games. Try some of the packaged games which come with Linux first: Go to Applications, Add/Remove software, then click 'games' and in here rearrange so that the 5 star games are at the top, look through here for games you find interesting. I would recommend:
[LIST=1]
[*]Widelands
[*]Open arena
[*]Alien arena
[*]scorched 3D
[*]tremulous
[*]blob wars
[/LIST]

Another great game is Astromenace. Hours of fun: [http://www.viewizard.com](http://www.viewizard.com)

There is a ppa here with it in it: [https://launchpad.net/~rzr-team/+archive/ppa]("https://launchpad.net/%7Erzr-team/+archive/ppa")

You need to add it to your sources list, along with a key, follow instructions on the web site.

Ok so...

I have these:

```
deb [http://ppa.launchpad.net/rzr-team/ppa/ubuntu](http://ppa.launchpad.net/rzr-team/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/rzr-team/ppa/ubuntu](http://ppa.launchpad.net/rzr-team/ppa/ubuntu) karmic main
```

how do I add this?

Also I have been playing Alien Arena for like 4 hours now.. And Is Open Arena Like it>?

---

### Post by 3rdalbum on 2009-06-08
> Packages contain the binary only. You have to download the full WIN Zip-Archive (above) too!
Please read the included txt-file for details.

Did you download the Windows zip archive? The website explains (in technical language, regrettably) that the Linux download is JUST the actual game engine, and you need to also download the Windows package to get the actual levels, sprites, sound effects, etc.

Not the best way of packaging the program, but oh well.

How to use:



- get full CS2D at [www.cs2d.com/download](www.cs2d.com/download)


(this is the Windows package that contains the levels and stuff)

- extract the archive to a folder of your choice

- copy this binary into this folder


(Copy the CounterStrike2D program file that you initially downloaded, into the folder where you extracted the levels)

- Install libstdc++5 or higher with your package manager


(Don't worry about this, it's already installed)

- run it

(How I told you to run programs, but DON'T put "sudo" in front of it)


The reason why you're finding this confusing is because you're trying to do things the Windows way (going to the Internet in search of games). Stick to the repositories and Deb packages.

If you want Tile Racer in your Applications menu, you need to create a menu item for it. Right-click the Applications menu and you'll get an option to "Edit Menus". This is another good reason to use Deb packages, as they more often have menu items automatically created for them.

You shouldn't ever need to look around for where a file has been installed. If it's a program that's been installed to your filesystem, you can run it by typing its name into the terminal.

You'll need to post system specs in order for us to know why this game isn't running well for you. Tile Racer does seem to require a reasonably good system; your graphics card should have been made in the last two years.

If you switched to Ubuntu because you heard it's good for games... then you probably won't be here for long. The quality and quantity of games in the open-source world is nothing compared to the proprietary software world. But there are some very addictive games for Linux :-)

---

