---
title: "How do I upgrade Vuze from 4.0 to 4.2?"
date: 2009-03-26
forum: General Help
---

### Post by danootz on 2009-03-26
I've tried searching over a three day period on forums and such and I can find no recent info or guides.

I have Ubuntu 8.10 and I have Vuze 4.0.1..etc (Lets call it 4.0)
I would like to upgrade it to 4.2.

I tried using Synaptic and it said it removed Vuze.
There is no repository with the latest 4.2 or a site with a .deb file. So I manually downloaded 4.2 from the Vuze website. I followed a command to install it and it appears in /opt and I made an app launcher in the Main Menu under Internet.

When I launch Vuze and check About it says it is 4.2 but it is lacking the new feature (Devices tab)

According to the official site and other sites, it was a cross platform upgrade and should be included.

Is it possible that I overlooked something when installing? Did I not fully delete all traces of Vuze 4.0 and it only overwrote some info and that's why About tells me its 4.2 but it does not have the actual software features the newest version has?

Additionally, does someone have a simple barebones guide to the file structure of Linux? Like programs are installed in this directory. (Like, Windows under Program Files.)

Or is there a a simpler way to install and uninstall in Ubuntu? I mean Synaptic is awesome but its reliant on repositories and they don't seem to get updated much and I imagine there are sources I know nothing about and might not find on my own. It seems users occasionally have to fall back on manual installs and it's still greek to new users like myself.

thanks in advance.

---

### Post by Neo_The_User on 2009-03-26
Wasn't Vuze supposed to be a bittorrent client? now its like some internet browser or something. I can't even use it for torrents anymore.

---

### Post by danootz on 2009-03-26
> **Neo_The_User said:**
> Wasn't Vuze supposed to be a bittorrent client? now its like some internet browser or something. I can't even use it for torrents anymore.

That's right. It is getting kind of bloated but it's just because they're pushing to make it a source of legitimate torrents and media. But I like it for all the tweaking I can do. At least on Linux. That and my downloads seem much faster on it then any other client.

---

### Post by peakshysteria on 2009-04-13
I would like how to upgrade to 4.2. The auto update suddenly doesn't seem to work. Tried it in Intrepid Ibex. Now been running Jaunty Jackalope for a few hours. But I still can't seem to found out how to upgrade Vuze. Anyone?

---

### Post by droenn on 2009-04-16
Check out this link. Looks like Devices isn't supported in Linux yet even though this was a "cross-platform update". [http://faq.vuze.com/?View=entry&EntryID=336]("http://faq.vuze.com/?View=entry&EntryID=336")

---

### Post by SiN_AmoR on 2009-04-20
I found it !! :D

first, make Vuze download the updated (.jar) file.
then copy it (as root) to /usr/share/java :
```
sudo cp Azureus4.2.0.2.jar /usr/share/java
```

you can override the existing file (Azureus2.jar), but to avoid errors you finally have to edit /usr/bin/azureus :
```
sudo gedit /usr/bin/azureus
```

the next line under "exec" change the path (/usr/share/java/Azureus2.jar) to (/usr/share/java/Azureus4.2.0.2.jar.jar)

then restart vuze :guitar:

good luck ):P

---

### Post by Tyndie on 2009-04-22
No need to do so much :)

Say for example vuze is installed in /usr/share/vuze then in terminal

```

sudo chown -R username:username /usr/share/vuze/

```

* Change "username" to your actual username in ubuntu

Then from now on all you will have to do is restart vuze when it updates.

---

### Post by fycloops on 2009-04-28
> **SiN_AmoR said:**
> I found it !! :D



the next line under "exec" change the path (/usr/share/java/Azureus2.jar) to (/usr/share/java/Azureus4.2.0.2.jar.jar)

good luck ):P

I suspect you meant cahnage the path to: /usr/share/java/Azureus4.2.0.2.jar

You had an extra jar in there!

---

### Post by djodjoman on 2009-05-01
> **SiN_AmoR said:**
> I found it !! :D

first, make Vuze download the updated (.jar) file.
then copy it (as root) to /usr/share/java :
```
sudo cp Azureus4.2.0.2.jar /usr/share/java
```

you can override the existing file (Azureus2.jar), but to avoid errors you finally have to edit /usr/bin/azureus :
```
sudo gedit /usr/bin/azureus
```

the next line under "exec" change the path (/usr/share/java/Azureus2.jar) to (/usr/share/java/Azureus4.2.0.2.jar.jar)

then restart vuze :guitar:

good luck ):P

Thanks, that really worked!

---

### Post by twerky on 2009-06-14
Worked great for me, thanks all:popcorn:

---

### Post by riazrahaman on 2009-08-30
Refer to [https://launchpad.net/~knorr/+archive/ppa](https://launchpad.net/~knorr/+archive/ppa)

update your sources.list and do a sudo apt-get update and sudo apt-get upgrade

---

