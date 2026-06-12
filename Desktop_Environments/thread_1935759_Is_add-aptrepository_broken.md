---
title: "Is add-aptrepository broken?"
date: 2012-03-04
forum: Desktop Environments
---

### Post by Acharn on 2012-03-04
I want to set my default sound volume to a higher level. I started to follow the instructions in the SoundTroubleShooting Procedure, but the very first command, "sudo add-apt-repository ppa:ubuntu-audio-dev/ppa" produced errors:

~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
[sudo] password for xxxxx: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (6, "Couldn't resolve host 'launchpad.net'")

I searched the forums without result (I don't think the forum Search page has EVER helped me), and even my friend Google didn't help. There was an article on Install Linux Mint Mate Desktop In Ubuntu 11.10 that mentioned in passing editing the /etc/lsb-release file, but mine already contains the correct entries. That article also does not use acc-apt-repositories to add the needed repo, but instead advises editing /etc/apt/sources.list, but I don't have the full name (starteing with "deb") for the repository I want. I was able to use add-apt-repository w couple of weeks ago, but not now. What should I do?

---

### Post by kazztan0325 on 2012-03-05
Hi Acharn,

Have you tried other ways to add repository?


1. Using **"Software Sources"**

-1 Open "Software Sources".
-2 Click on "Other Software" tab.
-3 Click on "Add..." button.
-4 Input APT Line text box as below:

ppa:ubuntu-audio-dev/ppa

-5 Click on "Add Source" button.
-6 Close "Software Sources".
-7 Reload repository and Install packages which you need with "Software Center" or "Synaptic Package Manager".


2. I would like to recommend to use **"Y PPA Manager"** for adding repository.

Please refer these web pages about the tool.

- **"WebUpd8" team  Y PPA Manager in Launchpad**
[https://launchpad.net/~webupd8team/%2Barchive/y-ppa-manager]("https://launchpad.net/~webupd8team/%2Barchive/y-ppa-manager")

- **"Y PPA MANAGER 0.0.8.4 RELEASED, FINALLY WORKS IN KDE TOO"**
[http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html]("http://www.webupd8.org/2011/11/y-ppa-manager-0084-released-finally.html")


Hope these helps.

---

### Post by Acharn on 2012-03-05
Oops. Think I found the problem(s). A couple of Python packages were broken, I used Synaptic to fix them, and I discovered GPG uses port 11371, so I had to open that on my router. Hope that's got it fixed.

---

### Post by Acharn on 2012-03-05
Hey, thank you. That worked. I thought I had to have the whole "http://deb..." thing, and was to lazy to track it down. I'll remember this in the future. I'll check out Y PPA MANAGER, but in truth I don't have to add repos very often. I wa just trying to make my sound more useable (some of the files I want to play have very low volume, some videos, too). I've really liked what I've seen at the WebUpD8 site, too. They have a lot of good ideas.

---

### Post by kazztan0325 on 2012-03-05
You are welcome, Acharn!

Well, if you have liked "Web Upd8" website, I think you would surely like **"OMG! Ubuntu!"** website too.
The link to the site is:
[http://www.omgubuntu.co.uk/]("http://www.omgubuntu.co.uk/")

Please check it out, if you are interested in.

---

