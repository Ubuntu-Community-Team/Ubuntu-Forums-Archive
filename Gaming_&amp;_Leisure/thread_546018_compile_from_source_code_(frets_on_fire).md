---
title: "compile from source code (frets on fire)"
date: 2007-09-08
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2007-09-08
Ok, so there is this great game FretsonFire, and this great mod RFmod, which just released a new version 4.0.  The problem is that no one has compiled the new mod for linux.  I would love to help, but I have no idea where to even start.

There are instructions for the windows version
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896)

and the windows version containing the source code
[http://www.prison.net/FretsOnFire/RF-mod-4-win32.zip](http://www.prison.net/FretsOnFire/RF-mod-4-win32.zip)

I try to follow the windows instructions, but at python FretsOnFire.py, I get a no module openGL.GL.  I have no idea what this means, or how to fix it.

If I want to create the executable, the instructions list python setup.py p2exe ...which is a windows program, I dont know the linux equivelent for this command.

I have no idea what Im doing, can anyone lend a hand with teaching me?

---

### Post by Perfect Storm on 2007-09-08
Most of those you can get through synapatic/apt-get/aptitude. You don't come far with the windows version ;)

Also you need to install compiling tools, and -dev packages of required libs.

---

### Post by Naegling23 on 2007-09-08
i cant seem to get amanith and pyamanith installed, is there a package somewhere?

---

### Post by Perfect Storm on 2007-09-08
I think you'll get nowhere, as the soource is for windows. It requires that you can hack/re-code it.

---

