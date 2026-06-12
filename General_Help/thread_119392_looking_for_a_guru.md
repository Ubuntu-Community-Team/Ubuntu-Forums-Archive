---
title: "looking for a guru"
date: 2006-01-19
forum: General Help
---

### Post by danoyoto on 2006-01-19
Hey all.  I am a UBUNTU lover and a somewhat terminal happy noob.  Most everything I can figure out by searching this forum and taking advantage of the amazing community here!  BUT......can someone please help me get the following application up and running?

[http://sourceforge.net/project/showfiles.php?group_id=126818](http://sourceforge.net/project/showfiles.php?group_id=126818)

PLease let me know what you need from me in terms of system info or anything.  If anyone can help I will be HUGELY endebted to you.  Thanks.

---

### Post by lysis on 2006-01-19
"this document contains no data"

what's the name of the application?  thanks

---

### Post by chris_andrew on 2006-01-19
Hi,

Just download the file and then:

tar -zxvf *filename*

Hope this helps.  It looks like worthwhile software.

Cheers,

Chris.

Just downloaded it.  You'll need to read the file called README.

---

### Post by danoyoto on 2006-01-19
OK, I will try it when I get home.  The application is called ACCOUNTABILITY PAL.

I did try to follow the readme once about a week or two ago but to no avail.....

I will try your above suggestion and let you all know how it goes....

THANKS FOR THE QUICK RESPONSE!!

---

### Post by danoyoto on 2006-01-19
Heres what happened so far.

I downloaded and unzipped into a folder in my home directory....when I do a ./configure it says this.

dan@ubuntu:~/DANS/accpal-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
dan@ubuntu:~/DANS/accpal-0.1.1$ make
bash: make: command not found

do I need to download the "libharu" stuff that is in the README file?

any help is appreciated.

---

### Post by rattking on 2006-01-19
sudo apt-get install build-essential 
will install make and C compiler for you

---

### Post by danoyoto on 2006-01-19
Thanks,  that worked....sortof!  Everything looks good when I do ./configure
but then it won't let me do make or make install, says :

make: *** No targets specified and no makefile found.  Stop.

not sure what to do next..........

---

