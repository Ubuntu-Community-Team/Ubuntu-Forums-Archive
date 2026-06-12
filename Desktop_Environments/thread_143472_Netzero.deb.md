---
title: "Netzero.deb"
date: 2006-03-12
forum: Desktop Environments
---

### Post by kemah201 on 2006-03-12
I use NetZero internet access on my Windows box and I would like to know if I can run NetZero on Ubuntu. There is a Lindows version on their website with an extension of .deb. Can I run this on Ubuntu?

Thanks.

Steve

---

### Post by taurus on 2006-03-12
If it is compatible with Ubuntu, then you can install it as
```

sudo dpkg -i netzero.deb

```

---

### Post by bluevoodoo1 on 2006-03-12
Well.... I cannot say for sure if it will work, in fact I have no idea about Netzero / dialup access in Ubuntu (netzero is dialup right?). But. Ubuntu can handle .deb files.

You would install a deb file like this...

```

sudo dpkg -i filename.deb
```

Again, you should look around for other people's experience with this sort of thing. Or do some experimenting. I know what wasn't much help. I hope something works out for you...

---

### Post by kemah201 on 2006-03-12
I have successfully unzipped the NetZero.deb archive and the client is listed as installed in the software manager but it is not on the Applications menu. Once it is installed how do I execute the client? I should probably post this on the beginner forum but I have already started the thread here. Please help!

Thanks.

Steve

---

### Post by taurus on 2006-03-12
Try to run it from a terminal to see what happens...
```

NetZero
-or-
netzero

```

---

### Post by kemah201 on 2006-03-12
I tried running *netzero* from the root terminal and I get a *command not found* error message.

---

### Post by bluevoodoo1 on 2006-03-12
What about running "NetZero" as taurus suggested? (with cap. N and Z)

---

### Post by kemah201 on 2006-03-12
I ran every variation of *netzero* possible with no success. I noticed that the entry for netzero in Synaptic Package Manager doesn't have the triangular Ubuntu logo next to its name. The contents of the program are located in the /opt/nzclient folder. I tried *nz*, *nzclient*, everything possible. Please help! I want to be to use Ubuntu at home but I need internet access!

---

### Post by kemah201 on 2006-03-12
Any chance someone could install the software on a test box? Here is a link:

[http://my.netzero.net/s/download?cf=wwwb1](http://my.netzero.net/s/download?cf=wwwb1)

Thanks.

---

### Post by bluevoodoo1 on 2006-03-12
I'd tried the link but you have to be a member to download it. 

Maybe you can post the contents of your /opt/nzclient folder?

```
ls /opt/nzclient
```

---

### Post by taurus on 2006-03-12
The reason "netzero" or "NetZero" doesn't work because /opt/nzclient is NOT in your path!!!  What is the output of this command then,
```

ls -la /opt/nzclient

```

---

### Post by djheadley on 2006-03-12
You have to have java installed in order to use netzero.deb.  When I installed netzero with dpkg then it showed up in the menu under internet.  If it doesn't then go to Applications>System Tools>Applications Menu Editor and add it.  The command should be sudo bash /opt/nzclient/runclient.sh

[email]djheadley1@netzero.com[/email]

---

