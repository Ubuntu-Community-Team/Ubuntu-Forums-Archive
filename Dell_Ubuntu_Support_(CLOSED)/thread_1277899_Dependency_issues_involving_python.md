---
title: "Dependency issues involving python"
date: 2009-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-09-28
I am currently trying to install a program that requires a specific version or older of python to be installed. So, I installed an older version of python next to my current version. I now have python 2.5 and 2.6 installed. The problem is, when I try to install the program that depends on an older version of python, it doesn't seem to know that an older version is there. All it sees is the newer version. 

Can someone help to get this program to "call" the old version of python? 

P.S. The program in question here is "python-gpsbabel" which, itself, is a dependency for the program cache901. Cache901 is really what I'm trying to get installed here.

---

### Post by astrakhan on 2009-09-29
instead of python *programname*.py, try: 

```
python2.5 *programname*.py
```

that should call the older version.

---

### Post by Arndtwe on 2009-09-29
Okay, If I have to resort to compiling the program myself, I will use that. But for right now, I am trying to do all of this via synaptic. Is there a way that I can get it call the older version, and still use synaptic? Or is this hopeless through synaptic?

---

### Post by jkysam on 2009-09-29
Have you tried "update-alternatives" to try to change the version of python to 2.5?

---

### Post by Arndtwe on 2009-09-29
> **jkysam said:**
> Have you tried "update-alternatives" to try to change the version of python to 2.5?

No, But my problem is not needing python 2.5. I have that, what I need is for python-gpsbabel to know that.

---

### Post by jkysam on 2009-09-29
I take that the problem is that the command "python" which "python-gpsbabel" might be trying to use is associated with with python version 2.6. The only way I can think of changing the version associated with python through the synaptic-package manager would be using "update-alternatives" but i don't know if it works.

What I do to change the default version of python in the system is the following.
On my machine I have two versions of python:
{code}
~$ ls -l /usr/bin/ | grep python
-rwxr-xr-x  1 root   root       7835 2009-03-09 11:42 dh_python
lrwxrwxrwx  1 root   root         23 2009-06-28 12:34 pdb2.5 -> ../lib/python2.5/pdb.py
lrwxrwxrwx  1 root   root         23 2009-06-12 14:59 pdb2.6 -> ../lib/python2.6/pdb.py
lrwxrwxrwx  1 root   root          9 2009-06-12 14:59 python -> python2.6
-rwxr-xr-x  1 root   root    1177204 2009-04-04 15:13 python2.5
-rwxr-xr-x  1 root   root    2268568 2009-04-18 22:53 python2.6
lrwxrwxrwx  1 root   root         29 2009-06-12 14:59 pyversions -> ../share/python/pyversions.py
{code}

Note that python is linked to python2.6.
If I want to change the version that is associated with python I would simply remove the current python link:
{code}
rm /usr/bin/python
{code}

And add a new link:
{code}
ln -s /usr/bin/python2.5  /usr/bin/python
{code}

This way when "python" is issued by a user or app it will pickup version 2.5.

HTH

---

### Post by sphyg04 on 2009-11-27
I get this message. 

cache901:
 Depends: python-xml  but it is not installable
 Depends: python-gpsbabel but it is not going to be installed
  Depends: python (<2.6) but 2.6.4-0ubuntu1 is to be installed

How do I fix it.. Please be specific because I am a noob. Thanks

---

### Post by devil404 on 2009-11-30
Following the other user's instructions won't make cache901 install from packages. Luckily, I got it to work by building it from source. Here's what I did:

Start by linking python to the python2.6 binary like **jkysam** showed.

Then grab python-gpsbabel 
```
wget http://www.cache901.org/downloads/python-gpsbabel-0.9.0.tar.gz
```

...and extract it...

```
tar -zxvf python-gpsbabel-0.9.0.tar.gz
```

...jump into that directory...

```
cd python-gpsbabel-0.9.0
```

...and install python-gpsbabel

```
sudo python setup.py install
```

There's the prerequisite that wouldn't install because of some messed up dependencies. Now for the bread and butter. Since it's a lot like the previous installation, I'll rush things along a bit:

```
cd ..
wget http://www.cache901.org/downloads/cache901-0.6.1.tar.gz
tar -zxvf cache901-0.6.1.tar.gz
cd cache901*
sudo python setup.py install
```

And there ya go. It wasn't quite what I was expecting, but at least we can keep track of our geocaches natively in Linux.

---

