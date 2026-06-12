---
title: "Kubuntu + open office printing"
date: 2007-04-21
forum: Desktop Environments
---

### Post by charles_elwood on 2007-04-21
Ok, i'm running into irritating issues with printer configurations and missing documentation that I probably shouldn't be. I live in an area where more than half of the people I know have been running linux of some description for >5 years, and print systems just working has been pretty much the norm.

Most of like KDE, and Kubuntu is very quickly becoming the general purpose distribution of choice. And for the most part migrations to Kubuntu from other distros has been pretty painless. I have, however, been searching for the '*ubuntu way' of dealing with networked cups printers and open office.

The first thing most users seem to do is poke the KDE printer settings by System settings -> Printers -> Print Manager -> Configure -> CUPS server and set it to point at thelocalprintserver.localdomain:631. And this mostly works quite well, all the KDE applications are now quite happy. And I'm happy, as I get a lot less questions that have answers that are more complicated than can be scribbled on the back of a beermat after 

And then the magic of *ubuntu falls apart as soon as I hear cries of 'open office won't print'. There doesn't yet seem to be a non-ugly answer to this. [http://kubuntuforums.net/forums/index.php?topic=13473.0](http://kubuntuforums.net/forums/index.php?topic=13473.0) suggests setting up kprinter as a pdf-converter, which is doable but ugly. 

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) recites the old ritual for sorting cups out, which is pretty much the gentoo way of search /etc for the right file, read the manpage, and edit until your heart's content, although it's missing the one-liner that solves most of the issues I'm grumbling about above:

```
echo "ServerName myprintserver.localdomain" | sudo tee /etc/cups/client.conf
```

Am I missing the 'ubuntu way' of doing this, or is this and area which needs attention?
And where is the 'correct place' for dealing with issues like this, kubuntu.org or ubuntu.com + ubuntuforums.com? I always hate giving someone an answer along the lines of 'it's on the ubuntu forum, or possibly the kubuntu one.........'

---

