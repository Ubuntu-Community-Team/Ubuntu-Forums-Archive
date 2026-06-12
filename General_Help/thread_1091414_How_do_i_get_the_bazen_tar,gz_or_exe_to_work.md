---
title: "How do i get the bazen tar,gz or exe to work?"
date: 2009-03-09
forum: General Help
---

### Post by w.g.hanna on 2009-03-09
I like the idea of a party jukebox. Rhythmbox in party mode is ok . . . but I found an application called Bazen which allegedly defaults in kiosk mode and can be operated exclusively with a numeric key pad. it looks like a real easy interface. It's described as: "a PHP and MySQL-driven script, which is capable of indexing music, edit id3-tags and more."

I'm still running hardy on the computer i tried it on, but i ultimately intend to run it on a laptop running intrepid. i'm not as committed to the laptop's operating system, and would be open to trying another distro if that would make a difference. a windows dual boot is out of the question.

I don't know anything about mysql. Synaptic indicates i have mysql-client-5.0 and mysql-common installed. i don't know what php is. i installed every php entry on synaptic that had the ubuntu symbol next to it.

From what i can tell, Bazen is not in the repositories. There are two versions you can download from [http://linux.softpedia.com/get/Multi...ox-34192.shtml](http://linux.softpedia.com/get/Multi...ox-34192.shtml)

One is a tar.gz, the other is an exe

The tar,gz is just a folder full of folders and files that i don't know what to do with.

When i clicked on the exe wine ran me through a windows-esqe installation. Bazen then appears in the wine programs menu (i try to run as close to 100% open source as i practically can, so i don't have alot of experience with wine).

When I click on Bazen, a black screen with text breifly appears on my screen if i'm using kde - in gnome, a few screens do the same, one big and several small screens. they go up and down fast - way to fast for me to see whats on them.

then nothing.

So that's where i'm at. Any ideas?

---

### Post by ianhaycox on 2009-03-09
Off the top of my head, try this.

You need to install Apache (a web server) + MySQL + PHP.

```

sudo apt-get install apache2

```

Then browse to [http://localhost](http://localhost)

and you should be a message 'It Works'

Then enable user directories with

```

$ sudo a2enmod userdir
$ sudo /etc/init.d/apache2 restart

```

Install PHP5

```

$ sudo apt-get install php5 libapache2-mod-php5
$ sudo /etc/init.d/apache2 restart

```

Create a file called test.php with the following line.

<?php phpinfo(); ?>

Make a directory thus:

$ mkdir ~/public_html

and put test.php into public_html then check that [http://localhost/~yourloginname/test.php](http://localhost/~yourloginname/test.php)

displays a load of stuff about PHP

Then install mysql + php hooks remembering the database root password.

```

$ sudo apt-get install mysql-server php5-mysql
$ sudo /etc/init.d/apache2 restart

```

unpack your bazen archive, 

```

$ cd ~/public_html
$ tar xzf your-.gz-file

```


Browse to [http://localhost/~user/jukebox/install-manual.php](http://localhost/~user/jukebox/install-manual.php) and follow the instructions.

Good luck

---

### Post by Slim Odds on 2009-03-09
BaZen looks interesting. Except for the "alpha" status and the "last update" of almost 4 years ago.....

---

