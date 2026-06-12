---
title: "UPS software installation instructions don't fit 9.04"
date: 2009-05-09
forum: General Help
---

### Post by alanwalterthomas on 2009-05-09
I recently bought a UPS that comes with Linux management software but the instructions don't seem to fit 9.04 & I'd rather avoid messing up my system too badly.
Here are the instructions:

Download jdk-6u7-linux-i586.bin from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp). However, I think that's taken care of by the default-jdk package I found in Synaptic & I'd rather use that.
Next move it to /opt & make it executable then run/install it. Problem: ubuntu doesn't have /opt. I could make it, but then I think things are getting too screwy.
Next part: Configure environment variables
I'm told that for the software to find jdk, I have to edit environment variables (whatever those are) JAVA_HOME & PATH. I'm told to put the following at the end of /etc/bash.bashrc :
JAVA_HOME = /opt/jdk1.6.0_07
PATH = $JAVA_HOME/bin:$PATH
Export JAVA_HOME PATH
The result of that was that whenever I open a terminal, I get:
bash: JAVA_HOME: command not found
bash: PATH: command not found
bash: Export: command not found
So it would be really really nice to find a way around putting these lines at the bottom of bash.bashrc

The way around it may have to do with the following. I'm told that if it doesn't find jdk automatically, I can inform the directory. Unfortunately locate jdk printed pages & pages of entries & I've no idea what to do about it. Is it likely that the program will work without having to bother with editing bash.bashrc if I inform the correct jdk directory? (e.g. /etc/java-6-openjdk /usr/lib/jvm/java-6-openjdk ...?)

Many thanks for any help,

P.S. I'd rather use the software made for this UPS rather than use NUT if possible.

---

### Post by irv on 2009-05-09
> **alanwalterthomas said:**
> I recently bought a UPS that comes with Linux management software but the instructions don't seem to fit 9.04 & I'd rather avoid messing up my system too badly.
Here are the instructions:

Download jdk-6u7-linux-i586.bin from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp). However, I think that's taken care of by the default-jdk package I found in Synaptic & I'd rather use that.
Next move it to /opt & make it executable then run/install it. Problem: ubuntu doesn't have /opt. I could make it, but then I think things are getting too screwy.
Next part: Configure environment variables
I'm told that for the software to find jdk, I have to edit environment variables (whatever those are) JAVA_HOME & PATH. I'm told to put the following at the end of /etc/bash.bashrc :
JAVA_HOME = /opt/jdk1.6.0_07
PATH = $JAVA_HOME/bin:$PATH
Export JAVA_HOME PATH
The result of that was that whenever I open a terminal, I get:
bash: JAVA_HOME: command not found
bash: PATH: command not found
bash: Export: command not found
So it would be really really nice to find a way around putting these lines at the bottom of bash.bashrc

The way around it may have to do with the following. I'm told that if it doesn't find jdk automatically, I can inform the directory. Unfortunately locate jdk printed pages & pages of entries & I've no idea what to do about it. Is it likely that the program will work without having to bother with editing bash.bashrc if I inform the correct jdk directory? (e.g. /etc/java-6-openjdk /usr/lib/jvm/java-6-openjdk ...?)

Many thanks for any help,

P.S. I'd rather use the software made for this UPS rather than use NUT if possible.

Your file system does have an opt directory. 
Did you have this working on 8.10 before you went to 9.04?
Your Linux Managing software must have a conf file some were to edit the Configure environment variables.
The PATH etc has to be set in our system not entered at the terminal.

---

### Post by Alterax on 2009-05-09
No need to tinker with the bulk of that.  Just install the Sun Java 6 JDK, log out, then log back in.  Part of the installation sets the environment variables, so you're good on that; logging out and back in ensures that they are uniformly set.

Next, as far as /opt goes, you definitely have one.  It's right off the root directory (/), not in your home directory.  It's seldom used except for commercial programs--which your management software does fall into the category of.

---

### Post by irv on 2009-05-09
alanwalterthomas if you are new to Ubuntu Linux, you are starting out in deep water if you don't swim well.
From you post, I don't even know if you installed you management software for you UPS. The Java part is required by it but is not part of it. It just make it possible for the software to communicate with the UPS.
Like another post just said you need to install the Java which is separate from the manager.

---

### Post by alanwalterthomas on 2009-05-09
Thanks for the replies :)

About /opt... oops. You're right. I thought it didn't exist by default because it was empty except for what I had mv'd into it. Then I looked at another box, & it's there, empty. BTW, this is a fresh install & new UPS at the same time. Never before used.

I searched for JDK in synaptic but I'm not quite certain what JDK packages ought to be installed. sun-java6-jdk seems most likely. I installed these likely candidates (& whatever's automatically marked along with them) to hopefully take care of any/all Java related stuff I'll ever deal with:
default-jdk
default-jre (+ headless)
openjdk-6-jdk
openjdk-6-jre (+ headless + lib)
sun-java6-bin
sun-java6-jdk
sun-java6-jre

I think openjdk put an openjdk webstart program that I don't understand in Apps - Internet. Can I get rid of it or might it be important for joe user & his ups?

As for installing the software, I got as far as starting the install script which immediately asked me to inform the jdk directory. It gave an example "/usr/java/jdk1.5_0_06". Any suggestions about what I ought to try? If I were to guess I'd say /usr/lib/jvm because that's where most of sun-java6-jdk's files go.

As for getting into deep water, well, the nice thing about computers is I can drown over & over again until I swim like the fishes ;)

---

### Post by irv on 2009-05-10
Did you install the Linux management software yet? and if so what does it do when you run it? Are there any error? 
I am out here hit and miss so if I don't get back right away it is because I am gone.
Great come back on the swimming in deep water. That's the way I learn thing. I first screw them up then have to fix them. I am starting to believe that no one can ever learn everything about Linux. It is a great OS. Someone once said that windows is for mouse clickers but with Linux you need to use your brain. 
One more thing, does the Linux management software that came with the UPS run in a browser or does it have it own interface?

---

### Post by alanwalterthomas on 2009-05-10
No, I haven't installed it.
I click on install.sh. If I run, nothing happens. If I run in terminal, it asks me for the directory where java is installed.
I believe it has its own interface. I looked through the manual & there is never any mention of going to a browser, although part of the configuration does involve telling it the connected computer's ip address. In fact, I think that there's an option to use the terminal to manage it from Linux.
It's a Brazilian UPC manufacutrer, SMS. It's called SMS powerview client, & the technologies it says it uses are Java, RMI, Webservice, Socket.
So what I really need right now is a good guess of what java directory it's talking about so I can continue with the install.

Thanks a lot for your help.

---

### Post by irv on 2009-05-10
> So what I really need right now is a good guess of what java directory it's talking about so I can continue with the install.

I have openjdk-6-jdk installed on my Laptop and when I did a search for it I found it in the /var/lib/dpkg/info directory. I don't know if that is what you are looking for but that all the info I can give you for now. This was the package I installed out of the Synaptic Package Manager

---

### Post by irv on 2009-05-10
Oh ya, I did a search for Java on my system, and it found 1,314 Java files.

---

### Post by alanwalterthomas on 2009-05-11
I haven't gotten the GUI portion to work yet (it freezes while "starting services") but the command line part now works.
I gave the directory /usr/lib/jvm/sun-java6-openjdk & that let it install.
I'll post again if I can get the rest of it to work somehow.

---

