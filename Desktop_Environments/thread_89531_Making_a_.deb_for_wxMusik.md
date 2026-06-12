---
title: "Making a .deb for wxMusik"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Jamesia on 2005-11-12
Hi all, 
I've compiled wxMusik, and I wanted to make it available to people via a .deb. However, I don't really know how to make one. There are several dependences for wxMusik, and the install isn't that friendly from source. Not that I could do a better job myself. The only other option I can do is simply put all the made make files into a folder, and write a simple bash script to execute them when appropriate. I find that clumsy, though. I don't mind sending what I have to someone more knowledgeable, either.
James

---

### Post by Corvillus on 2005-11-12
If you're not planning on using it for widespread distribution, checkinstall may be just what you are looking for. Basically, after compiling an application from source, instead of running make install you run checkinstall. This tracks the install, creates a deb package and installs it. The package remains in the directory you ran checkinstall from.

[https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)

---

### Post by citizenkeith on 2006-09-22
Did you ever get this deb working?

---

### Post by NoSmokingBandit on 2007-10-24
I would very much love a deb of wxmusik. Amarok breaks my sound so i have to find something different. I use the xp version of wxmusik, but the linux one looks like a nightmare to compile. I dont understand why the devs were too lazt to compile it into debs and rpms for people.

---

