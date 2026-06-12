---
title: "how to install &quot;build essential&quot; for ubuntu 8.10 intrepid"
date: 2009-02-16
forum: General Help
---

### Post by eagleye on 2009-02-16
Hi, I am kind of new to ubuntu and I would like to know how to install "build essential" if I have it on my homefolder (on my computer) and please dont tell me to download it cause I don't have an internet connection.
I tried to navigate to "build essential" folder and then I typed "make" but it said that there is no option to "make"(an error occoured).
so how do I install it?

---

### Post by MasterProg on 2009-02-16
Do you mean *build-essential* package? As far as I know, it's a metapackage that depends on lots of other packages. They include compilers, headers and so on.

---

### Post by ajgreeny on 2009-02-16
That will be difficult without a connection to the internet, but it can be done by downloading to another computer the 10 or so packages that build-essential asks for (it is a sort of meta-package, not just one).  Put all the downloaded .deb files into an empty temporary folder and then navigate to that folder with ```
cd temporary
``` or whatever you called it and run ```
sudo dpkg -i *.deb
```Life will be very difficult without a connection to the net, however, and updating will not be possible without difficulty, and I wonder if you really need to build packages and compile anything.  Where will you get the source code from, it normally comes from the repos which require an internet connection, so you are back at square one!

---

### Post by snowpine on 2009-02-16
Eagleye,
This link will show you the dependencies for build-essential: [http://packages.ubuntu.com/intrepid/build-essential](http://packages.ubuntu.com/intrepid/build-essential)

Make sure you also check the dependencies for each of the dependencies.

If at all possible, it is much easier to connect to the internet and:

```
sudo apt-get install build-essential
```

Can you back up a bit and explain to us what you're doing and why you need build-essential?

---

### Post by eagleye on 2009-02-17
thanks I'll try it and inform you about the prograss.
snopoine, are the dependencies under the header:"Other Packages Related to build-essential" and is there really only 4? ( dpkg-dev,  g++ ,  libc6-dev ,  make) - and am I supposed to download the ones with the "depen" icon (the red icon) and if I understood correctly , am I soppused to download all the "depen" files related to each of the four dependencies of build essential. just tell me if I'm correct and i'll be heading on to download it all.
and by the way THANK YOU!

> Can you back up a bit and explain to us what you're doing and why you need build-essential? 

my friend and I made a bet that I will try to crack his wep but I have to do it from scratch without a connection to the internet( without all the easy ways to do stuff- "apt get" ext..) and I can only transfer stuff through a USB (flash memory).
thanks for the interest. 
it also gives me a lot of knowledge of how things work and what needs what to operate.

---

### Post by oldos2er on 2009-02-17
build-essential should be on the Ubuntu installation cd. Check System, Administration, Software Sources to make sure CD-ROM is enabled.

---

### Post by MasterProg on 2009-02-18
> **eagleye said:**
> my friend and I made a bet that I will try to crack his wep

Good luck then, but don't get into trouble. :D

---

### Post by loomsen on 2009-02-18
Hello.

You can get a list of packages considered to be build-essential by issuing following command:

```

grep-status -FEssential -sPackage -ni yes

```

All essential pkges are also build-essential, but there are also build-essential pkges that are not essential.

Essential (and thus also build-essential pkges)
```
cat /usr/share/build-essential/essential-packages-list
```

Build-essential, but not essential pkges
```
cat /usr/share/doc/build-essential/list
```


The debian policy gives the definition:
    It is not necessary to explicitly specify build-time relationships
    on a minimal set of packages that are always needed to compile,
    link and put in a Debian package a standard "Hello World!" program
    written in C or C++.  The required packages are called
    _build-essential_, and an informational list can be found in
    `/usr/share/doc/build-essential/list' (which is contained in the
    `build-essential' package).

So basically build-essentials are the pkges you always need to build a debian pkg from source. And as every deb u want to build depends on at least those pkges, they are called build-essentials and theres no need to specify them as dependencies of your newly build pkg, as described above.

Hope this helped.

*edit*

You might want to take a look at the pkg(es) debian-policy/ubuntu-policy for futher information.

---

### Post by wildman4god on 2009-02-18
> **oldos2er said:**
> build-essential should be on the Ubuntu installation cd. Check System, Administration, Software Sources to make sure CD-ROM is enabled.

I can confirm that build-essentials is indeed on the cd as a deb, I don't know about using sudo apt-get install but if you go digging around the cd you'll find a deb for build-essentials.

---

### Post by oldos2er on 2009-02-18
> **wildman4god said:**
> I can confirm that build-essentials is indeed on the cd as a deb, I don't know about using sudo apt-get install but if you go digging around the cd you'll find a deb for build-essentials.

 As long as CD-ROM is part of your sources, aptitude or apt-get (or Synaptic or Add/Remove) will work.

---

### Post by eagleye on 2009-02-23
never mind that I succeded to install build essential.
thank you all a lot for all your help, you are probably the best forum I encountered.
but now I have a new problem that I will now publish. 
You were awsome you guys and I hope you will be able to help me in my new problem. thanks for the patiens.

---

