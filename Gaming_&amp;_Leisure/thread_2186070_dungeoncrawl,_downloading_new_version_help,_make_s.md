---
title: "dungeoncrawl, downloading new version help, make sense of commands?"
date: 2013-11-05
forum: Gaming &amp; Leisure
---

### Post by 2ed.gomez on 2013-11-05
Hello, can I please have some help with following instructions or what exactly I have to type to download the new version of dungeon crawl.
Their website instructions are as follows:

----------------------------------------------------------
[h=3]Packages for Debian-based Operating Systems[/h][FONT=Trebuchet MS]We are also offering packages for Debian-based operating systems (Debian, Ubuntu, Mint, etc) for the architectures i386, amd64 and armel. Add the line from below to your /etc/apt/sources.list:[/FONT]
[FONT=Trebuchet MS]deb [http://crawl.develz.org/debian](http://crawl.develz.org/debian) crawl 0.13[/FONT]
[FONT=Trebuchet MS]Additionally you should download and install our [signing key]("http://crawl.develz.org/debian/crawl-key.gpg") to prevent warnings and to verify the packages:[/FONT]
[FONT=Trebuchet MS]wget [http://crawl.develz.org/debian/pubkey](http://crawl.develz.org/debian/pubkey) -O - | apt-key add -
(if not done as root, please insert “sudo” before apt-key)[/FONT]
[FONT=Trebuchet MS]The available packages to apt-get are named: **crawl**, [B]crawl-tiles
-------------------------------------------------------------


ok, but when i do it, i get a "broken pipeline"

can someone create a thingymajig that is easier to install, like from ubuntu software, but it only downloads the old version =(



[/B][/FONT]
I would appreciate some help, thanks




Dammit Jim!, I'm a doctor not an ubuntu coder!

---

### Post by oldrocker99 on 2013-11-05
OK, it took a little time, but I got crawl-tiles 0.13.0 installed. Here's how I did it:
1) went to [http://crawl.develz.org/debian](http://crawl.develz.org/debian)
2) followed the instructions for adding the repository
3) had the same error you had
4) downloaded the crawl-key.gpg file to [wherever] [and thanks for putting the link to that file above]
5) cd [wherever]
6) sudo apt-key add crawl-key.gpg
7) sudo apt-get update && sudo apt-get install crawl-tiles

And it worked. A few extra steps, but it runs great on my Acer C7 running Chrubuntu 12.04. I had to search for the apt-key add command myself; it's the old way of doing things, and I'd forgotten:oops:. It should work for you; if you have any more trouble, post here.

This game should really have a PPA, which is Ubuntu's easy way to add repositories, which automatically installs the GPG key. That command is:

sudo apt-add-repository ppa:whateverthePPAis/is

which, as I said, adds everything automatically.

---

