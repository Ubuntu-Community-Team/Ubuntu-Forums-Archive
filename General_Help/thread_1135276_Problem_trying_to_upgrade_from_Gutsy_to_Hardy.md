---
title: "Problem trying to upgrade from Gutsy to Hardy"
date: 2009-04-24
forum: General Help
---

### Post by shelbyvision on 2009-04-24
I decided to try the upgrade button on the Update Manager to upgrade to 8.04, since 7.10 is now obsolete. Problem is, it won't work. It gives me this error message: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110430&d=1240278167[/IMG]

What can be done to make it work? Do I need to file a bug report?

---

### Post by snowpine on 2009-04-24
Gutsy is no longer supported, so my suggestion is back everything up, do a fresh install of 8.04, 8.10, or 9.04, and restore any important documents.

ps I think there is an ugly, unsupported workaround that might work. Edit your /etc/apt/sources.list and change all instances of "gutsy" to "hardy", then sudo apt-get update && sudo apt-get dist-upgrade. I personally would do the fresh install, but just giving you all the options.... :)

---

### Post by shelbyvision on 2009-04-24
I was all ready to except that answer, but then realized, it can't be right. Just yesterday my wife performed the very same upgrade on her laptop, and it went flawlessly. I suppose the difference is she has nothing but the basic software that came with the original installation, while I have a few "unofficial" things installed.

---

### Post by snowpine on 2009-04-24
> **shelbyvision said:**
> I was all ready to except that answer, but then realized, it can't be right. Just yesterday my wife performed the very same upgrade on her laptop, and it went flawlessly. I suppose the difference is she has nothing but the basic software that came with the original installation, while I have a few "unofficial" things installed.

If you've added anything to your sources.list, try commenting out those lines by adding a # at the start of the line. You can try un-commenting them again once your upgrade is (hopefully) successful.

---

### Post by shelbyvision on 2009-04-24
> **snowpine said:**
> If you've added anything to your sources.list, try commenting out those lines by adding a # at the start of the line. You can try un-commenting them again once your upgrade is (hopefully) successful.

I'm not sure which sources.list you're referring to, but I searched and found what seemed the most relevant, /etc/apt/sources.list.distUpgrade.
There were two repositories there that were described as unsupported, and I commented them out. It made no difference.

---

### Post by micdhack on 2009-04-24
Im having the same problem only on a server edition. i replace the source list and did an update, dist-upgrade but now im getting this error:
> Setting up libc6 (2.9-4ubuntu6) ...
Checking for services that may need to be restarted...
Checking init scripts...
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 20
Errors were encountered while processing:
 libc6
E: Sub-process /usr/bin/dpkg returned an error code (1)

i tried apt-get install -f, configure but results are always the same.

---

### Post by zvacet on 2009-04-24
Back up your sources list 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
```

and then open it 

```
gksudo gedit /etc/apt/sources.list
```

add new lines

```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

Now you should be able to upgrade to Hardy.

---

### Post by shelbyvision on 2009-04-24
> **zvacet said:**
> Back up your sources list 

<snip>

```
sudo apt-get update && sudo apt-get upgrade
```

Now you should be able to upgrade to Hardy.

How I wish it were true. Unfortunately, it still gives the same error message. When it's done the update manager shows up at the top and says I have 574 updates available. There are actually only 20, and only 14 or so are checked. The heading at the top of the list says "Backports". Are these what I need to put the system back the way it was or what? I'm afraid to go ahead without knowing.

---

### Post by zvacet on 2009-04-24
We can try other way.Open your source list and delete lines I suggested you to put in on.Sorry if that means anything to you.When you do that then replace every line witch have **archive.ubuntu.com** in it with **old-releases.ubuntu.com** .For example

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

to

deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) gutsy main restricted

save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by shelbyvision on 2009-04-24
OK, that took it a little further, I think, but now it gives me a new error message:

---

### Post by zvacet on 2009-04-25
It looks like it is time to take **snowpine** advice.

---

### Post by shelbyvision on 2009-04-25
> **zvacet said:**
> It looks like it is time to take **snowpine** advice.

You mean downloading the CD and installing with that?

---

### Post by zvacet on 2009-04-25
Back all your repositories as they were before and then replace gutsy with hardy in every line.Save and close and 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by shelbyvision on 2009-04-25
Thank you, Zvacet. I did what you suggested and at first it didn't work, but I looked at the sources it tried to access, and the top two lines had to do with the Ubuntu CD. So I decided to try again, with the original Ubuntu 7.10 installation CD in in the CD ROM, and it worked! Does that make any sense? It took about 7 hours to get it all installed, whew! But it's done and working. THANKS! :)

---

