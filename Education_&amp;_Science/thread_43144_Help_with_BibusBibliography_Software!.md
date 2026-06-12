---
title: "Help with Bibus/Bibliography Software!"
date: 2005-06-20
forum: Education &amp; Science
---

### Post by Karl S. on 2005-06-20
Hi. Totally ignorant about computers.

Having a good Bibliographic program available (i.e., one that can retrieve records from libraries, insert citations either automatically or by cut and pasting, and format Bibs according to different guidelines) seems to me imperative for Ubuntu , and Bibus ([http://bibus-biblio.sourceforge.net/](http://bibus-biblio.sourceforge.net/)) seems to fit the bill in a way that Sixpack ([http://www.santafe.edu/~dirk/sixpack/](http://www.santafe.edu/~dirk/sixpack/)) doesn't. But it's a pain to get set up! I've been trying to hours.

I could possibly use Endnote through Wine (if I could get it to work, but that's another issue) or Crossover Office, but: a) since I'm making the Linux switch, I'd rather not use Windows programs if I can do without them; b) Wine/CrossOver Office just doesn't work that well with Endnote, unless, I suppose, I do some tweaking. But even so, EndNote works best with MS Word as does RefWorks (for which my University doesn't provide a free license, unlike Endnote), so both of these apps are automatically sucky.

Bibus seems best. Those who can get it working praise it. And it seems to integrate perfectly with OpenOffice, once you can get it running. But if you look at the links below, getting it to work is very difficult, especially for someone like me who knows nothing about Unix commands &c.

So, as an Absolute Beginner, any suggestions? I've been installing all sorts of packages, but I'm hitting walls  ](*,) at several steps.


Here's some discussion and instruction on installing.
[http://bibus-biblio.sourceforge.net/html/en/LinuxInstall.html#mozTocId494898](http://bibus-biblio.sourceforge.net/html/en/LinuxInstall.html#mozTocId494898)

[http://www.oooforum.org/forum/viewtopic.phtml?t=12477&postdays=0&postorder=asc&start=0](http://www.oooforum.org/forum/viewtopic.phtml?t=12477&postdays=0&postorder=asc&start=0)

Could someone who knows something about Ubuntu look at these instructions/discussions and tell me where a Newbie is likely to go wrong? Could someone who knows something about Ubuntu who might need bibliographic software (an academic, for instance) try to install it just to see if it works?

Just trying to get it going through Synaptic after I edited source.list to get me backport access to Bibus gives me this error message, by the way:

Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed

--

Main question: Is there a better way to go about this stuff than what these instructions tell me to do? Is there a way to get some kind of support for Bibus or something like it for those of us we need this kind of software?

---

### Post by sethmahoney on 2005-06-20
I've got two quick questions for ya: Are you trying to install Bibus using the Debian instructions on this page (which is probably your best bet): [http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381](http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381)

Second question: can you cut and paste your sources.list?  To pull it up, open up a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Karl S. on 2005-06-20
[QUOTE=sethmahoney]I've got two quick questions for ya: Are you trying to install Bibus using the Debian instructions on this page (which is probably your best bet): [http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381](http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381)

Second question: can you cut and paste your sources.list?  To pull it up, open up a terminal and type:

```
sudo gedit /etc/apt/sources.list
```[/QUOTE]

Among the instructions I used were the Debian instructions.
When I do this:
apt-get install bibus bibus-doc-en openoffice-pyuno
I get this:
Reading package lists... Done
Building dependency tree... Done
bibus-doc-en is already the newest version.
openoffice-pyuno is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bibus: Depends: python (< 2.4) but 2.4.1-0ubuntu2 is to be installed
E: Broken packages

Also, when I do this:
apt-get install libsqliteodbc python-sqlite
I get this:
Reading package lists... Done
Building dependency tree... Done
python-sqlite is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsqliteodbc: Depends: libsqlite3-0 (>= 3.2.1) but it is not going to be installed
E: Broken packages

--

Sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

---

### Post by Karl S. on 2005-06-22
Okay, I've tried again.

At the Bibus site, it tells me to go here ([http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381](http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381)) for a GNU/Linux installation. I'm guessing that's what kind of installation I should do, yeah?

I instruction page is here: [http://bibus-biblio.sourceforge.net/installation.txt](http://bibus-biblio.sourceforge.net/installation.txt)

It asks me to install the following packages:

> 1) Python 2.2.x
2) wxPython >= 2.4 If possible with unicode and gtk2 (linux) support. 
   (Don't use 2.5 for the moment except for Windows98, it will crash).
3) Either MySQL-python or pySQLite
4) ODBC
5) ODBC driver for MySQL and/or SQLite

In Debian the following packages must be installed:
	python2.2-xmlbase
	python2.2-sqlite   ! does not contains unicode support. If you need it install from source.
	python2.2-mysqldb
	python2.2-dev	(needed below to compile wxPython)
	python2.2
	libmyodbc
	odbcinst1
	unixodbc


So I did that.

But when I try to install Bibus (in Synaptic), I get this: 

>  Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed

My problem is probably here; from the instructions:

> 1) You must have the python-uno bridge installed.
   It is normally installed by default if you use OpenOffice.org > 1.1
   To know if it is installed try in a console:
	prompt> $OO/program/python
   you should get:
	Python 2.2.2 (#1, Jul 21 2003, 15:13:13)
	[GCC 3.2.2] on linux2
	Type "help", "copyright", "credits" or "license" for more information.
	>>>

2) If it is not the case. 
   Restart OpenOffice.org installation, choose 'custom install' and 
   check that the python-uno bridge is indeed checked for installation.

3) As you see, the python installed by OpenOffice.org is 2.2.2 (linux) 
   and it is compiled with GCC 3.2.2
   For the installation to work, you must use below the "same" python than OpenOffice.org 
   (or a bug fix like 2.2.3) 
   and a "compatible" GCC (in my case 3.3.3 was fine). 
   If you have problem, try to use exactly the same versions.

But here's what I have:

karl@ubuntu:/usr/lib/openoffice/program$ python
Python 2.4.1 (#2, Mar 30 2005, 21:51:10)
[GCC 3.3.5 (Debian 1:3.3.5-8ubuntu2)] on linux2

So, any idea how to fix this? I think I'm going to e-mail the fellow who put this program together and crosspost this at OpenOffice.

---

### Post by Karl S. on 2005-06-24
Okay, some movement here if anyone can help me.

I wrote to Pierre Martineau, author of Bibus, and he said, "I know you can install it on Ubuntu. The problem is that you are mixing two installation instructions."

Okay. 
He added:

> 1) You can use Debian packages, but in that case the best solution is to
also install python2.3

2) You can use the normal install.

He gave me the e-mail of a fellow who's successfully installed Bibus on Ubuntu, but in case he doesn't write back, I'm posting further information here.

On [this page](http://bibus-biblio.sourceforge.net/html/en/LinuxInstall.html#mozTocId183447) it says that 

> Most modern distribution contains python2.3 as the default python and don't propose to use python2.2. The python-uno bridge is compatible with python2.3 is you system python has been configured with the option --enable-unicode=ucs2. This is not the case of the Debian python2.3.

    * To know if you python is compiled with ucs2 or ucs4 do:
    * prompt> python2.3
    * prompt>>> import sys
    * prompt>>> print sys.maxunicode
    * if you get : 1114111, your python is UCS4
    * if you get : 65535, your python is UCS2 and it should work with the python-uno bridge. To really test, see below.

Here's what I get:

root@ubuntu:/opt/bibus-1.0.0 # python2.3
Python 2.3.5 (#2, Mar 29 2005, 15:41:06)
[GCC 3.3.5 (Debian 1:3.3.5-8ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.maxunicode
1114111
>>>

Any ideas? I also just tried downloading the [bibus-biblio](http://sourceforge.net/projects/bibus-biblio/) package from here, but once I unpack the file, I don't know what to do. [This](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html#s-sourcepkgs) doesn't seem to help me. 

So...uh, if someone's bored and looking for a challange, try to install Bibus on your machine and get it working. And then let me know how I did it. Bonus points to anyone who can explain to me what I'm doing wrong.

---

### Post by Canguçu on 2005-06-24
It seems we will have to recompile a lot of things by ourselves (and I am not really sure that it will be a good idea) to make this software work... :(

Well, I hope you can post here the instructions from that the guy who happened to successfully install bibus on ubuntu!

---

### Post by cjoshuav on 2005-08-06
I'm getting 

Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed

as well, which I assume means "needs earlier version of Python and you have a more recent version".

Any suggestions would be appreciated.

- Joshua

---

### Post by rsay on 2005-08-06
Did you try the installation method in the bibus howto? It worked well for me.

[Bibus Ubuntu Howto](http://www.ubuntuforums.org/showthread.php?t=50762)

---

### Post by Eric DANE on 2006-01-25
There is a new [Bibus page]("https://wiki.ubuntu.com/Bibus") on Ubuntu/Wiki. It is still almost empty but you'll find there few links.

Don't hesitate to edit it so as to help Ubuntu's user to use bibus.

---

### Post by NeTo on 2006-01-30
I have built bibus packages that install on Ubuntu with python 2.4 + OOo2 support. That way the installation of Bibus on Ubuntu should hopefully be simplified.

You check the small how-to I made about this in [thread=122841]this thread[/thread]. the diffs used for building the package are also included, in case it needs to be recompiled in the future.

---

### Post by zugvogel on 2006-01-30
I would also highly recommend Jabref ([http://jabref.sourceforge.net/)](http://jabref.sourceforge.net/)). It imports bibtex files downloaded from Inspec or web of knowledge, etc, and lets you create groups based on keywords found in the title, abstract, etc. As I recall I had to install the sdk java version to get it working though.

---

### Post by PacShady on 2007-05-08
Hey, is it just me, or is the latest OpenOffice on Feisty INCREDIBLY unstable, so unstable that to even TOUCH it with Bibus it crashes? Anyone been able to get it to work at all in Feisty?

'Shady

---

### Post by coady on 2007-05-10
I have not upgraded to 'Feisty' but if there are problems with OOo Writer and Bibus then that would be a real disaster. I depend on both of these. Any information about this would be greatly appreciated.

coady

---

### Post by Zeedok on 2007-05-10
I have successfully installed Bibus on Feisty without any problems. It hasn't crashed for me.

I just followed the instructions on the bibus wiki for Ubuntu and then installed via synaptic.

Incidentally . . . I was trying to install bibus on a Mepis system and it refused to connect with OO2. I later found that this has also been reported on Kubuntu . . . something about KDE seems to object to bibus.

Bibus is fine, when it's working, but I'm really keen to see either:

1. [ Zotero]("http://www.zotero.org/") interact with OO2 directly - ie cite while you write
or
2. OO2 to develop their Bibliography features (as the Bibliography project has promised)

I'd be interested to know the progress of either of these if anyone knows . . .

---

### Post by MacD on 2007-05-11
I've got bibus working with OO in feisty with no problems at all.  As I recall I just installed through synaptic.  I have only python 2.5

---

### Post by David Valentine on 2007-05-12
Kubuntu users who keep experiencing OpenOffice.org Writer crashes when attempting to open UnoConnectionListener.sxd can get enable OpenOffice - Bibus connectivity directly by doing the following (thanks to Stephan Gromer reporting on Bug #106858 on LaunchPad).

```
sudo cp /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu.backup
kdesu kate /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu

```[FONT=monospace]Search for the entry> <node oor:name="Office">Straight after that add
```
<prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
<value>pipe,name=OOo_pipe;urp;</value>
</prop>
``` [/FONT]

---

### Post by coady on 2007-05-14
OK. I upgraded yesterday and have installed 'bibus' and it works without any trouble. Note that I installed 7.04 to a spare partition and then after installing 'bibus' and setting up the SQLlite link to OOo Writer, I then copied over all my 'bibus' settings (personal styles, shortcuts, etc.) and the '.bibus' file in '/home/username'. :)  Next time I launched 'bibus' it was just the same as using it on Ubuntu 6.10. (Actually, I have home on a separate partition and Feisty will work just fine, including all you personal settings and configs when you point the Feisty '/home' to the Edgy '/home').
coady

---

### Post by PacShady on 2007-06-01
> **David Valentine said:**
> Kubuntu users who keep experiencing OpenOffice.org Writer crashes when attempting to open UnoConnectionListener.sxd can get enable OpenOffice - Bibus connectivity directly by doing the following (thanks to Stephan Gromer reporting on Bug #106858 on LaunchPad).

```
sudo cp /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu.backup
kdesu kate /usr/lib/openoffice/share/registry/data/org/openoffice/Setup.xcu

```[FONT=monospace]Search for the entryStraight after that add
```
<prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
<value>pipe,name=OOo_pipe;urp;</value>
</prop>
``` [/FONT]

Thanks, this seemed to work!

I got it working on my Desktop by purging the previous install of OpenOffice and installing it again from the repositories, but I'm on my laptop at the moment and it's got a slow connection, so this worked well.

The problem seems to be the Kubuntu OpenOffice not wanting to run macros. It does the same problem when trying to run the built-in dictionary tool as well.

'Shady

---

