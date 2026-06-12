---
title: "Python &amp; NumpyTest"
date: 2009-05-26
forum: General Help
---

### Post by julienq on 2009-05-26
Hello there,

I am currently working on a script in which I use [FONT=Courier New]scipy.optimize.leastsq[/FONT] so as to fit a gaussian. The problem is, when i launch it, i get:
Traceback (most recent call last):
  File "./essai.py", line 7, in <module>
    import scipy.optimize
  File "/usr/lib/python2.5/site-packages/scipy/optimize/__init__.py", line 18, in <module>
    from numpy.testing import NumpyTest
ImportError: cannot import name NumpyTest

The Numpy librairy is installed on my system.
My config:
ubuntu 8.04, 64b
python 2.5.2

I have search the web and found somewhere that the problem was related specificaly to ubuntu8.04 and python2.5.2. They say the only solution was to upgrade ubuntu to a newer release. 

Does anybody knows if this is true ? Isn't there another way to proceed ?

Thanks in advance for your answers.

Jq

---

### Post by geirha on 2009-05-26
I got 8.04 32-bit, and "import scipy.optimize" works just fine for me. It might be that the numpy-module hasn't been properly symlinked into /usr/lib/python2.5/. If that is the case, then reinstalling the package should fix it. ```
sudo aptitude reinstall python-numpy
```

---

### Post by julienq on 2009-05-26
yeah thanks, you're right
Actually the reinstallation of numpy doesn't work fine, some errors are left during apt-get.

I'll try to fix this
Thanks again.

---

### Post by mrule on 2009-07-17
I am also getting this error, re-installing numpy does nothing. this sucks, because upgrading to 8.10 will force me to reinstall / re-hack a lot of other libraries that I have just barely gotten working on 8.04.

---

### Post by mrule on 2009-07-17
ok, a simple upgrade to 8.10 did not eliminate this error.

so I went through the scipy files and deleted all references to NumpyTest

and now things run.

---

### Post by ahmatti on 2009-07-23
Julienq, just a note that you might consider posting numpy and computation related issues in general to the "Education and Science" section of the forum where a lot of people are using these tools. I'm just posting this because I see you are quite new to the forum. Glad to see you found some help here too.

---

### Post by davclark on 2009-10-10
As an aside, I downloaded and did a "python setup.py install" over top of the stock ubuntu 1.1.1 numpy install (so I could leave matplotlib, et al in place). Probably better to do an easy_install -U numpy. This should avoid tromping on dpkg managed stuff anyhow.

But the real issue - I think the NumpyTest error is simply that numpy 1.3 doesn't have that anymore. You need to update to a scipy that supports numpy 1.3 (e.g. 0.7+). If you don't have any dependencies for python-scipy, I generally do straight setup.py installs these days. They are faster if you end up having lots of your own self-installed libs.

---

