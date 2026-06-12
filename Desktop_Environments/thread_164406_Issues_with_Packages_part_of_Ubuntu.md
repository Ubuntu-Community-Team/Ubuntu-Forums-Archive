---
title: "Issues with Packages part of Ubuntu"
date: 2006-04-22
forum: Desktop Environments
---

### Post by JohnN on 2006-04-22
Hello Folks,

I just installed Ubntu, and I have a simple issue with the Packages website for 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
I downloaded the 5.10 Brezzy verision and installed it earlier this afternoon.


When I Go and pick a software project to download, and open it, it opens up a program called "Archive Manager"  and gives the following error message

"Could not open "filename.deb"
Archive type not supported.

Filename is replaced with the long file title that I am trying to download.
What can do to get this to install the programs, what else would I need to download to get it work, and understand the .deb filetype?

Please Help,

Have a blessed day!

John N

---

### Post by croak77 on 2006-04-22
Are you trying to install programs? If you want to install something that is listed at packages.ubuntu.com, just use apt-get or synaptic.  Since you are new to ubuntu, you should read [http://help.ubuntu.com/starterguide/C/index.html]("http://help.ubuntu.com/starterguide/C/index.html")
Chaptor 2 deals with installing programs.

---

### Post by JohnN on 2006-04-22
Well, where do i get that apt-get program? or if it's already installed, where do I get it?

---

### Post by croak77 on 2006-04-22
It's already installed. You can use apt-get from a terminal:
Applications->Accessories->Terminal
Synaptic should be there too:
System->Administration->Synaptic Package Manager 

I strongly recommend reading the starterguide.
[http://help.ubuntu.com/starterguide/C/index.html]("http://help.ubuntu.com/starterguide/C/index.html")

---

### Post by andyf on 2006-04-22
Open a terminal (applications > accessories > terminal) and type in the following:

sudo apt-get install (followed by the name of the program you want to install)

This will then download and install the required software.

---

