---
title: "[SOLVED] tex file through SSH in Kile"
date: 2007-08-02
forum: Education &amp; Science
---

### Post by rohan000 on 2007-08-02
I'm trying to edit a tex file which is on an SSH server through Kile. I was able to open the file with "fish://user@server:22/home/user/filename.tex".

But I can't compile it through Kile: Kile thinks that it's on the local filesystem and tries to compile a file called "/home/user/filename.tex".

Has anyone compiled files through SSH? How do I get it to send the right file to Latex?

---

### Post by finer recliner on 2007-08-03
so you're using kile on the local machine to open a remote file via ssh? sounds like your using ssh for an unintended purpose. i suggest either FTPing the file to the local machine to work on, and then upload it back when done. or you set up a samba server to share the partition on the remote machine with the local one. another option is to set up your remote machine for remote desktoping (not practical if its just text editing though)

if you insist on using ssh, i suggest enabling X-Forwarding and launch kile from the remote machine via command line. OR use another a text editor that doesnt use a GUI (i.e. emacs/vi/pico). you would then compile the tex document on the command line as well.

choose your poison! enjoy

---

### Post by willdex on 2007-08-07
Hey, is there an equivalent of Kile for Ubuntu [Gnome]?

---

### Post by mali2297 on 2007-08-08
> **willdex said:**
> Hey, is there an equivalent of Kile for Ubuntu [Gnome]?

My choice of LaTeX editor is Emacs with AUCTeX. It isn't equivalent to Kile, but perhaps an alternative.

---

### Post by apetresc on 2007-08-08
> **willdex said:**
> Hey, is there an equivalent of Kile for Ubuntu [Gnome]?

The [LaTeX plugin for Gedit]("http://live.gnome.org/Gedit/LaTeXPlugin") is *very* comprehensive, and though not *quite* as good as Kile, it's darn close.

As for Rohan's problem, if this is the path you want to follow, you should definitely mount the remote drive as an sshfs. More info on that here: [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

---

