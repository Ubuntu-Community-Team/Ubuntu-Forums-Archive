---
title: "MakeFile error with tar.gz"
date: 2009-03-23
forum: General Help
---

### Post by RedSingularity on 2009-03-23
I am trying to install a tar.gz source file and i get this message with the make command,

```
make: *** No targets specified and no makefile found.  Stop.
```

The ./configure works just fine though.  Can someone help me?  This is not the first time i have received this message and i would like to know what i am doing wrong.

---

### Post by kevmitch on 2009-03-23
My first question would be is there indeed a makefile?

```
ls Makefile
```

and are 100% certain ./configure exited successfully. You can check with 

```
echo $?
```

immediately after configure has finished running and the answer should be "0".

Seeing as how you're able to get though configure and you actually get a semi meaningful message from make, you've probably already
```
aptitude install build-essential
```
right?

What are you trying to install? Do you have a link to it?

---

### Post by RedSingularity on 2009-03-23
Echo command has a "1" after it.  I am installing brasero.  I know its in the repos but i think that one is out of date.

---

### Post by RedSingularity on 2009-03-23
Here are the packages it says are missing at the end of configure....

No package 'gstreamer-0.10' found
No package 'gstreamer-interfaces-0.10' found
No package 'gstreamer-plugins-base-0.10' found

---

### Post by kevmitch on 2009-03-23
Ok, well if you're getting 1, then configure is not working. What is the last thing it says before returning you to the command line? My guess is that there's some unsatisfied dependency which you can basically count on whenever you compile something from source because not only do you need the packages that the tarball in question depends on, but you also need their "-dev" counterparts.  

You're in luck since brasero is in the repositories. You can automatically get all of the dependencies with 

```
sudo apt-get build-dep brasero
```

Of course this will download the build dependencies for the version in the repositories, but this will work 90% of the time. However, it turns out on my Debian system I also needed to do 

```
sudo apt-get install intltool
```

After doing that, I can run configure and get the following report

> 
brasero configuration summary:
----------------------------------
Version: 2.26.0
        Update caches: yes
        Build Nautilus extension : no
        Build inotify: yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build cdrtools plugins : yes
        Build cdrkit plugins : yes
        Build libburnia plugins : no


If you want to turn some of those "no"s into a "yes", you'll need to get some more dev packages. My guesses would  be "libnautilus-extension-dev"  and "libburn-dev".

In any case I am now able to run make and compile the whole mess.

---

### Post by kevdog on 2009-03-23
You need to install these packages -- easist would be from repository!

---

### Post by RedSingularity on 2009-03-23
> **kevdog said:**
> You need to install these packages -- easist would be from repository!


Thats what i thought but when i go to package manager and search the first one "gstreamer-0.10" there is no package that goes by that name.........

---

### Post by kevmitch on 2009-03-23
> 
Thats what i thought but when i go to package manager and search the first one "gstreamer-0.10" there is no package that goes by that name.........
The thing to remember is that the upstream packagers don't necessarily adhere to the same naming scheme as Ubuntu. So when configure wants "gstreamer-0.10", you really want to install "libgstreamer0.10-dev". This confusion is avoided however if you just use "apt-get builddep".

---

### Post by hyper_ch on 2009-03-23
install apt-file - it can search for specific files in packages and lists the package name.

---

### Post by kevmitch on 2009-03-23
> **hyper_ch said:**
> install apt-file - it can search for specific files in packages and lists the package name.

Yeah, apt-file is a godsend for source compilation. For those times that configure is less than helpful about which file it's really looking for, you can take a look in config.log

---

### Post by kevdog on 2009-03-23
apt-cache is also helpful.  You can search something like:

apt-cache search gstream

Between apt-cache and apt-file you should be able to find what you want.  And yes it will likely have a lib extension as a prefix.  This is usually a debian naming convention.

---

### Post by RedSingularity on 2009-03-23
> **kevmitch said:**
> Yeah, apt-file is a godsend for source compilation. For those times that configure is less than helpful about which file it's really looking for, you can take a look in config.log

Where can i find the config.log information?

And can i see an example of the apt-file command?

---

### Post by hyper_ch on 2009-03-23
shadow:

in order to use apt-file you

(a) have to install it

(b) have to initialize its database

(c) query it :)

---

### Post by RedSingularity on 2009-03-23
How do i do B and C?  

Sorry for bugging ya :)

---

### Post by hyper_ch on 2009-03-23
well, I'd start with having a look at the man pages ;)

---

### Post by RedSingularity on 2009-03-23
You mean the documentation pages at Ubuntu.com?

---

### Post by hyper_ch on 2009-03-23
nope, the manual pages... all cli programs have man pages... you get to it by issuing:

```

man PROGRAMNAME

```

you exit it by issuing "q"uit

You navigate it by using page up/down or up/down arrow keys

---

### Post by RedSingularity on 2009-03-23
Ok great i finnaly got it to install.  Now when i click the desktop icon i get the loading mouse pointer wheel and nothing happens.  I run it from Terminal to see any errors and get the following.....

"brasero: error while loading shared libraries: libbrasero-media.so.0: cannot open shared object file: No such file or directory"

What does this mean now?

---

### Post by hyper_ch on 2009-03-23
it's missing that file. use apt-file to search what library contains that file and install that library.

---

### Post by RedSingularity on 2009-03-23
This has been bugging me as well.  When i do apt-file update i get this......

Can't get [http://archive.canonical.com/ubuntu/dists/intrepid/Contents-amd64.gz](http://archive.canonical.com/ubuntu/dists/intrepid/Contents-amd64.gz)
Can't get [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Contents-amd64.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Contents-amd64.gz)

Any ideas on a solution?

---

### Post by kevmitch on 2009-03-23
> Can't get [http://archive.canonical.com/ubuntu/...tents-amd64.gz](http://archive.canonical.com/ubuntu/...tents-amd64.gz)
Can't get [http://ppa.launchpad.net/openoffice-...tents-amd64.gz](http://ppa.launchpad.net/openoffice-...tents-amd64.gz)

That's just saying that two of your repositories don't have contents files which is unfortunate, but they appear to be add-on repositories from what I can tell, (though, I'm not exactly sure what archive.canonical.com is). In any case, the major repositories should still be indexed and you should be able to query those just fine. 

> Where can i find the config.log information?
You should be able to find the config.log file in the same source directory from which you ran the configure script.

> "brasero: error while loading shared libraries: libbrasero-media.so.0: cannot open shared object file: No such file or directory"

In any case, it looks like libbrasero-media.so.0 should have been put in /usr/local/lib when you ran  
```
sudo make install
```
(you did run that after make right?)

Check if libbrasero-media.so.0 is there
```
ls /usr/local/lib/ibbrasero-media.so.0  
```

if it is then you might just need to update your library cache

```
sudo ldconfig
```

---

### Post by RedSingularity on 2009-03-23
Ok i finally got it.  Thanks alot:) :)

And as for the repos that "dont have contents files" should i leave them alone or delete them??

---

### Post by kevmitch on 2009-03-23
Was it the ldconfig that got you working or did you still have to do a make install? 

As for the repos, well, keep them if you still want access to their packages. The contents files only tell you what files are in what packages. The packages themselves are probably still good. You'll just have to put up with those error messages whenever you do an apt-file update.

---

### Post by RedSingularity on 2009-03-23
I did a make install again and it seems to have fixed everything.  

Thanks again to everyone for the help.  I feel like i better understand whats going on now which is always good.

---

