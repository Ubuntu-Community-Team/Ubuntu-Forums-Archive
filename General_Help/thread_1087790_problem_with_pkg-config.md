---
title: "problem with pkg-config"
date: 2009-03-05
forum: General Help
---

### Post by natialos on 2009-03-05
Trying to install salasaga from the .deb file, but when I run ./configure, I get the following errors:

Package gdk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-2.0' found
Package gdk-pixbuf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-pixbuf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-pixbuf-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package libgnome-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnome-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnome-2.0' found
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found
Package gdk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-2.0' found
Package gdk-pixbuf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-pixbuf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-pixbuf-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package libgnome-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnome-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnome-2.0' found
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found


I don't know about all of these packages, but I know I have some of them, so I don't think that's the problem. It seems more like pkg-config isn't seeing them for some reason. How do I fix this?

---

### Post by C-- on 2009-03-05
Type

```
echo $PKG_CONFIG_PATH
```

in the terminal. If the resulting value does not list the directory /usr/lib/pkgconfig add the following line to your .bashrc file in your home directory:

```
export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib/pkgconfig
```

If echoing the variable doesn't produce any output you can leave out the $PKG_CONFIG_PATH: part in your .bashrc file.

---

### Post by natialos on 2009-03-06
Where exactly in the file am I supposed to add that line? I added it to the end and left a blank line afterward, and the echo command still comes back blank. 

Thank you for your help, btw!

---

### Post by C-- on 2009-03-06
Huh. As a test I put 
```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```

At the bottom of my .bashrc file and it worked for me.

Did you:

1) Save the file to your home directory? You can go to your home directory in the terminal by typing:

```
cd
```

2) Make sure to put the period before .bashrc? As in, the file is called [DOT]bashrc?

3) Did you try restarting your terminal and then trying to echo it?

4) Are you using a shell other than bash for your terminal? In that case, put the export statement in you .profile file ([DOT]profile) in your home directory, log out of gnome, and then log back in. .bashrc is run every time you open a bash shell, .profile is run every time you log in.

---

### Post by snova on 2009-03-06
Try installing the **gnome2-dev** package. Are you sure you have it?

---

### Post by natialos on 2009-03-09
I'm running KDE, not Gnome. So gnome2-dev isn't in my repositories. Should I go and try to get it anyway, or is there something else I should be getting for KDE?

I tried all the things you suggested, C--, and now the echo command comes back /usr/lib/pkgconfig, but running ./configure on salasaga still yields the same errors. :/

---

### Post by snova on 2009-03-09
> **natialos said:**
> I'm running KDE, not Gnome. So gnome2-dev isn't in my repositories. Should I go and try to get it anyway, or is there something else I should be getting for KDE?

Your choice of desktop environment shouldn't matter.

On the other hand, my own silly mistakes might, as it's actually called **libgnome2-dev**. Sorry. :)

---

### Post by natialos on 2009-03-10
> **snova said:**
> Your choice of desktop environment shouldn't matter.

On the other hand, my own silly mistakes might, as it's actually called **libgnome2-dev**. Sorry. :)

Installed **libgnome2-dev**, logged out and in again, same results. :(

---

### Post by snova on 2009-03-10
> **natialos said:**
> Installed **libgnome2-dev**, logged out and in again, same results. :(

Odd. I know that package contains the file... well, we'll give PKG_CONFIG_PATH a shot:

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
./configure
```

Also, I took a look at their homepage, the packages in the repos are only one alpha behind. Is it necessary to build from source?

---

### Post by natialos on 2009-03-10
> **snova said:**
> Odd. I know that package contains the file... well, we'll give PKG_CONFIG_PATH a shot:

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
./configure
```

Also, I took a look at their homepage, the packages in the repos are only one alpha behind. Is it necessary to build from source?

Used the code you gave, still same results.

Where  did you find the package? I try apt-get install salasaga and it says it isn't there. Synaptic also doesn't seem to have it. Sorry, I'm a bit a of a newbie and I don't know much about repositories and so on.

I also know that I'm running 64 bit, if that changes anything.

My error seems very close to this error here [http://www.salasaga.org/forum/index.php?topic=29.0](http://www.salasaga.org/forum/index.php?topic=29.0) but there is no solution there that I can see, so that doesn't seem to help.

---

### Post by snova on 2009-03-10
> **natialos said:**
> Where  did you find the package? I try apt-get install salasaga and it says it isn't there. Synaptic also doesn't seem to have it. Sorry, I'm a bit a of a newbie and I don't know much about repositories and so on.

There's a handy little tool called apt-cache; among a number of useful commands, it can tell you where a particular package comes form:

```
$ apt-cache policy salasaga
salasaga:
  Installed: (none)
  Candidate: 0.8.0~alpha4-1
  Version table:
     0.8.0~alpha4-1 0
        500 http://us.archive.ubuntu.com intrepid/**universe** Packages

```

In this case, it's in the universe component.

Now, there is a graphical tool in KDE to manage repos, but since I don't know where it is on the menu, just type this into Alt-F2:

```
kdesudo software-properties-kde
```

And make sure that "Community-maintained Open Source software (universe)" is checked, then close the window (and reload when it prompts). It should show up in whatever package manager you use afterwards.

---

### Post by natialos on 2009-03-11
> **snova said:**
> There's a handy little tool called apt-cache; among a number of useful commands, it can tell you where a particular package comes form:

```
$ apt-cache policy salasaga
salasaga:
  Installed: (none)
  Candidate: 0.8.0~alpha4-1
  Version table:
     0.8.0~alpha4-1 0
        500 http://us.archive.ubuntu.com intrepid/**universe** Packages

```

In this case, it's in the universe component.

Now, there is a graphical tool in KDE to manage repos, but since I don't know where it is on the menu, just type this into Alt-F2:

```
kdesudo software-properties-kde
```

And make sure that "Community-maintained Open Source software (universe)" is checked, then close the window (and reload when it prompts). It should show up in whatever package manager you use afterwards.


the apt-cache command returns "W: Unable to locate package salasaga". Which I suppose makes sense if it isn't in my repositories?

The other command you gave me I'm a bit confused about. "kdesudo" is not a command, and if I run that as just "sudo software-properties-kde", nothing happens.
However, I opened up synaptic and went into the repositories manager in there, and it seems to be saying that my universe repos *are* enabled.

I'm running Hardy. Maybe I'm too out of date?

---

### Post by anotherk on 2011-01-05
I'm sure it's too late for the original poster, but for anyone else who happens upon this thread.  I had this problem and installing **libgnome2-dev** did not solve it, but installing **gnome-devel** did.

Hope that helps.

---

