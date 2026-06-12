---
title: "Repository Problems"
date: 2006-06-06
forum: Desktop Environments
---

### Post by anton_botha on 2006-06-06
Hey people,

I have recently installed Ubuntu 5.10 (still waiting for 6.06 which a buddy ordered). The installation was fairly easy, heck, less annoying than the windows installation.

Once I was finished with the installation I even got my network set up, no problems, was astonished.

Then I came across "Synaptic", and for the sake of just wanting to toy around, I managed to completely boggle up the repositories. I then removed them and tried setting them up again, still errors. ](*,) 

So onfortunately there source.lst.save is already overwritten with a faulty one, and I cannot go back to the original by manually changing it.

Is there some way I could fix this, or am I looking at permanent damage (which I doubt as it is a plain flat text file), or could I posibly copy the source.lst from another computer?

If anyone could share some information on 1) a way to fix this so that I could remember for future times or 2) a good working/proper source.lst location which I can look at or 3) preferably both :-D 

Sorry about the, most likely, stupid question but it is my first time running a *nix distro and as with any other os' I will be testing it out as much as possible.

Kind regards,
  Anton Botha

---

### Post by matthew on 2006-06-06
You can use one from another computer with no problems...you can add/subtract stuff from that file and recover from it (within reason, of course). Here's the main things you will want, just copy it from here and paste it to /etc/apt/sources.list on your computer, run Synaptic again and ignore any errors when it first comes up. Click "reload" and wait. Then you should be all set.

You can also look at [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") as it is a good resource to find proper repositories and a few extra, unofficial ones.

```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
# deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
# deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

```Note: I have the source code repos commented out (they have a # in front of te line) just to make things a little faster. If you find you want the source code for a certain program you can just uncomment those lines, reload, and you will be set.

---

### Post by anton_botha on 2006-06-07
Hey Matthew,

Thank you for your post. I have tried what you have posted, to no avail. Even using a generated (I presume it is generated) file from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic).

I am attaching two screenshots of the errors I am getting, I cut some of the outsides off to decrease the size of the images, but they should give an idea of where my problem lies.

Kind regards,
  Anton Botha

P.S Any information that can help would be great, and I don't mind to "play" around with it as I can always reinstall, but I would prefer trying to fix it so that I know for future references.

---

### Post by matthew on 2006-06-07
[quote=anton_botha]Hey Matthew,

Thank you for your post. I have tried what you have posted, to no avail. Even using a generated (I presume it is generated) file from [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic").

P.S Any information that can help would be great, and I don't mind to "play" around with it as I can always reinstall, but I would prefer trying to fix it so that I know for future references.[/quote]For some reason you are being denied access to the servers in the sources.list I posted. Those are the main servers. I would recommend going to the source-o-matic site and generating a list for yourself using the South Africa mirrors (you just have to know the 2 letter country code for S.A and I don't...) and then try again. Otherwise you may have a bigger problem on your hands relating to internet access. (?)

---

### Post by anton_botha on 2006-06-07
Hey Matthew,

I think it might be that I used the wrong 2-letter country code, will be googling for some more information on it. As for my internet connection, it is 100% correct (or I presume so) as I am running an Small Business 2003 server, along side with a Windows XP Home, Windows XP Pro and Windows Vista system without any problems.

I can also connect and work on the Ubuntu machine on the internet without any hassles, be it through my wireless network or the wired one, and it can't be that they are clashing as I disable the one I am not using.

I am almost sure that the problem is idiocity of end-user, but I am going to see what I can find out and post it on here.

Kind regards,
  Anton Botha

---

### Post by matthew on 2006-06-07
Okay. If the internet connection is working otherwise (on the Win stuff) that's a good thing. Somehow I think the two letter code for South Africa is za, but I cold be mistaken.

---

