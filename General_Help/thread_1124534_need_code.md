---
title: "need code"
date: 2009-04-13
forum: General Help
---

### Post by mrsmither on 2009-04-13
hi
i have just installed ubuntu and i am very impressed:p
but i am trying to make a simple program (you know whith a txt document)
that checks if a cd is in drive and if there is ejects it
any help would be much appreciated!
i'm fascinated by it all and find it realy interesting!
thanx in advance 
mr smither

---

### Post by Copernicus1234 on 2009-04-13
Try typing "eject" in a command prompt. It will open the drive. Its pretty cool. "eject -t" to close it.

So what you want is to write some basic bash code to check if the drive has content and then run the commands above depending on what it says. :)

This was so simple that I wrote some code for you just for fun:

> 
#!/bin/bash

HAS_DISC=`df -k | grep media/cdrom | wc -l`

if [ $HAS_DISC == 0 ]; then
eject -t
else
eject
fi

What the script does is list your devices with the command df -k. If there is a row with media/cdrom in it, you have a cd in the drive so grep will filter out that row from the df -k output. wc -l will list the number of rows outputted (will be 1 row if disc is in drive). This "1" will be put in the HAS_DISC variable. Then the if will check if HAS_DISC is 1 or 0 and act on that.


Put the code in a file somewhere and name it something, make it executable with chmod +x filename and run it with ./filename.

---

### Post by mrsmither on 2009-04-13
thanx for the reply!
i have several problems
one is i can not make exe beacouse it says file or path does not exist
the second is that i can not run it, an eror comes up saying no windows programe avaeble to run file

please help
mr smither

---

### Post by mrsmither on 2009-04-13
anyone?

---

### Post by miegiel on 2009-04-13
try :
```
sh filename
```

filename is the name of the script file you saved ofc

---

### Post by Copernicus1234 on 2009-04-13
> **mrsmither said:**
> thanx for the reply!
i have several problems
one is i can not make exe beacouse it says file or path does not exist
the second is that i can not run it, an eror comes up saying no windows programe avaeble to run file

please help
mr smither

I think you are probably not standing in the same directory as where you saved the file. So do this (im using the /tmp folder as an example).

1) Type "cd /tmp"
2) Type "nano myscript"
3) Paste contents of script above into editor and press CTRL+Z (and answer yes) to save the file.
4) Type "chmod +x myscript"
5) Type ./myscript (this will run it).

---

### Post by mrsmither on 2009-04-13
sorry but it says can't open "filename"

---

### Post by mrsmither on 2009-04-13
a can do evrithing until the save bit:
if i type yes it just keeps on typing "y"
and i cant stop it 
please help

---

### Post by miegiel on 2009-04-13
You're getting "sh: Can't open filename" either because it dosn't exist or because the file can't be found.

I don't know what name you used to save the file or where it is. I only used "filename" as an example. If you follow Copernicus1234's instructions in his last post it should work. He's more knowledgeable then me ;)

> **mrsmither said:**
> a can do evrithing until the save bit:
if i type yes it just keeps on typing "y"
and i cant stop it 
please help

I don't know what you mean to say there

---

### Post by mrsmither on 2009-04-14
thanx to all got it

---

