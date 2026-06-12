---
title: "Savage Game installation..."
date: 2005-12-31
forum: Gaming &amp; Leisure
---

### Post by Bloke on 2005-12-31
Hi - when I run the INSTALL.linux file copied from the cd, I get the follow console message:

"This installation doesn't support glibc-2.1 on Linux / x86
Please contact Loki Technical Support at [email]support@lokigames.com[/email]"

How can I get this to install?

Screenshot attached.

---

### Post by ATAQ on 2006-01-02
I also have a problem. When I go to run the game, I get the following:

ataq@ubuntu-laptop:~/Savage$ ./silverback.bin
./silverback.bin: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory
ataq@ubuntu-laptop:~/Savage$ ./savage.bin
Traceback (most recent call last):
  File "<string>", line 10, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/urllib2", line 90, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/socket", line 41, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 347, in doimport
  File "iu.py", line 184, in getmod
  File "iu.py", line 46, in getmod
ImportError: libssl.so.0.9.6: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out
ataq@ubuntu-laptop:~/Savage$



Can someone help me figure this out?
thanks.

---

### Post by dgbauer on 2006-01-02
I get exactly the same error as Bloke up there...  No luck thus far in finding a solution.

---

### Post by Perfect Storm on 2006-01-03
First error:
> error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory

Get libpng2:

```
sudo apt-get install libpng2
```


second error:
> ImportError: libssl.so.0.9.6: cannot open shared object file: No such file or directory

get libssl0.9.6:

```
sudo apt-get install libssl0.9.6
```

---

### Post by Perfect Storm on 2006-01-03
[QUOTE=Bloke]Hi - when I run the INSTALL.linux file copied from the cd, I get the follow console message:

"This installation doesn't support glibc-2.1 on Linux / x86
Please contact Loki Technical Support at [email]support@lokigames.com[/email]"

How can I get this to install?

Screenshot attached.[/QUOTE]


Do you get that error with libstdc++2.10-glibc2.2 installed?

---

### Post by ATAQ on 2006-01-03
I think my setup just lacks dependancies, Can you reccommend any ones that re commonly used in games?
Because there is something I am missing out on.

I have libstdc++5 installed.

Thanks

---

### Post by Perfect Storm on 2006-01-03
You can take a look of mine and take out what you want/need:

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


---

### Post by ATAQ on 2006-01-03
Thanks, is there any packages in those repositorys that you would reccommend I use, that may help with my games problems?

Thanks again

---

### Post by Perfect Storm on 2006-01-03
make sure to enable universe and multiverse, that should be it.

---

### Post by ATAQ on 2006-01-03
how do I do that?

---

### Post by Perfect Storm on 2006-01-03
```
sudo gedit /etc/apt/sources.list
```

when done save and then write in the terminal to update the list:

```
sudo apt-get update
```

---

### Post by ATAQ on 2006-01-03
done, still no difference tho, cant get any of these two games to run.

---

### Post by Perfect Storm on 2006-01-03
Same error? Did you installed the package(s) I suggested?

---

### Post by ATAQ on 2006-01-03
yeah, exact same error, I dont understand what else it could be.

---

### Post by Perfect Storm on 2006-01-03
Where did you install savage?

```

whereis savage
```

---

### Post by ATAQ on 2006-01-03
I installed it in /home/ataq/games/savage

Could this have something to do with it?

---

### Post by Perfect Storm on 2006-01-03
No , I don't thinks so. But this is a shot in the air:

```
cd /home/ataq/games/savage
sh savage
```

---

### Post by ATAQ on 2006-01-03
Its asking me for libtiff.so.3 now but It cant be found in repositorys when i try to apt-get it!

---

### Post by Perfect Storm on 2006-01-03
```
sudo apt-get install libtiff4
cd /usr/lib
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

```

---

### Post by ATAQ on 2006-01-03
It ran there for a second or two and crashed, and the output was:


Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers
There was an error (error 256 - Unknown error 256) running the updater!  bailing out
ataq@ubuntu-laptop:~/games/Savage_Demo$ ./savage.bin
Traceback (most recent call last):
  File "<string>", line 10, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/urllib2", line 90, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/socket", line 41, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 347, in doimport
  File "iu.py", line 184, in getmod
  File "iu.py", line 46, in getmod
ImportError: libssl.so.0.9.6: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out
ataq@ubuntu-laptop:~/games/Savage_Demo$ sh savage

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers
There was an error (error 256 - Unknown error 256) running the updater!  bailing out

---

### Post by ATAQ on 2006-01-03
Itsokay, I got it, I ran it as sudo there and it ran. Thanks for al your help, I really would not have been able to do it with out you.

Thanks Again

---

### Post by Perfect Storm on 2006-01-03
again a shot in the air, I'm not really sure what that error means. I got the full games and never seen that error. It can be something wrong with the demo.

```
 sudo apt-get install xlibs xlibs-data xlibs-dev xlibs-static-dev xlibs-static-pic
```


EDIT: ok, no problem ^^

Remember to make a script to run savage easy

---

### Post by Perfect Storm on 2006-01-03
By the way did you installed savage with sudo? (sudo sh /bla/bla/bla/svage.sh)

---

### Post by ATAQ on 2006-01-03
I think I did actually, but it still needed all those dependancies.
it runs pretty well now

---

### Post by Perfect Storm on 2006-01-03
Okay, but I think when you have the nerve ;) to install it again, do it as normal user :)

---

### Post by ATAQ on 2006-01-03
i am just in the process of it as we speak!! I don't know why i did it as super user,
:p

---

