---
title: "Panda security"
date: 2009-01-12
forum: General Help
---

### Post by keerim on 2009-01-12
Hi..
How can i install Panda Security?

---

### Post by oilchangeguy on 2009-01-12
> **keerim said:**
> Hi..
How can i install Panda Security?

you might want to read this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by keerim on 2009-01-12
i download in [http://www.pandasoftware.com/download/linux/linux.asp](http://www.pandasoftware.com/download/linux/linux.asp)
but i dont install 
help me ?

---

### Post by cariboo on 2009-01-12
Although you don't nned an antivirus program, have a look [here]("http://www.pandasoftware.com/download/linux/instala.asp") for installation instructions.

Jim

---

### Post by oilchangeguy on 2009-01-12
> **keerim said:**
> i download in [http://www.pandasoftware.com/download/linux/linux.asp](http://www.pandasoftware.com/download/linux/linux.asp)
but i dont install 
help me ?

did you even read post #2?

---

### Post by lswb on 2009-01-12
There is an open source antivirus program available in the repositories that may be better suited to ubuntu than the Panda product. In synaptic search for "clam"

---

### Post by oilchangeguy on 2009-01-12
> **lswb said:**
> There is an open source antivirus program available in the repositories that may be better suited to ubuntu than the Panda product. In synaptic search for "clam"

the bottom line is, anti-virus and anti-spyware software is simply not needed in the linux world. it's a complete waste of system resources to install this software. .exe files will not run in linux. and to those who say what if we send emails to windows users. well for years most isp's scan emails for virus'. and security is up to the computer (windows) user. linux users should not have to protect windows users. it's up to them to protect themselves. i'm not going to waste system resources by running this un-needed software.

---

### Post by jimv on 2009-01-12
I love it, someone asks how to do something, and without knowing WHY this person wants to do it, people on this forum tell them not to do it or to do something else.

Anyway, here are Panda's instructions:


> If Red Hat Package Manager (rpm) is not installed -for example in Debian-, use the .tgz file. In this case follow the steps below:

    * Copy the pavcl_linux_i386.tgz file to the root / directory.
    * Decompress the file using the following command:
      gzip &#8211;d pavcl_linux_i386.tgz
    * The file pavcl_linux_i386.tar is created.
    * In order to install the antivirus, type:
      tar &#8211;xvf pavcl_linux_i386.tar


---

### Post by lswb on 2009-01-12
> **oilchangeguy said:**
> the bottom line is, anti-virus and anti-spyware software is simply not needed in the linux world. it's a complete waste of system resources to install this software. .exe files will not run in linux. and to those who say what if we send emails to windows users. well for years most isp's scan emails for virus'. and security is up to the computer (windows) user. linux users should not have to protect windows users. it's up to them to protect themselves. i'm not going to waste system resources by running this un-needed software.

That's an opinion. Using a linux-based virus scanning program on a linux server in a network that also has windows computers is a valid use case and could conceivably save the administrator many headaches. It could for example prevent the spread of a virus from one windows PC to others on the local net or prevent a windows machine from sending out an infected email or file.

Just how do you think those *"isp's scan emails for virus"* anyway?

---

### Post by axramos on 2009-01-12
I hope you could install Panda Security. A little bit more difficult is to uninstall  it (there is no instructions nowhere and Synaptic does not find the Panda in your system!).

To remove Panda Security for Linux (in Ubuntu distro):
sudo apt-get remove panda-security

Regards,

axramos

---

### Post by karlmp on 2009-01-12
[http://esr.ibiblio.org/?p=745#comment-231436](http://esr.ibiblio.org/?p=745#comment-231436)

---

