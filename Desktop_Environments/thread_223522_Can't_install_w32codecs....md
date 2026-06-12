---
title: "Can't install w32codecs..."
date: 2006-07-26
forum: Desktop Environments
---

### Post by wargames on 2006-07-26
Hi, I followed the Ubuntu wiki section in the Restricted Formats section to install the w32codecs and I can't get them to install.

Here's my terminal output:

```
~$ wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
--13:26:43--  [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
           => `w32codecs_20060611-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.debian.org](http://www.debian.org) [following]
--13:26:44--  [http://www.debian.org/](http://www.debian.org/)
           => `index.html'
Resolving [www.debian.org](www.debian.org)... 194.109.137.218
Connecting to www.debian.org|194.109.137.218|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

~$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
Password:
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb

```
I've tried several times and it says it downloaded it, but it can't find it. I did a file search on the hard drive and can't find any trace of this file. So where is it located? It took about 2 seconds to download on my dial-up connection, so something tells me that something is not right.

Any ideas on how to install it, and why I keep getting this error?

---

### Post by Cornmuffin on 2006-07-26
```
sudo apt-get install w32codecs
```

Try that.  It worked for me when I was getting mplayer to work.  I'm almost positive that is the package's name, but I'm at work right now so I cannot double check...but try that and let me know.

---

### Post by wargames on 2006-07-26
> **Cornmuffin said:**
> ```
sudo apt-get install w32codecs
```

Try that.  It worked for me when I was getting mplayer to work.  I'm almost positive that is the package's name, but I'm at work right now so I cannot double check...but try that and let me know.

No, doesn't work. Says it cannot find package.

---

### Post by matthew on 2006-07-26
The package is available at the location listed...I just checked. I recommend trying again. Maybe there was a weird glitch somewhere. The process on the wiki page really should work.

---

### Post by wargames on 2006-07-26
> **matthew said:**
> The package is available at the location listed...I just checked. I recommend trying again. Maybe there was a weird glitch somewhere. The process on the wiki page really should work.

Just tried it again, and still it doesn't work. Keeps giving the same message as above over and over. What did it really download anyway and where is it?

---

### Post by matthew on 2006-07-26
> **wargames said:**
> Just tried it again, and still it doesn't work. Keeps giving the same message as above over and over. What did it really download anyway and where is it?Odd. I have a couple of ideas you can try.

First, look in your home directory (/home/yourusername) and see if the file w32codecs_20060611-0.0_i386.deb is there. If it is, just click on it to open it and the new deb installer that came with Ubuntu 6.06 should begin the installation process. If the file is there but that doesn't work, then delete the file. 

If the file isn't there, then click on this link. When the dialog box asks what you want done with the file, select "Open with" and Gdebi Package Installer. It will download the w32codecs file to your computer and begin the installation process for you. This should work as long as there isn't a corrupted downloaded file already sitting in your home directory.

[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)

---

### Post by matthew on 2006-07-26
> **matthew said:**
> Odd. I have a couple of ideas you can try.

First, look in your home directory (/home/yourusername) and see if the file w32codecs_20060611-0.0_i386.deb is there. If it is, just click on it to open it and the new deb installer that came with Ubuntu 6.06 should begin the installation process. If the file is there but that doesn't work, then delete the file. 

If the file isn't there, then click on this link. When the dialog box asks what you want done with the file, select "Open with" and Gdebi Package Installer. It will download the w32codecs file to your computer and begin the installation process for you. This should work as long as there isn't a corrupted downloaded file already sitting in your home directory.

[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)

EDIT: I just tested this second method as I had posted the idea knowing it should work in theory. I'm happy to state it worked beautifully for me.

---

### Post by aysiu on 2006-07-26
If, for some reason, that repository doesn't work for you, you can try this one: ```
wget -c http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32*.deb
```

---

### Post by wargames on 2006-07-26
Thanks Matthew.

Your link worked. It appears that whenever I used the wiki instructions, the wget command would download a index.html file and placed that into my Home directory instead of the *.deb file. Is the wget command getting redirected to a index.html file from debian.org?

Anyway thanks for the help. :D

---

### Post by matthew on 2006-07-26
> **wargames said:**
> Thanks Matthew.

Your link worked. It appears that whenever I used the wiki instructions, the wget command would download a index.html file and placed that into my Home directory instead of the *.deb file. Is the wget command getting redirected to a index.html file from debian.org?

Anyway thanks for the help. :DGlad we got it working for you. I'm not sure why the wget link didn't work right for you. It is written correctly. Just one of those odd occurrances I guess.

---

### Post by cuz on 2006-08-01
I just wanted to add that I had the same problem (down to the downloading of the index.html file instead of the package). Also, the link worked fine for me. Thanks.

---

### Post by Roasted on 2006-11-29
> **aysiu said:**
> If, for some reason, that repository doesn't work for you, you can try this one: ```
wget -c http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32*.deb
```

After doing a search I came across this thread. I tried adding a repository as the above quote said (or I'm assuming that's what I was supposed to do). Now, we have a problem.

Now I get 2 errors when I try to reload:

Error 1:

E: Type 'wget' is not known on line 68 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Error 2:

E: Type 'wget' is not known on line 68 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'wget' is not known on line 68 in source list /etc/apt/sources.list
E: Unable to lock the list directory


Now what? Also, I can't seem to install W32codecs. And before you folks say automatix, I just tried it about 30 times. Doesn't work.

---

### Post by aysiu on 2006-11-29
*wget* shouldn't be in your sources.list.

It is a command you issue from [the terminal](http://www.psychocats.net/ubuntu/terminal).

Open up [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste in the first command and press the **Enter** key on your keyboard.

Then paste in the second command and press **Enter**.

The first command fetches (using *wget*) the installer file for w32codecs. The second command installs the w32codecs.

---

### Post by Roasted on 2006-11-29
How do I reverse what I did then?

---

### Post by aysiu on 2006-11-30
> **Roasted said:**
> How do I reverse what I did then?
Try [this](http://www.psychocats.net/ubuntu/sources).

---

### Post by Roasted on 2006-11-30
When I ran that command in terminal to install the codecs, I got this:

curtis@curtis-desktop:~$ wget -c [http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
--21:01:13--  [http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
           => `w32codecs_20060611-1plf1_i386.deb'
Resolving packages.freecontrib.org... 88.191.37.159
Connecting to packages.freecontrib.org|88.191.37.159|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:01:13 ERROR 404: Not Found.



:(

---

### Post by aysiu on 2006-11-30
Seems that link is down. Try this, then: ```
wget -c http://packages.freecontrib.org/plf/pool/edgy-plf/non-free/w32codecs_20060611-1plf6.10_i386.deb
sudo dpkg -i w32codecs_20060611-1plf6.10_i386.deb
```

---

