---
title: "Compiling the XE emulator"
date: 2009-02-24
forum: Gaming &amp; Leisure
---

### Post by pezmanlou on 2009-02-24
I was having some trouble getting XE to compile, but after a little research, this is what worked for me on both 64 bit Intrepid and 64 bit Lenny.

I downloaded the source:
```
wget http://www.xe-emulator.com/files/xe-x86-64-bin.2.16.1.tar.bz2
```

Extracted it:
```
tar -jxvf xe-x86-64-bin.2.16.1.tar.bz2
```

Installed some packages needed for it to compile:
```
sudo apt-get install build-essential libgtk2.0-dev libasound2-dev libxv-dev libxxf86vm1 libxxf86vm-dev
```

Changed directorys:
```
cd xe-x64/
```

Compiled it:
```
sudo make
```

And ran it:
```
./xe
```

In Debian Lenny, it installed fine.

```
$ sudo make install 
xe successfully installed
```

But in Intrepid Ibex:

```
$ sudo make install
[: 37: ==: unexpected operator
Must be logged on as root.
```

```
$ sudo su
# whoami
root
# make install
[: 37: ==: unexpected operator
Must be logged on as root.
```

```
$ sudo ./install.sh 
[: 37: ==: unexpected operator
Must be logged on as root.
```

Clearly, I am root.  Since the binary runs perfectly fine without installing it, I will be running it from this folder.

I'm guessing the dependencies are the same on a 32 bit system.  If someone can verify this, please post a reply.

Lot's of credit goes to this old post:
[http://ubuntuforums.org/showthread.php?t=303561](http://ubuntuforums.org/showthread.php?t=303561) (They had the same installation problem in Ubuntu back in 2006)

Download page for XE:
[http://www.xe-emulator.com/index.php?m=download](http://www.xe-emulator.com/index.php?m=download)

---

### Post by A_arthur_N on 2009-04-13
I was pretty disappointed in the performance of a lot of the Genesis emulators out there and remembered that Xe did a great job when I tried it a couple of years ago.  So I went to try to install it and I ran into the same problem.  

Here is how to install Xe in all its glory:

```

wget http://www.xe-emulator.com/files/xe-x86-32-bin.2.16.2.tar.bz2
tar xvjf xe-x86-32-bin.2.16.2.tar.bz2
cd xe-x86
make

```

now if you run "make install" it will give you the error saying that you must be logged in as root, however we can change the install script so that it will not stop on this error.

```

gedit install.sh

```

delete the following lines:

At the top:
```

if [ `whoami` == root ]; then

```

At the bottom:
```

else

  echo Must be logged on as root.

fi

```

Then run the following command
```

sudo bash ./install.sh

```

ENJOY!

---

### Post by caspertk on 2009-09-27
I deleted the lines specified above. Result:

```

sudo bash ./install.sh
unable copy files to /usr/local/lib/xe

```

I am using ubuntu 9.04 and I was logged in as root.

---

