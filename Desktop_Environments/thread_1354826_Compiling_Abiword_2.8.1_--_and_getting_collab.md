---
title: "Compiling Abiword 2.8.1 -- and getting collab"
date: 2009-12-14
forum: Desktop Environments
---

### Post by etitor on 2009-12-14
My uname -a is *Linux ws7113 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux*.

As you all know, the version of Abiword in our Ubuntu repos is rather old. Some nice features of Abiword's last version (2.8.1) convinced me of trying to compile the program.

These are the steps I took:

1. Download the source code:

```
wget http://www.abisource.com/downloads/abiword/2.8.1/source/abiword-2.8.1.tar.gz
```

2. Untar it into its own directory.

3. Install some dependencies (you may need others in addition since this is not the first time I compile a program):

```
sudo apt-get install libfribidi-dev libgsf-1-dev libwv-dev librsvg2-dev libasio-dev libgnomevfs2-dev libgsf-gnome-1-dev libbonobo2-dev
```

4. Enter the directory created in step 2.

5. Launch the configuring script:

```
./configure --with-gnomevfs --enable-plugins --enable-builtin-plugins --enable-clipart --enable-templates --enable-collab-backend-service
```

6. Compile the program:

```
make
```

7. Install the program:

```
sudo make install
```

8. Create a symlink for a library:

```
cd /lib && sudo ln -s /usr/local/lib/libabiword-2.8.so
```

Once these steps are over, I have a working Abiword, version 2.8.1. Since plugins were enabled in step 5, you are supposed to get them.

However, the feature I was most interested in, collab, doesn't appear in the plugin list and so cannot be used. For those not in the know, collab is a new feature of Abiword that lets a team work on the same document at the same time (see [https://abicollab.net](https://abicollab.net) for details).

Can anyone help me?

---

### Post by Rodney9 on 2010-01-19
Thank You for helping me compile the lastest Abiword, I'm sorry I can not help with collab though.

Rodney

---

### Post by kjano on 2010-01-24
hey,

i installed the deb packages for lucid on my 9.10 ubuntu and see the collaboration menu in abiword. hope this helps...

---

### Post by fwallace99 on 2010-01-31
I too have problems. I don't care about collab, I can't get Abiword to give me:

1. Insert autotext
2. Scripting

I'm on Ubuntu 8.10 Intrepid Ibex (i386-i686). So no repositories for me, or even a deb package. I *CAN* get Abiword to build, but don't get the scripting (it's greyed out) AND I don't get auto-text either. Perl scripting is great btw, it's a top-end feature on Mac OSX programs like Write Now Professional. But Abisource has no instructions on how to compile, and their site itself is a crap-shoot if it will work.

I really NEED both scripting and auto-text on Abiword, to avoid Open Office which is slow and bloated. I do have spelling and grammar working.

I have the abiword 2.8.1 tarball, and I've done what the above poster notes, i.e. the dependencies, and also this:

[http://ubuntuforums.org/showthread.php?t=1309570](http://ubuntuforums.org/showthread.php?t=1309570)

i.e.:

Code:

```
apt-get build-dep abiword
```

and here is my (abbreviated) ./configure:

```

./configure --with-gnomevfs --enable-plugins --enable-builtin-plugins --enable-clipart --enable-templates --enable-collab-backend-service 
configure: WARNING: goffice plugin: dependencies not satisfied - libgoffice-0.8 >= 0.7.10
configure: WARNING: psiconv plugin: program psiconv-config not found in path
configure: WARNING: gda plugin: dependencies not satisfied - libgda >= 1.2.0 libgnomedb >= 1.2.0
configure: WARNING: rsvg plugin: not needed with gtk
...
config.status: executing libtool commands

Configuration:
  host                  i686-pc-linux-gnu
  dynamic binary        no
  static binary         yes
  platform              unix (embedded: no)
  toolkit               gtk
  debug                 no

Optional features:
  menubutton            no
  printing              yes
  spell checking        yes
  status bar            yes
  emacs keybinding      yes
  vi keybinding         yes
  clipart               yes
  templates             yes

Optional dependencies:
  gtk2 > 2.14           yes
  gnome-vfs             yes
  gio			yes
  gsf-gio               no
  goffice               no
  gucharmap             no

Builtin plugins         
Plugins                  loadbindings paint hrtext pdb gimp mif mht applix docbook wikipedia babelfish command garble ots google opendocument wordperfect urldict opml eml pdf wmf t602 mswrite clarisworks freetranslation aiksaurus hancom iscii openxml gdict s5 mathview grammar bmp openwriter latex presentation wml passepartout wpg xslfo kword sdw

```

My assumption is that the warnings are not what is killing either scripting or insert autotext.

Can anyone give me a hand? Thanks. I really do appreciate it.

---

### Post by newb85 on 2010-02-02
I hope this isn't a dumb question, but if Abisource has a repo for Karmic (and others), why doesn't adding that repo to Synaptic give the latest version of Abiword?

---

### Post by fwallace99 on 2010-02-05
Sadly it does not for Ibex through IIRC, Jaunty. Only the latest release of Ubuntu has the current stable release (2.8.1) of Abiword.

I'm staying off upgrading as its a pain, and there seems to be stability issues with Jaunty.

---

### Post by newb85 on 2010-02-08
Hmm...that's weird.  The abisource repo for karmic just updated to 2.8.1 today.  Go figure!

---

