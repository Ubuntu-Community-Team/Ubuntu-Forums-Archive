---
title: "Big problems upgrading 8.04 hardy to ubuntu 10"
date: 2011-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kgreasy on 2011-01-05
Hello. I have a dell mini with 8.04 hardy. I am trying to upgrade to ubuntu 10 netbook remix. I have tried to check my updates to maybe download it there but I get the "could not download all repository indices" message. I also tried to put the new ubuntu 10 manually by adding the file to my computer and hoping that it would install when I clicked it. That did not work as well. Any suggestions?????

---

### Post by mikewhatever on 2011-01-05
Dell mini 10's that were sold with 8.04 had a custom LPIA version of Ubuntu installed. Since then, the LPIA architecture has been discontinued, so that there is nothing to upgrade to, let alone that 'ubuntu 10' doesn't exist (there are 10.04 or 10.10).
What you can do it backup your files and reinstall.

---

### Post by kgreasy on 2011-01-05
> **mikewhatever said:**
> Dell mini 10's that were sold with 8.04 had a custom LPIA version of Ubuntu installed. Since then, the LPIA architecture has been discontinued, so that there is nothing to upgrade to, let alone that 'ubuntu 10' doesn't exist (there are 10.04 or 10.10).
What you can do it backup your files and reinstall.


I never knew that my dell had a custom version of Ubuntu installed. Well, my goal is to install a newer version of Ubuntu on this netbook. My current problems with this OS are probably due to the update problem. Anyway that I can manually install Ubuntu 10.04 or 10.10? P.S. When you say reinstall, do you mean my current version of Ubuntu or a newer version?

---

### Post by matt_symes on 2011-01-05
Hi

> When you say reinstall, do you mean my current version of Ubuntu or a newer version

I'm pretty sure he means a newer version.

Kind regards

---

### Post by fjgaude on 2011-01-05
Here's a site that spills-the-beans about Dell and the 8.04 version of their Mini 10s:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

From there you will know enough to do what you want to do. I have both 10.04 working perfectly, and 10.10 without video camera working.

Take a look at this post:

[http://ubuntuforums.org/showthread.php?p=10320818#post10320818](http://ubuntuforums.org/showthread.php?p=10320818#post10320818)

Let us know how you are doing.

---

### Post by mikewhatever on 2011-01-05
Yeah, LPIA was an obscure architecture, not quite sure why Dell chose to go with it. By the way, you should probably verify that's what you have by running the **uname -m** command.
You should be able to install any version of Ubuntu manually, in fact, I don't know of any other way to do it. [Ubuntu.com]("http://www.ubuntu.com/desktop/get-ubuntu/download") has detailed instructions on how to prepare a USB stick and install Ubuntu. There are also lots of tutorial on the very same subject.
By reinstall, I mean installing the chosen version of Ubuntu.

---

### Post by kgreasy on 2011-01-05
hmmm

---

### Post by fjgaude on 2011-01-05
BTW, the LPIA is the Atom CPU, _l_ow _p_ower Intel _a_rchitecture, which runs just fine with i686 software. The Atom is used on just about all netbooks!

---

### Post by snowpine on 2011-01-05
You'll find some good tutorials for Ubuntu on the Dell Mini at this website:

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

As mentioned earlier, if your netbook uses the Intel GMA500 "Poulsbo" graphics card (certain models of Mini 10 and Mini 12, use the terminal command 'lspci' if you're not sure), your options are very limited.

---

### Post by mikewhatever on 2011-01-05
Do you mean i686 software runs on lpia OS? Aren't there errors about wrong architecture when installing?

---

### Post by fjgaude on 2011-01-05
> **mikewhatever said:**
> Do you mean i686 software runs on lpia OS? Aren't there errors about wrong architecture when installing?

Well, i686 is i386 with a few more instructions in the set. Of course all 32-bit Ubuntu Linux OSs runs on lpia hardware, which is Atom from Intel. Dell didn't have a special OS when they came out with the Mini 9 and 10. In some cases they made sure the Intel video drivers would auto-install when the OS was installed. That's all!

On my Mini 10n I'm running Ubuntu 10.04 on the hard drive, and on a 16GB USB stick I'm running Ubuntu 10.10. Of course, both are the 32-bit versions of the OS.

---

### Post by mikewhatever on 2011-01-05
Apparently, you seem to think lpia is a hardware architecture. I could be totally wrong, but I've always thought it to be i386 with more agressive power management achieved by adding a bunch of gcc flags. I've also never seen the term lpia applied to Intel's Atom cpus.:confused:

---

### Post by fjgaude on 2011-01-05
I could be totally wrong too, but what difference does it make? Ubuntu 32-bit OSs run on Atom and regular i386 processors. Lpia doesn't stop you from using these kinds of OSs.

Do google search and see what you get for "lpia". <smile>

---

### Post by snowpine on 2011-01-05
Any recent i386 or i686 distro (including Ubuntu) should run fine on the Atom processor. :)

---

### Post by mikewhatever on 2011-01-05
> **fjgaude said:**
> I could be totally wrong too, but what difference does it make? Ubuntu 32-bit OSs run on Atom and regular i386 processors. Lpia doesn't stop you from using these kinds of OSs.

Do google search and see what you get for "lpia". <smile>

I can't seem to find anything Atom related. Can you help me out.
I found this though.
[http://lwn.net/Articles/247003/](http://lwn.net/Articles/247003/)

> The Ubuntu Mobile project uses a new architecture "lpia"; the architecture
resembles "i386", but uses different optimizations options in the compiler,
different configuration and build options for some packages. Because Ubuntu
Mobile uses only a subset of main, and almost nothing of universe, a large part
of the archive is not yet built for this architecture. The buildds are currently
building the archive, so you might get notice about build failures for your
uploads. Build failures outside the Ubuntu Mobile project are handled with the
same priority as for our community ports.

"lpia" uses GCC-4.2 as the system compiler (instead of GCC-4.1 for the other
architectures), so some packages which are not yet built may fail to build due
to a stricter compiler.



---

### Post by fjgaude on 2011-01-05
> **mikewhatever said:**
> I can't seem to find anything Atom related. Can you help me out.

Try this for a start:

[http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/](http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/)

Atom and lpia go together.

---

### Post by mikewhatever on 2011-01-05
> **fjgaude said:**
> Try this for a start:

[http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/](http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/)

Atom and lpia go together.

Well, I've first seen that link quite some time ago, and do you know how many times 'Atom' is mentioned there? Exactly zero.
This discussion is of topic and I am going to withdraw. You have fun with Atom and lpia, together.):P

---

### Post by fjgaude on 2011-01-05
Here's another link:

[http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml](http://news.softpedia.com/news/Canonical-Drops-Support-for-LPIA-on-Ubuntu-10-04-128175.shtml)

This lpia is really gone over the top, no longer around.

---

### Post by snowpine on 2011-01-05
lpia was an Ubuntu-specific thing as far as I know; it never caught on with Debian, Fedora, Red Hat, etc.

---

