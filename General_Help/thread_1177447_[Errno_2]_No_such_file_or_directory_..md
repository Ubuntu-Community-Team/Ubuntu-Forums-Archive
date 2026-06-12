---
title: "[Errno 2] No such file or directory: ."
date: 2009-06-03
forum: General Help
---

### Post by titopagan on 2009-06-03
Hi everyone:

I have searched for a couple of hours trying to figure out how to solve this [Errno 2] No such file or directory: ....

Can anybody please point me in the right direction.

---

### Post by jonobr on 2009-06-03
Hello

COuld you give more information?

What are you doing, what are trying to do?
Whats you setup/hardware etc...

---

### Post by titopagan on 2009-06-04
Hi thank you for replying

This is my setup

PC:
Apex MI-008 Mini-itx Tower computer case
1 TB Hard drive
2 gigs of RAM
Intel Pentium dual core 2.5Ghz
Zotac 630i/Ge-force 7100 Wifi Intel motherboard (Wifi chip vt6656)
PICOpsu.
Ubuntu 9.04

I am tryng to compile a software called Entertainer 0.4.2
[https://launchpad.net/entertainer/entertainer-0.4/entertainer-0.4.2]("https://launchpad.net/entertainer/entertainer-0.4/entertainer-0.4.2")

I have installed all of the depedencies as instructed. The last step is to run "sudo python setup.py install".

When I run "sudo python setup.py install" it says [Errno 2] No such file or directory at the end of the run.

---

### Post by SuperSonic4 on 2009-06-04
I assume you're in the directory containing the makefiles>?

---

### Post by titopagan on 2009-06-04
Yes.  All the files are in "/entertainer" folder.

The setup.py file is also there.

Thanks for your prompt reply.

---

### Post by jonobr on 2009-06-04
Hello

Just curious here,
are you installing this "by hand"
I.e. are you downloading the tarball and unpacking and then running

It looks as if the repository is setup and you need to just add the entertainer rep[repository

> 
[http://wiki.entertainer-project.com/wiki/StartUpGuidehttp://wiki.entertainer-project.com/wiki/StartUpGuide](http://wiki.entertainer-project.com/wiki/StartUpGuidehttp://wiki.entertainer-project.com/wiki/StartUpGuide)

Add the Entertainer Release Team PPA to your software sources list (System -> Administration -> Software Sources -> Third Party Software). Add the deb line that you find at [https://launchpad.net/~entertainer-releases/+archive/ppa](https://launchpad.net/~entertainer-releases/+archive/ppa). PPAs default to the current Ubuntu development release. If you're using Ubuntu, be sure to select the proper version. Launchpad lists, the Ubuntu versions by codename, so if you do not know the Ubuntu codename of your operating system, simply check [https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames).


---

### Post by WIGGMPk on 2009-06-04
titopagan you should check out XBMC it is awesome.

I was looking at entertainer and I think you might like XBMC more.

```
http://xbmc.org/
```

---

### Post by baseface on 2009-06-04
is python installed?

---

### Post by titopagan on 2009-06-04
@ jonobr

I have tried installing the entertainer from the PPAs but its version 0.3 and had problems with it.  The version I am trying to install is 0.4.2. 

@WIGGMPk

I have also tried XBMC and I loved it but it keeps crashing. I have installed and unistalled but the samething keeps happening.  I have looked at the xbmc forums but could not find the answer I was looking for.  Any advise would be very helpful.

@baseface

Yes, its istalled.


Thank you all for your replies.

---

### Post by vinutux on 2009-06-04
Very simple rename your file **[COLOR="Red"]without space[/COLOR]** ........... means rename your .py file to single name such as "entertainer" . Then compile it..coz terminal didn't read space in file names...................:p

---

### Post by titopagan on 2009-06-04
@vinutux

Let me see if I understand you.

Ok there is a file named setup.py 

You want me to rename it entertainer.py

I really don't understand what you are trying to say.

---

### Post by vinutux on 2009-06-04
> **titopagan said:**
> @vinutux

Let me see if I understand you.

Ok there is a file named setup.py 

You want me to rename it entertainer.py

I really don't understand what you are trying to say.

sorry 4 misunderstanding...............

make sur you are in that folder from terminal cd /your path 2 folder

or sudo drag .py file to terminal and enter

---

### Post by titopagan on 2009-06-04
Thanks for clarifying.  Yes I was in the folder when I ran the command.

---

### Post by vinutux on 2009-06-04
try to build .deb with the help of [COLOR="Red"]giftwrap[/COLOR] and install it

install it from [https://launchpad.net/~giftwrap/+archive/ppa]("https://launchpad.net/~giftwrap/+archive/ppa")



Homepage: [http://giftwrap.tuxfamily.org ]("Homepage: http://giftwrap.tuxfamily.org")

---

### Post by titopagan on 2009-06-04
@vinutux

Thanks great idea.

I will try it tonight and post my results.

---

### Post by titopagan on 2009-06-05
I tried giftwrap on the Entertainer program but it did not work.  Thanks for trying.

I am going to reinstall Ubuntu and give XBMC another try.

---

### Post by vinutux on 2009-06-05
There are other optins tooo for media center



1. freevo    

 [COLOR="Red"]*sudo apt-get install freevo*[/COLOR]



2. Elisa media center (now called moovida)

[COLOR="Red"]*sudo apt-get install elisa*[/COLOR]

new vesion download from here [COLOR="Red"][www.moovida.com]("www.moovida.com")[/COLOR]

:D

---

### Post by titopagan on 2009-06-05
I have moovida installed and it was ok. 

Does freevo have better looking skins?

---

### Post by vinutux on 2009-06-05
no............i think moovida is best media center 

[COLOR="DarkGreen"]Freevo[/COLOR] is old-fashioned media center

there is other options like [COLOR="Red"]mythtv[/COLOR] specially desingned for watchin tv

[[COLOR="Red"]Boxee[/COLOR]]("http://boxee.tv") -- a new media center solution

There is review of linux media centers here[ http://regebro.wordpress.com/2008/12/12/i-test-media-center-software-for-linux/]("http://regebro.wordpress.com/2008/12/12/i-test-media-center-software-for-linux/")

):P

---

### Post by titopagan on 2009-06-05
I will try out Boxee.

---

### Post by vinutux on 2009-06-05
ok.........i found XBMC worthfull program:KS

my recomendation is XBMC or moovida.....

i am using both of them now.............

anyway thanks.............:popcorn:

---

### Post by titopagan on 2009-06-05
I hope you don't mind me asking.  When I tried XBMC it worked for a while but then it would crash right after it was started.  Would you know what may have caused it?

---

