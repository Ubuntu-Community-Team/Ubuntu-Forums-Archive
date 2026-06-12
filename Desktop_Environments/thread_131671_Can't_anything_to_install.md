---
title: "Can't anything to install"
date: 2006-02-16
forum: Desktop Environments
---

### Post by ThirdGenLS1 on 2006-02-16
So everytime i try to complie and install useing sudo this is what i get.

SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/pyshell.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/pyshell.py", line 103
    locals=None, properties=None, banner=None):
                                              ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rcsizer.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rcsizer.py", line 62
    __in__init__(self):
                      ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rightalign.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rightalign.py", line 68
    __in__init__(self, parent, id, *args, **kwargs):
                                                   ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rpcMixin.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rpcMixin.py", line 103
    __in__init__(self,method,args):
                                  ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/scrolledpanel.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/scrolledpanel.py", line 36
    name = "scrolledpanel"):
                           ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/sheet.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/sheet.py", line 19
    __in__init__(self, parent, id, grid):
                                        ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/shell.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/shell.py", line 68
    __in__init__(self, parent, shell, id=-1):
                                            ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py", line 49
    nnnnnnnnnnnnnnnnncallback = None):
                                     ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splitter.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splitter.py", line 60
    nnnnnnnnnnnnnnnnnstyle = 0, name="multiSplitter"):
                                                     ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/statbmp.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/statbmp.py", line 23
    nnnnnnnnnnnnnnnnnname = "genstatbmp"):
                                         ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/stattext.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/stattext.py", line 33
    nnnnnnnnnnnnnnnnnname = "genstattext"):
                                          ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/throbber.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/throbber.py", line 34
    __in__init__(self):
                      ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker.py", line 36
    fps=20,nnnnnnnnnnnnnnnn     #frames per second
      ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker_xrc.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker_xrc.py", line 18
    __in__init__(self):
                      ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxPlotCanvas.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxPlotCanvas.py", line 55
    nnnnif wx.Platform == '__WXMSW__' and wx.GetApp() isnnot None:
            ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxpTag.py ...
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxpTag.py", line 106
    __in__init__(self):
                      ^
SyntaxError: invalid syntax

dpkg: error processing python-uno (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org2-writer:
 openoffice.org2-writer depends on python-uno (>> 2.0.1); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org2-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2:
 openoffice.org2 depends on openoffice.org2-writer; however:
  Package openoffice.org2-writer is not configured yet.
dpkg: error processing openoffice.org2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bittornado
 python-wxgtk2.6
 bittornado-gui
 python2.4-gnome2
 python-gnome2
 ndisgtk
 python-uno
 openoffice.org2-writer
 openoffice.org2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ThirdGenLS1 on 2006-02-17
anyone??????????

---

### Post by gingermark on 2006-02-17
When you say compile do you actually mean compile? I'm assuming that as you are using dpkg that you are actually installing regular debs.

Searching around the forums, it seems the error code 1 has many causes. Maybe posting the repositories you are using might help, as I'm guessing there's a problem with at least one of the deb packages.

I notice you've posted this in the Ubuntu forum as well. Whilst cross-posting is frowned upon, I can understand as this seems an uncommon problem. But just to confirm, are you using Ubuntu or Kubuntu?

If you have synaptic package manager installed, run it and see if any packages are broken, and if you can fix them.

---

### Post by ThirdGenLS1 on 2006-02-17
[QUOTE=gingermark]When you say compile do you actually mean compile? I'm assuming that as you are using dpkg that you are actually installing regular debs.

Searching around the forums, it seems the error code 1 has many causes. Maybe posting the repositories you are using might help, as I'm guessing there's a problem with at least one of the deb packages.

I notice you've posted this in the Ubuntu forum as well. Whilst cross-posting is frowned upon, I can understand as this seems an uncommon problem. But just to confirm, are you using Ubuntu or Kubuntu?

If you have synaptic package manager installed, run it and see if any packages are broken, and if you can fix them.[/QUOTE]


Sorry i'm running kubuntu, i'll keep it to this section for now on.  Anyways i dont have synaptic installed, and i dont really know where to find the repositories to post.  Sorry but i'm still kinda new this this linux thing, been suing it for about a month now, had ubuntu installed, then installed KDE on it and really liked it, so did a fresh install of kubuntu and now i'm having these problems......Thanks a lot for the input.

---

### Post by Jucato on 2006-02-18
your repository list could be found in /etc/apt/sources.list
Adept is Kubuntu's counterpart to Synaptic. However, I recommend you install and use Synaptic instead.

Could you explain what you were trying to compile/install? It could help if we knew what you were trying to do so that we could have an idea where the problem comes from.

---

### Post by ThirdGenLS1 on 2006-02-20
alright i was geting that message basicly when ever i was trying to do anything.  using ./configure for ksmoothdock, got it when i was trying to use sudo apt-get install for basicly anything, but now i restarted my comp and now when ever i try to open up adept to view my reository i get this 

Malformed line 35 in source list /etc/apt/sources.list (dist parse)

I also get that when i try to use sudo apt-get install 

Thanks for the help guys

---

### Post by Jucato on 2006-02-20
ok, I'm not sure as to what the ./configure problem is. but that malformed line 35 has something to do with your repository list. If you don't mind, could you post your /etc/apt/sources.list for us to review?

---

### Post by ThirdGenLS1 on 2006-02-21
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arnieamuleadded


I hope this is what your looking for

---

### Post by Jucato on 2006-02-21
how about trying to disable/comment out those repositories that you don't need/use? for example these:

wine -  deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
 
PLF stuff -  deb [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free
PLF  stuff -  deb-src [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free
 
Opera browser -  deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
 
KDE 3.5.1 upgrade -  deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

I don't know this repository - deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
I don't know this repository - deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

If you don't need those repositories, try disabling them for the moment and see what happens.  If I'm not mistaken, one of these repositories might be the culprit.

---

### Post by jrcmuniz on 2006-06-10
Same problem here before your tip!

Thank you very much! 

Joao.

---

