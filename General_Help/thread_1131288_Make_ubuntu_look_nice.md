---
title: "Make ubuntu look nice"
date: 2009-04-20
forum: General Help
---

### Post by ironsight2000 on 2009-04-20
I am trying to find a theme that looks nice the has glass and also 

what would be a good dock dock would be nice as I have tried Cairo but it seems buggy. any suggestions, also i get an error when trying to use desklets in 9.04

---

### Post by brunogirin on 2009-04-20
What sort of error do you get with desklets and when does it happen? Can you post a screen shot or the full text of the error, with a description of how to reproduce it?

---

### Post by scottuss on 2009-04-20
> **ironsight2000 said:**
> I am trying to find a theme that looks nice the has glass and also 

what would be a good dock dock would be nice as I have tried Cairo but it seems buggy. any suggestions, also i get an error when trying to use desklets in 9.04

Get GnomeDo [http://do.davebsd.com/](http://do.davebsd.com/) and then put it in Dock mode, it's awesome

---

### Post by blazemore on 2009-04-20
The theme is called Docky, and is selected the same way as any other GnomeDo theme.

---

### Post by ironsight2000 on 2009-04-20
> **brunogirin said:**
> What sort of error do you get with desklets and when does it happen? Can you post a screen shot or the full text of the error, with a description of how to reproduce it?

click on applications > accessories > gDesklets

Could not launch 'gDesklets

Failed to execute child process
"gdesklets" (no such file or directory")

---

### Post by blazemore on 2009-04-20
What happens when you run the command gdesklets from a terminal?

---

### Post by ironsight2000 on 2009-04-20
usr/bin/python2.5 bad interpreter :No such file or dir

---

### Post by blazemore on 2009-04-21
```
sudo apt-get install python
```
That's a weird error.

---

### Post by ironsight2000 on 2009-04-21
still getting the same error could it be because i am using 9.04 RC

---

### Post by Slim Odds on 2009-04-21
> **scottuss said:**
> Get GnomeDo [http://do.davebsd.com/](http://do.davebsd.com/) and then put it in Dock mode, it's awesome

GnomeDo is in the Ubuntu repositories.

But I don't see a "dock" mode.???

---

### Post by scottuss on 2009-04-21
> **Slim Odds said:**
> GnomeDo is in the Ubuntu repositories.

But I don't see a "dock" mode.???


Go to Theme and select Docky. Sorry, I worded it incorrectly, my fault :)

---

### Post by Darael on 2009-04-21
EDIT: saw the post above that went in while I was writing...

---

### Post by Slim Odds on 2009-04-21
> **scottuss said:**
> Go to Theme and select Docky. Sorry, I worded it incorrectly, my fault :)

I don't see a "Docky" theme.

Only "Classic", "Glass Frame" and "Mini"

---

### Post by chriskin on 2009-04-21
> **Slim Odds said:**
> I don't see a "Docky" theme.

Only "Classic", "Glass Frame" and "Mini"

why not install a later version of gnome do then? if you add their repository (deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main) you will get the latest

---

### Post by Slim Odds on 2009-04-21
> **chriskin said:**
> why not install a later version of gnome do then? if you add their repository (deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main) you will get the latest

I like to stick to the standard repositories unless there is a very compelling reason not to. I'm not really compelled in this case.

---

### Post by chriskin on 2009-04-21
> **Slim Odds said:**
> I like to stick to the standard repositories unless there is a very compelling reason not to. I'm not really compelled in this case.

i don't think that you can get the docky theme then. try awn or wait for the stable version of cairo-dock 2 to be released (considering that you have a problem with third party repositories, i would think that you have problem with their unstable releases, if not sorry)

---

### Post by Slim Odds on 2009-04-21
> **chriskin said:**
> i don't think that you can get the docky theme then. try awn or wait for the stable version of cairo-dock 2 to be released (considering that you have a problem with third party repositories, i would think that you have problem with their unstable releases, if not sorry)

I didn't say I had a problem. I just don't need them most of the time.

GnomeDo works just fine as is.

---

### Post by chriskin on 2009-04-21
> **Slim Odds said:**
> I didn't say I had a problem. I just don't need them most of the time.

GnomeDo works just fine as is.

if you don't avoid them in order to make sure that your system is 100% stable (my brother does that - can't say that my list of third party repos has less than 30 of them in it) this one might interest you, i used docky a lot in the past.

anyway

why not use avant window navigator? it looks like a simple version of cairo but it can do a lot (they call it dock-like though, can't see why it is not a full dock. or kiba (or is it named kida? never managed to remember)

---

### Post by Maheriano on 2009-04-21
I have some quick semi-topic questions.

1. What's a dock?
2. What's a desklet?

---

### Post by chriskin on 2009-04-21
> **Maheriano said:**
> I have some quick semi-topic questions.

1. What's a dock?
2. What's a desklet?
 

2.desklets (and screenlets) are little wigdets on your screen that do various works, ranging from clocks, cpu info, on-desktop menus, etc etc. i use a screenlet that tells me everything about the computer (cpu, ram , temperature , wifi, ) and stuff about the weather, and another that lets me navigate through windows easily.

1. if you have seen a mac it is the thing at the lowest part of the screen. if you haven't (and still are too bored to check the google image search for "dock") i hope i can make you understand :P (messy definition ahead) a dock is a place on the screen where you can place some icons to use them fast. in most docks you can also see the apps that are currently running.

---

### Post by blazemore on 2009-04-21
```
sudo su
echo deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main >> /etc/apt/sources.list && sudo aptitude update && sudo aptitude install gnome-do
```
Updates to latest Gnome-Do.

---

### Post by hyperdude111 on 2009-04-21
Gnome do has a nice dock or you can try AWN

---

### Post by scottuss on 2009-04-21
> **Slim Odds said:**
> I didn't say I had a problem. I just don't need them most of the time.

GnomeDo works just fine as is.


Then you don't get the Docky theme. Stop complaining :P

---

### Post by Maheriano on 2009-04-21
> **chriskin said:**
> 2.desklets (and screenlets) are little wigdets on your screen that do various works, ranging from clocks, cpu info, on-desktop menus, etc etc. i use a screenlet that tells me everything about the computer (cpu, ram , temperature , wifi, ) and stuff about the weather, and another that lets me navigate through windows easily.

1. if you have seen a mac it is the thing at the lowest part of the screen. if you haven't (and still are too bored to check the google image search for "dock") i hope i can make you understand :P (messy definition ahead) a dock is a place on the screen where you can place some icons to use them fast. in most docks you can also see the apps that are currently running.

AWESOME, thanks! I made a post a few months ago asking how to get that shelf thing on my desktop but nobody posted in it. I thought all was lost, I'm going to go download that now.

---

### Post by Maheriano on 2009-04-21
> **Slim Odds said:**
> GnomeDo is in the Ubuntu repositories.

But I don't see a "dock" mode.???

No it's not. I checked for it just now and it found nothing.

---

### Post by Slim Odds on 2009-04-21
> **Maheriano said:**
> No it's not. I checked for it just now and it found nothing.

Indeed it is. It's installed by default in 8.10

---

### Post by Maheriano on 2009-04-22
> **Slim Odds said:**
> Indeed it is. It's installed by default in 8.10

I searched Add/Remove and Synaptic Package Manager and found nothing. How do you get it?

---

### Post by Slim Odds on 2009-04-22
> **Maheriano said:**
> I searched Add/Remove and Synaptic Package Manager and found nothing. How do you get it?

The package is called "gnome-do"

---

### Post by scottuss on 2009-04-22
If you can't find it and don't have a problem with 3rd party repos (I don't see why you should...) then you can add the official Gnome Do PPA to get latest versions

[http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu]("http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu")

Edit: I'm not interested in people telling me why I shouldn't use 3rd party repos by the way. I can't be bothered with debating it :p

---

### Post by Slim Odds on 2009-04-22
> **scottuss said:**
> Edit: I'm not interested in people telling me why I shouldn't use 3rd party repos by the way. I can't be bothered with debating it :p

Boy are you hung up on this.

If you want to use anything, go ahead. No one is stopping you.

Some of us are just pointing out that GnomeDo is in the standard repositories and that it works fine.

---

### Post by scottuss on 2009-04-22
> **Slim Odds said:**
> Boy are you hung up on this.

If you want to use anything, go ahead. No one is stopping you.

Some of us are just pointing out that GnomeDo is in the standard repositories and that it works fine.

And I was just stating that for the up to date version you can use the PPA.

You are absolutely right, the standard repository does contain Gnome-Do.

---

### Post by DaLightBender on 2009-07-15
Thanks you guys are really making my UBUNTU experience very easy.  I now have a Dock and plan on downloading a Desklet.  Can you point me in the direction of some of those cool pictures for backgrounds.

---

