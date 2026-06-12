---
title: "Adding repositories in Debian"
date: 2008-06-26
forum: Debian
---

### Post by geo909 on 2008-06-26
Hello everybody,

 I have installed debian on a laptop. I want to install some non-free stuff like unrar and cannot find it on the repos. Do you know the multiverse, universe etc equivalents for debian?

 Also, is there an "ubuntu restricted extras" package equivalent for debian?

 thanks a lot in advance.

---

### Post by kerry_s on 2008-06-26
add-> contrib non-free
to the end of your current repos.

---

### Post by geo909 on 2008-06-26
Thanks! Yes, that did the job.
I found the nonfree unrar for example.
Though, I cannot fint ntfs-3g..
Any ideas?
What repo should I add for this one?

---

### Post by tturrisi on 2008-06-26
> **geo909 said:**
> Thanks! Yes, that did the job.
I found the nonfree unrar for example.
Though, I cannot fint ntfs-3g..
Any ideas?
What repo should I add for this one?

Better to just download the tgz and manually build and install ntfs3g.

as root...
apt-get install build-essemntial linux-headers-`uname -r`
download latest stable ntfs3g from here:
[http://www.ntfs-3g.org/index.html](http://www.ntfs-3g.org/index.html)
extract to /usr/src
cd /usr/src/ntfs3g directory
./configure
make
make install

edit /etc/fstab to mount ntfs partitions at boot:
create dirs in /mnt for ntfs partitions and add a line to fstab for each partition
/dev/sda1 /mnt/ntfs-dir-name-here ntfs-3g defaults 0 0

docs:
[http://www.ntfs-3g.org/support.html#questions](http://www.ntfs-3g.org/support.html#questions)

---

### Post by Inxsible on 2008-06-26
I am not sure if you have already added this but debian-multimedia is an important repo for Debian since it provides quite a few multimedia related apps as well.

---

### Post by geo909 on 2008-06-26
> **Inxsible said:**
> I am not sure if you have already added this but debian-multimedia is an important repo for Debian since it provides quite a few multimedia related apps as well.

Could you give me the exact address for this?

---

### Post by Inxsible on 2008-06-26
> **geo909 said:**
> Could you give me the exact address for this?The repo is ```
deb http://www.debian-multimedia.org/ lenny main
```

Of course if you are using etch or sid, you will have to change it accordingly

---

### Post by geo909 on 2008-06-26
> **Inxsible said:**
> The repo is ```
deb http://www.debian-multimedia.org/ lenny main
```

Of course if you are using etch or sid, you will have to change it accordingly

I added the line:

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) etch main

but when I open synaptic I get
> W: Couldn't stat source package list [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages (/var/lib/apt/lists/www.debian-multimedia.org_dists_etch_main_binary-i386_Packages) - stat (2 No such file or directory)


Is that normal?

---

### Post by benuski on 2008-06-26
> **geo909 said:**
> I added the line:

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) etch main

but when I open synaptic I get


Is that normal?

That just means that you need to install the package "debian-multimedia-keyring" through your favorite package manager.

If you want ntfs-3g through Debian, which is better than building it from source IMHO, its available through backports.org or from lenny.

---

### Post by Inxsible on 2008-06-26
As a side note, I would also recommend that you move up to lenny. Although its called testing, it very stable. much more than Ubuntu too, IMO.

You will also get a lot of newer versions of software.

---

### Post by benuski on 2008-06-26
> **Inxsible said:**
> As a side note, I would also recommend that you move up to lenny. Although its called testing, it very stable. much more than Ubuntu too, IMO.

You will also get a lot of newer versions of software.

Seconded.  Ubuntu is built from Sid, the Debian Unstable branch.  I run Sid, and its also pretty stable, but sometimes has pretty big bugs.  Testing, which is Lenny right now, is much more stable than Sid, and gets continuous updates to the software.

---

### Post by geo909 on 2008-06-26
Thanks for the useful info!

I was sort of confused with debian versions..
They name them "unstable" so I see red flags.

So, first of all an upgrade..
Is it just **sudo apt-get dist-upgrade**?

Though I haven't installed many things..
maybe I should go for the lenny netinstall iso if it is safer..
What do you say?

---

### Post by Inxsible on 2008-06-26
> **geo909 said:**
> Thanks for the useful info!

I was sort of confused with debian versions..
They name them "unstable" so I see red flags.

So, first of all an upgrade..
Is it just **sudo apt-get dist-upgrade**?

Though I haven't installed many things..
maybe I should go for the lenny netinstall iso if it is safer..
What do you say?
i dont think Debian works that way. The dist-upgrade is ubuntu only - i could be wrong.
But a simple way of upgrading is to simply change your sources.list file to point to lenny instead of etch and then do ```
sudo apt-get update && sudo apt-get upgrade
```

if you are planning a re-install ... I would always go for the business iso and then install whatever DE or WM I want. I do that exclusively now. I never use the pre built distros, because I almost always do not like the apps that they give you as default.

---

### Post by benuski on 2008-06-27
dist-upgrade is debian as well, since the apt-get and aptitude commands were created by debian.  The easiest way to upgrade to lenny is to just change your sources.list to have everything that now says etch to lenny.

Then do an "aptitude update" and an "aptitude dist-upgrade". (or apt-get if you prefer).

That should work just fine, and then you'll be tracking lenny.

---

### Post by Inxsible on 2008-06-27
I am sorry... I didn't mean that the apt-get didnt have the dist-upgrade option. What I meant was using apt-get dist-upgrade will not switch from etch to lenny, like it does in Ubuntu. 

Honestly, I have not tried it, so I still can't say for sure. You might wanna try it and see if it works.

Let us know as well. :)

---

### Post by geo909 on 2008-06-27
Thank you guys for the feedback.
I'll let you know when I try, this will probably be in a couple of days due to exams.

> **Inxsible said:**
> 
if you are planning a re-install ... I would always go for the business iso and then install whatever DE or WM I want. I do that exclusively now. I never use the pre built distros, because I almost always do not like the apps that they give you as default.

 Yes, that was the first time I did it and I am amazed too. It gives life to older machines that would normally be barely usable with XP or one of the most popular linux distros.

 I have an old compaq presario 700 (AMD 1.2 GHz, 256 MB Ram). It had some broken plastic parts (screen could barely stand), LOTS of tape all over (even on a serious part of the screen), electrical problems and other bad stuff. A kind woman gave it to me for free (have you heard of *freecycle*?).
 I spent 40 bucks on ebay to buy a new battery and manage to fix the problems, removed all the tapes and glued the corresponding plastic parts. Unfortunately the ethernet doesn't work so I have to occupy one of the two usb (what is the word? "Ports"?). But other than that it is 100% usable.

 So, I installed debian, the base thing along with X and openbox. Having firefox and a couple of xterms running, the amount of used ram reached the 60MBs..
 Then I did a super test:
Amarok+ Maple* + Transmission + Firefox + 4 X xterm + conky = 145 MBs!!! 
[COLOR="Silver"]*a quite heavy app for symbolic computation that uses Java.[/COLOR]
 
 I am new to all this, so I am truly amazed!

 Now the only drawback is some slow motion when I move/resize windows or scroll down a page in firefox. 

Do you thing that this can be fixed or is it because the machine is rather old? 

 I also managed to get ntfs-3g. I found some deb files but it can be also found on the backports repository as you said. If the whole thing works well, maybe I won't upgrade, since I don't really mind not having the very latest stuff, but I'm not sure..

---

### Post by basenvironment on 2008-06-30
sounds like you should just go ahead and try out lenny
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by geo909 on 2008-07-01
> **basenvironment said:**
> sounds like you should just go ahead and try out lenny
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

Well, I did.. And I am sort of dissapointed.
I did the very base thing as I did with etch.
Then I installed Xorg and openbox with apt-get.

Now when I start X, openbox loads by default with a super
shinny and fancy skin and the memory used is 40MBs, while with etch and the same process it was 27.

 Then I installed amarok. When I did that in etch, it installed amarok and it's needed libraries. In Lenny It installed every KDE component and switched all my defaults to the KDE ones (web browser to konqueror, terminal to konsole etc)..
It also starts a bunch of kde appson the startup..

 So what is with all those things? Why do they remove the joy of configring everything from scratch?

EDIT: Ok after a reinstallation I installed amarok from synaptic and no extra stuff was included.
Now openbox boots with 46 MBs of memory used.

---

### Post by Inxsible on 2008-07-01
You should use the -R or --without-recommends flag with aptitude. That will install only the libraries that are needed and not the recommended ones.

---

### Post by geo909 on 2008-07-01
> **Inxsible said:**
> You should use the -R or --without-recommends flag with aptitude. That will install only the libraries that are needed and not the recommended ones.
I will do that next time, i didn't know it.

What I had done was that I added a line like
```
APT::Install-Recommends "false";
```
In /etc/apt/apt.conf
but It didn't seem to work..

---

### Post by Inxsible on 2008-07-01
> **geo909 said:**
> I will do that next time, i didn't know it.

What I had done was that I added a line like
```
APT::Install-Recommends "false";
```In /etc/apt/apt.conf
but It didn't seem to work..
Hmmm.. checking the man pages is always a good idea. Those flags, I mentioned, are for aptitude...but I think there should be similar flags for apt-get as well.

---

### Post by geo909 on 2008-07-01
yes what I did was for apt-get but I will follow your advice for the -R flag for aptitude when I try again..

---

### Post by basenvironment on 2008-07-01
> **geo909 said:**
> 
In /etc/apt/apt.conf
but It didn't seem to work..
should of worked....did it tell you such and such is recommended but will not be installed?

might try

APT::Install-Recommends "0";

---

### Post by geo909 on 2008-07-02
I mean it didn't work for openbox. It installed a bunch of things.
So I guessed it installed the recommended ones. I will have to check again to be sure..

---

### Post by Inxsible on 2008-07-02
Before installing anything you can check what dependencies it has by simulating the install using the -s flag in both aptitude and apt-get ```
aptitude -s install openbox
``` or ```
apt-get -s install openbox
```It will list all the packages that will be installed using those commands. You can then peruse through them and see if it is acceptable to you.

I almost always do this now and then depending on the result i either use the -R flag or not

---

### Post by geo909 on 2008-07-06
Hello again everybody!

Finally I did the installation of my dreams using ICEWM which I found amazing and superlight even with a fancy theme..
It runs with conky and a wallpaper with something  like 35 MBs of RAM consumed.. Truly amazing

---

### Post by basenvironment on 2008-07-06
> **geo909 said:**
> Hello again everybody!

Finally I did the installation of my dreams using ICEWM which I found amazing and superlight even with a fancy theme..
It runs with conky and a wallpaper with something  like 35 MBs of RAM consumed.. Truly amazing
just to clarify...35mb total for the system

icewm itself only uses around 3mb

---

### Post by Inxsible on 2008-07-07
Yup. Openbox, fluxbox and Icewm are all nice and light.

I have a triple boot of debian + flux, debian +icewm and arch + openbox.

Icewm takes about 5MB on boot, fluxbox takes 6MB and Openbox takes 8MB according to ps_mem.py

I would say they are all comparable. Openbox seems more polished to me than flux or icewm.

But they all have their pluses and minuses.

---

### Post by ubernuber on 2008-07-08
Thanks Inxsible,

its a great idea to use the -s and -R flags for aptitude. I didn't know about them.

Not to self: Read the man pages more often :)

---

### Post by Nebutron on 2008-07-19
> **Inxsible said:**
> The repo is ```
deb http://www.debian-multimedia.org/ lenny main
```

Of course if you are using etch or sid, you will have to change it accordingly

I am trying to do the same thing.  When I add the url to the repositories, I get a message:

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

Or it says something about a public key.  Any ideas?

---

### Post by geo909 on 2008-07-19
> **Nebutron said:**
> I am trying to do the same thing.  
...
Or it says something about a public key.  Any ideas?

If by the "same thing" you mean adding the multimedia repository, then 
you should install the package "debian-multimedia-keyring" in order to have access to the repository.

---

### Post by Nebutron on 2008-07-20
Thanks Geo!!  I will give that a shot.

---

