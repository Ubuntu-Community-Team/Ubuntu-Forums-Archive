---
title: "Problem with NX Client instalation"
date: 2005-02-16
forum: Desktop Environments
---

### Post by Dearhell on 2005-02-16
I have just downloaded the official nx client from the nomachine webpage.

Then I have installed with sudo dpkg -i nxclient.deb

It was installed without problems, but . . .

How can I run it?

Where is installed?

I tried to find in home directory, but there is nothing, I also tried to type nxclient, nx, nxsetup, ./nxclient, etc, etc

But none of these commands have worked to me.

I also have read all the FAQ about FreeNX, but I think it's another client different from that I have already download, because I can't configure it neither run it with what it's said there. 

Regards

---

### Post by rufius on 2005-02-16
[QUOTE=Dearhell]I have just downloaded the official nx client from the nomachine webpage.

Then I have installed with sudo dpkg -i nxclient.deb

It was installed without problems, but . . .

How can I run it?

Where is installed?

I tried to find in home directory, but there is nothing, I also tried to type nxclient, nx, nxsetup, ./nxclient, etc, etc

But none of these commands have worked to me.

I also have read all the FAQ about FreeNX, but I think it's another client different from that I have already download, because I can't configure it neither run it with what it's said there. 

Regards[/QUOTE]

Out of curiosity are you on Warty or Hoary. If you're on Hoary, the [Ubuntu Backports](http://backports.ubuntuforums.org) project has those built especially for Ubuntu Hoary. But if not, to find the client try a "sudo find /usr -name \*nx\*"

---

### Post by Dearhell on 2005-02-16
> Out of curiosity are you on Warty or Hoary. If you're on Hoary, the Ubuntu Backports project has those built especially for Ubuntu Hoary. But if not, to find the client try a "sudo find /usr -name \*nx\*"

I have no idea of my Ubuntu it's warty or Hoary, I downloaded 4.1 version of Ubuntu, How can I know it?

So with that command I at last find where is NX client installed, it's at usr/NX.

In usr/NX/bin there is the nxclient file, I tried to type ./nxclient but it's said to me:

> ./nxclient: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

So I have supposed that those libraries were necessary, so I typed sudo apt-get install libstdc, but it hasn't worked (the package wasn't find)

Any idea?

Regards

---

### Post by piller on 2005-04-26
[QUOTE=Dearhell]I have no idea of my Ubuntu it's warty or Hoary, I downloaded 4.1 version of Ubuntu, How can I know it?

So with that command I at last find where is NX client installed, it's at usr/NX.

In usr/NX/bin there is the nxclient file, I tried to type ./nxclient but it's said to me:



So I have supposed that those libraries were necessary, so I typed sudo apt-get install libstdc, but it hasn't worked (the package wasn't find)

Any idea?

Regards[/QUOTE]
 Hi,
Ubuntu version 4.10 is warty.

I went to the nomachine.com web page and downloaded the nxclient-1.4.0-91.i386.tar.gz file.
I  copied the file into /usr directory.
Next I unpacked the file.
The nxclient application is at /usr/NX/bin/nxclient.

I tried to run nxclient but got the same error about libstdc++-libc6.2-2.so.3.  The solution was to enable the universe repository in synaptic, and then install libstdc++2.10-glibc2.2.

After this I was able to successfully run the nxclient application.

--Chip

---

