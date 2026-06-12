---
title: "Wikipad equivalnet for linux?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Remmelas on 2005-11-20
Any suggestions for a functional equivalent to wikidpad(windows software).

---

### Post by magnusbb on 2005-11-20
[http://wikidpad.python-hosting.com/wiki/InstallLinux](http://wikidpad.python-hosting.com/wiki/InstallLinux)

---

### Post by Remmelas on 2005-11-20
Yeah, did that, actually have it working in Linux via svn checkout, but it's buggy(don't know if it's wikidpad's issue, or ubuntu's issue) and wasn't really up to figuring it out.  Perhaps tonight I'll rebuild it's dependencies from source using the latest versions and see how it goes.  I really like this software as a 'notetaker/organizer', and have it installed on my work machine for that purpose, would be nice to be able to do the same at home and I refuse to run winbloze to do it.

---

### Post by Remmelas on 2005-11-21
heh, well, i blew up my ubuntu, and had to reinstall, and now wikipad works great, other than the need for the sitecustomize.py trick to change character encodings.

---

### Post by jandi on 2006-08-02
I absolutely love WikidPad, and use it extensively in Windows, however, I have failed miserably in trying to use it on Ubuntu.  I tried the instructions on the website, but get a bunch of error messages.

Some alternatives are Tomboy, Newton Desktop Wiki and Zim Wiki, however, none have all the features of WikidPad, and I'd rather have a cross platform solution

---

### Post by jandi on 2006-08-02
I'm getting this error message when I try to run WikidPad

$ python WikidPad.py
Traceback (most recent call last):
  File "WikidPad.py", line 1, in ?
    import WikidPadStarter
  File "/home/jandi/wikidpad/WikidPadStarter.py", line 133, in ?
    from pwiki.PersonalWikiFrame import PersonalWikiFrame
  File "lib/pwiki/PersonalWikiFrame.py", line 14, in ?
    import Configuration
  File "lib/pwiki/Configuration.py", line 36, in ?
    from StringOps import utf8Enc, utf8Dec, mbcsDec, strToBool
  File "lib/pwiki/StringOps.py", line 65, in ?
    elif isLinux():
  File "lib/pwiki/Configuration.py", line 30, in isLinux
    return os.uname[0] == "Linux"
TypeError: unsubscriptable object

I figured it had something to do with the system not being properly identified as Linux, so I went and edited lib/pwiki/Configuration.py
and changed 
return os.uname[0] == "Linux"
to
return True

which I doubt is the best solution, but since I am already sure that my computer is running Linux, I guess I can live without it checking it.  Probably there should be a better solution...

But for now, this works.

---

### Post by jonj on 2006-08-20
Thanks jandi for the > return os.uname[0] == "Linux"
 tip

I added this and a couple of other things to the wikipad wiki
[http://wikidpad.python-hosting.com/wiki/IssuesUnderLinux]("http://wikidpad.python-hosting.com/wiki/IssuesUnderLinux")

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

### Post by jandi on 2006-09-25
Thanks for looking into this!  Far more elegant solution ;)

---

### Post by ryu kun on 2007-01-01
I get this error when I try to run wikidpad,

```
python WikidPad.py
Traceback (most recent call last):
  File "WikidPad.py", line 1, in ?
    import WikidPadStarter
  File "/home/ertugrul/src/source/wikipad/WikidPadStarter.py", line 22, in ?
    from wxPython.wx import *
ImportError: No module named wxPython.wx

```

Any help would be appreciated.

---

### Post by ryu kun on 2007-01-01
solved:

```
sudo aptitude install python-wxgtk2.6
```

---

### Post by ryu kun on 2007-01-02
WikidPad works but it is buggy. I recommend [Zim]("http://zoidberg.student.utwente.nl/zim/"). 

[SIZE="4"]How to install Zim?[/SIZE]

It is available in universe repositories but for the latest version add these two lines to **/etc/apt/sources.list**

! Please note that this repository is currently only for Dapper and Breezy.

```
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
```

and

run in terminal:

```
sudo aptitude update
sudo aptitude install zim
```

You'll find the icon in Applications - Accessories.

Enjoy.

---

### Post by ryu kun on 2007-01-02
duplicate post. please delete.

---

