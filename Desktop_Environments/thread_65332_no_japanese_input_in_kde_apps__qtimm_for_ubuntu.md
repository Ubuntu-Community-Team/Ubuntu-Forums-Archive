---
title: "no japanese input in kde apps / qtimm for ubuntu"
date: 2005-09-13
forum: Desktop Environments
---

### Post by TheRealCryss on 2005-09-13
I'm not able to input japanese in any kde app. This site ([http://lists.suse.com/archive/m17n/2005-Mar/0034.html](http://lists.suse.com/archive/m17n/2005-Mar/0034.html)) tells me that I need qtimm but there isn't any package in ubuntu.

Can sombody help me? Thanks.
Chris

---

### Post by mlomker on 2005-09-13
You should search on **scim** in Synaptic:

scim
scim-tables-ja

This is the [main website for the project.](http://www.scim-im.org/) 

Unfortunately Ubuntu doesn't currently have skim, which is the part that sits in your KDE application tray.  I had to download and compile it myself (I use the tool for Chinese).

---

### Post by TheRealCryss on 2005-09-14
Thank you for your answer.
I have both (and half a dozen another things with (*-ja-*) installed but it doesn't work.
Hm. ok compiling is not a problem for a 3 year gentoo-user, but what if in, maybe 20 years, there is also a skim package for ubuntu available? Will there be conflicts?
I don't like to mix up. But it seems there is no other way.

skim needs a newser version of scim. I should deinstall the ubunto version of
 scim
 scim-tables-ja
right?
Do I need qtimm?

---

### Post by mlomker on 2005-09-15
If you're going to compile then remove the Ubuntu ones and they'll never attempt to overwrite.

They compile easily, btw.  You might need to grab the **kde-devel** package for skim.

---

### Post by TheRealCryss on 2005-09-15
I got the following error message when ./configure skim (after successfully installed scim 1.4.0)

```

Checking for Python               :  /usr/bin/python
Checking for SCons                :  Use Bundled scons.
Checking for kde-config           :  kde-config was found
Checking for kde version          :  3.4.0
Checking for the qt library       :  qt was found as /usr
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/
Checking for scim >= 1.3.3 ...  Not Found
Checking for scim-x11utils ...  Not Found
scim >= 1.3.3 was not found (mandatory).
Perhaps you should add the directory containing "scim.pc"
to the PKG_CONFIG_PATH environment variable


```

When I set the PKG_CONFIG_PATH with "export PKG_CONFIG_PATH="..." nothing change.

Chris

---

### Post by mlomker on 2005-09-16
Try:

```

updatedb
locate scim
whereis scim
echo $PATH

```

Might be something up with the path, the install, etc.

It should be in /usr/local/bin.

---

### Post by nihilocrat on 2005-09-16
[QUOTE=TheRealCryss]I got the following error message when ./configure skim (after successfully installed scim 1.4.0)

```

Checking for Python               :  /usr/bin/python
Checking for SCons                :  Use Bundled scons.
Checking for kde-config           :  kde-config was found
Checking for kde version          :  3.4.0
Checking for the qt library       :  qt was found as /usr
Checking for uic                  :  uic was found as /usr/bin/uic
Checking for moc                  :  moc was found as /usr/bin/moc
Checking for the qt includes      :  the qt headers were found in /usr/include/qt3/
Checking for the kde includes     :  the kde headers were found in /usr/include/kde/
Checking for scim >= 1.3.3 ...  Not Found
Checking for scim-x11utils ...  Not Found
scim >= 1.3.3 was not found (mandatory).
Perhaps you should add the directory containing "scim.pc"
to the PKG_CONFIG_PATH environment variable


```

When I set the PKG_CONFIG_PATH with "export PKG_CONFIG_PATH="..." nothing change.

Chris[/QUOTE]

I got the same error when trying this out. I've installed kde-devel. SCIM is not installed to /usr/local/bin, but instead /usr/bin. If I want to compile SKIM myself, should I need to compile a local binary of SCIM first?

---

### Post by mlomker on 2005-09-16
> If I want to compile SKIM myself, should I need to compile a local binary of SCIM first?

I compiled my own copy of scim.   The latest version of skim requires a newer copy than what is available in the Hoary repositories.

---

### Post by TheRealCryss on 2005-09-17
[QUOTE=mlomker]Try:

```

updatedb
locate scim
whereis scim
echo $PATH

```

Might be something up with the path, the install, etc.

It should be in /usr/local/bin.[/QUOTE]

scim is in /usr/local/bin
But what should I do with my error?
Or do you mean it has to do with the scim-binary that lies in /usr/local/bin instead of /usr/bin?

---

### Post by TheRealCryss on 2005-09-19
nobody who can help?

---

### Post by mlomker on 2005-09-19
[QUOTE=TheRealCryss]nobody who can help?[/QUOTE]

This error *Checking for scim >= 1.3.3 ...  Not Found* means that it can't find scim where it is looking for it or the version is too old.

If you type **scim --help** at a prompt what version does it come back with?

---

### Post by TheRealCryss on 2005-09-19
1.4.0

---

### Post by mlomker on 2005-09-19
Hmm.  You say that you've tried this?

```

export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
./configure

```

---

### Post by TheRealCryss on 2005-09-19
I deleted ALL scim* related directorys and files from my linux. Now it works, but I don't get the ICON when starting scim with "scim".
With "scim -d" my keyboard locks and I can't switch kde desktops with the mouse. I have to reset. :-/

---

### Post by TheRealCryss on 2005-09-19
OK. Now it works. I made skim but forgot to install it.  :---)
Thank you for your help.

---

### Post by mlomker on 2005-09-19
I'm glad that it worked out!

---

### Post by TheRealCryss on 2005-09-19
Oh no!

I installed anthy, scim-anty and a few other input methods (some languages are shown/activated in the skim configuration menue including japanese) but if i left-click the skim icon in the tray nothing is shown. Only a empty small box...

What's wrong this time...  ](*,)

---

### Post by mlomker on 2005-09-19
Ah.  If you scour the README's you'll discover that you have to set some environment variables before it'll work.

Create a file called /etc/X11/Xsession.d/S75skim with the following contents:

```

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"

```

Once you restart KDE it should be cool.  The default for starting the input method is Ctrl-Spacebar.

---

### Post by TheRealCryss on 2005-09-20
No. Same problem.
What other information do you need to help me?
I use ubuntu hoary with kde as desktop manager and I want to use skim as frontend for scim (if I understand it right how it works)



Chris

---

### Post by GoldBuggie on 2005-09-20
In the konsole try

```

killall scim-launcher
killall scim-panel-gtk
scim-panel-kde -d -f
scim -d

```

---

### Post by TheRealCryss on 2005-09-21
That didn't help.
I give it up and write my japanese emails with windows.
Perhaps there will be an updated version of skim and scim for ubuntu in the future.

---

### Post by mlomker on 2005-09-22
[QUOTE=TheRealCryss]That didn't help.
I give it up and write my japanese emails with windows.
Perhaps there will be an updated version of skim and scim for ubuntu in the future.[/QUOTE]

This is basically what we did and it's tailored to gnome, but I thought I'd post it as an FYI.

[Gnome scim install how-to](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by TheRealCryss on 2005-09-24
As written in your guide I should e.g. "apt-get install scim-gtk2-immodule"
But this has dependencies with the old scim 1.??.
And there's no skim in ubuntu. With the guide I was able to input with firefox but not in any kde app.

---

### Post by mlomker on 2005-09-24
It isn't my guide.  [Mr Bass](http://www.ubuntuforums.org/member.php?userid=14223) created that and a few other how-to's on his website.

---

### Post by TheRealCryss on 2005-09-24
Ah ok. Sorry.

---

### Post by TheRealCryss on 2005-10-07
It works now. But not how it should do.

Please have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?p=392424#post392424](http://www.ubuntuforums.org/showthread.php?p=392424#post392424)

---

