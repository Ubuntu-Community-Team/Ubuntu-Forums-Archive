---
title: "Acrobat 9.1.1-1 install on Ubuntu 9.04 (not happening)"
date: 2009-06-15
forum: General Help
---

### Post by wittsend on 2009-06-15
[FONT=Arial][SIZE=2]**Hello, below is an analogy of my experience with Ubuntu 9.04 and Adobe Acrobat. I hope you can see my pain and humor through all this. Jump to point #2 below to get to the problem. Thanks**[/SIZE][/FONT]

**[FONT=Arial][SIZE=2]Point #1[/SIZE][/FONT]**

[FONT=Arial][SIZE=2]**Me:** "Hi, can you tell me how to get to the Johnson place." (**analogy to installing Acrobat 9.1.1-1 in Ubuntu 9.04**).[/SIZE][/FONT]

[FONT=Arial][SIZE=2]**Mr. Linux advisor information at Adobe and/or Ubuntu help menu:**[/SIZE][/FONT]
[FONT=Arial][SIZE=2]"Well, you go down the road a piece. You go by the Holme's place and just about where old man Holme's pig died in 1972 your gun-a turn left. Now the road forks of a time or two. So, at the first fork your gun-a go left and at the second fork your gun-a go right. Then you'll be going by the Jone's place, - that is the Jone's place until their third young-in was born. At some times of the year there is a lake. It's called Jones Lake - when there is a lake - even though the Jones don't live near it no more.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Anyways, on the far side of that there lake is another road you can turn left, or you can turn right. It really doesn't matter much on a count-a that road done runs in a circle. Now on that circle there are three roads. And the good news for you is that two of them roads will take you to the Johnson place. I can't remember which road it is, but if ya take one and you doesn't get to Johnson's then just go back and take one of the other two.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Oh..., and ahh... did ya want Jimmy Johnson's or Billy Johnson's. I ask on account-a Billy don't live in the same parts any more. (**Analogy to advise available on internet**)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]------[/SIZE][/FONT]

[FONT=Arial][SIZE=2]**Point #2**[/SIZE][/FONT]

[FONT=Franklin Gothic Medium][SIZE=2]Pardon my exasperation. I'm new to Linux. I downloaded Adobe Flash and it didn't install. Then I tried again - and it did. Weird..., that is advice I got off the internet, but "chance" seems like an odd way of having an install succeed. Then I got to Acrobat. It downloaded as a .bin file (Flash was not a .bin). [/SIZE][/FONT]
 
[FONT=Franklin Gothic Medium][SIZE=2]NOTHING is even remotely similar to the method Adobe illustrates to install. There is no "edit option" in a non-existent yellow bar on the Firefox browser. When I attempt to install (double click on downloaded file) it asks me for an application to choose. And, none of those option start the install (I assume this is a compressed file that needs to be opened???).[/SIZE][/FONT]
 
[FONT=Franklin Gothic Medium][SIZE=2]I've been through all that "canonical archive" (internet advice claims Adobe Acrobat is there - it isn't) stuff and all that "third part" stuff and that gets me nowhere. So, can someone PLEASE tell me how to install Acrobat 9.1.1-1 into Ubuntu 9.04 (specifically) and remember like the analogy above I HAVE NO IDEA WHAT I AM DOING!!![/SIZE][/FONT]
 
[FONT=Franklin Gothic Medium][SIZE=2]My apology if I'm a little frustrated. After all this is free advice about a free software. On the other hand if people want to see Linux succeed getting commonly loaded software installed without difficulty would go a long way to that end. I'm sure 9 out of 10 people get to the point I am and just say "Screw it (Linux), I'll pay Gate's to not have to hassle this"." Me, I'm too stubborn and cheap to quit yet.[/SIZE][/FONT]
 
[FONT=Franklin Gothic Medium][SIZE=2]Thank you for your time.[/SIZE][/FONT]
[FONT=Franklin Gothic Medium][SIZE=2]Tom[/SIZE][/FONT]

---

### Post by nolliecrooked on 2009-06-15
[Different language or operating system?]("http://get.adobe.com/uk/reader/otherversions/") <= go here

click "Select an OS"

and select "Linux - x86 (.deb)

then click "Continue"

and then click the yellow button thats says "Download Now"

Then when it brings up the download window choose

"Open with gDebi Package Installer"

hope that helps dude.

---

### Post by Celauran on 2009-06-15
You need to set executable permissions.

```
chmod 755 AdbeRdr9.1.1-1_i486linux_enu.bin
./AdbeRdr9.1.1-1_i486linux_enu.bin
```

Also, I'm assuming you have a specific reason for installing Adobe Reader. Ubuntu comes with at least one pdf reader (evince) preinstalled, and it has always worked fine for me.

---

### Post by donkyhotay on 2009-06-15
Honestly the easiest way to install anything is through the repositories. In windows you went to the website, downloaded an .exe and ran it. Here you just pull up a program (like synaptic) and select the file and install it. Seriously, in linux going to the website and downloading something should be the *last* option not the first. An example of the easiest way to install flash player is to run
```

sudo apt-get install flashplugin-nonfree

```
in the terminal. There are similar commands for reader and of course ways of doing through the GUI as well.

---

### Post by nolliecrooked on 2009-06-15
> **donkyhotay said:**
> Honestly the easiest way to install anything is through the repositories. In windows you went to the website, downloaded an .exe and ran it. Here you just pull up a program (like synaptic) and select the file and install it. Seriously, in linux going to the website and downloading something should be the *last* option not the first. An example of the easiest way to install flash player is to run
```

sudo apt-get install flashplugin-nonfree

```in the terminal.

yea, that dosent always work.

---

### Post by wittsend on 2009-06-15
I'm not trying to disrespect anyone here. I understand you did not have to reply. However, this is why I went to the trouble to write the analogy regarding "ineffective information" above.
 
"***Nolliecrooked"*** send me to a site and I'm told to download "Linux - x86 (.deb)"
**But ._deb_ is an option offered file format at the Adobe site I was steered to. Only .bin, .tar.gz, .rpm, and .tar.bz2 files are offered!!!**
 
"***Celauran"*** Tells me to set executable permissions:
chmod 755 AdbeRdr9.1.1-1_i486linux_enu.bin
./AdbeRdr9.1.1-1_i486linux_enu.bin
**But never tells me how running line commands in Linux (Ubuntu) is accomplished! **
**And, how on earth would a layman begin to know these commands anyway (how does this information come about)???**
 
**"*Donkeyhotay*" **Tells me to load software through the Repositories. 
**I have updated and search the Reposities and Adobe Acrobat is not an offering. For that matter NOTHING Adobe comes up - period, in ANY of the Repositories!!!**
 
As a first time Linux (Ubuntu) user I'm very discouraged. It seems you either need to be a Linux Genius from day one, or accept the software "as/is" with little hope of adding selected items that aren't in the Repository.
 
Aside from that I like the product. But if loading a single item of software is going to be a 12 hour disappointment for nothing I'm not sure I grasp the advantage other than the joy of knowing Bill Gate's never got a dime.
 
(I'm at my) Wittsend

---

### Post by Cuba71 on 2009-06-15
Both, the reader and the flash plug-in are offered in the repository under the names:

[INDENT]acroread
adobe-flashplugin[/INDENT]

Should be easy enough

---

### Post by cariboo on 2009-06-15
Is there really a reason you need the latest version? If not you can add the Medibuntu repositories and install acrobat using Add/Remove Programs or Symaptic PAckage Manager. 

[list=1]
[*] Enable the Medibuntu repositories -- go [here]("https://help.ubuntu.com/community/Medibuntu"), and follow the instructions for your version
[*] Go to System-->Administration-->Synaptic Package Manager and click the search button, and type **acroread**, don't enter it in quick search, as it may not be in the database yet.
[*] Once synaptic is finished go to Applications-->Office and click Acrobat Reader
[/list]

I use the alpha version of the next release, because I know how to fix it when it breaks, In a lot of cases depending on which version of Ubuntu you are using, the bleeding edge version will break something else.

---

### Post by wittsend on 2009-06-15
Thank you cariboo 907 that is the descriptive information and process I needed.  I was able to load the software from Adobe.  I think a slightly older version, but in the 9's none the less.
 
Question.  When I looked (scrolled) the Repositories I never found the Adobe software.  But when I searched as you instructed me they were there.  How is that?
Tom

---

### Post by oldos2er on 2009-06-15
> **wittsend said:**
> Question.  When I looked (scrolled) the Repositories I never found the Adobe software.  But when I searched as you instructed me they were there.  How is that?


 The Medibuntu repository is not set up by default, because some of the non-free (i.e. not open source) software it contains is not legal to download in some countries.

 Since you're a new user, I suggest you read the following links:

 [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

 [https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

 [https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

 [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by nolliecrooked on 2009-06-15
its pretty weird that he couldnt find the .DEB on the Adobe download page.

---

### Post by donkyhotay on 2009-06-17
> **wittsend said:**
> I'm not trying to disrespect anyone here. I understand you did not have to reply. However, this is why I went to the trouble to write the analogy regarding "ineffective information" above.
 
"***Nolliecrooked"*** send me to a site and I'm told to download "Linux - x86 (.deb)"
**But ._deb_ is an option offered file format at the Adobe site I was steered to. Only .bin, .tar.gz, .rpm, and .tar.bz2 files are offered!!!**
 
"***Celauran"*** Tells me to set executable permissions:
chmod 755 AdbeRdr9.1.1-1_i486linux_enu.bin
./AdbeRdr9.1.1-1_i486linux_enu.bin
**But never tells me how running line commands in Linux (Ubuntu) is accomplished! **
**And, how on earth would a layman begin to know these commands anyway (how does this information come about)???**
 
**"*Donkeyhotay*" **Tells me to load software through the Repositories. 
**I have updated and search the Reposities and Adobe Acrobat is not an offering. For that matter NOTHING Adobe comes up - period, in ANY of the Repositories!!!**
 
As a first time Linux (Ubuntu) user I'm very discouraged. It seems you either need to be a Linux Genius from day one, or accept the software "as/is" with little hope of adding selected items that aren't in the Repository.
 
Aside from that I like the product. But if loading a single item of software is going to be a 12 hour disappointment for nothing I'm not sure I grasp the advantage other than the joy of knowing Bill Gate's never got a dime.
 
(I'm at my) Wittsend


 Windows actually expects you to be a 'windows genius' from day one as well. Same is true of any other OS such as osX, BSD, solaris, etc. Most people forget this but there was a time where you would have been told 'go to the adobe website and install flash player' without knowing how to use a web browser, how to download, or what to do with the executable. I know because I answer those types of questions to new windows users over the phone (for a fee of course). When you ask for help online we have no clue whatsoever what level of expertise you have but it's generally assumed you know the basics of browsing the web, can find a program located in the applications list and can copy and paste. If you have problems following the instructions posted then ask "how do I get to the terminal?", "How do I copy/paste?" or whatever it is you don't know how to do yet. Get an error message? Post the error message! Help us to help you. If you don't want to do that then you're more then welcome to pay for phone support which is what most new windows users do. Yes if you ask 1 question you will get about 5 different answers, all of which are absolutely correct! Welcome to linux, you actually *have* choices available to you, there is no 'best' method of doing anything. Simply choose the one that sounds simplest to you and do it. Personally I consider the instructions you followed to get this installed much more complicated compared then using the terminal commands but as I mentioned before it's all a matter of having choices.

---

### Post by dbjack on 2009-06-23
> **nolliecrooked said:**
> its pretty weird that he couldnt find the .DEB on the Adobe download page.

On the Adobe download page you need to select "Other languages and OSs" or something like that. It will take you to the various packages of which a deb is available. Hope that helps!

---

### Post by egphilippov on 2009-12-19
**Part One. Short.**

sudo apt-get install acroread
E: Couldn't find package acroread
sudo apt-get install gv
pdf2ps 1.pdf
gv 1.ps 

**Part Two. Dedicated to S.V.Rachmaninov and P.I.Tchaikovsky.**

Rare species of rare animals. Rare species of white and black swans.

**Part Three. With Proof.**

desktop1 ROUBLE sudo apt-get install acroread
E: Couldn't find package acroread
desktop1 ROUBLE sudo apt-get install gv
[sudo] password for user1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xaw3dg
The following NEW packages will be installed:
  gv xaw3dg
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 350kB of archives.
After this operation, 1049kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) jaunty/main xaw3dg 1.5+E-17 [161kB]
Get:2 [http://ru.archive.ubuntu.com](http://ru.archive.ubuntu.com) jaunty/universe gv 1:3.6.5-2 [189kB]
Fetched 350kB in 6s (58.3kB/s)                                                 
Selecting previously deselected package xaw3dg.
(Reading database ... 212780 files and directories currently installed.)
Unpacking xaw3dg (from .../xaw3dg_1.5+E-17_i386.deb) ...
Selecting previously deselected package gv.
Unpacking gv (from .../gv_1%3a3.6.5-2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up xaw3dg (1.5+E-17) ...

Setting up gv (1:3.6.5-2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
desktop1 ROUBLE pdf2ps 1.pdf
desktop1 ROUBLE ls -lh
... 3.8M 2009-12-20 07:07 1.pdf
... 431M 2009-12-20 07:11 1.ps
(* NOTICE TIME DIFFERENCE; top: 98% *)
desktop1 ROUBLE gv 1.ps
(* AND IT'S ALL GRAPHICAL :gv :guitar: mediaproject silence *)

**P.S.**

This .ps was Sal Rachele's LIFE ON THE CUTTING EDGE translated into Russian... [http://www.salrachele.com/](http://www.salrachele.com/) (publishing this link just out of my generosity, will read forum rules later a bit and maybe edit this post).

---

