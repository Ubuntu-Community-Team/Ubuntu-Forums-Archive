---
title: "Install software?"
date: 2006-01-02
forum: General Help
---

### Post by Bruce Hall on 2006-01-02
I am very familiar with windows pc's. I have built several and have to reformat/reinstall at work. I don't seem to understand some basic things about ubuntu. I am currentyl dual booting xp/breezy badger 5.10. I don't understand how the concept of "installing" software works in linux. I downloaded the new version of firefox, but I don't see that there is any "installing" to it. I created a folder on the desktop, decompressed it and am running it with no problems. When one downloads a "binary", what are you getting? You can see that my problem is that I grew up with windows as an os so that some of the concepts simply don't apply the same way. I have read extensively, but I'm not finding anything online which explains some of these seemingly very basic concepts. I am looking for a document which will explain how some of the things that I routinely do with xp relate to linux. (Install software, create shortcuts, etc.) Sorry if this is a bit lengthy, but any pointers to documentation that would explain linux from a comparison to windows perspective would be appreciated.
Thanks,
Bruce

---

### Post by Sef on 2006-01-02
Search the posts here, and also go to wiki:  [https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")

There is lots of information between the two sites.

---

### Post by meborc on 2006-01-02
there is a very helpful guide about how to start using ubuntu... it is called **ubuntu 5.10 starting guide **and it is placed in the **help **menu in the **aplications **(if i am not mistaken as i'm not near my ubuntu box)... go through the basics there... it is very good and got me started...

to install programs, use a tool called **synaptic**... there is a big chance that the program you are looking for is up in the ubuntu repositories... to find out how to use synaptic -> again ubuntu starter guide...

have fun and explore :)

---

### Post by hajk on 2006-01-02
First off, people in the Linux/Unix world don't use the word "folder" much...:p 

The beauty of a Debian-based OS, like Ubuntu, is that the package manager takes care of installing the chosen software in the right place(s). One should, as a matter of policy, be very reluctant to install software that is not yet packaged as a .deb. 

But, sometimes, a piece of needed software just isn't available yet as a .deb package. It is recommended to install such software to the /usr/local tree. Often, after unzipping/untarring, a Makefile is available that compiles/installs the software there; if not, the Makefile can be edited to do so. An alternative is to use "alien" to repackage a .tgz archive as a .deb first, and then install that .deb under package manager control. All such installation can be done from a temporary directory, like My Downloads; the downloaded stuff can be removed afterwards.

---

### Post by Norberg on 2006-01-02
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by Bruce Hall on 2006-01-02
[QUOTE=hajk]First off, people in the Linux/Unix world don't use the word "folder" much...:p 

The beauty of a Debian-based OS, like Ubuntu, is that the package manager takes care of installing the chosen software in the right place(s). One should, as a matter of policy, be very reluctant to install software that is not yet packaged as a .deb. 

But, sometimes, a piece of needed software just isn't available yet as a .deb package. It is recommended to install such software to the /usr/local tree. Often, after unzipping/untarring, a Makefile is available that compiles/installs the software there; if not, the Makefile can be edited to do so. An alternative is to use "alien" to repackage a .tgz archive as a .deb first, and then install that .deb under package manager control. All such installation can be done from a temporary directory, like My Downloads; the downloaded stuff can be removed afterwards.[/QUOTE]
Hey thanks! So, for firefox, I did try to do the package update, but, of course, version 1.5 wasn't available from the repositories. Am I understanding correctly then that after decompressing the file, there is a piece of software that converts it to a .deb file? The I add a line to the source list file which references the location of that file on the hard drive? Am I getting it at all?
Bruce

---

### Post by kaamos on 2006-01-02
I think the only way you could create a deb file for firefox 1.5 would be to compile it from source. Not too sure about this though.

Anyway, if you installed with a package from mozilla.com, it was the same thing as in windows to do this:
- download a software as a .zip
- unzip
- move to C:\Program Files

In the case of linux the last part is done with this
> sudo ln -s /opt/firefox/firefox /usr/bin/firefox
This creates a link from the file /opt/firefox/firefox to the location /usr/bin/firefox. The directory /opt is usually just a place to put stuff out of the way. /usr/bin is one of the locations of executable files. In fact, I think it would be nicer if the link would point to /usr/local/bin/firefox, for reasons mentioned in a previous post.

---

### Post by Bruce Hall on 2006-01-02
[QUOTE=kaamos]I think the onyl way you could create a deb file for firefox 1.5 would be to compile it from source. Not too sure about this though.

Anyway, if you installed with a package from mozilla.com, it was the same thing as in windows to do this:
- download a software as a .zip
- unzip
- move to C:\Program Files

In the case of linux the last part is done with this

This creates a link from the file /opt/firefox/firefox to the location /usr/bin/firefox. The directory /opt is usually just a place to put stuff out of the way. /usr/bin is one of the locations of executable files. In fact, I think it would be nicer if the link would point to /usr/local/bin/firefox, for reasons mentioned in a previous post.[/QUOTE]

Ahhhh, now I begin to understand thank You! So  it's more like software in the old days, no registry to write to, etc. Essentially then, all I'm really doing is decompressing the archive and putting the files in a subdirectory of my choice? And, because the kernel is completely seperate from the application, the worst you typically get is an app that doesn't run?
Bruce

---

### Post by hajk on 2006-01-02
You can use "alien" to convert between various packaging methods -- for example between the Red Hat .rpm or the Slackware .tgz methods and .deb.
The "man alien" command has the details. Making a .deb package from scratch is also possible, after all that's what the Debian/Ubuntu developers are doing all the time -- look at various dpkg utilities like dpkg-buildpackage (not for the faint-hearted).

---

