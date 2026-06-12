---
title: "ArgoUML"
date: 2009-05-14
forum: Desktop Environments
---

### Post by faldore on 2009-05-14
Does anyone know why there is no package for ArgoUML?  Were there some politicks or something?  (I'm curious)  I see that debian had the source at some point, then got rid of it, and it never graduated past unstable.

But ArgoUML is way better than Umbrello. (and Dia does not compete on UML really) 

Since there's no package I am forced to run it from a java webstart link.

The problem with running it from a java webstart link, is that I don't get file associations.  (you can't pass arguments to a webstart application)  So, I can't double-click my .zargo and have it open in ArgoUML, as I would be able to if there were a package for it.

FYI, One thing about ArgoUML - you have to install the 32-bit Java, because it doesn't work on 64-bit.  (Weird..)  

So the command line for running it is:
```
/usr/lib/jvm/ia32-java-1.5.0-sun/bin/javaws http://argouml-downloads.tigris.org/jws/argouml-0.26.2.jnlp
```

Anyway, I ramble, my point is, I would like to get ArgoUML installed on my Ubuntu, as a full fledged application, with file associations and all.  Despite the fact that there's no package for it.  Anyone know how to do it?

---

### Post by Locutus_of_Borg on 2009-05-14
try to compile it from this source: [https://launchpad.net/ubuntu/feisty/+source/argouml/0.19.6-2.1/+files/argouml_0.19.6.orig.tar.gz](https://launchpad.net/ubuntu/feisty/+source/argouml/0.19.6-2.1/+files/argouml_0.19.6.orig.tar.gz)

---

### Post by faldore on 2009-05-14
So old...  Feisty?

---

### Post by faldore on 2009-05-14
I saw there was Intrepid too, but same version of ArgoUML (0.19.6)
[https://launchpad.net/ubuntu/intrepid/+source/argouml/]("https://launchpad.net/ubuntu/intrepid/+source/argouml/")

---

### Post by Locutus_of_Borg on 2009-05-14
> **faldore said:**
> So old...  Feisty?
source is source, if you can find a more recent version of the programs source, use that

---

### Post by Brandon Williams on 2009-05-14
Well, it's Java, so there's no need to compile from source. Just download ArgoUML-0.28.tar.gz, decompress it into your ~/bin/ directory, and then create a symlink to argouml.sh in ~/bin/: '$ ln -s $HOME/bin/argouml-0.28/argouml.sh $HOME/bin/argouml'. Now, you will be able to run the app just by executing argouml.

[This documentation](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-0.html.en) provides explanations of how to add a mime type and an application association for the type.

---

### Post by faldore on 2009-05-18
Thank you for the tip.

I got it to work.

It's unfortunate that it was this difficult.

---

### Post by tfmorris on 2009-05-18
I haven't tried it, but there is a packaged version at

  [http://www.getdeb.net/app/ArgoUML](http://www.getdeb.net/app/ArgoUML)

---

### Post by pooja on 2009-10-24
Hi everybody,
I have to use ArgoUML as part of a university course. I'm having some trouble installing the source code in Ubuntu 9.04.
This is what I've done so far:
[LIST=1]
[*]downloaded the ArgoUML-0.28.1.tar.gz from their website in **/home/pooja/**
[*]from terminal, untarrred the tarball file [FONT="Courier New"]tar -zxvf ArgoUML-0.28.1.tar.gz[/FONT]
[*]entered the directory created when extracting the tar.gz file
[*]**configure**
[*]**make**
[*]**make install**
[/LIST]

At this point the Terminal returns the following message:
> Warning: tclStubInit.c may be out of date.
Developers may want to run "make genstubs" to regenerate.
This warning can be safely ignored, do not report as a bug!
Installing libtcl8.4.so to /usr/local/lib/
cp: cannot create regular file `/usr/local/lib/#inst.26845#': Permission denied
mv: cannot stat `/usr/local/lib/#inst.26845#': No such file or directory
chmod: cannot access `/usr/local/lib/libtcl8.4.so': No such file or directory
make: *** [install-binaries] Error 1
pooja@Ubuntu-LAPTOP:~/argouml-0.28.1$ 

What does it mean? Where am I going wrong? How do I actually run the program? Just type argouml in the Terminal doesn't work...help me please.

---

### Post by pooja on 2009-10-24
I tried typing [FONT="Courier New"]sudo make install[/FONT] then giving in my password.
This time the system accepted the command and went on installing the executable. Still when I write [FONT="Courier New"]$ argouml[/FONT], it doesn't recognize the command.

This is what it gave back once I typed in my user password:
> Installing libtcl8.4.so to /usr/local/lib/
Installing tclsh as /usr/local/bin/tclsh8.4
Installing tclConfig.sh to /usr/local/lib/
Installing libtclstub8.4.a to /usr/local/lib/
Making directory /usr/local/lib/tcl8.4
Making directory /usr/local/lib/tcl8.4/http2.5
Making directory /usr/local/lib/tcl8.4/http1.0
Making directory /usr/local/lib/tcl8.4/opt0.4
Making directory /usr/local/lib/tcl8.4/encoding
Making directory /usr/local/lib/tcl8.4/msgcat1.3
Making directory /usr/local/lib/tcl8.4/tcltest2.2
Installing header files
Installing library files to /usr/local/lib/tcl8.4
Installing library http1.0 directory
Installing library http2.5 directory
Installing library opt0.4 directory
Installing library msgcat1.3 directory
Installing library tcltest2.2 directory
Installing library encoding directory
Making directory /usr/local/share/man/man1
Making directory /usr/local/share/man/man3
Making directory /usr/local/share/man/mann
Installing and cross-linking top-level (.1) docs
Installing and cross-linking C API (.3) docs
Installing and cross-linking command (.n) docs
pooja@Ubuntu-LAPTOP:~/argouml-0.28.1$

So what do I do now to start the program?

---

### Post by tfmorris on 2009-10-24
I'm not sure what you built/installed, but if I had to guess, I'd say it was Tcl.  It certainly wasn't ArgoUML.

As was stated earlier in the thread, ArgoUML is a Java app, so it doesn't need to be built.  Just download it and run it (or run the Java WebStart version directly [http://argouml-downloads.tigris.org/jws/argouml-latest-stable.jnlp](http://argouml-downloads.tigris.org/jws/argouml-latest-stable.jnlp)).

Tom

---

### Post by pooja on 2009-10-24
Oh great! I've wasted an entire afternoon doing something useless! Now, how do I undo the mess? :mad:

Meanwhile I created a launcher for Argo_UML in the Desktop. I linked it up to the [FONT="Courier New"]argouml.sh[/FONT] script contained in the extracted directory [FONT="Courier New"] /home/pooja/argouml-0.28.1[/FONT]. When I need it I just double click the launcher, wait a couple of seconds and Argo's splash screen appears. 

I guess the problem's solved. About that [FONT="Courier New"]tcl package[/FONT] you were mentioning in your post, I don't know whether I should remove it 'cause last week I have installed NS-2 and it uses tcl language, so I should perhaps just let things be as they are. Should I?

---

### Post by maxpolk on 2012-07-30
> **Brandon Williams said:**
> ... [This documentation]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-0.html.en") provides explanations of how to add a mime type and an application association for the type.

For those wanting step-by-step, unpack to ~/usr.

Create file ~/.local/share/applications/argouml.desktop (replace LOGIN with home dir):[INDENT][Desktop Entry]
Version=1.0
Type=Application
Name=ArgoUML
GenericName=UML Editor
Comment=UML modeling tool
Exec=/home/LOGIN/usr/argouml-0.34/argouml.sh %U
Icon=argouml
Terminal=false
Categories=Development;
StartupNotify=true
MimeType=application/x-zip;application/zip;
[/INDENT]Copy the icon file (and rename to match Icon= above):[INDENT]cp ~/usr/argouml-0.34/icon/ArgoIcon128x128.png ~/.local/share/icons/argouml.png
[/INDENT]Run:[INDENT]update-desktop-database ~/.local/share/applications
[/INDENT]Log out and login again.  Open file manager, right click on .zargo file, it should show "Open with ArgoUML" with the nice icon.

If you installed elsewhere, replace all /home/LOGIN/usr or ~/usr above to the parent directory of where you unpacked it.

---

### Post by wildmanne39 on 2012-07-30
Hi, please do not create duplicate threads it dilutes the communities efforts.
Thanks

---

