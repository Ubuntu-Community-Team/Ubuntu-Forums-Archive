---
title: "Installing KDE on Ubuntu"
date: 2005-12-28
forum: General Help
---

### Post by noeluylee on 2005-12-28
I want to install KDE on my ubuntu, but before. I just want to know how large is the total file that should be added on top of ubuntu? in short, how large the kde is? :-) for hard disk space reason.

when I install kde, is it the same as kubuntu 100%?

and does my ubuntu works 100% if I install kde? how about my installed programs? does it appears on Kunubtu/ Kde as well? I have lots of applications installed on my ubuntu already like inkscape, scribu, dia, eclipse etc.

Thanks a lot.

Regards,
Noel

---

### Post by aysiu on 2005-12-28
[QUOTE=noeluylee]I want to install KDE on my ubuntu, but before. I just want to know how large is the total file that should be added on top of ubuntu? in short, how large the kde is? :-) for hard disk space reason.[/quote] Open up a terminal and type ```
sudo apt-get install kde
``` It should list a bunch of packages to be installed *and* how much space it'll take up. Say "no" if you think it'll take up too much room.

> 
when I install kde, is it the same as kubuntu 100%? No, but the differences are minor.

> 
and does my ubuntu works 100% if I install kde? how about my installed programs? does it appears on Kunubtu/ Kde as well? I have lots of applications installed on my ubuntu already like inkscape, scribu, dia, eclipse etc. Yes. All programs will work in both Gnome and KDE. Your menus will also be cluttered up with both sets of programs.

---

### Post by runlevel0 on 2005-12-28
[quote=noeluylee]I want to install KDE on my ubuntu, but before. I just want to know how large is the total file that should be added on top of ubuntu? in short, how large the kde is? :-) for hard disk space reason.[/quote]

Ups. I was tring to make du -sh /usr/kde/3.5, but Ubuntu stores the KDE binaries directly in /usr. From df -h I read that my /usr filesystem contains 2.8 Gb of data, this of course includes *teh whole* KDE 3.5, Gnome 2.12, and a good amount of assorted stuff like development environemts for C, Perl and Python, Office suits, LaTeX, Emacs, half a dozen desktops and lotsa gamez and silly stuff a real geek can't live w/o (ever asked yourself how boing live can be w/o fortunes or cowsay?). I would say that all the KDE binaries amounts to less than 500MB.

[quote]
when I install kde, is it the same as kubuntu 100%?
And does my ubuntu works 100% if I install kde? how about my installed programs? does it appears on Kunubtu/ Kde as well? I have lots of applications installed on my ubuntu already like inkscape, scribu, dia, eclipse etc.
[quote]

Yes, that is it. Kubuntu is exactly the same as Ubuntu, but shipping KDE isntead of Gnome. If you look at the repositories (/etc/apt/sourcs.list) look at the URL how the point both to the same respositories called *ubuntu* and how they are exactly the same as the ones in Ubuntu/Gnome.

I'm not sure, but I believe that Kubuntu will disappear, or better said, teher will be only one flavour of this distro called "Ubuntu" and using KDE as default desktop.

Now some tips:
There are 2 meta-packages which installs KDE into you system: kde or kubuntu-desktop. The first means *all* the available KDE stuff and a developer's dog installed into your system, the latter means a basic KDE but with some stuff missing (like Kile, I don't know how a Human Being can live w/o Kile). 

If you try to apt-get install kde you will get an error telling you that this is not possible because there is a package missing that is not going to be installed. (Kspy and kdesdk). 
This problem can be solved issuing:

```

apt-get install kde
[ERROR]
apt-get -f install 

```

[ERROR] means that apt spits out an error message. Issue the second command after it and apt will know what to do.

If you have trouble allocating disc space, use kubuntu-desktop instead.

good luck and happy Xmas!

---

### Post by nandasunu on 2005-12-28
i am also wanting to do the same thing. I have been using ubuntu for about 6 weeks now and would like to try kde. Will installing kde mess up/change my standard gnome setup at all? I have it all set up how I want it (and a bunch of programs installed etc..) and am not so great and fixing things...

thanks.

---

### Post by Lord Illidan on 2005-12-28
No, it shouldn't mess up your gnome setup at all. At least, it didn't on mine.

---

### Post by MrSweet on 2005-12-28
[QUOTE=aysiu]Open up a terminal and type ```
sudo apt-get install kde
``` It should list a bunch of packages to be installed *and* how much space it'll take up. Say "no" if you think it'll take up too much room.

 No, but the differences are minor.

 Yes. All programs will work in both Gnome and KDE. Your menus will also be cluttered up with both sets of programs.[/QUOTE]

Hello.

I just got kde 3.5 installed by getting the repositories off the Kubuntu forums.  There were some extra things that I wanted to get, so I searched synaptic and noticed that the kde package was not installed.  I have tried to install this with synaptic, and also with apt-get as stated in this post.  Unfortunatly the package seems to be broken.  I attempted to get the missing packages, but I ended up getting a series of package errors, on broken pak after another.  Is there some upgrade going on to the depo's?  Or has anyone else seen this problem?

Mr. Sweet

---

### Post by noeluylee on 2005-12-28
Thank you so much for the help :-) I will try to install kde now... :)

Merry Xmas to all :)

God Bless...

---

### Post by pelle.k on 2005-12-28
Hi all...

> Hello.
 
 I just got kde 3.5 installed by getting the repositories off the Kubuntu forums. There were some extra things that I wanted to get, so I searched synaptic and noticed that the kde package was not installed. I have tried to install this with synaptic, and also with apt-get as stated in this post. Unfortunatly the package seems to be broken. I attempted to get the missing packages, but I ended up getting a series of package errors, on broken pak after another. Is there some upgrade going on to the depo's? Or has anyone else seen this problem?

Did you add jonathan riddells kde 3.5 repository to sources.list?
I dont know if that is how you should install kde from base or ubuntu-desktop...
I *think* you are supposed to install kde or kubuntu-desktop and then add jonathan riddells repository and **update** kde. correct me if i'm wrong. :)
Ask again if you don't understand what i mean...

---

### Post by noeluylee on 2005-12-28
Hi,

I was able to install the kde and it worked on my system with no errors, however, there are icons in systems that also appears in utilities, such as User and Groups... how can I remove icons? specifically, delete it from the system. 

Also it is stated that 510mb will be added once I installed kde, but when I checked, it took 700mb, i think the downloaded files still in my computer, how can i delete it? :-) 

Thanks a lot

---

### Post by nandasunu on 2005-12-29
I've also now installed kde, thanks for the advice! :D

---

### Post by runlevel0 on 2005-12-29
[QUOTE=MrSweet]Hello.
Unfortunatly the package seems to be broken.  I attempted to get the missing packages, but I ended up getting a series of package errors, on broken pak after another.  Is there some upgrade going on to the depo's?  Or has anyone else seen this problem?
Mr. Sweet[/QUOTE]

I explained the fix in my answer above. The fact is that there are 2 meta-packages for KDE: One is called kubuntu-desktop, that installs the KDE desktop you get off-the-shelf with Kubuntu and the second meta-package is called simply 'kde'. 

The 'kde' package returns a dependency error. To solve it you need to use the console and issue *apt-get install kde* and after the error message *apt-get -f install* to resolve the needed dependencies.

This will install almost every KDE related package.

You can, however, install  all the individual packages you want, just search "KDE" in Synaptic and select what you need. Thus you can avoid getting silly stuff like games and toys or applications you don't need.

---

### Post by pelle.k on 2005-12-29
Hello again :)

> Also it is stated that 510mb will be added once I installed kde, but when I checked, it took 700mb, i think the downloaded files still in my computer, how can i delete it?

I will always recommend "man", as in "man apt-get" (in a terminal). This will tell you amongst other cool things, to use "apt-get clean" or "apt-get autoclean". Find out for yourself what the difference is. good luck.

---

### Post by MrSweet on 2005-12-29
[QUOTE=pelle.k]Hi all...



Did you add jonathan riddells kde 3.5 repository to sources.list?
I dont know if that is how you should install kde from base or ubuntu-desktop...
I *think* you are supposed to install kde or kubuntu-desktop and then add jonathan riddells repository and **update** kde. correct me if i'm wrong. :)
Ask again if you don't understand what i mean...[/QUOTE]

Pelle, 

That is exactly what I did.  I followed the directions on the Kubuntu site, added the repo, added the key, spt-get update, then upgraded from synaptic.  I am running 3.5 currently, and when browsing synaptic later that is when I noticed the un-installed kde package.  I was just wondering why that package had so many references to broken packages.

Also, if anyone is interested, I could never figure out how to change the Kubuntu desktop to get my menu's back and such.  I happened to have a backup compy of .kde/share that I moved over to /home and I got all my settings back for Konquerer.  If someone could tell me the specific file that holds those settings I would be more then willing to post them.  That way, with one file, you can have all the menu's and settings available to you.  

Let me know and I will do what I can.

Mr. Sweet

---

### Post by MrSweet on 2005-12-29
[QUOTE=runlevel0]
The 'kde' package returns a dependency error. To solve it you need to use the console and issue *apt-get install kde* and after the error message *apt-get -f install* to resolve the needed dependencies.

This will install almost every KDE related package.
[/QUOTE]

Runlevel0, 

Thanks for the apt-get line.  I did not know about the -f key.  I am still new to this and I don't know all the commands yet and how to best use them.  The best thing is I learn something new everyday.  :D 

Mr. Sweet

---

### Post by noeluylee on 2005-12-29
if you like the kde, you have to download and install the kdm.. else you wont get any shutdown option.

sudo apt-get kdm

run.
sudo dpkg-reconfigure kdm

---

### Post by veloct on 2005-12-30
[QUOTE=runlevel0]I'm not sure, but I believe that Kubuntu will disappear, or better said, teher will be only one flavour of this distro called "Ubuntu" and using KDE as default desktop.[/QUOTE]

Can you provide where you got this information from?  I would like to read more on that subject.

---

