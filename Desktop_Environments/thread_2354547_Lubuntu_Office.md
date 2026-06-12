---
title: "Lubuntu Office"
date: 2017-03-03
forum: Desktop Environments
---

### Post by otto1983 on 2017-03-03
Hi All, I dont have the laptop yet but i'll soon be installing lubuntu onto a Compaq Armada E500.
From what ive heared on youtube this does not come prepackaged with open office (which obviouly I can install later)
My question is, are there better basic office programs I should download or just go for OO?
IE should I dowload individual programs, AbiWord for example?

Could you possibly suggest some programs to fulfill the below purposes:

WORD
EXCEL
OUTLOOK
MEDIA PLAYER (im guessing this will be VLC)
PUBLISHER

Thanks for any advice

David

---

### Post by howefield on 2017-03-03
> **otto1983 said:**
> Hi All, I dont have the laptop yet but i'll soon be installing lubuntu onto a Compaq Armada E500.
From what ive heared on youtube this does not come prepackaged with open office (which obviouly I can install later)
My question is, are there better basic office programs I should download or just go for OO?
IE should I dowload individual programs, AbiWord for example?

A lot depends on the specifications of the laptop. If it can comfortably run [LibreOffice]("https://www.libreoffice.org/") that would be my choice, possibly even [WPS Office suite]("https://www.wps.com/linux").

> Could you possibly suggest some programs to fulfill the below purposes:

WORD
EXCEL
OUTLOOK
MEDIA PLAYER (im guessing this will be VLC)
PUBLISHER
 
Word and Excel could be LibreOffice or WPS Office although there are good results from running MS Office in Linux via Wine.
Outlook I guess would be Thunderbird or as above Wine.
Media Player could be VLC but Parole Media Player is also pretty good and might be a little lighter.
Publisher could be Scribus.

There are a few sites where alternatives to Windows software are listed, eg [http://alternativeto.net/platform/linux/](http://alternativeto.net/platform/linux/), [http://www.linuxalt.com/](http://www.linuxalt.com/), and [https://linuxappfinder.com/alternatives](https://linuxappfinder.com/alternatives), There are many others.

---

### Post by ajgreeny on 2017-03-03
I have just carried out a quick search of the Compaq Armada E500, and I begin to wonder if even Lubuntu is not too large an OS for it; it appears to have only 64 or 128MB ram in some of its models which will not be sufficient to run or install Lubuntu in a useful manner.  If you know the exact specs of that machine tell us and we can perhaps point you towards other available distros that might perfrorm better.

Whatever the outcome of that query, Libreoffice is now the replacement for the Microsoft Office applications, OpenOffice is no longer the default in the Ubuntu family, and you are correct that Lubuntu does not have Libreoffice when installed, but uses Abiword and Gnumeric as the word processor and spreadsheet applications instead.

Libreoffice is just a few clicks away. however, and is my recommendation for you if it is not too large and unwieldy for that machine.  Remember, however, it is not Microsoft Office, and not all files created in MS Office will open without the odd formatting glitch in LO, though those are usually easily overcome in my experience.

VLC? Yes definitely the one to install as it will play almost anything.

Sort out the hardware specs, however, or you may be disappointed.

---

### Post by otto1983 on 2017-03-03
> **ajgreeny said:**
> I have just carried out a quick search of the Compaq Armada E500, and I begin to wonder if even Lubuntu is not too large an OS for it; it appears to have only 64 or 128MB ram in some of its models which will not be sufficient to run or install Lubuntu in a useful manner.  If you know the exact specs of that machine tell us and we can perhaps point you towards other available distros that might perfrorm better.

Whatever the outcome of that query, Libreoffice is now the replacement for the Microsoft Office applications, OpenOffice is no longer the default in the Ubuntu family, and you are correct that Lubuntu does not have Libreoffice when installed, but uses Abiword and Gnumeric as the word processor and spreadsheet applications instead.

Libreoffice is just a few clicks away. however, and is my recommendation for you if it is not too large and unwieldy for that machine.  Remember, however, it is not Microsoft Office, and not all files created in MS Office will open without the odd formatting glitch in LO, though those are usually easily overcome in my experience.

VLC? Yes definitely the one to install as it will play almost anything.

Sort out the hardware specs, however, or you may be disappointed.

Hi There!

The laptop currently has a 80G HD and will be upgraded to 512MB RAM prior to any install of OS, apparently this is the max the E500 can cope with :)

---

### Post by ajgreeny on 2017-03-04
> **otto1983 said:**
> Hi There!

The laptop currently has a 80G HD and will be upgraded to 512MB RAM prior to any install of OS, apparently this is the max the E500 can cope with :)
OK, it may just about be possible to install and run Lubuntu but I think it will be pretty slow; try it and you'll soon see.
You will probably also find that Libreoffice or OpenOffice are too much of a stretch for that spec machine so I would suggest you stick with abiword and gnumeric to see if they fit the bill for you.
I'm not sure about outlook or publisher replacements but thunderbird and scribus may be what you need; how well they'll run with your spec I don't really know so it's trial and error again.

---

### Post by otto1983 on 2017-03-04
Maybe I should re evaluate the OS...... Is ther anything lighter than 
lubuntu?

---

### Post by Irihapeti on 2017-03-04
Possibly if you start with a command-line install plus graphics and install Openbox as your window manager, you may get a lighter system. I use something of the kind on my old Asus EeePC 900. I've not measured how much memory the system actually uses, though, and my machine has 1 GB of RAM.

Alternatively, there may be other Linux distros that are lighter on memory. Do make sure that they're still maintained before using them. Puppy Linux and possibly BunsenLabs might be worth a look. (Disclaimer: I've not run either of them, at least not recently.)

---

### Post by otto1983 on 2017-03-04
Thanks for the advice, as soon as the E500 arives i'll post up my findings..... I know its unsupported now but I had an E500 about 6 years ago and I  ran Saucy Salamader ok... is ther anyway of getting a copy of that?

---

### Post by Irihapeti on 2017-03-04
Saucy Salamander was a non-LTS release which is no longer supported. Therefore, it wouldn't be a good idea to try to run this now, as there could be all sorts of security bugs that haven't been patched.

---

### Post by Perfect Storm on 2017-03-05
Never run unsupported version, it's a security risk. And I'm not sure you still can get source.list to so old ubuntu version.

---

### Post by Irihapeti on 2017-03-05
I'm not sure that it should be necessary, anyway. I've been playing around with a virtual machine which I set to 512MB of RAM, with 16.04. (In fact, I'm using it now.) Of course, it's not a direct equivalent, because I still have a moderately new CPU, but with a careful choice of window manager and other programs, and not trying to run too many things at once, you may have a chance.

It may involve a certain amount of tinkering, but it's a great way to learn more about Linux, even if in the end it doesn't quite work out.

---

### Post by RobGoss on 2017-03-05
> The laptop currently has a 80G HD and will be upgraded to 512MB RAM prior to any install of OS, apparently this is the max the E500 can cope with 

Even bumping up your Ram to **512-MB** will be cutting it close as suggested something lighter will be a good fix for this machine

As time passes it might slow down because of the low amount of Ram the suggestions of the lighter distributions would be best

---

