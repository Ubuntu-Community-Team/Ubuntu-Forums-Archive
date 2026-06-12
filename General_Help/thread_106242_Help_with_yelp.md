---
title: "Help with yelp"
date: 2005-12-20
forum: General Help
---

### Post by TeeAhr1 on 2005-12-20
Okay, I've been puzzling over my missing GNOME Help for some weeks now, and I think I've got it pinned down.  It's tied in to the Firefox package, so when I removed 1.07, yelp went with it.

Okay, so now that I've figured that out, I am led into another problem.  Trying to reinstall yelp through Synaptic, I am told that Firefox 1.07 will also be installed, as it is considered a dependency.  Needless to say, I don't want FF1.07 back, it was enough of a pain in my ass getting rid of it the first time ;)

So the question of the morning is: How to install yelp without messing with Firefox?  I have 1.5 installed.  I installed it manually, so I'm guessing Synaptic doesn't know it's there...anyone got some good advice on this front?  Thx, y'all...

---

### Post by BathroomNinja on 2005-12-20
Break up with packages is never fun.

The best I can think of, is perhaps try this.

```

sudo apt-get install -d yelp

```
'yelp' is the name of the package right?  If not, substitute with package name.  -d will download the files only, not install.  Next, you want to find and delete the files you don't want.  Honestly, I'm not sure where apt downloads too.  I guess you could use beagle to find the packages.

then, you would want to do something like
```

sudo apt-get install --no-download -m yelp

```
which should force it to not download any packages, use only packages that are already downloaded and also to ignore missing packages.

I'm sure there is an easier way, but none that I can think of.  Then again, I'm not Mr. Ubuntu Guru.  Edit to add that I'm sure someone is going to kill me for suggesting this horrible way of doing things.

---

### Post by TeeAhr1 on 2005-12-20
Okay, on step one.  Trying to -d it, it still wants to download the additional packages.  But with -d it will not install them, correct?  (sorry if this seems basic, but the last thing I need is for FF1.07 to install itself again)

---

### Post by BathroomNinja on 2005-12-20
[QUOTE=TeeAhr1]Okay, on step one.  Trying to -d it, it still wants to download the additional packages.  But with -d it will not install them, correct?  (sorry if this seems basic, but the last thing I need is for FF1.07 to install itself again)[/QUOTE]


Correct, it will download ONLY.  Let it download all of the packages.  Then, you have to find where it downloaded the packages to (I've no clue).  Then, delete the packages you don't want (FF), etc..

---

### Post by TeeAhr1 on 2005-12-21
Okay, done.  At the end of the process I get the message "download complete and in download only mode."

But now I can't find the file.  First I tried to search for a file named firefox that had been modified today, including hidden/system files, figuring that would cut to the chase better than anything else, but I came up with nothing.  Ditto for yelp, this gave me five files (see screenshot), none of which is a package.

Thoughts/advice/mockery?

---

### Post by BathroomNinja on 2005-12-21
After a bit of searching, it looks like it downloaded them here:
/var/cache/apt/archives

Along with EVERY other deb you ever downloaded.  Perhaps try this.

rename /var/cache/apt/archives to /var/cache/apt/archives-temp
and then start my steps from above.  This should make it easier to find what your looking for. 


So something along these lines:

First, we rename the only archives folder so we don't have to deal with 1000 other deb files.
```
sudo mv /var/cache/apt/archives /var/cache/apt/archives-temp
```

Next, we create a new folder for the debs
```
sudo mkdir /var/cache/apt/archives
```

Next, we tell apt to ONLY download the needed files for yelp
```

sudo apt-get install -d yelp

```

Next, go into /var/cache/apt/archives and remove any of the debs that you don't want.  I don't know what they are since yelp is working for me and I'm using firefox 1.0.7, so I can't recreate your problem.  This part you will have to go at alone.

After you got rid of the files you don't want, we install yelp, telling apt to only used downloaded files and to ignore missing packages
```

sudo apt-get install --no-download -m yelp

```

At this point, apt *should* install yelp. 

After your done, do the following

we rename the newly made /archives folder since we don't really need it any more.
```
sudo mv /var/cache/apt/archives /var/cache/apt/archives-2
```


Finnaly, we rename the original /archives folder back to it's proper name.
```
sudo mv /var/cache/apt/archives-temp /var/cache/apt/archives
```



Cross your fingers.

---

### Post by TeeAhr1 on 2005-12-21
I'm at the office right now, but I'm gonna try this when I get home.  Thx for your help, I'll let you know how it goes...

---

### Post by TeeAhr1 on 2005-12-21
Okay, back home.  I get this:
[QUOTE=terminal]sudo apt-get install --no-download -f -m yelp
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts xprint
The following NEW packages will be installed:
  firefox yelp
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 8467kB/8688kB of archives.
After unpacking 26.7MB of additional disk space will be used.[/QUOTE]
My question is this: Is this saying that it's going to download firefox even though I specified --no-download?  Or (as I suspect and fervently hope) is it just telling me that "these are the dependencies associated with this package?"

(Unrelated note: looking at the man page for apt-get, I learned that if you put a dash at the end of the package name when apt-getting, it will delete the .deb file after installation.  Ex: "apt-get install yelp-"  This will keep your archives folder from getting bloated.)
(EDIT: "apt-get clean" will clear out your archive folder completely.)

---

### Post by BathroomNinja on 2005-12-21
you can do the clean.  I was just assuming you wanted to keep the files..

Whatever you choose, the goal is to have the /archives folder only show you the files it downloaded with the first step.  That way, you can manully delete the ones you don't want (firefox), THEN run the install with downloaded files only.

---

### Post by BathroomNinja on 2005-12-22
I really have no idea why I didn't think of this before, but you can probably just download and install yelp by itself:
[ftp://ftp.gnome.org/mirror/gnome.org/sources/yelp/2.10/yelp-2.10.0.tar.gz](ftp://ftp.gnome.org/mirror/gnome.org/sources/yelp/2.10/yelp-2.10.0.tar.gz)

That might be easier than all of the hoops I'm trying to have you jump through (I still say it should work however).

---

### Post by TeeAhr1 on 2005-12-29
Solved.

Download a new copy of 1.5.

Delete the old one, wherever you had it (make sure you get all its components too, search for firefox and find all the extention folders and stuff).

Unpack the tarball anywhere that isn't /usr/lib/mozilla-firefox/ (I used /usr/lib/firefox/ but it doesn't matter).

Through synaptic or the terminal, install the firefox package.  It will download to mozilla-firefox.  Yelp comes with it.

Make sure all your widgets are pointing to your newly installed file (in my example, /usr/lib/firefox/firefox).

You're done.

---

### Post by Briquet on 2006-01-07
I didn't get it, finally you installed FF 1.0.7 just to install yelp?, I'm having the same problem and I don't want FF 1.0.7 anymore

---

