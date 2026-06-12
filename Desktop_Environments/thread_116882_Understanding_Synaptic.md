---
title: "Understanding Synaptic"
date: 2006-01-13
forum: Desktop Environments
---

### Post by joshearl on 2006-01-13
I've followed lots of guides thanks to these forums and learned a lot in the process! But I seem to be having a problem with accessing certain downloads with *apt-get* or *synaptic.*

almost every time I attempt *apt-get* i get the message *E: Couldn't find package <insert various package here>* (sys-rc-conf mainly).

reading on I found a reply noting to activate universal repositories in synaptic. I ran synaptic, but could not find any option for this. It seems that I indeed to activate this  to have access to more packages. any advice?

---

### Post by hillbilly on 2006-01-13
After you modified your source.list did you do a > sudo apt-get update

---

### Post by kennyhow on 2006-01-13
download automatix.  It changes your sources list for you.

---

### Post by southernman on 2006-01-13
To add universe repos do this:

On your taskbar menu do System > Administration > Synaptic Package Manager. Enter your password when prompted.

Once the app is open go to Settings > Repositories. This will give you a popup window where you need to click on Settings (lower left side of the window). 

Another window will popup and you need to tick the first box at the top "Show disabled software sources" - click close.

After all that you can select the universe repos and click ok. Once that's done click on the reload button in the original popup window.

You should be set to go now...

---

### Post by 5-HT on 2006-01-13
Hi, Ubuntu utilizes four "spheres of influence" for repository sources- main, restricted, universe, & multiverse.

In order to access universe (and multiverse for that matter), you need to edit a configuration file to explicitly allow synaptic/aptitude/apt-get to both read the lists of packages (for all intents and purposes: programs) available in these repositories as well as to download any such given package.


To do so you have two options, either a direct route by editing the configuration file that synaptic will reference, or by editing this file through a synaptic interface.

I'll describe both for you here in terms of 'universe' (for 'multiverse', simply follow the same steps, though substitute any occurrence of universe for multiverse), but would suggest the direct route, if for nothing else but to familiarize yourself with a prominent linux (debian based) file.

A. Editing the direct sources list (found in /etc/apt/sources.list)

Do this in a terminal:

1. Backup the file in case anything goes wrong...

```
 cp /etc/apt/sources.list /etc/apt/sources.list.backup 
```

2. Open up the file for editing

```
 sudo nano /etc/apt/sources.list 
```

3. Uncomment the Universe repository

*Note: any line within this file preceded with an "#" is a comment, and will not be interpreted by synaptic/apt-get/aptitude etc..., the good news is that universe is already in the file, but it is commented so it is not 'activated' in that sense.

So, you need to look for these lines:


```
#deb http://archive.ubuntu.com/ubuntu breezy universe
 #deb-src http://archive.ubuntu.com/ubuntu breezy universe 
```

and uncomment them (remove the '#)

Also, it would be good to allow general/security updates to packages in universe by creating these lines:
```

 deb http://archive.ubuntu.com/ubuntu breezy-updates universe
 deb http://security.ubuntu.com/ubuntu breezy-security universe 
```


***NOTE: depending on your country (I'm guessing U.S. based on your profile info, you may be using a mirror server. This means that your default sources.list may have entries such as [http://us.archive.ubuntu](http://us.archive.ubuntu)...

You can keep this style, or simply delete the mirror (in the example: "us").

4. To save the file and exit nano:

Press control + "X"


*If anything should go wrong, a backup was made and can be retrieved. If you follow my advice and a problem happens, post again and we can easily retrieve the original file and get everything working.


B. Adding universe via synaptic:

1. Open up synaptic ```
 sudo synaptic 
```

2. Click on settings > repositories > add

3. Select each of the three options, and for each put a check upon "community maintained (Universe)"

4. "Ok" out of the windows

5. Click on "Reload", and you're good to go


Hope that helps.


*Edit: southernman beat me to it.

---

### Post by southernman on 2006-01-13
[QUOTE=5-HT]*Edit:  southernman beat me to it.[/QUOTE]
But yours is much more detailed! ;)

---

### Post by PMO6022 on 2006-01-13
[quote=joshearl]almost every time I attempt *apt-get* i get the message *E: Couldn't find package <insert various package here>* (sys-rc-conf mainly).[/quote] 
Another thing to consider once you've set up all the repos: are you trying to install *sysv-rc-conf* (note the "v")?  Misspellings will cause this error because apt-get really can't find the package.

---

### Post by aysiu on 2006-01-13
If you want an explanation so that you really understand Synaptic, read the second link of my signature.

---

### Post by southernman on 2006-01-13
[QUOTE=aysiu]If you want an explanation so that you really understand Synaptic, read the second link of my signature.[/QUOTE]I'm confused, that link doesn't say a thing about "synaptic."

It only gives a quickie howto on editing a sources.list IMO.

Maybe my firefox is malconfigured or something and won't display the whole page... ;p

---

### Post by aysiu on 2006-01-13
[QUOTE=southernman]I'm confused, that link doesn't say a thing about "synaptic."[/QUOTE] Read the *second* link...  about installing software. The first link is the quickie sources.list.

---

### Post by southernman on 2006-01-13
My apologies aysiu, I was having a senior moment (brain fart).

---

