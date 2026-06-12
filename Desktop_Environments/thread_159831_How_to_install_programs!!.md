---
title: "How to install programs?!!"
date: 2006-04-13
forum: Desktop Environments
---

### Post by oltix on 2006-04-13
I'm new to Linux and I'm having a lot of problems with it. The biggest problem is that I don't know how to install programs. I have seen the threads here, but they don't help. Please can someone here explain me how to install softwares?

Lets say I have downloaded a program and I have the dowloaded file/s into the desktop, what kind of commands in terminal do I have to do to install it?! 

Thanx!

---

### Post by UbuntuJohan on 2006-04-13
Hi,

It is hard to give a simple answer to that since it depends on what format the file you downloaded is in.

I would recomend that you take a look at [http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")
Even if it doesn't contain the programs you're interested in you get an understanding on how to do it, I hope ;) 

Otherwise I think you should try synaptic or the add application programs that are in the menus in ubuntu.

Good Luck,
//Johan

---

### Post by taurus on 2006-04-13
If you want to install something extra to your system, try using synaptic and search for it.  If it's not available, then search the web using Google.  Look for the file with .deb extension because you can install it with dpkg command from a terminal or prompt.  Otherwise, download the source and build it yourself.  Now, what programs do you have in mind?

---

### Post by oltix on 2006-04-13
[QUOTE=UbuntuJohan]Hi,

It is hard to give a simple answer to that since it depends on what format the file you downloaded is in.

[/QUOTE]

I have here in desktop Opera browser downloaded with the format .deb
Let me know the commands now :)

---

### Post by apjone on 2006-04-13
sudo dpkg -i whatever.deb

---

### Post by oltix on 2006-04-13
....and I get this:

```
Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by derjames on 2006-04-13
Hi there
There are several ways

(1) The basic: SYNAPTIC package manager.
go to System>administation>Synaptic package manager
then select the software you wish to install just (put a tick), and press apply

(2)If you feel more confident, you can use "apt get" using the syntax indicated by OLTIX

(3) Download the xxxxxx.deb package and extract them using dpgk command
(4) if for any reason you need a packege in .RPM format just download it, then use the ALIEN command to transfor it to .deb and finnaly use dpkg

(4) Download the source code, and compile it by yourself (or even modify it)
(5) Crate your own applications using any of available programming tools (Python, C++, C, RealBAsic, Java, etc, etc, etc)

All this is very well documented, please have a look at the official wiki, read other posts, surf the web for more info or even by a book about LINUX.

Cheers

---

### Post by oltix on 2006-04-13
Can me someone explain what this means?
```

root@oltix:/home/alma# apt-get install libqt3c102-mt libqt3-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3c102-mt has no installation candidate
root@oltix:/home/alma# apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
synaptic is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  opera: Depends: libqt3-mt (>= 3.3.4) but it is not installable or
                  libqt3c102-mt (>= 3.3.4) but it is not installable
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
```

---

### Post by Sef on 2006-04-13
> You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  opera: Depends: libqt3-mt (>= 3.3.4) but it is not installable or
                  libqt3c102-mt (>= 3.3.4) but it is not installable
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

First a dependency is a program that you need to make another program run.

In your case, libqt3-mt (>= 3.3.4) and libqt3c102-mt (>= 3.3.4).  Without them Opera will not work.

Second, apt-get -f install will try and download those dependencies.  You may have to do this several times to get it to work right.

---

### Post by Ramses de Norre on 2006-04-13
Did it work?
Otherwise: run ```
sudo dpkg -r packagename_of_installed_opera
sudo gedit /etc/apt/sources.list
```
and add the lines ```
## opera web browser
deb http://deb.opera.com/opera/ etch non-free

``` at the bottom.
Then do ```
sudo apt-get update && sudo apt-get install opera
```
It then gives you a version specially built for ubuntu.

---

### Post by oltix on 2006-04-14
Thank you guys, but still I can't install it!
```

alma@oltix:~$ su
Password:
su: Authentication failure
Sorry.
alma@oltix:~$ su
Password:
root@oltix:/home/alma# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9552kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 57013 files and directories currently installed.)
Removing opera ...
root@oltix:/home/alma# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@oltix:/home/alma# sudo dpkg -r packagename_of_installed_opera
dpkg - warning: ignoring request to remove packagename_of_installed_opera which isn't installed.
root@oltix:/home/alma# sudo dpkg -r opera_8.54-20060330.6-shared-qt_en_etch_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@oltix:/home/alma# sudo gedit /etc/apt/sources.list

(gedit:9412): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
## opera web browser
deb http://deb.opera.com/opera/ etch non-free
sudo apt-get update && sudo apt-get install opera
root@oltix:/home/alma# ## opera web browser
root@oltix:/home/alma# deb http://deb.opera.com/opera/ etch non-free
bash: deb: command not found
root@oltix:/home/alma# sudo apt-get update && sudo apt-get install opera
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
root@oltix:/home/alma# cd Desktop
root@oltix:/home/alma/Desktop# sudo apt-get update && sudo apt-get install operaReading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
root@oltix:/home/alma/Desktop#

```

---

### Post by missmoondog on 2006-04-14
i was almost going to guess you were trying to install opera, until i read the whole thread. opera sucks when it comes to installing on linux. the easiest and best way to install opera is using automatix. it will install it and even create an icon in the applications/internet menu.

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by oltix on 2006-04-14
Where is this Automatix? Is it on my system? If yes, where? If not, where can I find it, how can I get it on my system. 

PS: Sorry for my "stupid" questions!

---

### Post by Mr Egg on 2006-04-14
To install Automatix, open Terminal then type:
```
wget http://beerorkid.com/automatix/automatix_5.7-3_i386.deb
```
and hit the Enter key. When the download is done, type:
```
sudo dpkg -i automatix_5.7-3_i386.deb
```
and hit Enter. After Automatix is done installing type
```
Automatix
```
then hit Enter. Or, you can find Automatix in the Applications menu.

If you want to un-install Automatix type
```
sudo apt-get remove automatix
```
and hit the Enter key.

Remember, Automatics only works on Breezy Badger.

---

### Post by Ramses de Norre on 2006-04-14
First of all you don't need to do this as root, using sudo is way more secure, so if you're still logged in as root do 'exit' to become regular user.
> sudo dpkg -r packagename_of_installed_opera
You needed to fill in the correct package name, but the previous command did allready remove opera so it wasn't necessary nomore neither.
It seems like you didn't really get my commands.
do ```
sudo gedit /etc/apt/sources.list
``` and give in your userpassword, you'll then get a text editor with the sources of apt.
At the bottom of that file you need to paste this lines: ```
## opera web browser
deb http://deb.opera.com/opera/ etch non-free
```
And then you save the file.
Then you go back to your terminal and run this command: ```
sudo apt-get update && sudo apt-get install opera
```
Opera should install now ;)

---

