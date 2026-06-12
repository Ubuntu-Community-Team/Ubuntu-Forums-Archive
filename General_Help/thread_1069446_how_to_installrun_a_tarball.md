---
title: "how to install/run a tarball?"
date: 2009-02-14
forum: General Help
---

### Post by excbuntu on 2009-02-14
i'm trying to install [ssvnc]("http://downloads.sourceforge.net/ssvnc/ssvnc_unix_only-1.0.22.tar.gz?use_mirror=") on intrepid:

the readme file says that there's nothing to install and can be ran after unpacking. i unpacked it to my ~/ directory, and executed the ~/ssvnc/unix/ssvnc file (via double clicking) as described in the readme. it asked me to 'run from terminal,' or 'run.' neither did anything. the only thing that runs is the ~/ssvnc/bin/tightvncviewer file, but it's nothing close to what i'm looking for. [this]("http://www.karlrunge.com/x11vnc/ssvnc.html") is what i'm looking for. please help me.

first month on linux ubuntu and i'm beginning to understand it's power!! thanks in advanced everyone.

---

### Post by dcstar on 2009-02-14
> **excbuntu said:**
> i'm trying to install [ssvnc]("http://downloads.sourceforge.net/ssvnc/ssvnc_unix_only-1.0.22.tar.gz?use_mirror=") on intrepid:

the readme file says that there's nothing to install and can be ran after unpacking. i unpacked it to my ~/ directory, and executed the ~/ssvnc/unix/ssvnc file (via double clicking) as described in the readme. it asked me to 'run from terminal,' or 'run.' neither did anything. the only thing that runs is the ~/ssvnc/bin/tightvncviewer file, but it's nothing close to what i'm looking for. [this]("http://www.karlrunge.com/x11vnc/ssvnc.html") is what i'm looking for. please help me.

first month on linux ubuntu and i'm beginning to understand it's power!! thanks id advanced everyone.

Open a terminal, manually type in the command and see what messages appear.

---

### Post by excbuntu on 2009-02-14
^ thanks for the reply. but what do you mean? i was able to view the text contents of the ~/ssvnc/unix/ssvnc file, which contained commands that cd'ed into the ~/ssvnc/bin to execute another ssnvc file. in other words, the text pretty much contained "exec ~/ssvnc/bin/ssnvc" .

but doing that manually in the terminal did nothing. please help.

---

### Post by krunge on 2009-02-14
> **excbuntu said:**
> 
but doing that manually in the terminal did nothing. please help.

You probably need to install the "tk" or "tk8.4" package to get /usr/bin/wish installed.

The wish app was standard on linux distros for the last 10 or 15 years. I'm not sure why some distros have stopped installing it by default.

---

### Post by excbuntu on 2009-02-14
^ what do you mean?

---

### Post by Chris Musampa on 2009-02-14
I stumbled across SSVNC a couple of weeks ago after much searching for a scaling vnc client (KRDC is terrible in kde 4), I didn't fancy compiling but found this:
```
deb http://ppa.launchpad.net/saivann/ppa/ubuntu intrepid main
```

Just add it as a repository in synaptic, click reload, type ssvnc in the search box and away you go.

---

### Post by krunge on 2009-02-14
Something like:

```
apt-get install tk
```

or otherwise add the "tk" package via the gui tool (which I believe is called synaptic.)

What about this didn't I make clear with 'You probably need to install the "tk" or "tk8.4" package' ??

---

### Post by mc4man on 2009-02-14
If you extracted to your home folder (you should have a ssvnc folder 

Then just open a terminal and copy and paste this in

```
./ssvnc/Unix/ssvnc
```
and you'll see (screen

---

### Post by excbuntu on 2009-02-14
> **Chris Musampa said:**
> I stumbled across SSVNC a couple of weeks ago after much searching for a scaling vnc client (KRDC is terrible in kde 4), I didn't fancy compiling but found this:
```
deb http://ppa.launchpad.net/saivann/ppa/ubuntu intrepid main
```

Just add it as a repository in synaptic, click reload, type ssvnc in the search box and away you go.

wow, thanks for the easy way out. but if you didn't show that to me, i wouldn't know what i was doing.

i only know that the whole "./configure, make, and make install" sequence for compiling. there was no configure file in the tarball, so i was stumped. hopefully someone could guide me on this 'more advanced' installation. please?

thanks again.

---

### Post by krunge on 2009-02-14
> **excbuntu said:**
> 
i only know that the whole "./configure, make, and make install" sequence for compiling. there was no configure file in the tarball, so i was stumped. hopefully someone could guide me on this 'more advanced' installation. please?


From what you said previously, I believe the tarball you downloaded is not a source tarball, but one that contains prebuilt binaries.

So all you need to do is run the "./ssvnc/Unix/ssvnc" command.  No need for configure or make (there is an ssvnc source tarball available too, but I don't believe that is what you have).

You ran the ./ssvnc/Unix/ssvnc" command and you said it failed.  I assumed this was because you didn't have the "tk" ubuntu package installed (ssvnc needs that package installed to work.)

**Did you install the tk package? Or was it already installed?**

---

### Post by excbuntu on 2009-02-15
> **krunge said:**
> **Did you install the tk package? Or was it already installed?**

i installed the tk package and it worked! thanks man! next time i'll make sure to check dependencies in the documentation. 'learned my lesson.

and yes, it was the prebuilt binaries tar that i downloaded ('thought i had the source). i am now practicing installing the ssvnc conventional source tarball on another computer (i'm sure it's the source tarball this time ;) ). the documentation tells me to run the following commands after unpacking:

```

cd ssvnc-1.0.21
make config
make all
make PREFIX=/my/install/dir install

```

after installing the tk/tcl package, the "make config" command gave me the following error:

sh -c 'type xmkmf'
xmkmf is /usr/bin/xmkmf
sh -c 'type javac'
javac: not found
make: *** [config] Error 127

there is no configure file but a premade Makefile. the "make" command gave me the same error. i'm guessing i have to install something called "javac" but i'm not sure. there exists a "javacc" in synpatic--yes, "javacc"-- should i install this one or am i on the wrong track?

you guys are awesome and i sincerely appreciate your help.

---

### Post by excbuntu on 2009-02-16
anyone?

---

### Post by krunge on 2009-02-17
> **excbuntu said:**
> 
after installing the tk/tcl package, the "make config" command gave me the following error:

sh -c 'type xmkmf'
xmkmf is /usr/bin/xmkmf
sh -c 'type javac'
javac: not found
make: *** [config] Error 127

there is no configure file but a premade Makefile. the "make" command gave me the same error. i'm guessing i have to install something called "javac" but i'm not sure. there exists a "javacc" in synpatic--yes, "javacc"-- should i install this one or am i on the wrong track?


javac is a Java compiler.  It will be in a package with 'jdk' (java developement kit I suppose) in its name.  Mine is sun-java6-jdk. (I recommend using sun's java over others).

BTW, be sure to read the "README.src" file for the ssvnc source tarball.  It describes additional dependencies you need to install on the box.  The biggest one will be stunnel (named "stunnel4" on debian.)  See the readme for the full list.

---

