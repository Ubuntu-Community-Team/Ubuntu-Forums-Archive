---
title: "please insert ubuntu cd.. what cd! this is the only one I have!"
date: 2006-02-25
forum: Desktop Environments
---

### Post by jimbodot on 2006-02-25
ok

I<m trying to do apt-get install build-essential, and it ask me for my ubuntu cd, I do insert my "install ubuntu cd" and it doesnt take it

WT... now.. do I need to download another cd version( because Ive updated my ubuntu) because I just don't find anything else than install cd iso

---

### Post by taurus on 2006-02-25
Perhaps you need to look in /etc/apt/sources.list and comment out any line that has your CD-ROM on.  Let it use the network then...

```

sudo gedit /etc/apt/sources.list

```

You can comment out lines by placing a # in front of them...  Also, you need to run apt-get as root,

```

sudo apt-get install build-essential

```

---

### Post by jimbodot on 2006-02-25
thx

but now I think I messed up something, I couldnt save with a text editor so Ive open it with open office writer, since it couldnt read some caracter in line 1 of the file, Ive delete that line 1, now it doesnt understand the rest of the file...

If it wasnt for all I did succeed to install, I would wipe out and reinstall

---

### Post by taurus on 2006-02-25
You couldn't save it with gedit!!!  Are you sure you ran this command,

```

sudo gedit /etc/apt/sources.list

```

There is a pic of a floppy disk with the word Save under that...

---

### Post by abhaysahai on 2006-02-26
Please do post your sources.list file here.

---

