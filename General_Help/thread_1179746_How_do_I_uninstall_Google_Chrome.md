---
title: "How do I uninstall Google Chrome?"
date: 2009-06-06
forum: General Help
---

### Post by bhishan on 2009-06-06
I downloaded a deb file and installed google chrome. Now how do I uninstall it?

---

### Post by jenkinbr on 2009-06-06
sudo dpkg -r chromium

That should do the trick.

---

### Post by bhishan on 2009-06-06
> **jenkinbr said:**
> sudo dpkg -r chromium

That should do the trick.

It says "dpkg - warning: ignoring request to remove chromium which isn't installed."

---

### Post by jenkinbr on 2009-06-06
Do you have the deb file laying around somewhere or can you point me in the right direction?

---

### Post by thegreenblob on 2009-06-06
Systen --> Administration --> Synaptic Package Manager

Search: chrome

Right click mark for removal and hit apply.

Or possibly just:

```
sudo apt-get remove google-chrome-unstable
```

In a terminal.

That is assuming you're not mistaking chromium with google chrome.

Hope this helps. :)

---

### Post by Soul-Sing on 2009-06-06
All .debs should be visible in sypatic package manager....

---

### Post by Kadajski on 2009-06-06
> **jenkinbr said:**
> sudo dpkg -r chromium

That should do the trick.

The package is actually "chromium-browser". So...

```
sudo dpkg -r chromium-browser
```

---

### Post by Tibuda on 2009-06-06
> **Kadajski said:**
> The package is actually "chromium-browser". So...

```
sudo dpkg -r chromium-browser
```

They are not talking about chromium, but the branded chrome preview released yesterday. The package name is google-chrome-unstable

---

### Post by bhishan on 2009-06-06
> **thegreenblob said:**
> Systen --> Administration --> Synaptic Package Manager

Search: chrome

Right click mark for removal and hit apply.

Or possibly just:

```
sudo apt-get remove google-chrome-unstable
```

In a terminal.

That is assuming you're not mistaking chromium with google chrome.

Hope this helps. :)

Thanks a lot.
```
sudo apt-get remove google-chrome-unstable
``` worked

---

### Post by hub_cap on 2009-07-16
> **bhishan said:**
> Thanks a lot.
```
sudo apt-get remove google-chrome-unstable
``` worked

Same here and again thanks
Fred:D

---

### Post by dpratima14 on 2009-08-28
> **thegreenblob said:**
> Systen --> Administration --> Synaptic Package Manager

Search: chrome

Right click mark for removal and hit apply.

Or possibly just:

```
sudo apt-get remove google-chrome-unstable
```In a terminal.

That is assuming you're not mistaking chromium with google chrome.

Hope this helps. :)

I got the message Couldn't find package google-chrome-unstable. I need to uninstall chrome because ubuntu updates are not going through due to some chrome issue. Is anyone else having a similar problem?

---

### Post by ali4949 on 2009-12-12
hi
search for Chromium in the synaptic package manager and then u can mark it for complete removal

---

### Post by TriWolf on 2009-12-14
Well actually they changed Chrome so the best way to uninstall it is by the Synaptic Package Manager.

Just search for it by either entering chrome or Google and look for it.
Hope this helps :D

---

### Post by mici_angora on 2010-02-24
> **dpratima14 said:**
> I got the message Couldn't find package google-chrome-unstable. I need to uninstall chrome because ubuntu updates are not going through due to some chrome issue. Is anyone else having a similar problem?


I have the very same problem! My synaptic package manager can't even find chrome..... what do I do? Where exactly do I type that code?

---

### Post by darolu on 2010-02-24
> **mici_angora said:**
> I have the very same problem! My synaptic package manager can't even find chrome..... what do I do? Where exactly do I type that code?

I've seen a lot of confusion between Google Chrome and Chromium (the project behind Google Chrome). First identify what browser is the one you have installed, the easiest way is to click the "About" option on the "tool" menu; it says the name there, if you need something more graphical the Google Chrome icon has MS-Windowish colors while Chromium is blue.

You type that command in the command-line terminal; press Alt+F2 and type "gnome-terminal" in the window that pops up, or you can click on Applications - Accessories - Terminal.

For **Google Chrome**:
```
$ sudo apt-get remove google-chrome-unstable

or

$ sudo apt-get remove google-chrome-beta
```

For **Chromium**:
```
$ sudo apt-get remove chromium-browser
```

Learn more about Command-Line here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by mici_angora on 2010-02-26
> **darolu said:**
> I've seen a lot of confusion between Google Chrome and Chromium (the project behind Google Chrome). First identify what browser is the one you have installed, the easiest way is to click the "About" option on the "tool" menu; it says the name there, if you need something more graphical the Google Chrome icon has MS-Windowish colors while Chromium is blue.

You type that command in the command-line terminal; press Alt+F2 and type "gnome-terminal" in the window that pops up, or you can click on Applications - Accessories - Terminal.

For **Google Chrome**:
```
$ sudo apt-get remove google-chrome-unstable

or

$ sudo apt-get remove google-chrome-beta
```

For **Chromium**:
```
$ sudo apt-get remove chromium-browser
```

Learn more about Command-Line here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)



thank you for the reply! however, the response is "couldn't find package google-chrome-beta" or the unstable one...
what now?

---

### Post by hannon on 2010-03-21
> **darolu said:**
> I've seen a lot of confusion between Google Chrome and Chromium (the project behind Google Chrome). First identify what browser is the one you have installed, the easiest way is to click the "About" option on the "tool" menu; it says the name there, if you need something more graphical the Google Chrome icon has MS-Windowish colors while Chromium is blue.

You type that command in the command-line terminal; press Alt+F2 and type "gnome-terminal" in the window that pops up, or you can click on Applications - Accessories - Terminal.

For **Google Chrome**:
```
$ sudo apt-get remove google-chrome-unstable

or

$ sudo apt-get remove google-chrome-beta
```

For **Chromium**:
```
$ sudo apt-get remove chromium-browser
```

Learn more about Command-Line here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Thank you so much!

---

### Post by typogenerator on 2010-06-19
Here are some updated instructions on this topic. The original issue may be "Solved" but since then, Google has released a so-called "stable" version. 

I just upgraded to Lucid, AGAIN, and Chrome, which I installed in 9.10, but not Chromium, crashes my entire X session. May be related to my crappy intel 855GM...

Regardless, to remove the latest ("stable") version of Chrome, this should do the job:

```
$ sudo apt-get remove google-chrome-stable
```

Cheers

---

### Post by mannamae on 2010-07-02
ok, so I searched Synaptic for both google and chrome and cant find it. I put all of the codes into the terminal and none of them are installed, although google chrome is installed on my machine. I have Ubuntu 8.04 btw and here is the terminal feed
~$ sudo apt-get remove google-chrome-unstable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-unstable
~$ sudo dpkg -r chromium-browser
dpkg - warning: ignoring request to remove chromium-browser which isn't installed.
~$ sudo apt-get remove google-chrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome
~$ ls -l /usr/bin | grep chrom
lrwxrwxrwx 1 root root         32 2010-06-25 15:58 google-chrome -> /opt/google/chrome/google-chrome
~$ sudo apt-get remove google-chrome-beta
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-beta
~$ sudo apt-get remove google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-stable

---

### Post by MooseDog on 2010-07-14
respectfully, this thread should not be marked solved.

just tried every single command-line option presented through the whole thread and nothing worked.  i.e. every single response back from ubuntu was of the package nto found or installed variety, as with mannamae posted above.

i **want** to install the open-source chromium, but this is pissing me off atm.  major ding in my impression of goog too.

---

### Post by thahir1986 on 2010-07-14
Is chromium a google product ?

---

### Post by monster597 on 2010-09-08
I have the same problem only in my case its a little more complex. Anyaways so I installed CHROMIUM first using the Synaptic Package Manager. Later I found that there CHROME actually was available for use in Linux Ubuntu 10.04. So using the Synaptic Manager I uninstalled/removed CHRMOIUM. It was uninstalled successfully. Then went to the google homepage and dowloaded the Google CHROME installer for Linux. CHROME was then successfully installed. However here comes the problem. I attempteed to unistall CHROME using the Synaptic Package Manger, then Ubuntu Software Center, then via the terminal 

sudo apt-get remove google-chrome-stable

Google CHROME gets unistalled "apparently". However when I restart the machine, google Chrome appears again only this time without the ICON. But it still appears in the "Internet section". 

Does anyone have any ideas on how to completely remove it, it will be great because its still being listed but when selected an error is given. 

Thanks in advance!!!!

---

### Post by wribeiro on 2010-09-08
sudo apt-get remove google-chrome-stable

---

### Post by gandaran on 2010-09-08
> **monster597 said:**
> I have the same problem only in my case its a little more complex. Anyaways so I installed CHROMIUM first using the Synaptic Package Manager. Later I found that there CHROME actually was available for use in Linux Ubuntu 10.04. So using the Synaptic Manager I uninstalled/removed CHRMOIUM. It was uninstalled successfully. Then went to the google homepage and dowloaded the Google CHROME installer for Linux. CHROME was then successfully installed. However here comes the problem. I attempteed to unistall CHROME using the Synaptic Package Manger, then Ubuntu Software Center, then via the terminal 

sudo apt-get remove google-chrome-stable

Google CHROME gets unistalled "apparently". However when I restart the machine, google Chrome appears again only this time without the ICON. But it still appears in the "Internet section". 

Does anyone have any ideas on how to completely remove it, it will be great because its still being listed but when selected an error is given. 

Thanks in advance!!!!
using synaptic you should always mark for complete removal any application that you are removing.
to get rid of the icon in internet section use the system » preferences » main menu utility, find the entry and delete it.
and remove or delete the chrome user profile configuration files in home directory (/home/user/.config/google-chrome)

---

### Post by monster597 on 2010-09-10
Thanks alot, I managed to get it uninstalled. I re-downloaded the installation package and installed google chrome again. Then went to the synaptic package manager and search for google-chrome-stable and marked for complete removal. For some reason this time it worked and the are no more traces of it left. WEIRD since I was doing the same exact thing before. Anyways problem sorted. 

Also thanks for the helpful suggestions..!!

---

### Post by FahadMKS on 2010-09-10
> **thegreenblob said:**
> Systen --> Administration --> Synaptic Package Manager

Search: chrome

Right click mark for removal and hit apply.

Or possibly just:

```
sudo apt-get remove google-chrome-unstable
```In a terminal.

That is assuming you're not mistaking chromium with google chrome.

Hope this helps. :)


Using the Synpatic is the easiest way to uninstall/install a software.

---

### Post by NickGenious on 2010-10-29
Find out the package name (can change according to the distribution) :
[FONT=Courier New]user@sligo:~$ dpkg -l | grep chr
ii  **google-chrome-beta**                                  5.0.342.9-r43360                            The web browser from Google
ii  libatm1                                             2.4.1-17.2                                  shared library for ATM (Asynchronous Transfe
ii  libevent-1.4-2                                      1.4.11-stable-1                             An asynchronous event notification library
ii  libpisync1                                          0.12.4-3ubuntu1                             synchronization library for PalmOS devices
ii  libschroedinger-1.0-0                               1.0.8-2                                     library for encoding/decoding of Dirac video
ii  xserver-xorg-video-openchrome                       1:0.2.903+svn758-0ubuntu1                   X.Org X server -- VIA display driver
**[FONT=Arial]now remove it ![/FONT]**
user@sligo:~$ sudo apt-get remove google-chrome-beta[/FONT]

---

### Post by Make Space for Science on 2011-02-16
cheers

---

### Post by Whiskeypawz on 2011-02-22
> **NickGenious said:**
> Find out the package name (can change according to the distribution) :
[FONT=Courier New]user@sligo:~$ dpkg -l | grep chr
ii  **google-chrome-beta**                                  5.0.342.9-r43360                            The web browser from Google
ii  libatm1                                             2.4.1-17.2                                  shared library for ATM (Asynchronous Transfe
ii  libevent-1.4-2                                      1.4.11-stable-1                             An asynchronous event notification library
ii  libpisync1                                          0.12.4-3ubuntu1                             synchronization library for PalmOS devices
ii  libschroedinger-1.0-0                               1.0.8-2                                     library for encoding/decoding of Dirac video
ii  xserver-xorg-video-openchrome                       1:0.2.903+svn758-0ubuntu1                   X.Org X server -- VIA display driver
**[FONT=Arial]now remove it ![/FONT]**
user@sligo:~$ sudo apt-get remove google-chrome-beta[/FONT]

I've tried every option posted on here & I still can't delete Chrome. I get the "couldn't find package" message. Here is the latest from this particular suggestion....


misty@misty:~$ dpkg -l | grep chr
ii  google-chrome-stable                        8.0.552.237-r70801                                            The web browser from Google
ii  libatm1                                     2.4.1-17.1build1                                              shared library for ATM (Asynchronous Transfe
ii  libpisync1                                  0.12.3-4ubuntu1                                               synchronization library for PalmOS devices
misty@misty:~$ sudo apt-get remove google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package google-chrome-stable
misty@misty:~$ 

I'd really like to keep Chrome but it's interfering with my updates, which are more important. I don't speak computer so PLEASE translate any suggestions to "dummy"!

---

### Post by Chutney3k on 2012-02-08
> **thegreenblob said:**
> Systen --> Administration --> Synaptic Package Manager

Search: chrome

Right click mark for removal and hit apply.

Or possibly just:

```
sudo apt-get remove google-chrome-unstable
```In a terminal.

That is assuming you're not mistaking chromium with google chrome.

Hope this helps. :)

This worked for me, thank you! although, I had the 'Stable' version apparently lol.

```
sudo apt-get remove google-chrome-stable
```

Issues with Chrome:

I had no chrome icon visible on desktop or launcher after putting them there.

Most importantly: Chrome would not appear in the Software centre anywhere!

So once again, ty for your help

---

### Post by oldos2er on 2012-02-08
Closed, necromancy.

---

