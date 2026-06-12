---
title: "Hulu"
date: 2009-06-08
forum: General Help
---

### Post by biffthemandible on 2009-06-08
I downloaded the swfflashplayer plugin as well as the adobe flash plugin and downloaded adobe flash player and sun java 6 runtime but videos still won't load on hulu. I don't know what it is I'm doing wrong.

EDIT: nevermind. After restarting my computer for the 4th time it seems to have taken effect.

---

### Post by Therion on 2009-06-08
Assuming you've installed the Adobe plugin, and it sounds like you have, open Synaptic Package Manager and in the Search box type in: **swf**.

If you find you have the package **swf-mozilla-plugin** installed, mark it for removal and close Synaptic.  Try going back to Hulu now.

---

### Post by Wiebelhaus on 2009-06-08
Let's try to knock out all those pesky restricted packages real fast while performing some quick maintenance!

Run:

```
sudo apt-get remove swfdec-mozilla
``````
sudo apt-get -f install
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```Then Run:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```Then:

```
sudo apt-get install libdvdcss2
``````
sudo apt-get install w32codecs
``````
sudo apt-get install ubuntu-restricted-extras
``````
sudo apt-get install flashplugin-nonfree 
```You could consolidate those last four into one command but let's watch those packages install for diagnostic reasons , Then log out and then back in and report back , good luck!

---

