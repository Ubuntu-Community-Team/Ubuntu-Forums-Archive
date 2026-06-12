---
title: "penguintv"
date: 2006-01-27
forum: Desktop Environments
---

### Post by shizow on 2006-01-27
how do i install penguintv in kubuntu (breezy)?

[http://penguintv.sourceforge.net/](http://penguintv.sourceforge.net/)

---

### Post by shizow on 2006-01-31
can no one help?

---

### Post by gingermark on 2006-01-31
If only the source code it available, you'll have to compile it yourself. And I can't remember how to do that (I'm still a bit of a noob). I think you can also compile it into your own .deb package, and then install that (so it's easy to remove later) but I can't remember how to do that either.

Make sure you install the dependencies first (I think they're all in the repositories) and I think you'll need the dev packages to compile, but again I'm not sure.

You can see why I hesitated answering your thread in the first place, but hopefully that will give you a place to start from, or someone else will post precise instructions. Sorry, I know this barely counts as any help at all.

---

### Post by gingermark on 2006-01-31
OK, forget all that. For this program do the following.

Download the tar.gz file on offer on the site. For ease, just download it to your home directory.

Open up a terminal window.

Type the following:

```
tar zxvf PenguinTV-1.02.tar.gz

cd PenguinTV-1.02

sudo python setup.py install
```

To run the program type "PenguinTV". The case seems to matter.

Remember to install the packages (via apt-get or Synaptic / Adept) it depends on (listed on the site) first.

---

### Post by shizow on 2006-02-01
can you tell me the exact packages i have to install?



i get this error
~/PenguinTV-1.02$ sudo python setup.py install
Traceback (most recent call last):
  File "setup.py", line 3, in ?
    from penguintv import subProcess
  File "/home/shizow/PenguinTV-1.02/penguintv/__init__.py", line 4, in ?
    import penguintv
  File "/home/shizow/PenguinTV-1.02/penguintv/penguintv.py", line 15, in ?
    import gnome.ui
ImportError: No module named gnome.ui

maybe the gnome bindings are missing?
i did not find them
by the way i use kubuntu

---

### Post by gingermark on 2006-02-01
As you might have been able to tell, I'm not really the best person to help. But yeah, it definitely needs some basic gnome components. I'd suggest installing "ubuntu-base" - I think that is the minimal gnome installation. Not too sure what those errors mean.

I am also a Kubuntu user, but have gnome installed, and it worked fine, so I guess maybe give that a go and report back again?

Where are all the knowledgable people??!!! :)

---

### Post by christhemonkey on 2006-02-01
On the site it says it needs
Pysqlite
Pycurl
python-xml
python gtkhtml2
gnome bindings

Dunno if any of those are in the repos, assume most of the python ones are!

---

### Post by gingermark on 2006-02-01
[QUOTE=christhemonkey]On the site it says it needs
Pysqlite
Pycurl
python-xml
python gtkhtml2
gnome bindings

Dunno if any of those are in the repos, assume most of the python ones are![/QUOTE]
They are all available in the repos (although python gtkhtml2 is called python-gnome2-extras) apart from gnome bindings. But I installed PengionTV fine, which is why I suggested installing ubuntu-base. Can anyone confirm if that is the correct way to go?

---

### Post by shizow on 2006-02-01
i had ubuntu-base installed before, so thats not the problem

but i need to know to exact names of the packages to install
the ones from the site i dont find in the repositories

---

### Post by gingermark on 2006-02-01
My apologies, I misunderstood.

See if you can install the following from the repositories:

python2.4-pysqlite2
python2.4-pycurl
python-xml
python-gnome2-extras (I'm not sure if the dev package is required or not - I installed it just to be certain).

If you can't, post the contents of your sources.list file (located in /etc/apt) and we'll take it from there (and if you can, try the 'sudo python setup.py install' command again).

---

### Post by shizow on 2006-02-02
i had to install more packages: python-gnome python-glade2 

now i could install penguintv, 
but i cannot import feeds or add a feed
there is  no error, but i dont see any feeds

---

### Post by gingermark on 2006-02-02
Well, I'd check out the Readme file. The developers email address is in there, and it says to email if you have questions. Best get in contact with him.

---

