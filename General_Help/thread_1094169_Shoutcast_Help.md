---
title: "Shoutcast Help"
date: 2009-03-12
forum: General Help
---

### Post by sports fan Matt on 2009-03-12
How Would I run this application? [http://www.shoutcast.com/download-files](http://www.shoutcast.com/download-files)

---

### Post by oldos2er on 2009-03-12
Have you read README.TXT?

---

### Post by kmac on 2009-03-12
1044 posts and can't build from source?

sudo apt-get install build-essential

Extract the tar.gz file to a new folder (I suggest /home/user/installers/shoutcast)

cd into the folder.

```

./configure
make 
sudo make install

```

It might be different for that package, so do what oldos2er said and read the README file.

---

### Post by sports fan Matt on 2009-03-12
kmac,honestly never have had to..always a 1st for something :)

---

### Post by oldos2er on 2009-03-12
It isn't source code, it's already compiled.

---

### Post by kmac on 2009-03-12
> **oldos2er said:**
> It isn't source code, it's already compiled.

Ah, I see. I hadn't even opened the archive. (Oops!)

Straight from README:

[QUOTE=README]
Installation:



Windows:  The provided installer will automatically install the DNAS,

an uninstaller, and Start Menu shortcuts.



Unix versions:  Use gunzip and tar to decompress and extract the necessary

binaries for your particular operating system.  When complete, you should

have three files:  the server binary, server config file, and this readme.

Make certain the server is chmod u+x, and that the config file is readable

by the user you want to run the server as.  The server does *not* need to

be run as root, unless you want to use port numbers below 1024 to serve

SHOUTcast audio streams.







Configuration:



Windows:  Launch the GUI SHOUTcast DNAS by going to Start Menu -> SHOUTcast

DNAS.  Click on Edit Config in the menu bar, and a text editor will appear 

with the configuration file for the SHOUTcast server.  When finished, save 

your changes, and kill the GUI server.  You have to restart the DNAS for 

changes to take effect.



Unix:  Edit the sc_serv.conf file in the text editor of your choice.  Tom

would prefer you use Emacs, because it makes Justin really mad.  Justin would

prefer you use vi, because he thinks Tom suffers from some vicious malaise.

You'll probably be lame and end up using Pico.



There's additional documentation available on the parameters on shoutcast.com

in the documentation section.


[/QUOTE]

---

### Post by Naiki Muliaina on 2009-03-13
Read the following link for a guide on running that program. Its the only shoutcast broadcasting software that really works for me on Linux.

[Linky to Shoutcast guide]("http://naiux.wordpress.com/2009/01/24/linux-shoutcast-guide-part-1/")

The read me is ruddy awful for that thing. Pointless, unhelpful silly thing ^^

---

