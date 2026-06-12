---
title: "Alien error"
date: 2009-06-02
forum: General Help
---

### Post by subzone on 2009-06-02
Hello

I need help explaining this error and how to fix it.

"mkdir: cannot create directory `Epson-ALC1100-filter-cups-1.2': File exists
unable to mkdir Epson-ALC1100-filter-cups-1.2:  at /usr/share/perl5/Alien/Package.pm line 257."

This follows the command: sudo alien -k Epson-ALC1100-filter-cups-1.2-0.i386.rpm

Cheers

---

### Post by upbeat.linux on 2009-06-02
What was the initial command you ran?

alien is a tool that allows you to convert .rpm packages for LSB, Red Hat, Fedora, Stampede and Slackware packages into Debian packages.  You can then use dpkg to install the package.

You may need to run the script as root in order to force creation of the directory.

---

### Post by subzone on 2009-06-02
Hi
 
Thanks for your reply.
 
The initial command run was sudo alien -k Epson-ALC1100-filter-cups-1.2-0.i386.rpm

I was under the impression sudo granted root! is that not so?
 
Cheers

---

### Post by upbeat.linux on 2009-06-02
That is correct.

The error message is telling you that the directory already exists: Epson-ALC1100-filter-cups-1.2

Try deleting it and running alien again to create the package.

---

### Post by subzone on 2009-06-02
Once again thanks...
 
I looked for the directory but all the message points to is a Package.pm file.
 
When I open the file and go to the line number there is no reference to a directory location and I can't follow the script to see if it's else where.
 
Where would alien normals create the packages?
 
Cheers

---

### Post by upbeat.linux on 2009-06-09
Sorry for the late response have been AFK for quite some time.  You can download those drives and compile from source as well:

[http://www.avasys.jp/lx-bin2/linux_e/laser/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/laser/DL1.do)

This site also has the rpm the updated rpm in question. Try the -d switch instead of or in addition to the -k:

```
sudo alien -d Epson-ALC1100-filter-cups-1.2-0.i386.rpm
sudo dpkg -i Epson-ALC1100-filter-cups-1.2-0.i386.deb
```

You could also try purging alien, cleaning apt, and reinstalling it.

---

### Post by subzone on 2009-06-09
Thanks again. No problem about the slow reply - I've been busy myself.
 
I will try your suggestions ASAP.
 
Cheers

---

