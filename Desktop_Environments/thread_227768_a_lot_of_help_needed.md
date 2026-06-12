---
title: "a lot of help needed"
date: 2006-08-02
forum: Desktop Environments
---

### Post by jan1024188 on 2006-08-02
im a fedora core user,but now i installed ubuntu 6.06.
1)how to log in as root in command-line(first how to acess it)
2where to get wine or cedega and how to install it
3)im a GNOME user but i would like to try other desktopsWhere can i get them and how to install them
4)on fedora core i needed kernel-module-ntfs to mount ntfs partition.do i need it on ubuntu too?

---

### Post by cantormath on 2006-08-02
> **jan1024188 said:**
> im a fedora core user,but now i installed ubuntu 6.06.
1)how to log in as root in command-line(first how to acess it)
2where to get wine or cedega and how to install it
3)im a GNOME user but i would like to try other desktopsWhere can i get them and how to install them
4)on fedora core i needed kernel-module-ntfs to mount ntfs partition.do i need it on ubuntu too?

1) login as created user and type
sudo -i
or sudo -s -H

you should passwd here and set the root password.
root password is not set by default (debian thing)

I would definitely recommend that you always login with your created user and sudo into root.  It is not recommend that you login to gui as root.

---

### Post by cantormath on 2006-08-02
2) Depending on what you want to do, you might want to use crossover office, its nice because it makes wine easy.

if you dont want to deal with crossover.....
The easiest way to install wine is with Automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)


If you want to do it more manually.....
I think wine is in the normal repos.  If not, uncomment the Universe repos in your /etc/apt/source.list

1 Install wine
Code:

sudo apt-get update
sudo apt-get install wine


2 Setup disc drives in wine
Code:

winecfg

Go to the Drives tab.
Press the Autodetect button.
Press the Show Advanced button.
Change the type of your CD drive(s) to CD-ROM.

3 Test audio in wine
Code:

winecfg

Go to the Audio tab.
If it crashes follow the instructions here.
[http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7](http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7)


NOTE
here are the bleeding edge repos for wine.

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by jan1024188 on 2006-08-02
but how to login guias root?

---

### Post by jan1024188 on 2006-08-02
but how to login gui as root?
on fc you yust type root but here on ubuntu you cannot.

---

### Post by jan1024188 on 2006-08-02
but how to login gui as root?
on fc you just type root but here on ubuntu you cannot.

---

### Post by cantormath on 2006-08-02
> **jan1024188 said:**
> but how to login guias root?

when i say gui, Im mean gnome.  and its really not recommend that you run as root all the time in debian systems.  Anytime you need to act as root, you can open terminal and 
sudo <whatever you want>
or
sudo -i
and you are root.
if you want, you can install the nautilis scripts from automatix and open anything as root with a right click.

---

### Post by jan1024188 on 2006-08-02
sorry for posting so much times but i didn understand that with 20 sec

---

### Post by jan1024188 on 2006-08-02
what about if i want to open directory in terminal?what to type?

---

### Post by arkangel on 2006-08-02
just  follows his directions  as given 
he is using  sudo (su + does ) 
if you need any command as root  just type sudo before the command

if you are using the  account you set during the installation  then you belong to the administrative group by default ,  

if you  want to set a root password anyway 

sudo -s

and enter your password (remember you are in the administrative group)
 then your prompt have changed to 
root@host>

so here type 
passwd 


--- the advante of sudo is (for me)  I dont have to take care whether i am  root or not, which is much safer ---

---

### Post by jan1024188 on 2006-08-02
what about if i want to open directory in terminal?what to type?
Edit/Delete Message

---

### Post by jan1024188 on 2006-08-02
what about if i want to open directory in terminal?what to type?
Edit/Delete Message

---

### Post by givré on 2006-08-02
I hope that the help for 1) and 2) is enough, say it if not. If you want to understand the ubuntu sudo model, read that [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).
Now i can reply to 3) and 4):
3) As you now, each 3 major desktop environement has is own distro in ubuntu world:
-kubuntu for kde
-ubuntu for gnome
-xubuntu for xfce
But you always can install kubuntu in ubuntu, xubuntu in kubuntu...
You just have to install a metapackage that will install all the specific package to each distro.
```
sudo apt-get install kubuntu-desktop
```
will install you kde
```
sudo apt-get install xubuntu-desktop
```
will install you xfce
4) fedora/redhat remove the ntfs driver from their kernel (even if it's in the vanilla tree), in ubuntu it's in by default, so you should be able to mount ntfs partition easily. see this howto [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
And if you want read/write access using ntfs-3g, try my howto : [www.ubuntuforums.org/showthread.php?t=217009](www.ubuntuforums.org/showthread.php?t=217009)

And welcome here :D

---

### Post by cantormath on 2006-08-02
> **arkangel said:**
> just  follows his directions  as given 
he is using  sudo (su + does ) 
if you need any command as root  just type sudo before the command

if you are using the  account you set during the installation  then you belong to the administrative group by default ,  

if you  want to set a root password anyway 

sudo -s

and enter your password (remember you are in the administrative group)
 then your prompt have changed to 
root@host>

so here type 
passwd 


--- the advante of sudo is (for me)  I dont have to take care whether i am  root or not, which is much safer ---



I think you can just type 
$ sudo passwd root

to set the root password, no?

---

### Post by etank on 2006-08-02
> **cantormath said:**
> I think you can just type 
$ sudo passwd root

to set the root password, no?That is the way that I have done it in the past. 

Is it better to use ```
sudo apt-get install *something*
```or ```
sudo aptitude install *something*
``` Doesn't aptitude do better dependency checking?

---

### Post by sulobanks on 2006-08-02
For wine, I went to the winehq.com website and added the repositories there.  Then I went and got winetools from [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/) and installed them.  It made the process almost as easy as crossover office.

To install other desktops, open up System->Administration->Synaptic Package Manager
Search for 'window manager' or 'desktop' and it should list a lot of them. Among the more popular are GNOME, KDE, XFCE, Window Maker, Enlightenment and Fluxbox (although I'm sure I'll be informed of how many I've missed) ;D.

---

### Post by orlox on 2006-08-02
Sometimes I find it more comfortable to have nautilus open as root. you can do this from a terminal by typing:

sudo nautilus

but to save yourself the effort of opening a terminal, you can simply run it on the execute program option from the menu (or execute application, i don't know what it says in english), and type:

gksu nautilus

wich will open a prompt asking the root password, and after typing it, it will open the file explorer as root....

---

