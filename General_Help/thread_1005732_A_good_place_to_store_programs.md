---
title: "A good place to store programs?"
date: 2008-12-08
forum: General Help
---

### Post by johnnyxxxcakes on 2008-12-08
Where is a good place to store programs? Example: I downloaded, and compiled from source, both Allegro-4.2.2 game dev for C++, and Python 2.6, but they're stored in the /home folder. Is that a good place to store files? I don't think it's good to mix that up with basic things such as music, pictures, or videos, is it?

---

### Post by ohzopants on 2008-12-08
You won't lose or gain any functional by placing programs in other places, but I agree that's it's probably not the best idea to store that stuff in your home folder.

I tend to place programs I download manually in /opt/; there's no particular reason for this, it's just a folder I chose for this purpose.

The "make install" part of compiling some programs will make links for you, so if you move the programs now the links may become invalid.

Usually I place my programs in /opt and then just make links to them in /usr/bin.

---

### Post by Keith Hedger on 2008-12-08
I think its more usual ( though not cast in stone!) to install programs to /usr/local/bin, at least most install scripts will put them there unless you tell them otherwise

---

### Post by cmay on 2008-12-08
> **johnnyxxxcakes said:**
> Where is a good place to store programs? Example: I downloaded, and compiled from source, both Allegro-4.2.2 game dev for C++, and Python 2.6, but they're stored in the /home folder. Is that a good place to store files? I don't think it's good to mix that up with basic things such as music, pictures, or videos, is it?
nothing happens doing this. in fact i suggest t do this if it is program one has written for one self. but i can not see why there should not be a makefile and install scripts with the compiled programs you have. i do not know the exact programs yu have but the few times i have compiled from source the install procedure let it install using configure make make install just as its supposed to do. /opt is most used as a place to store commercial programs as i think of it. it is on solaris anyway. i must confess i do not know if it is that way on linux that a commercial program would like to have the /opt folder per default or not since i only use apt-get and if i really have to then use compiling from source.

---

### Post by snova on 2008-12-08
The typical place for compiled programs is /usr/local. That directory exists for this purpose, in fact- localally installed programs.

I don't like messing with /usr/local for various reasons, however, so I prefer to install to ~/Install/Appname-Version.

---

### Post by russo.mic on 2008-12-08
[www.linuxcommand.org](www.linuxcommand.org)

The first section spells this out really well.  Nice tour of the linux environment.  The rest is great for learning bash.

Russo

---

### Post by toucher5 on 2008-12-08
It's really a preference not necessarily anything you have to do. You can have your compiled programs in your home directory but I would put a '.' in front of the folder name so that it is hidden.
Or if you want to make sure that nothing gets changed by mistake just do the following 'sudo mv ~/yourprogramfolder /'

This will place it into the root directory. 

Then do this 'sudo chmod -R 755 /yourprogramfolder'

This will change the permissions of everything so that you can navigate to the folder but to make changes you will have to use the sudo command.

Or

You could look at some sites to see if the program is offered in a .deb format.
[http://www.getdeb.net/](http://www.getdeb.net/) is a good one. There are many but this one is a canonical site.

I hope this helps.

---

### Post by snova on 2008-12-08
Please do not put anything in the root directory, it is not meant for this sort of thing (or anything at all except what is already there). /opt would be better in this example.

---

### Post by Alvinius on 2008-12-08
Opening a world of headaches there for a lot of users Toucher5

---

### Post by johnnyxxxcakes on 2008-12-08
Thanks for the info guys, but here's another question:

When I compiled Python 2.6 from source, I moved the folder where I did all the ./configure, make, and then make install to the directory /home/john.

[http://i33.tinypic.com/2djnywj.jpg](http://i33.tinypic.com/2djnywj.jpg)

But I see Python in the /usr/local/bin folder as well. Is it safe to delete the Python-2.6 folder in /home/john?

[http://i33.tinypic.com/2qtzd37.jpg](http://i33.tinypic.com/2qtzd37.jpg)

---

### Post by HotShotDJ on 2008-12-08
> **johnnyxxxcakes said:**
> But I see Python in the /usr/local/bin folder as well. Is it safe to delete the Python-2.6 folder in /home/john?No.  Don't do that.  You'll had a devil of a time uninstalling it later.

What I think you did was compile it in the directory in you home folder, and then ran something like sudo ./make install -- that installed the software on the system.  It is not running from your home directory.

The "proper" place for that directory is probably /usr/src in a subdirectory ... for example, /usr/src/Python.  But there is no reason not to keep it in your home folder.  What I would do is create a subdirectory in home called /home/johnnyxxxcakes/custom_software and then move the stuff there.

---

