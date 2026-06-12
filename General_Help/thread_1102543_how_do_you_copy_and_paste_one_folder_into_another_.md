---
title: "how do you copy and paste one folder into another via the terminal?"
date: 2009-03-21
forum: General Help
---

### Post by coops351 on 2009-03-21
im trying to copy and paste one folder to another, and i know the konsole is another way of doing it, how to you copy this folder; 

/home/luke/Ark Files

to this folder;

/usr/share/amsn


cheers for the help

---

### Post by hikaricore on 2009-03-21
What exactly do you need to copy into a root owned directory?

> sudo cp -R /home/luke/Ark\ Files/* /usr/share/amsn

Will do the trick but make sure you're not going to muck something up :p

p.s. text terminals don't really use copy and paste when it comes to directories

---

### Post by boof1988 on 2009-03-21
> **coops351 said:**
> im trying to copy and paste one folder to another, and i know the konsole is another way of doing it, how to you copy this folder; 

/home/luke/Ark Files

to this folder;

/usr/share/amsn


cheers for the help

Is the space in "*Ark Files*" giving you problems? ;)  A back-slash "\" is used to "escape" the space in between the words.  So you just type the back-slash and then the space as shown in the following.  I am (slowly) trying to eliminate spaces in my storage directories so that I don't have to deal with the escape.

To **copy** the folder (and it's contents)... provided you have proper permissions:

```
sudo cp -r /home/luke/Ark\ Files /usr/share/amsn/
```

And will result in *Ark Files* and it's contents being copied into */usr/share/amsn* indicated as the following:

```
/usr/share/amsn/Ark\ Files
```

If you wish to **cut-paste** (or move) the directory and contents of */home/luke/Ark\ Files* to [I]/usr/share/amsn
[/I] use:

```
sudo mv /home/luke/Ark\ Files /usr/share/amsn/
```

The -r (for recursive) is not needed to mv (move).

Also the *sudo* is probably needed because (on my system) the */usr/share/* directory does not allow writing to it by anyone but root.

Also (when you can) check out the man pages for cp and mv (if you haven't done so yet):

```
man cp
man mv
```

---

