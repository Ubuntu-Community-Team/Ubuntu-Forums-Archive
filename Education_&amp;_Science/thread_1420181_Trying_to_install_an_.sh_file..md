---
title: "Trying to install an .sh file."
date: 2010-03-02
forum: Education &amp; Science
---

### Post by pepsifx357 on 2010-03-02
I was trying to install Digital Universe and I used the code

```
sudo sh ./milkyway.sh
```

It came up with and error

```
./partiview: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I tried 

```
sudo apt-get install libstdc++5 libstdc++5-3.3-dev
```

Came up with

```
E: Couldn't find package libstdc++5
```

Where is it?

---

### Post by epitaph on 2010-03-03
That library is gone in Karmic. You can choose to use the package from Jaunty (I have done this on multiple installs without any issue thus far).

Try from here: [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

---

### Post by pepsifx357 on 2010-03-06
I found where you could download the .deb files, both X86 and X64 versions.  It needed the X86 version of libstdc++5 and I couldn't install it due to the fact that I have the X64 version of Ubuntu.  I'm probably going to format and install X86 version, seems I have less trouble getting things to work in the 32 bit environment.

Thanks for the help. :)

---

### Post by dadosutter on 2010-03-31
I had the same problem trying to install Digital Universe ([http://www.haydenplanetarium.org/universe](http://www.haydenplanetarium.org/universe)) under Ubuntu 9.10

I found the answer at [http://www.haydenplanetarium.org/universe](http://www.haydenplanetarium.org/universe), installed libstdc++.so.5 and it solved my problem.

I had libstdc++.so.6 previously installed and I have not noticed any conflicts so far.

Hope it works for someone else too.

Best
Dado Sutter

---

### Post by Azrael3000 on 2010-04-03
just a thought: how about making a symlink from libstdc++.so.6 to libstdc++.so.5? In case the libraries didn't change too much this might be a sensible thing to do that wouldn't require you to reinstall the old version.

---

### Post by pepsifx357 on 2010-04-05
Apparently, this doesn't work for 64 bit systems.  So i've "downgraded" to 32 bit since I can't seem to get a lot of things to work in 64. Like flash, divx, and other web based applications.  I hope that 10.04 addresses these issues.

---

### Post by miguelastico on 2010-05-10
> **dadosutter said:**
> 

I found the answer at [http://www.haydenplanetarium.org/universe](http://www.haydenplanetarium.org/universe), 

Sorry, but where exactly did you find the solution there?

> **Azrael3000 said:**
> jhow about making a symlink from libstdc++.so.6 to libstdc++.so.5? 

I tried, I failed...

---

### Post by charlie1953 on 2010-07-03
I am also trying to install the Digital Universe and get the same problem as pepsifx357 with the version of libstdc++. Ubuntu Lucid has version 6 installed and it seems that I need version 5. Has anyone got this working? If so what are the steps? Thanks for any help...

---

### Post by pepsifx357 on 2010-07-04
> **charlie1953 said:**
> I am also trying to install the Digital Universe and get the same problem as pepsifx357 with the version of libstdc++. Ubuntu Lucid has version 6 installed and it seems that I need version 5. Has anyone got this working? If so what are the steps? Thanks for any help...

32 bit or 64 bit?

---

### Post by charlie1953 on 2010-07-05
sorry I should have said - 32 bit...

---

### Post by pepsifx357 on 2010-07-05
The problem I was having was that I had a 64bit Ubuntu and the lib files needed for that program were all 32 bit.  That's why I gave up.  You should be able to get it to work if you just lookup some of the packages in older ubuntu repositories.

---

