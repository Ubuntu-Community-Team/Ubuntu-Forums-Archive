---
title: "Tools/Data Sources in OOo2?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by jasplund on 2005-10-19
I'm trying to set up bibus to work with OOo2 accoring to [http://bibus-biblio.sourceforge.net/html/en/usingOOo.html](http://bibus-biblio.sourceforge.net/html/en/usingOOo.html) I am supposed to add my ODBC as new Data Sources in OOo2. But there are no Data Sources menu under Tools. the OOo2 help also tells me to go to Tools --> Data sources.

help!

---

### Post by GrumpyBob on 2005-10-19
Well, I'm sort of in the same situation, though my problems lie mostly with getting wxPython installed correctly - how did you do this?  The version from Synaptic seemed to want Python2.3.

With regard to your question, You may be able to get to data sources by Tools | options | OpenOffice Base 

I'd really like to know how you get on with installing Bibus!  I had it working some time ago, under Mandrake 9.0, though I never got it to work on Hoary.

Robert

---

### Post by jasplund on 2005-10-19
Hi thanks for trying to help but it the menu is not in base either.


as to your problem try sudo apt-get install python-wxgtk2.6
that worked for me


Johan
ps. bibus works fine for me but there's no bibus menus in OOo2. If I want to cite something I have to go to bibus and cite

---

### Post by jasplund on 2005-10-19
Here's how you add data source

[http://www.oooforum.org/forum/viewtopic.phtml?t=24525&highlight=sources](http://www.oooforum.org/forum/viewtopic.phtml?t=24525&highlight=sources)

I still haven't managed to get any bibus menus in OOo2 though

---

### Post by GrumpyBob on 2005-10-19
[QUOTE=jasplund]Hi thanks for trying to help but it the menu is not in base either.


as to your problem try sudo apt-get install python-wxgtk2.6
that worked for me


Johan
ps. bibus works fine for me but there's no bibus menus in OOo2. If I want to cite something I have to go to bibus and cite[/QUOTE]


As far as I recall, they way I had it working with OOo1.1.3 under Mandrake 9.0, you inserted citations into the document by clicking "insert citation" from within bibus...I never had bibus menu within OOo.

[I]Note added in edit:  I now have, thanks to help from Pierre Martineau and Daniel Myall, a working bibus.  AFAIK you don't get bibus specific menu items in OOo. 

I have connected to OOo via pipe - to insert a citation you click the cursor where you want the citation, go to bibus, highlight the reference and select "insert citation" from the OpenOffice.org menu in bibus.  It seems this is the better way to connect to the bibliography database that through the OOo database connection.
[/I]

Robert

---

### Post by Canguçu on 2005-10-20
> Note added in edit:  I now have, thanks to help from Pierre Martineau and Daniel Myall, a working bibus.  AFAIK you don't get bibus specific menu items in OOo. 

Robert, could you please post a step-by-step guide about how you installed bibus? I just couldn't install it on Breezy.

---

### Post by Canguçu on 2005-11-07
Robert answered me, so I think it is a good idea to share his how-to with everybody. 

**Thank you, Robert!**

> Hi!,

I have to say I had a hell of a time getting this to install! However, much of this was my inexperience with all things Python.

The bibus website has a full description of which packages are required, and which versions. Read the documentation carefully, particularly the parts concerning the OpenOffice.org menu in bibus. I used a pipe to connect to the OOo2rc that came with Ubuntu 5.10. The symlink at the end of the procedure is essential.

There is a first connection wizard which is very useful.
Incidentally, I chose sqlite as the database, it seemd easier to set up, and I would recommend that.

Pierre Martineau, the author of Bibus, sent me this description of what to do (I have added my comments in **bold**):

1) Install from Ubuntu (universe required)
python2.4
**This should be in your installation by default - check with synaptic**
libwxgtk2.5.3-python_2.5.3.2
**I couldn't find this package. I installed python-wxgtk2.6 from synaptic, which as far as I recall need me to install python2.3 and python-wxversion from synaptic**
python-sqlite_1.0.1

2) Now install from the Bibus site
dpkg -i openoffice-pyuno_20050203-1_i386.deb
dpkg -i --force-all bibus_1.0.0-1_all.deb bibus-doc-en_1.0.0-1_all.deb
**I couldn't get the bibus package to install. I used instead the bibus package from Daniel Myall. It's available from [http://ubuntu.zeno.co.nz/ubuntu/dists/breezy/bibus/](http://ubuntu.zeno.co.nz/ubuntu/dists/breezy/bibus/)**


3)
Now, you must fool the system by telling it to use python2.4 instead of 2.3
for this you must create a link in
/usr/lib/openoffice/program

As root:
> cd /usr/lib/openoffice/program
> ln -s /usr/lib/libpython2.4.so libpython2.3.so.1.0

Start Bibus in a xterm with "bibus"

=============
One other thing, I made a few false and failed starts with this installation. In the end, I removed all the python packages I had installed, including python2.3, before I followed the instructions I sent you.

It would be really useful if someone who knows about these things could construct a package for synaptic for bibus.

Robert

---

