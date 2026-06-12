---
title: "How to update Punkbuster?"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by feap on 2006-10-22
As punkbuster kicks me out after a short time playing Wolfenstein Enemy Territory True Combat: Elite mod, I've tried updating Punkbuster. I've spent the past two hours trying that. With ./pbweb.x86 I get several "htm-to-binary conversion failed" errors. I don't know how to run pbsetup.run as I get "no permission" with ./pbsetup.run, sh ./pbsetup.run and sudo sh ./pbsetup.run.

I gave write permissions via gksudo nautilus in the alt-F2 prompt to all files in the /pb directories (in usr/local/... and the hidden /etwolf/pb dir), still no game.

And I'm a n00b with Ubuntu in case that wasn't obvious.

---

### Post by Somniis on 2006-10-22
> **feap said:**
> As punkbuster kicks me out after a short time playing Wolfenstein Enemy Territory True Combat: Elite mod, I've tried updating Punkbuster. I've spent the past two hours trying that. With ./pbweb.x86 I get several "htm-to-binary conversion failed" errors. I don't know how to run pbsetup.run as I get "no permission" with ./pbsetup.run, sh ./pbsetup.run and sudo sh ./pbsetup.run.

I gave write permissions via gksudo nautilus in the alt-F2 prompt to all files in the /pb directories (in usr/local/... and the hidden /etwolf/pb dir), still no game.

And I'm a n00b with Ubuntu in case that wasn't obvious.

Errr.. I guess I read your post too fast, didn't see that you already tried that.  :-k 

Have you tried right-clicking pbsetub.run and select "Open"?  Kinda odd that you get permission errors.  Is pbsetup.run in a directory you have write access to?  (without sudo)

i.e. /home/name/PB/pbsetup.run

---

### Post by feap on 2006-10-22
Yes, I double-checked that I have read and write permissions in usr/local/games/enemy-territory/pb directory and all its files. pbsetup.run is in that dir, and I get the error "cannot execute binary file" if I try sh ./pbsetup.run in that directory in the terminal.

---

### Post by Somniis on 2006-10-22
> **feap said:**
> Yes, I double-checked that I have read and write permissions in usr/local/games/enemy-territory/pb directory and all its files. pbsetup.run is in that dir, and I get the error "cannot execute binary file" if I try sh ./pbsetup.run in that directory in the terminal.

Hmm.  Well, I believe usr/local/games requires root access to write to.  You can do a 'sudo -i' to log in as root in the terminal.  I'd try that, or move pbsetup.run to a folder under your home directory.  I know it will work simply because I have it in /home/name/PB/pbsetup.run. :)

If you want to do that via terminal (and you don't know how):
cd first to the dir in which pbsetup.run is in of course
```
sudo mv pbsetup.run /home/name/blah/blah
```

Where '/name/blah/blah' is your user name and whatever folders you want to put it in.

Make sure you move it to an empty folder so the files it downloads won't be mixed up with anything else. :)

When moved, do:
```
./pbsetup.run
```

after cd'ing to the directory.  Hope it works!

---

### Post by feap on 2006-10-22
As I've said, none of the commands work whether pbsetup.run is in my home folder, usr/... or anywhere else. I always get permission denied, even after the "sudo -i" command.

edit: Finally got it working. I needed to do chmod +x ./pbsetup.exe

---

### Post by MrBlond83 on 2006-10-23
[http://www.ubuntuforums.org/showthread.php?t=279918](http://www.ubuntuforums.org/showthread.php?t=279918)

---

### Post by maskil on 2006-12-25
right-click on the pbsetup.run file, have a look at the permissions tab, and then check the "executable" box
that should do it. at least that gave me the permission to execute the file

---

