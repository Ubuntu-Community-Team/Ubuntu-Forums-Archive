---
title: "Easy to install codecs"
date: 2007-03-25
forum: Development CD/DVD Image Testing
---

### Post by peterthewolf on 2007-03-25
Easy-to-install codec wizards: A new guided wizard for installing codecs not shipped with Ubuntu gives users a safe way of in

The above is from the release blurb, where do I find this wizard

---

### Post by Antman on 2007-03-25
> **peterthewolf said:**
> Easy-to-install codec wizards: A new guided wizard for installing codecs not shipped with Ubuntu gives users a safe way of in

The above is from the release blurb, where do I find this wizard

Good question...  :confused:

---

### Post by vasimakhtar on 2007-03-25
Even I didn't find the same. Most of the codecs installed through automatix in Ubuntu 6.6 are removed such as Acrobat.
How can we get this codecs Feiste?
Thanks

---

### Post by chalex on 2007-03-25
This article has a picture: [http://onlyubuntu.blogspot.com/2007/03/ubuntu-704-feisty-fawn-beta-preview.html](http://onlyubuntu.blogspot.com/2007/03/ubuntu-704-feisty-fawn-beta-preview.html)

Add/Remove Programs ->GStreamer plugins

It's the same as "sudo apt-get install gstreamer0.10-plugins-ugly"

---

### Post by bikeboy on 2007-03-25
Try playing something you don't have a codec for with Totem. It should bring up a dialog to install the approriate gstreamer-plugin and you simply select it. Very nice.

---

### Post by pppetter on 2007-04-12
Beatiful! Absolutely beatiful!

---

### Post by rahid on 2008-11-09
As a first time ubuntu user i have a great trouble with installing codec. But i found a great help at [ubuntu-help.co.cc]("http://ubuntu-help.co.cc/index.php/ubuntu-help/36-multimedia/47-multimedia-flash-and-java-support-on-ubuntu"). This is very simple & helpful.

---

### Post by glann.smith on 2008-12-23
Thanks for the information. I will try to install the codecs. If i have any problem with the installation, i will come back with the question.

---

### Post by gnomeuser on 2008-12-23
With Jaunty Ubuntu should include PackageKit which means all of this should be on-demand:

[http://rhughes.fedorapeople.org/screencasts/packagekit-codec-install.ogg](http://rhughes.fedorapeople.org/screencasts/packagekit-codec-install.ogg)

---

### Post by Bablefish on 2009-02-15
Oh come on now, just adding restricted drivers doesn't mean everything is now working as it would say in Windows. The issue as I see it is much more complicated than that. When I first installed Ubuntu it took me about 4 months to get all the codecs I thought I needed to install, and even now I still have issues. I agree there should be an easier way to install all the codecs. I also think it should be added to add/remove to make the process simpier. Also it should be made much more clearer which files should be running smoothly and which ones you still can not play.

---

### Post by eye208 on 2009-02-17
> **Bablefish said:**
> it took me about 4 months to get all the codecs
Why did it take you so long?

---

### Post by Bablefish on 2009-02-19
Easy it's called trying to figure out what I needed. I just want to remind those hotshots out there that there is more than one source that tells you what codec does what. I discovered the hard way that not everyone is right. I just hope when I do a clean install of Jaunty it does not take so long.

---

### Post by Triggerhapp on 2009-02-19
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by terry_gardener on 2009-02-20
the best and easy way that i install codecs after fresh install is using quickstart.

[http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)

or you could use. 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by eye208 on 2009-02-20
> **Bablefish said:**
> Easy it's called trying to figure out what I needed.
Ubuntu's default media player will figure this out automatically when you open a file. You said it's easier in Windows, but I've never seen Windows work like this. If you don't know what codecs are and where to get them, Windows won't help you at all.

---

### Post by Bablefish on 2009-02-23
That is my BIGGEST pet peeve when people say just install Restricted. In 4 words - it did not help. Even when it was the first thing I installed back when I first installed Ubuntu well over a year ago. That is why it took me 4 months to get what I could working. Even now I still have problems with some not all Quicktime and real player files. While AVI files don't play at all. I hope what they say about Jaunty is true and I have less problems.

---

### Post by maybeway36 on 2009-02-23
Ubuntu wants to stay away from these codecs and not point users to them so they don't get in any legal trouble. I think it's completely understandable.

---

### Post by Bablefish on 2009-02-25
I have one last thing to say on the subject Automatrix

---

