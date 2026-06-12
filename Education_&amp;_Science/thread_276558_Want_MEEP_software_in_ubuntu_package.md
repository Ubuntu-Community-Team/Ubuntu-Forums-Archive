---
title: "Want MEEP software in ubuntu package"
date: 2006-10-13
forum: Education &amp; Science
---

### Post by chanhoe on 2006-10-13
This is a request to the Ubuntu developers.

I am interested to use a electromagnetic wave FDTD simulator for my project. But I have not much time to learn about software installation in a Linux system.

Can someone kindly incorporate the "MEEP" software into ubuntu packages?

This is the link
[http://ab-initio.mit.edu/wiki/index.php/Meep_Installation](http://ab-initio.mit.edu/wiki/index.php/Meep_Installation)

Thank you very much ....
Chan Hoe:)

---

### Post by jpkotta on 2006-10-21
The packages that I needed to get the thing to compile were:

[LIST=1]
[*]fftw3-dev
[*]guile-1.6-dev
[*]refblas3-dev
[*]lapack3-dev
[/LIST]

You will certainly need build-essential as well.  You will probably need a couple of other packages too.  To figure out what these are, just follow this procedure:
[LIST=1]
[*]run ./configure
[*]look at what it fails on
[*]seach for that thing in synaptic or your favorite package manager
[*]install the -dev package associated with it (often there will be a "lib" prefix too)
[*]repeat until ./configure succeeds
[/LIST]

Anyway, after installing these, I could build harminv and libctl:

```
tar zxvf libctl*tar.gz
cd libctl*
./configure && make
sudo checkinstall
cd ..
tar zxvf harminv*tar.gz
cd harminv*
./configure && make
sudo checkinstall
cd ..
tar zxvf meep*tar.gz
cd meep*
./configure && make
sudo checkinstall

```

Then I had meep, and maybe I will actually learn to use it someday.

Now, meep looks like the kind of thing that you would actually not want an easy to use but unoptimized binary package.  I'll bet that if you compile meep and it's (math-heavy) dependencies, you can get a big performance boost.  By playing with compiler options, I was able to get the fractal generator Fractint to run 15% faster; Fractint uses a lot of floating point math as I'm sure these do as well.

---

