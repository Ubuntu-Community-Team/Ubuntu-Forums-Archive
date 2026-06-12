---
title: "Need Help With Downloading Stuff With Ubuntu"
date: 2009-01-10
forum: General Help
---

### Post by Pipzus on 2009-01-10
I was happy when i got linux! Now im really new to it and im trying to 
download the adobe flash player but wouldnt work. also I Tryed downloading
compiz, it lets you chenge the desktop to a 3d cube. wouldnt work.

So, in general, im am going to just say it instead of boring you...

How do you download things with Linux.

Thats my question exactly. Please Help!!!

---

### Post by abn91c on 2009-01-10
how are you  "downloading"? All the programs you mentioned are available in Synaptic
for flash go to applications>accessories>terminal then type sudo apt-get install flashplugin-nonfree
for compiz sudo apt-get install compiz

---

### Post by taurus on 2009-01-10
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by binbash on 2009-01-10
did you check the tutorial section of the forum?There are tons of guides there including compiz-fusion

---

### Post by akelsall on 2009-01-10
Pipzus, there are multiple ways to add/remove programs in Linux. The most popular are:

1. Synaptic Package Manager
2. aptitude
3. apt-get
4. .deb packages

[COLOR="Blue"]**Synaptic Package Manager **[/COLOR]
The is probably the easiest if you're new to Linux (or if you don't know the name of the program). You access it from the System | Administration menu (this is found on the top panel). When prompted, you'll need to enter the password you used when  you first logged into Linux. It's pretty straight forward. 

Just type in the program name (or part of the name) you're looking for in the search box. It will display all matches. Those with a green box to the left of the name are already installed. If it's an empty box to the left of the program name, that means it's available for download, but hasn't been installed yet. If you want to install a program, just click the box. Another box will appear (I'm not in front of my Linux box, but I think it says something like "Accept"). You can mark multiple programs for install. Once they're all marked, there's a button you can click near the top of the screen (I believe it says Accept or Install) and this will install the program(s) for you. 

[COLOR="Blue"]**aptitude**[/COLOR]

This program is ran from the command line (a.k.a. the terminal window). This has many options. You can query an installed package to see the details of it, install, remove, etc. For help on this command, enter **sudo aptitude --help**. The general syntax to install a program with aptitude is:  **sudo aptitude install *program_name***. To remove a program, it's just as easy (just replace the word "install" with "remove".

[COLOR="Blue"]**apt-get**[/COLOR]

This is used just like aptitudue. From what I've read, aptitude is the newer and preferred way, as it does a better job of installing and removing programs cleanly.

[COLOR="Blue"]**.deb packages**[/COLOR]
The .deb packages are files you can download, then double-click on to install. If you come across a program that isn't in the Canonical repositories, you will most likely find it available as a .deb file. Just download the file, double-click, and install.

Hope this gets you started with learning how to install packages (programs) in Ubuntu.

Andy

---

