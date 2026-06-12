---
title: "Can I run Windows 7 Outlook from Ubuntu ?"
date: 2010-07-20
forum: Desktop Environments
---

### Post by ronbarak on 2010-07-20
Hi,

I read the Wine and Ubuntu documentation and searched on the web, but am unable to figure if the following is possible:

[LIST]
[*]I installed and run Ubuntu 10.04 as a file in Windows 7 (i.e., there no separate Linux partition).
[*]In Windows 7 I have Microsoft Outlook installed and working.[/LIST]
[COLOR="Navy"]My question is:
Is it possible to run the Microsoft Outlook that is installed on Windows 7 from Ubuntu using Wine. Namely, can I avoid having to install Microsoft Outlook twice, once in Windows 7 and once in Wine on Ubuntu ? [/COLOR]

Thanks,
Ron.

---

### Post by lkjoel on 2010-07-20
I am not entirely sure, but you can install PlayonLinux, an application that will be able to install many windows applications.
It uses wine.
Type this in a Terminal (Applications->Accessories->Terminal) window:
```
sudo wget http://deb.playonlinux.com/playonlinux_lucid.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```

---

### Post by howefield on 2010-07-20
> **ronbarak said:**
> Is it possible to run the Microsoft Outlook that is installed on Windows 7 from Ubuntu using Wine.

Short answer is no. Long answer is also no.

---

### Post by ronbarak on 2010-07-20
> **howefield said:**
> Short answer is no. Long answer is also no.

I don't see much difference between the long and short versions. Thanks.

---

### Post by ronbarak on 2010-07-20
> **lkjoel said:**
> I am not entirely sure, but you can install PlayonLinux, an application that will be able to install many windows applications.
It uses wine.
...

From your description I don't see how PlayonLinux will enable me to run the MS Outlook that is installed in Windows 7. Or dis I misunderstood ?

---

### Post by lkjoel on 2010-07-20
Do not read PlayOnLinux by its title.
It has a few scripts that install applications that run with WINE.
The scripts will do adjustments and other things.

---

### Post by Carlo1973 on 2010-07-20
I work in the IT department of a Windows only company. We have little to no Linux in the building. Our Ops manager, and I have started converting a few over to the glories of Linux (our help-desk ticketing system, some of our print servers, our security server and a few others have been implemented within Linux). 

I use my Ubuntu 10.04 laptop at work all the time. This includes for everything MS Office has to offer. On my main desktop at work, I'm using Windows 7 Ultimate, with Office 2010. The files I create within office 2010, at least so far, appear to be readable by the current version of OpenOffice.org.

For email, Evolution works great for me.  It handles everything just as well as Outlook can in my opinion.

I'm just wondering what would be the point of putting a MS Office/Outlook/Word on Ubuntu when the Linux alternatives work just as well?

If you absolutely need to use Outlook, may I suggest installing Virtual-box ([http://www.virtualbox.org/](http://www.virtualbox.org/)), which is a virtual machine, installing XP, Vista, or Windows 7 (as long as you have enough available ram and hard drive space for the virtual drive), and installing the few applications you absolutely require windows versions of within that. This way they remain secure (within the virtual machine), won't cause issues with your Linux distro, no wine configuration, and less hassles.  I use Virtual-Box currently for practicing toward my MCITP exam (combinations of Server 2008, XP, Windows 7, and Vista). Saves a bundle from having to build a bunch of systems specific for Windows.

---

### Post by QIII on 2010-07-20
> **ronbarak said:**
> I don't see much difference between the long and short versions. Thanks.

Unfortunately, the long and short versions are exactly the same:  You will not be able to do what you are describing, if I am understanding you correctly.

You have installed Ubuntu in Windows via Wubi as I understand it.  You wish to install Wine, as I understand it.  You wish to somehow use Wine to run a program installed in Windows.

Unfortunately, there is not a "loop" (except for the loop device that is used by Wine -- but that is a matter for a different thread) that takes you back from Wine to an application installed in the Windows host of your Wubi installation of Ubuntu.

Graphically, you can't get

Windows --> Wubi Ubuntu --> Wine --v
v         ^-----------------------------------<<
v
--> Windows application


The relationship is linear:

Windows --> Wubi Ubuntu --> Wine --> Windows application using Wine.

You can see that you are creating quite a nested system.

What this means is that you would have to install the application using Wine, and whether that would work would depend entirely on whether it will work with Wine.  Not all applications will.

The question I would have is this:  Why on Earth would you want to use your application in Ubuntu when all you would have to do is run it in Windows without the hassle of running it in Ubuntu when you have a Wubi installation?

---

### Post by Carlo1973 on 2010-07-21
Hey QIII your absolutely right. I miss-read his first post where he stated that he was using "Ubuntu within windows 7 as a file" aka WUBI, or some sort of VM.

But the answer still stands as to why one would want to install Outlook to begin with into Ubuntu.

I will admit there are applications made for Windows that I haven't found an ideal equivalent for (yet) that I've had to use with Wine or a VM machine running windows. But for something as benign as Outlook.....  I need to know more, was there something specific about MS Outlook that is required that is believed that Evolution (or any other Linux program) can't handle? Or is it just for familiarity sake? Testing purposes? An attempt to MacGuyver something?

---

### Post by paulisdead on 2010-07-21
I was able to get office 2007 installed in wine, and pretty much everything worked, but outlook was never able to connect to the exchange server.

For the most part, thunderbird with the lightning extension has worked really well for me.

As for why somebody would want outlook on Linux, there are still some tasks you need outlook for to manage your exchange server.  I've had to pull outlook up on another computer a few times to set up some filters on a mailbox, autoreply, and signatures, even though the filters run on the server.  At least since they run on the server, once they're setup, I don't have to keep outlook running.

I heard Exchange 2010 was supposed to allow OWA premium to run in other browsers like firefox, so maybe that can replace some of the need to use outlook to manage a few tasks.  I haven't had to mess with 2010 yet, so I'm not sure if it's OWA premium gives you the filtering controls you get in outlook.

---

### Post by ronbarak on 2010-07-22
> **Carlo1973 said:**
> ...

For email, Evolution works great for me.  It handles everything just as well as Outlook can in my opinion.

I'm just wondering what would be the point of putting a MS Office/Outlook/Word on Ubuntu when the Linux alternatives work just as well?

....

Hi Carlo,

I have quite a lot of old mails organised in Outlook folders, and the advanced searching facility of Outlook is good enough that I can use Outlook as a database of old mails.

Evolution may be good, but will it read inside Outlook pst/ost files ?

Bye,
Ron.

---

### Post by ronbarak on 2010-07-22
> **QIII said:**
> ...

The question I would have is this:  Why on Earth would you want to use your application in Ubuntu when all you would have to do is run it in Windows without the hassle of running it in Ubuntu when you have a Wubi installation?
The answer to that, QIII - is as follows.

Over the last 27 years I was working for companies which used Outlook as their mailing agents. Consequently, I have quite a lot of old mails organised in Outlook folders, and the advanced searching facility of Outlook is good enough that I can use Outlook as a database of old mails.

I'm working now for myself, developing Python apps on Ubuntu (who, in his right mind, given the choice, would develop on Windows ? ;-). So, whenever I need the odd file that is inside one of the Outlook private folders, I need to leave Ubuntu. So, I'm looking for a way not to leave Ubuntu just to read the odd message which (unfortunately) is inside Outlook.

Bye,
Ron.

---

### Post by bigboy_pdb on 2010-07-22
Apparently Thunderbird can import Outlook emails, but you'll have to install Thunderbird first on Windows, import the e-mails into Thunderbird and then export them to the mbox format, which should be readable by Thunderbird and Evolution.

The following link explains how to do it:
[http://support.real-time.com/tbird/outlook_import.html](http://support.real-time.com/tbird/outlook_import.html)

I've never tried it, but some things that you can search on are "convert pst mbox", "Thunderbird import pst", "Thunderbird import Outlook", and so forth (where any search would be done without the quotes). If you want to try with Evolution, just replace the word "Thunderbird" with "Evolution".

You should keep a backup of the original pst file and you should probably also check that the titles, dates, and other data gets converted properly (along with checking the number of e-mails in each folder).

Also, you should also be aware of the repercussions of switching **<EDIT>**back to the Outlook format**</EDIT>**. For example, converting mbox to pst was problematic the last time I attempted to do it. I was able to do the conversion, but dates were stripped leaving the e-mails useless with respect to their ordering.

---

### Post by Vincentlaborant on 2010-07-22
> Evolution may be good, but will it read inside Outlook pst/ost files ?


The migration of Outlook to Evolution goes the best if you go via Thunderbird.

Thunderbird can import the pst/ ost files from Outlook. 

The files can be export out of Thunderbird in (forgot the extension of the file) a format that can be read by Evolution.

---

### Post by ronbarak on 2010-07-23
> **Vincentlaborant said:**
> The migration of Outlook to Evolution goes the best if you go via Thunderbird.

Thunderbird can import the pst/ ost files from Outlook. 

The files can be export out of Thunderbird in (forgot the extension of the file) a format that can be read by Evolution.
 
Converting the nearly 1 GB of mails I have in Outlook pst files is something I very much want to avoid: hence, my quest to read mails inside Outlook pst files from Ubuntu.

---

### Post by bigboy_pdb on 2010-07-23
> **ronbarak said:**
> Converting the nearly 1 GB of mails I have in Outlook pst files is something I very much want to avoid: hence, my quest to read mails inside Outlook pst files from Ubuntu.

Then I'm guessing that you're going to have a difficult time. From what I've found, open source projects don't want to extensively support proprietary formats. They're usually only supported to the extent that you can convert to using open source formats.

One major problem with attempting to use pst files directly is that an open source project that does support it now may not support it in the future or the project might die in the future. It would be better to keep a backup of the pst file and convert it to another format. I'm guessing that you'll spend more time attempting to use the pst file directly than converting it or that it could cost you in the future if you intend on using open source software for a long time.

---

### Post by WinRiddance on 2010-07-24
> **ronbarak said:**
> Hi,

I read the Wine and Ubuntu documentation and searched on the web, but am unable to figure if the following is possible:

[LIST]
[*]I installed and run Ubuntu 10.04 as a file in Windows 7 (i.e., there no separate Linux partition).
[*]In Windows 7 I have Microsoft Outlook installed and working.
[/LIST]
[COLOR=Navy]My question is:
Is it possible to run the Microsoft Outlook that is installed on Windows 7 from Ubuntu using Wine. Namely, can I avoid having to install Microsoft Outlook twice, once in Windows 7 and once in Wine on Ubuntu ? [/COLOR]

Thanks,
Ron.

I installed Windows in a Ubuntu Virtual Box and that worked perfectly fine for everything but games ... so far. Another option would be to change over to Evolution which is basically Ubuntu's answer to Outlook. Evolution allows you to import data from Outlook .... :D

---

### Post by WinRiddance on 2010-07-24
> **ronbarak said:**
> Converting the nearly 1 GB of mails I have in Outlook pst files is something I very much want to avoid: hence, my quest to read mails inside Outlook pst files from Ubuntu.

Initially I had about 2300 messages within 12 folders and about 15 additional sub-folders spanning about 8 years which I was able to import in less than a minute, in perfect order, into Thunderbird.

There's a Thunderbird plugin out there, find it at the Mozilla site, which enables you to import entire folder structures. Once you use Thunderbird permanently you'll never have message import/export problems ever again. Even if you opt switching over to Evolution later, you'll still be able to import Thundebird content one entire folder at a time. That may take 30 minutes or so, but it's only a one time thing. No biggie ...
I wasn't willing to switch to Ubuntu unless I could achieve a **total** switch _without any_ losses (not counting games).

---

