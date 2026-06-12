---
title: "problem with AVG free under ubuntu jaunty"
date: 2009-06-15
forum: General Help
---

### Post by pythonscript on 2009-06-15
A few days ago, I installed AVG free edition for Ubuntu, but after about a day, I realized the my /var directory was completely full. The AVG folder within /var was taking up 32.1 GB of a 32.2 GB partition. Why is this? It hadn't detected any viruses whatsoever, and I can't see how the updates would have taken up this much space so fast. Anyone else had that problem, and if so, how'd you rectify it? Thanks in advance!

---

### Post by TrakerJon on 2009-06-15
Clear all that sludge out and install avast! instead.

It can be downloaded free for home use from [http://avast.com/eng/download-avast-for-linux-edition.html](http://avast.com/eng/download-avast-for-linux-edition.html) You'll need the home user free registration key (emailed to you from their site). The key can be pasted into a terminal window after you type avast at a terminal command prompt. The gui icon is located in Applications > Accessories. Update the program frequently and scan all questionable downloads. ;)

---

### Post by pythonscript on 2009-06-15
I would prefer to use AVG as opposed to Avast, especially given that it requires me to update with a serial number every so often, which is not something I would like to bother with, especially not when I deploy it to someone else's machine. Any ideas about AVG? Thanks for the quick reply!

---

### Post by arkara on 2009-06-15
Why do you need an ant-virus on linux?

---

### Post by munky99999 on 2009-06-15
[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

Oddly this antivirus works well in my experience. I use it on my comps with samba shares. 

However if you try to find this application on theirwebsite. It's basically impossible to do so.

---

### Post by mynameinc on 2009-06-17
> **arkara said:**
> Why do you need an ant-virus on linux?

That was my first thought after reading the title.  One of the reasons I switched to Linux is THE FACT THAT LINUX MALWARE IS ALMOST NON-EXISTENT, AND A SUBSTANTIAL PORTION IS ACCIDENTAL, SO IT IS VERY IMPROBABLE THAT MY COMPUTER BECOMES INFECTED (ABOUT THE SAME CHANCES OF NEVER GETTING A BSOD IN WINDOWS)!!!!!!!!!! (Not angry shouting, happy shouting :-))

---

### Post by pythonscript on 2009-06-17
However, windows CAN get viruses, and sometimes pretty serious ones that disable the system. So... it would make sense for me to install antivirus on my linux partitions so I can scan my windows partitions from within linux. Is anyone actually going to answer my question about avg? I'm looking into bitdefender, but I'm hoping for a solution involving avg...

---

### Post by mynameinc on 2009-06-17
Oh.  In that case, don't use AVG.  AVG slowed my Windows (when I still used XP) considerably.  I used avast! for the rest of my Windows tenure, and other than a few minor problems, it was satisfactory.

---

### Post by n45w73 on 2009-06-18
Where did you find Avg for linux ?

I install avast instead on my new xubuntu box,  it works ok ....

;)

---

### Post by pythonscript on 2009-09-06
I've since completely moved off windows so this isn't really a problem for me anymore, and I used clamav for the various usb devices that I need to scan on occasion. I did try avast for linux, however, and found it about the same as avast on windows. Higher resource footprint and less protection, which isn't exactly what I was looking for. Thanks for the help!

---

### Post by c0mput3r_n3rD on 2009-09-06
If you have antivirus on your linux box then you're defeating one of the major purposes of using linux!!!  I've been running linux on my machines for at least a year now, and have never encountered any type of malware issue.  Winblows, on the other hand, I've tried not using ant-virus and just being very careful instead... never lasted more then a few months.  My advice, just don't use antivirus, waste of time, resources, and memory.  :)

---

### Post by pythonscript on 2009-09-06
> **c0mput3r_n3rD said:**
> If you have antivirus on your linux box then you're defeating one of the major purposes of using linux!!!  I've been running linux on my machines for at least a year now, and have never encountered any type of malware issue.  Winblows, on the other hand, I've tried not using ant-virus and just being very careful instead... never lasted more then a few months.  My advice, just don't use antivirus, waste of time, resources, and memory.  :)

Read my previous posts. I was planning on using the antivirus for scanning my windows partitions, since it's much easier to catch viruses if windows isn't booted. Also, if gives me a file (either through e-mail, ftp, usb drive, whatever) that I plan on passing on to other users that might be using windows, it's the logical thing to do to scan it with antivirus to avoid passing on a possible virus. *We *use Linux, and therefore don't suffer from malware, viruses, etc, but as market share indicates, not everyone does, so as Linux users, we need to consider the other (larger!) chunk of the market.

---

### Post by Cardale on 2009-09-06
Windows sucks!! haha I believe there are Linux anti-virus software that is actually made for Linux.  Might try those instead to scan your windows drives. [http://www.clamav.net/](http://www.clamav.net/)

---

### Post by surfed on 2009-09-06
So what are the files in your var dir? Is there some type of insanly verbose logging?

---

### Post by fela on 2009-09-06
> **mynameinc said:**
> That was my first thought after reading the title.  One of the reasons I switched to Linux is THE FACT THAT LINUX MALWARE IS ALMOST NON-EXISTENT, AND A SUBSTANTIAL PORTION IS ACCIDENTAL, SO IT IS VERY IMPROBABLE THAT MY COMPUTER BECOMES INFECTED (ABOUT THE SAME CHANCES OF NEVER GETTING A BSOD IN WINDOWS)!!!!!!!!!! (Not angry shouting, happy shouting :-))

Getting a virus on Linux is a much, much smaller chance than getting a BSoD on windows I'm afraid :D

---

### Post by pythonscript on 2009-09-06
> **surfed said:**
> So what are the files in your var dir? Is there some type of insanly verbose logging?

Yes, the files in my /var directory were avg logs. It apparently decided to duplicate its logs a few hundred times over. 

[quote]Windows sucks!! haha I believe there are Linux anti-virus software that is actually made for Linux. Might try those instead to scan your windows drives. [http://www.clamav.net/](http://www.clamav.net/)[/quote/
[I]
Read my previous posts... [/I]I mention that I'm now using clamav. Also, must every post on linux security turn into a "windows sucks!!' comment from some user? That was not the purpose of this thread. Try to stay on topic. 
Also, avg for linux and avast for linux are "made for linux." They install perfectly fine on linux. They're not open source or free in any way but price, but they are designed to run on linux natively.

---

### Post by surfed on 2009-09-06
Why are you Kids incapable of staying on topic? Who cares if you dont need AV, some of us do for whatever reason. If you dont have a productive answer dont post your ego bloating garbage.

---

### Post by pythonscript on 2009-09-06
> **surfed said:**
> Why are you Kids incapable of staying on topic? Who cares if you dont need AV, some of us do for whatever reason. If you dont have a productive answer dont post your ego bloating garbage.

Thank you. Shouldn't marking a thread as solved end replies anyways?

---

### Post by surfed on 2009-09-06
> **pythonscript said:**
> Thank you. Shouldn't marking a thread as solved end replies anyways?

Not really as sometimes one solution does not work for all.

---

### Post by c0mput3r_n3rD on 2009-09-06
> **surfed said:**
> Why are you Kids incapable of staying on topic? Who cares if you dont need AV, some of us do for whatever reason. If you dont have a productive answer dont post your ego bloating garbage.

Sooo... wouldn't that include yours?

---

### Post by Cardale on 2009-09-06
> **c0mput3r_n3rD said:**
> Sooo... wouldn't that include yours?
haha classic. 

Just curious who has actually encountered a virus on linux?

---

### Post by Hosmion on 2009-09-06
Well..  This one virus I have does not scan everything (Or at least of what I have used of it..)  But, considering the chance of getting a virus on Linux is very very small..  No point :D..

Download it from [THIS]("http://clamtk.sourceforge.net/") site.

Available in Add/Remove Applications

---

### Post by pythonscript on 2009-09-06
> **Cardale said:**
> haha classic. 

Just curious who has actually encountered a virus on linux?

I've encountered several viruses on usb drives that I've received. Several of these same drives have been destined for other people that I know don't use linux, and I prefer to remove the viruses *before* passing on the data. Security 101, really. These viruses don't affect *my *computer, but no one should knowingly pass on a virus to someone else. At my university, doing so would probably cost me my job, anyways.

---

### Post by theZoid on 2009-09-07
> **munky99999 said:**
> [http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

Oddly this antivirus works well in my experience. I use it on my comps with samba shares. 

However if you try to find this application on theirwebsite. It's basically impossible to do so.

I'm a Bitdefender paid user in windows, so I'm using the Linux now...very nice...free key obtained....thanks for the post.

---

### Post by lisati on 2009-09-07
> **arkara said:**
> Why do you need an ant-virus on linux?
To scan Windows partitions and to scan files that you intend to share with Windows machines. Note: some email providers have a clause in their terms and conditions about not passing on malware.
> **n45w73 said:**
> Where did you find Avg for linux ?

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

(Note: it appears to be command line only, no GUI)

---

