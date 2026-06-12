---
title: "How to package a simple application"
date: 2005-07-15
forum: Desktop Environments
---

### Post by Altmenorg on 2005-07-15
Debian package système is powerfull, but generating is quite a bit complicated.

Reading at debian's documentation on that point (60 pages...) can be discouraging for many.

The purpose of this documentation is to give the first keys to create a .deb file from sources.

You will certainly not be able to compile KDE or Koffice with this, but it might be okay for the most common apps you might have to compile.

To start, you MUST have a source package in .tar.gz format.
If you have downloaded sources in .tar.bz2, uncompress and recompress it with .tar.gz extension

We will take the exemple of a "hello-1.0.tar.gz" file

**_Before creating the package :_**

  * Check that you have this command working :
     ```
dh_make
```
     If not, install it with "sudo apt-get install dh-make"

  * First of all, work as "root", same than to compile an application :
     ```
sudo -s
```

  * Place the source package in a forlder and unzip/untar it folder "temp" :
     ```
mkdir temp
cp hello-1.0.tar.gz temp/
cd temp/
tar xzvf hello-1.0.tar.gz
```

     You should get : temp/hello-1.0/
     If the obtained folder is called for example "hello", rename it to "hello-1.0".
     The version number in the folder name is important.

  * go in the folder :
     ```
cd hello-1.0/
```

  * Then, use the command :
     ```
dh_make -e [email]your@emailadress.com[/email] -f ../hello-1.0.tar.gz
```

  * At that point, you are prompted to select the package type.
     s for "single" (most common apps...)
     m for multiple (for apps generating mani binaries, example : Transcode)
     l for library (no need to explain...)
     k for kernel package (never tried, and never will ^_^)

     In a simple case, type just "s", and let the program work...

     The package creation is then initialized, and a debian folder with several files 
     insidehas been created.
     Here are the files that it can be usefull to modify :
          -  control : Contains about all the important informations of the package
          -  copyright : Place a copyright (optionnal)
          -  changelog : Modify with the dhc command to add a changelog (optionnal
             can be added in the package description...)

  * Open the "control file" :
     ```
vim debian/control
```

     Then edit those lines :
          Section: <ad the section here>

          I have a problem with it, I have never been able to get the full section list 
          used.
          Note that you can put anything, but in order to maintain something clean, 
          you need to check on an already existing package and the same "source".
          I personnaly use "Kubuntu Package Service Menu" to look for those infos and
          I look in /var/cache/apt/archives... If you have any help on that point, thanks ^_^

          Maintainer: replace "root" by your name, in complement to your email address

          Description: <you can add here a 60 characters little desc for the package>

          Concerning the full description, all you have to know is the following :
               - EVERY line has to start with a SPACE
               - Tu put a blank line write " ." (space + dot)

  * Preparation of the package is over...

**_Let's create the package :_**

  * In the rep "hello-1.0", type this (the magic) command :
     [/code]dpgk-buildpackage[/code]

  * That's all ;) If you don't have any compilation problem, you should get that in the "temp" folder :
     -  hello_1.0-1.diff.gz
     -  hello_1.0-1.dsc
     -  hello_1.0-1_i386.changes
     -  hello_1.0-1_i386.deb
     -  hello_1.0.orig.tar.gz

Hope that will help ;)

Note : Major problem you might meet (every problem I had in fact...) are compilations problem only...

---

### Post by geearf on 2005-07-15
Hello,

thanks for this tuto, but i have a question, is this very different from using checkinstall ?

Thanks,

---

### Post by Altmenorg on 2005-07-15
I don't know in fact what is the real difference with the two methods (never used checkinstall...)
I'm gonna check...

Edit : Here is a question. Can you, while makine a "./configure && make && checkinstall" specify the package's informations (author, description etc...) ?

---

### Post by skyboy on 2005-07-15
Yes, I've just made a debian version of Transcode and ffmpeg(shared_library) only with checkinstall.
wonder what is the difference

---

### Post by Altmenorg on 2005-07-15
[QUOTE=skyboy]Yes, I've just made a debian version of Transcode and ffmpeg(shared_library) only with checkinstall.
wonder what is the difference[/QUOTE]
 According to what I can read, packages build with checkinstall are not fully compliant to the debian standard, and miss a few informations inside.

Anyway, I've just read the manpage and I didn't find any way to add additionnal informations to the package (maintainer, desc, category etc...)

So it seems to be a good way to compile "home packages", but not to be put on a repo for example...

dh_make method isn't more complicated neither longer if you don't edit the "control" file for example, and allow more possibility if you want to make clean packages...

---

### Post by geearf on 2005-07-15
you can add what you want with checkinstall, it will ask you the information needed (or not) just after compiling.

---

### Post by Altmenorg on 2005-07-15
Okay ;)
As I said, I don't know Checkinstall at all.
I just read that globally, it was safier to use dh_make, which was building more "compliant packages".
Maybe there are no big differences ;)

Last question : Does checkinstall generates the .dsc, .orig.tar.gz and .diff.gz files ?

---

### Post by elsewhere on 2005-07-15
You're correct, I don't think checkinstall would necessarily be the best tool for building repo packages.  But it is a brilliant tool for installing apps from source while maintaining package manageability. I use it anytime I install software from a source like kde-apps.org etc.

Just my $0.02...

Cheers,
KV

---

### Post by geearf on 2005-07-15
[QUOTE=Altmenorg]Okay ;)
As I said, I don't know Checkinstall at all.
I just read that globally, it was safier to use dh_make, which was building more "compliant packages".
Maybe there are no big differences ;)

Last question : Does checkinstall generates the .dsc, .orig.tar.gz and .diff.gz files ?[/QUOTE]
Hmm it doesn't i think, but i don't know if you can give the .deb to a friend with the one generated by checkinstall (maybe not ?).

---

### Post by Tamir on 2005-07-15
Cool! but I think it should be more, like - how to config the copyright, changlog, rules.

---

### Post by Altmenorg on 2005-07-15
[QUOTE=geearf]Hmm it doesn't i think, but i don't know if you can give the .deb to a friend with the one generated by checkinstall (maybe not ?).[/QUOTE]
 You can give it to a friend, it'll work, but without the .dsc file, it will not work on a repo (note that this file can be created manually, but it is not very confortable). This file is used to create the packages index.

The two .gz files are necessary for the deb-src repos...

---

### Post by geearf on 2005-07-15
oh ok

---

### Post by Altmenorg on 2005-07-15
[QUOTE=Tamir]Cool! but I think it should be more, like - how to config the copyright, changlog, rules.[/QUOTE]
 I said it was not exhaustive ;)
Maybe in the future I will ad more informations for the other options !

---

### Post by martinjh99 on 2005-07-22
Nice one - packaged a couple of styles and windowdecs into my own repo!!

In order to compile the other style I have I need to pass a parameter to the configure script.  How do I do that and build the package at the same time?

---

### Post by Altmenorg on 2005-07-22
[QUOTE=martinjh99]Nice one - packaged a couple of styles and windowdecs into my own repo!!

In order to compile the other style I have I need to pass a parameter to the configure script.  How do I do that and build the package at the same time?[/QUOTE]
 Because I discovered yesterday technical thing I didn't thought about concerning the dependencies on a repo for example, I had to write a script to correct and automate the packaging...

I need to improve the erreor messages gesture, but at that point it works fine, and everything is fully automated, just launch, put your name, email address, description, and you get a .deb fully compliant with repo requirements (deps compatible with a from scratch Kubuntu installation, ~ added in version to improve the update possibilities while Kubuntu will be in breezy etc...)

I modify it in the next hour and will add it here...

Edit : Here is the script.
To you it, you have to install "php-cli", then put it in /usr/bin and chmod it to 755.

---

### Post by McQuaid on 2005-07-22
In modifying the control file you don't mention dealing with depends, pre depends suggests etc.  I know this are not required but isn't that what apt depends on to ensure that all dependencies are installed?

Also, I like to know how to make the .desktop entry for kde/gnome menus and specifying an icon.

Thanks for this great start, just wondering if some areas of this howto can be expanded.

---

### Post by az on 2005-07-22
The forums should hold a contest for the best "post-install" package.

Like the scripts that were floating around just after the Hoary release, but in deb form.  Maybe, we could even get the package winner's deb into the universe repo....


The spec:

- Would have to apply to Breezy.
- Install Java like the flashplayer-nonfree package install flash.  (If this is legal.  I asked MOTU and am wainting)
-Depend on Gstreamer plugins (codecs)
-Depend on flashplayer-nonfree
-Whatever else people want to get out of ubuntu, but is not in main....
- Be reconfigurable to do or undo stuff.


What do you think?

---

### Post by Altmenorg on 2005-07-22
Exact, I don't explain anything regarding the deps...

But in fact dpkg-buildpackage uses dh_shlibdeps which is enough to ensure that strictly required dependencies are present in the control file.

You can try and you will see that the "Depends" section is filled :)

Pre depends, suggests etc... have to be added manually (to what I know), and the aim for that HOWTO whasn't to be exhaustive and to form experts packagers (you have a 40 pages debian manual if you want all the details and possibilities...)
It was more to give a little idea on tha way to create a correct package, simply, than giving all details that you can find in many, many places on the web...

The problem with linux docs on the web is that most generally very complete, which is a good thing  in theory, but a begginer gets lost reading the 45 options while only 2 or 3 are  commonly used...

---

### Post by martinjh99 on 2005-07-23
[QUOTE=Altmenorg]The problem with linux docs on the web is that most generally very complete, which is a good thing  in theory, but a begginer gets lost reading the 45 options while only 2 or 3 are  commonly used...[/QUOTE]

True - Until I saw this HOWTO I ws really put off by reading the Debian New maintainers guide... ;)

Thanks for the HOWTO anyway...

---

### Post by esj on 2005-08-09
thank you for posting this how-to.  I am curious however how does one set up an application so that it can be configured as part of the install?  Or is that something best handled by a separate program in the package?

---

### Post by Altmenorg on 2005-08-10
[QUOTE=esj]thank you for posting this how-to.  I am curious however how does one set up an application so that it can be configured as part of the install?  Or is that something best handled by a separate program in the package?[/QUOTE]
 Deb packages offer the availability to had a configuration module/script/program that runs during the package installation, which is something that isn't supported in RPM's in my memory.
But I haven't practice this technique at the moment, and according to what I've heard, setting this isn't an easy job ;)

---

### Post by gingermark on 2005-08-10
Can anyone quickly clarify how to to close the control file when you've finished making the changes. I tried ctrl+c and it said "recording" at the bottom, but then doesn't seem to do anything else.

---

### Post by sas on 2005-08-17
[QUOTE=gingermark]Can anyone quickly clarify how to to close the control file when you've finished making the changes. I tried ctrl+c and it said "recording" at the bottom, but then doesn't seem to do anything else.[/QUOTE]
 press escape (this puts you into command mode) then type wq and then return.

There's a whole lot more you can learn about vi......but that's a seperate tutorial

---

### Post by derrick81787 on 2008-02-07
I know that no one has posted in this thread in a while, but I was wondering:

Is dpgk-buildpackage supposed to compile the package as well, or should I have to run 'make' manually?  If it is supposed to do it itself, then I am having problems...

---

