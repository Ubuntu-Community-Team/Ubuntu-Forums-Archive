---
title: "Converting Xubuntu to Kubuntu"
date: 2017-06-22
forum: Desktop Environments
---

### Post by RobGoss on 2017-06-22
Hello everyone I'm sure this has been ask many times here but I have to ask again.

I have a old Dell latitude D610 that has given me such a hard time to install any flavor of Ubuntu on it, well I finally was able to install Xubuntu on it and it seems to run ok

Question? is there a easy way to convert Xubuntu to Kubuntu without have to do a clean installation 

Thanks so much

---

### Post by CatKiller on 2017-06-22
It should just be a case of installing the kubuntu-desktop package and choosing which environment you log into on the log in screen. Be aware that KDE is significantly heavier than XFCE, so an older laptop may struggle. No harm in trying, though, you can always uninstall it again if you don't like it.

---

### Post by #&amp;thj^% on 2017-06-22
> **RobGoss said:**
> Hello everyone I'm sure this has been ask many times here but I have to ask again.

I have a old Dell latitude D610 that has given me such a hard time to install any flavor of Ubuntu on it, well I finally was able to install Xubuntu on it and it seems to run ok, question? is there a easy way to convert Xubuntu to Kubuntu without have to do a clean installation 

Thanks so much
Hello RobGoss :)
Read carefully the Choices below:
for a full blown system (about 2 Gb extra harddrive use) use:
```
sudo apt-get install kubuntu-full

```
for a smal laptop without plenty of resources use:
```
sudo apt-get install kubuntu-mobile
```

for a normal system use:
```
sudo apt-get install kubuntu-desktop
```

for a KDE only system without the kubuntu artwork:
```
sudo apt-get install kde-full
```
or
```
sudo apt-get install plasma-desktop
```
or
```
sudo apt-get install plasma-netbook

```
Nin'jed by CatKiller :)

---

### Post by vanadium on 2017-06-22
Take note of the packages that are being installed. Keep the list in a text file, so you can eventually remove all these packages later if you change your mind.

---

### Post by RobGoss on 2017-06-22
> **CatKiller said:**
> It should just be a case of installing the kubuntu-desktop package and choosing which environment you log into on the log in screen. Be aware that KDE is significantly heavier than XFCE, so an older laptop may struggle. No harm in trying, though, you can always uninstall it again if you don't like it.

Thanks so much for the tips will remember them

---

### Post by vasa1 on 2017-06-22
That's the first time I've seen mention of "kubuntu-full". Very interesting! After reading a bit about it, I think kubuntu-desktop would be adequate. OP could always install kubuntu-full later and that, I'm assuming, would bring in the remaining packages.

---

### Post by RobGoss on 2017-06-22
1Fallen, thank you sir for the helpful commands, I know it's a matter of just changing to another desktop environment but I wanted something a little more them Xubuntu

This Dell has about 60-GB of storage and 2GB of Ram, it works well with Fedora but! as I might have mentioned I don't really care for it

I will try to apply these changes as soon as I get to my office. I tried Installing Kubuntu but it just hangs right after you setup the user and password not sure why

---

### Post by #&amp;thj^% on 2017-06-22
> **vasa1 said:**
> That's the first time I've seen mention of "kubuntu-full". Very interesting! After reading a bit about it, I think kubuntu-desktop would be adequate. OP could always install kubuntu-full later and that, I'm assuming, would bring in the remaining packages.

Agreed should be plenty. And hence the  (about 2 Gb extra harddrive use)
Just added more for a more complete list of choices.;)
I myself like complete options for choices.
@Robgoss vanadium has a great advise to "Take note of the packages that are being installed. Keep the list in a text file, so you can eventually remove all these packages later if you change your mind."
But showing only 2 gigs of ram and not knowing your video adapter, This might not be a good DE for your lappy.
I'll be interested in your outcome here.
Good Luck :)

---

