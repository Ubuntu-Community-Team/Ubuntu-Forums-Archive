---
title: "Scala 2.8.1 in the the repos?"
date: 2010-11-17
forum: Desktop Environments
---

### Post by rickbeton on 2010-11-17
Will there be a Scala 2.8.1 release in the distribution repos any time soon? There is currently v2.7.7 available, which is considerably out of date now (it's from December 2009).

What's the process for getting the Ubuntu repo to hold newer versions of packages?

Rick
[Learning Scala and liking it.]

---

### Post by rickbeton on 2010-12-01
Hello?

Does no-one else care about the Scala package being so out of date in Ubuntu?

Can anyone answer my question on the process of getting package upgrades made?

Slightly disappointed.
Rick

---

### Post by hangle on 2010-12-13
> **rickbeton said:**
> Hello?

Does no-one else care about the Scala package being so out of date in Ubuntu?

Can anyone answer my question on the process of getting package upgrades made?

Slightly disappointed.
Rick

i am greatly disappointed. 

i am thinking of installing 2.8.1 from the tgz archive, however there are no explicit
instructions of what files are required and where they are to be located in the
root directories.  i found the following instructions at [http://lovehateubuntu.blogspot.com/2008/05/adventures-in-scala-part-i.html](http://lovehateubuntu.blogspot.com/2008/05/adventures-in-scala-part-i.html).  

at the time the code was executed, the repo was installing
scala 2.3 and the person wanted to upgrade to 2.7.7.  
-----------------------------------------------------------------------------------------------
wget [http://www.scala-lang.org/downloads/distrib/files/scala-2.7.7.final.tgz](http://www.scala-lang.org/downloads/distrib/files/scala-2.7.7.final.tgz)
tar -zxvf scala-2.7.7.final.tgz
sudo mv scala-2.7.7.final /usr/share/scala
sudo ln -s /usr/share/scala/bin/scala /usr/bin/scala
sudo ln -s /usr/share/scala/bin/scalac /usr/bin/scalacNow you have a working Scala implementation! Make sure to check the most up-to-date version on their website. I'll try and keep this up-to-date, but I'm only human and only check the Scala website every now and then.

To uninstall:sudo rm -rf /usr/share/scala /usr/bin/scala /usr/bin/scalac
-------------------------------------------------------

---

### Post by karlottofritz on 2010-12-14
> **rickbeton said:**
> 
Does no-one else care about the Scala package being so out of date in Ubuntu?


I do care and would like to see those repos updated as well.
Unfortunately, I have no idea how to help in that respect.

---

### Post by odLott on 2010-12-25
Add me to the list. Was hoping Maverick Meerkat would be upgraded to 2.8. Sure, installing it from the tgz is easy enough, but wish it was supported from repository.

I do however think the package should need to be renamed scala28. While I'm not using 2.7.7 at all, I can see how it could get nasty for somebody who is.

---

### Post by CluelessWinboxUser on 2011-01-15
Two possible solutions without waiting for Ubuntu to be updated:

1. [http://unki2aut.wordpress.com/2010/10/19/scala-2-8-0-and-ubuntu-10-10/](http://unki2aut.wordpress.com/2010/10/19/scala-2-8-0-and-ubuntu-10-10/)  which basically suggests to install from the .jar install file on the official website

2. Use Eclipse and install the Eclipse Scala plugin. How to can be found here [https://www.assembla.com/wiki/show/scala-ide/Requirements_and_Installation](https://www.assembla.com/wiki/show/scala-ide/Requirements_and_Installation)

I hope this might help.

---

### Post by ivotron on 2011-01-31
[This ppa]("https://launchpad.net/~bneijt/+archive/ppa") provides 2.8.0. Not 2.8.1 yet but I prefer this rather than having to install it manually. Also note that the lucid repo works for maverick (Java bytecode).

---

### Post by rickbeton on 2011-06-12
We're onto Scala 2.9.0.1 now. The Ubuntu repo is even more behind.

For those who want to use the newer version anyway, please do so by 

1. downloading it from [http://www.scala-lang.org/downloads](http://www.scala-lang.org/downloads)
(you need the Unix/Macos/Cygwin .tgz version).

2. unpack it in /opt, or somewhere else if you prefer. The command for this is
```
cd /opt
sudo tar zxvf scala-2.9.0.1.tgz
```

3. edit your $HOME/.bashrc by adding /opt/scala-2.9.0.1/bin to PATH
```
PATH=/opt/scala-2.9.0.1/bin:$PATH
```

You're likely to need SBT ([http://code.google.com/p/simple-build-tool/](http://code.google.com/p/simple-build-tool/)) too.
Rick

---

### Post by rickbeton on 2011-06-19
SBT is now up to version 0.10 but for some reason I don't understand has moved to another website.

[https://github.com/harrah/xsbt](https://github.com/harrah/xsbt)

Hope that helps,
Rick

---

