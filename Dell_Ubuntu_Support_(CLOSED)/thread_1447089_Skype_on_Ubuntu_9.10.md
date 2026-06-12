---
title: "Skype on Ubuntu 9.10"
date: 2010-04-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dogwonthunt on 2010-04-04
When I try to install Skype for Ubuntu the most recent version is 8.10.  When I try to install on my Dell Inspiron Mini 10 with 9.10 I get the error message "Error: Dependency is not satisfiable: libasound2".  I have seen other folks have Skype working on 9.10, what do I need to do?

---

### Post by Hman242 on 2010-04-04
Go into Synaptic and look for "libasound2". That should hopefully do it.

---

### Post by mikewhatever on 2010-04-04
I was under the impression that libasound2 was installed by default in 9.10. In fact, I have skype installed in 9.10 running on Dell mini 10. Could it be that you are not running 9.10?

What are the outputs of the following:

cat /etc/lsb-release

aptitude search libasound

---

### Post by dogwonthunt on 2010-04-05
When I run cat /etc/lsb-release I get the following:

cat: /etc/lsb-releasecat: No such file or directory
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1

---

### Post by dogwonthunt on 2010-04-05
When I run aptitude search libasound I get:

v       libasound-dev                -
i   A  libasound2                     - ALSA library
p       libasound2-dev              - ALSA library development files
p       libasound2-doc              - ALSA library developer documentation
p       libasound2-plugins        - ALSA library additional plugins

---

### Post by winjeel on 2010-04-05
Not much help now, but I can assure you that I have Skype running absolutely fine on my Mini 10v, so it can work on yours, too. Keep at it.

---

### Post by mikewhatever on 2010-04-05
> **dogwonthunt said:**
> When I run aptitude search libasound I get:

v       libasound-dev                -
i   A  libasound2                     - ALSA library
p       libasound2-dev              - ALSA library development files
p       libasound2-doc              - ALSA library developer documentation
p       libasound2-plugins        - ALSA library additional plugins

As you can see, libasound is installed, but I suspect Hardy has an older version, which makes Skype complain. Try looking around for an older version of Skype.

---

### Post by dogwonthunt on 2010-04-05
> **winjeel said:**
> Not much help now, but I can assure you that I have Skype running absolutely fine on my Mini 10v, so it can work on yours, too. Keep at it.
 
When you run the two commands in Terminal as suggested to me, what are your results?  Curious to see if they match the results I saw.  We just got our Mini 10v, this past Friday, so I would expect it to be up to date.
 
What are the outputs of the following:

cat /etc/lsb-release

aptitude search libasound 
 
Thank you to all for your help.  Ubuntu is new to me and while parts of it are great and easy to deal with, coming from a Windows environment things like this are new and frustrating.

---

### Post by mikewhatever on 2010-04-06
I think what you have is Dell's custom 8.04, which is reportedly shipped with the minis. Have you tried looking for skype in the repositories? I am not familiar with its interface and tools, and so stick to commands.

sudo apt-get update

aptitude search skype

Last but not least, Dell used to ship its minis with an lpia (low power intel architecture) built of Ubuntu. You can verify which one you have by running the following:

uname -m

---

### Post by ugm6hr on 2010-04-07
> **dogwonthunt said:**
> When you run the two commands in Terminal as suggested to me, what are your results?  Curious to see if they match the results I saw.  We just got our Mini 10v, this past Friday, so I would expect it to be up to date.

If you have not installed Ubuntu yourself, then you will have Dell's lpia version of 8.04 - not 9.10.

The reason for this is Dell committed itself to using LTS versions of Ubuntu for its Mini.

If you want Skype, you'll probably have to install Ubuntu yourself.

Good advice here: [www.ubuntumini.com](www.ubuntumini.com)

Might be worth looking into trying Ubuntu 10.04 - I suspect it works well - although I haven't yet put it on my Mini (I'm still on 9.04 on the Mini).

---

### Post by shaka_zulu on 2010-04-09
Obviously since you have 8.04 and you have downloaded Skype for 8.10+ versions you will not be able to install it. What is weird is that Skype do not support versions <8.10 which is a problem. I found somewhere that there is a command to force .deb package for 8.10+ to work on older Ubuntu versions but i just can not find it.

---

