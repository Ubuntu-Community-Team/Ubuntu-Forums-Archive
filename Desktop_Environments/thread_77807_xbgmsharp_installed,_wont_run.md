---
title: "xbgmsharp installed, wont run"
date: 2005-10-17
forum: Desktop Environments
---

### Post by f76 on 2005-10-17
Hi all!
 I updated to breezy and lucky for me gtk-sharp2 exist in repos, I had trouble getting it working in hoary... I installed xbgmsharp via apt-get and it seemed to be a painless install.. now i cant get it to work though...

do i need another version or some additional stuff from repos? it looks like it wants gtk-sharp ver 2 but i have gtk-sharp2 installed...
i cant get this...

on installing  gtk-sharp-gapi-unstable i got the following /var/cache/apt/archives/gtk-sharp-gapi-unstable_1.9.2-2ubuntu1_i386.deb: trying to overwrite "/usr/share/gapi-2.0/pango-api.xml" that also exists in package gtk-sharp2-gapi

is it some kind of conflict?
```
 $xbgmsharp

** (/usr/share/dotnet/xbgmsharp/xbgmsharp.exe:9958): WARNING **: The following assembly referenced from /usr/share/dotnet/xbgmsharp/xbgmsharp.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/share/dotnet/xbgmsharp).


** (/usr/share/dotnet/xbgmsharp/xbgmsharp.exe:9958): WARNING **: Missing method Init in assembly /usr/share/dotnet/xbgmsharp/xbgmsharp.exe, type Gtk.Application
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
```

---

### Post by f76 on 2005-10-18
I installed mono-gac and gacutils says i have gtk-sharp Version:    2.4.0.0 as opposed to the 2.0.0.0 that is asked for by the program.. am i right so far?

Should i download gtk-sharp v 2.0.0.0 and where would i find that specific ubuntu package? 

thanx!

---

### Post by matthias_k on 2005-10-18
Just wondering, from which repo did you isntall xbgmsharp? Because it doesn't exist in my repos.

---

### Post by f76 on 2005-10-19
according to homepage [http://xbgm.sourceforge.net/files.php#Debian](http://xbgm.sourceforge.net/files.php#Debian)
the repos for ubuntu are as follows

deb [http://xbgm.sourceforge.net/debian](http://xbgm.sourceforge.net/debian) unstable/
deb-src [http://xbgm.sourceforge.net/debian](http://xbgm.sourceforge.net/debian) unstable/

Can i convice the xbgmsharp app somhow to run with a newer library?

---

### Post by matthias_k on 2005-10-19
That's a repository for the Debian unstable branch (Sid), and thus includes dependencies which only apply for that branch. You really shouldn't use it with Ubuntu.

What's the problem with downloading a tarball archive? Just unpack it and run 'mono xbgmsharp.exe'. Works fine for me.

---

### Post by f76 on 2005-10-19
thanx! what archive was that? the mono-installer? could u link to it pls?

---

### Post by matthias_k on 2005-10-20
Hm, I just checked their website again and it seems that their debs are indeed supposed to work with Ubuntu. Well, since it didn't work for you, just download the binary package on [http://xbgm.sourceforge.net/](http://xbgm.sourceforge.net/)

Of course you will still have to install mono and gtk# using apt.

---

### Post by matthias_k on 2005-10-20
Okay, forget what I said, I am getting the same errors with the deb packages. Just remove them and install from source, that worked for me:

1.  Install 'mono' and 'gtk-sharp2'
2.  Install the package 'mono-mcs'
3.  Download the source code from sourceforge
4.  Unpack and enter the src/ directory
5.  Run 'make'
6.  Run 'sudo mkdir -p /usr/share/xbgmsharp'
7.  Run 'sudo cp ./xbgmsharp.exe /usr/share/xbgmsharp'
8.  Unzip the attachment
9.  Copy 'xbgmsharp' to /usr/bin (must be root)
10. Run 'sudo chmod +x /usr/bin/xbgmsharp'
11. Copy xbgmsharp.desktop to ~/.local/share/applications

That should get you all set. An entry called "Xbox Game Manager" should show up under "Accessories" in the GNOME panel. You can also start it from the shell using 'xbgmsharp'. Feel free to ask if something doesn't work.

---

### Post by f76 on 2005-10-21
Yes u rock! i just ran it from the tmp catalog.. and it seems to be running..

thanx mr!

---

### Post by matthias_k on 2005-10-24
Anytime :)

---

