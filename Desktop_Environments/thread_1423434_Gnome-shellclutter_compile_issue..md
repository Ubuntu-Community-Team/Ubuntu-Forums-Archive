---
title: "Gnome-shell/clutter compile issue."
date: 2010-03-06
forum: Desktop Environments
---

### Post by bruno9779 on 2010-03-06
every time I try to compile gnome-shell using an how-to like [this]("http://www.packtpub.com/article/install-gnome-shell-on-ubuntu-karmic-koala") I get some compile errors for clutter.:

```
 /usr/bin/install -c -m 644 DBusGLib-1.0.typelib DBus-1.0.typelib GConf-2.0.typelib Pango-1.0.typelib PangoFT2-1.0.typelib PangoCairo-1.0.typelib PangoXft-1.0.typelib Atk-1.0.typelib GdkPixbuf-2.0.typelib Gdk-2.0.typelib Gtk-2.0.typelib '/home/bruno/gnome-shell/install/lib64/girepository-1.0'
make[2]: Leaving directory `/home/bruno/gnome-shell/source/gir-repository/gir'
make[1]: Leaving directory `/home/bruno/gnome-shell/source/gir-repository/gir'
make[1]: Entering directory `/home/bruno/gnome-shell/source/gir-repository'
make[2]: Entering directory `/home/bruno/gnome-shell/source/gir-repository'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bruno/gnome-shell/source/gir-repository'
make[1]: Leaving directory `/home/bruno/gnome-shell/source/gir-repository'
*** Checking out clutter *** [3/8]
git clone git://git.clutter-project.org/clutter
Initialized empty Git repository in /home/bruno/gnome-shell/source/clutter/.git/
fatal: The remote end hung up unexpectedly
*** Error during phase checkout of clutter: ########## Error running git clone git://git.clutter-project.org/clutter *** [3/8]

  [1] Rerun phase checkout
  [2] Ignore error and continue to configure
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
choice: 

```

I get this error on my main 64bit desktop, and on my wife's 32 bit laptop

 any idea?

---

### Post by bruno9779 on 2010-03-07
I have tried many times also with jhbuild build -a -c -f, but the error is the same

---

### Post by bruno9779 on 2010-03-07
I have managed.

I have removed gnome-shell folder.
I have followed the instructions from Gnome site [here]("http://live.gnome.org/GnomeShell/#Building)") and I have got the same error.

at this point I have just kept choosing "[1] Rerun phase checkout" till it went through.

A connection issue...

---

### Post by antono on 2011-02-10
> **bruno9779 said:**
> I have managed.

I have removed gnome-shell folder.
I have followed the instructions from Gnome site [here]("http://live.gnome.org/GnomeShell/#Building)") and I have got the same error.

at this point I have just kept choosing "[1] Rerun phase checkout" till it went through.

A connection issue...

It's issue with git repository, not with your environment.


git clone git://git.clutter-project.org/clutter
Cloning into clutter...

no success.

---

### Post by LiteDrive on 2011-02-15
I've been having this issue, too. Are there any fixes? I would try the git-clone link, but unfortunately it seems like that didn't quite work either, judging from the poster above.

---

### Post by chuckhriczko on 2011-03-16
I'm experiencing this too and am trying to find a solution but the poster a couple posts above is right. It's the repository. I'm a git user so I'm familiar with how it works so maybe they have it mirrored somewhere but if not there's nothing we can do about this particular step since the repository is unreachable.

---

### Post by chuckhriczko on 2011-03-16
I've found one solution. The only problem is that it can't get the latest source code from the Git repo. Obviously git is best because the latest changes are automatically download when you update your build but until they fix the git repo you can download the source files and do the following:

1. Download /clutter-1.6.0.tar.gz (a newer version might work but I accidentally downloaded 1.6.0 thinking it was 1.6.8 so feel free to try if you want) from [http://source.clutter-project.org/sources/clutter/1.6](http://source.clutter-project.org/sources/clutter/1.6)

2. Find this line in your terminal:

```
Initialized empty Git repository in /home/your_username/gnome-shell/source/clutter/.git/
```

and copy the path without .git at the end like so:

```
/home/your_username/gnome-shell/source/clutter/
```

Open a seperate terminal without closing the one you're building with and, assuming it downloaded to the ~/Downloads folder enter the following:

```

cd ~/Downloads;
tar xvf clutter-1.6.0.tar.gz;
cd /home/your_username/gnome-shell/source/clutter;
mv ~/Downloads/clutter-1.6.0/* .;

```

Then in the other terminal, the one actually building gnome shell, use options 2 or [2] Ignore error and continue to configure. It should configure the make files and make and install clutter. After I did this I haven't received an error yet and I'm on step 35/41 (at the time of this writing). Feel free to ask if anyone has questions.

---

