---
title: "Installing Citrix"
date: 2009-03-10
forum: General Help
---

### Post by VanillaMozilla on 2009-03-10
Is it possible to use Citrix XenApp, formerly known as Meta Frame Presentation Client?  Or, in everyday terms, Citrix.  I need to access files at work.

Installing stuff like this is not easy.

I have file linuxx86-11.0.14039.tar.gz from Citrix.  Supposedly that requires libmotif 2.3.1.  Synaptic offers 2.2.3.2.  Great.  I read somewhere I'm supposed to use LessTif instead.  That's nice, but LessTif seems to be sort of vaporware, and Citrix says it probably doesn't support libXm3 or some such (I think that's what it was called).

Questions:
1. Can I run Citrix or can't I?
2. If I can exactly how do I install all this junk?  Exactly where do I put the file, what buttons do I press?  Are there specific instructions anywhere?

---

### Post by VanillaMozilla on 2009-03-13
Well, let's try another approach.  Generally where does one put software that didn't come with a package?  As a new directory in /opt/ ?  Or where?

There must be a search path, analogous to the DOS/Windows patch.  How is it set?

---

### Post by gheeke on 2009-03-15
It's quite easy to install the Citrix Client:

* Download the Client from the Citrix Homepage. Select the one with .tar.gz not the rpm
* Open a Console (Terminal). Change to the download folder (e.g. cd ~/downloads)
* Untar the Archive: tar xzf en.linuxx86.tar.gz (or whatever the name of the client is)
* Install the Software: sudo ./setupwfc (Answer some questions. Generally the default answer is ok)
* Use the software. If no windows open, you might need to install libmotif3 (sudo apt-get install libmotif3)

You might want to use the Linux Client 10.6 instead of 11.0. The Version 11.0 needs a newer libmotif library, which seems not to be available for ubuntu right now. If you access your remote applications via Citrix Secure Gateway you might even use Version 11.0, as it can open the applications, but you can't configure the client.

HTH

---

### Post by VanillaMozilla on 2009-03-17
Thanks.  It seems to be a piece of work getting 10.6, but I'm working on it.  I'll eventually get Citrix, I expect.

---

### Post by gheeke on 2009-03-18
I've done some further tests. The following trick *might* help to run Citrix Receiver Version 11. The solution is unsupported, use at your own risk.

Install the open-motif package 2.2.3-2. Its included in the libmotif3 package (sudo apt-get install libmotif3) Change to the directory where the library libXM.so.3 is installed (cd /usr/lib). Make a symbolic link from libXM.so.3 to libXm.so.4 (sudo ln -s libXm.so.3 libXm.so.4)
The Citrix Receiver should now open - and hopefully work without further problems.

---

### Post by VanillaMozilla on 2009-03-19
Thanks, still working on it.  This stuff sure isn't designed for Granny, or Mac users, ...or Windows users, or humans, for that matter.

---

