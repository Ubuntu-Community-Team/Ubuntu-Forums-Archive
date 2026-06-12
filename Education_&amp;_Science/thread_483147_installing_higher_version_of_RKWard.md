---
title: "installing higher version of RKWard"
date: 2007-06-24
forum: Education &amp; Science
---

### Post by edoviak on 2007-06-24
Ubuntu's repositories provide RKWard 0.4.2, but I would like the most recent release 0.4.7a because I would like to check out the SPSS plugins. 

I successfully installed 0.4.6 on Kubuntu Feisty by downloading the package from [**[COLOR="Navy"]the website's[/COLOR]**]("http://rkward.sourceforge.net/") download page and then running the command:
[B]
# dpkg -i rkward_0.4.6-1_i386.deb
[/B]
Prior to that success however, I broke the RKWard package by installing the 0.4.7a deb. Fortunately, it was easy to remove and reinstall with apt-get. 

Has anyone had any success in installing the latest version of RKWard?

Thanks,
- Eric
 
ps: For those of you who aren't familiar ... RKWard is a front-end for the R statistical programming language. It provides the console, the script editor, a very clever data editor and a GUI for routine tasks (producing descriptive statistics, correlation matrix, etc.) The best part is that one of the goals of the RKWard project is to provide seamless integration with an office-suite.

---

### Post by HotShotDJ on 2007-06-24
edoviak: I just tried to install 0.47.a from the deb provided at the linked site.  No joy was had.  That version (the sid deb) is not compatible with Ubuntu (for reasons unknown to me).  I'll see what I can find because, like you, I am intrigued by the many new functions introduced in 0.47!

---

### Post by edoviak on 2007-06-24
Well, there's one way that we could get RKWard 0.4.7a. We could enable Debian's Sid repository and do one huge upgrade. I don't think we'd like the results however. More than a few packages would be broken in the process (see quote below).

I managed to install RKWard 0.4.7a on another computer that runs Debian Etch. Unfortunately, that computer doesn't have enough RAM for data analysis. 

Here's how I installed RKWard 0.4.7a on that computer. (Standard Debian Warning: If you break it, you get to keep the pieces!).

First, I enabled the Debian unstable repository and attempted to install RKWard. The install was not successful and in the process, I uninstalled util-linux and tzdata. The following sequential steps enabled me to install RKWard 0.4.7a:

[LIST=1]
[*]install libgnome2-perl
[*]install getopt
[*]install util-linux (and tzdata)
[*]install php4-cli and php5-cli
[*]install rkward
[/LIST]

Like I said, that worked on Debian Etch, which leaves the problem: How do we do it on Kubuntu Feisty? The following quote contains (some) of the text output from a simulated install of RKWard 0.4.7a using the Debian Unstable repository on Kubuntu Feisty.

> 
# apt-get install -s rkward
Reading package lists... Done
Building dependency tree
Reading state information... Done

The following extra packages will be installed:
  gcc-4.2-base kdelibs-data kdelibs4c2a libart-2.0-2 libc6 libc6-dev libc6-i686 libgcc1 libgnutls13 libjasper1 libkeyutils1 libkrb53
  liblzo2-2 libopencdk8 libstdc++6 libxml2 menu-xdg r-base-core tzdata util-linux

The following NEW packages will be installed:
  gcc-4.2-base libjasper1 libkeyutils1 liblzo2-2 menu-xdg

The following packages will be upgraded:
  kdelibs-data kdelibs4c2a libart-2.0-2 libc6 libc6-dev libc6-i686 libgcc1 libgnutls13 libkrb53 libopencdk8 libstdc++6 libxml2 r-base-core
  rkward tzdata util-linux

16 upgraded, 5 newly installed, 0 to remove and 652 not upgraded.


Let me know if this helps at all,
- Eric

---

### Post by euler_fan on 2007-06-25
Have you tried downloading the source and compiling locally? Not ideal, I know, but a possibility.

Another is that within R, once you have it installed, you can install packages via the R repos. No, they're not the Ubuntu repos, but they will be up to date with the latest "stable" release of a package and reliable from what I have seen. I believe the command is install.packages. You can find more in the Intro to R and also the Administration manual. I have had no problems getting packages to work that I have installed that way. Then again, I haven't tried installing the latest version of RKWard :)

Good luck.

---

### Post by edoviak on 2007-06-25
> **euler_fan said:**
> Have you tried downloading the source and compiling locally? Not ideal, I know, but a possibility.

I've thought of that, but I've never compiled anything from source. I guess it's time to learn. After I read up on the subject, I'll give it a try and keep you posted on my progress.

> **euler_fan said:**
> Another is that within R, once you have it installed, you can install packages via the R repos. No, they're not the Ubuntu repos, but they will be up to date with the latest "stable" release of a package and reliable from what I have seen.

I already have the R packages that I need. What I want to explore is the SPSS plugins that are specific to RKWard.

Thanks for the suggestions! :D
- Eric

---

### Post by euler_fan on 2007-06-26
Is the version of RKWard in the R repos not the one you want? It is my impression you have been grabbing the .deb files from the precompiled Ubuntu packages library on the CRAN ftp site.

EDIT: Another question: it sounds like the capabilities you want are a built in part of the latest version of RKWard. So if that's true how do you have the packages you need?

If I'm wrong and you have been using install.packages() to get your packages installed, then why not download the source .tar.gz file and let R do the compiling for you (also using install.packages() set up to install from a local repository)? R has a built in capability to install R packages from source stored online or locally without all the usual fuss of doing an install from source.

I hope that helps you out. If you are having questions about using the install.packages function, please post them.

Good Luck.

---

### Post by edoviak on 2007-06-26
Sorry for the confusion and thank you for your patience.

The trouble here is that I'm not exactly sure what I want. All I know is that the [COLOR="Navy"]**[RKWard website]("http://rkward.sourceforge.net/")**[/COLOR] says that the latest version (0.4.7a) has some plugins that enable you to import from SPSS. Most of the people I work with use SPSS :( , so SPSS compatibility would be a very convenient feature for me to have.

In other words, these features seem to be features of RKWard (and not R), When I wrote that "I have the R packages that I need," I meant that I have the R packages that I need. What I don't have is the RKWard features that I want. The SPSS compatibility features are in RKWard 0.4.7a, whereas the version of RKWard in the Ubuntu repositories is RKWard 0.4.2.

RKWard 0.4.7a also seems to depend on R 2.5, so I'll try installing R 2.5 this weekend and then I'll see if I can compile the latest version of RKWard. 

Do you know of any good websites entitled: "A complete beginner's guide to compiling from source" ??

Thanks again,
- Eric

---

### Post by UbuWu on 2007-06-27
> **edoviak said:**
> 
RKWard 0.4.7a also seems to depend on R 2.5, so I'll try installing R 2.5 this weekend and then I'll see if I can compile the latest version of RKWard. 

Do you know of any good websites entitled: "A complete beginner's guide to compiling from source" ??

Thanks again,
- Eric

These are both in Gutsy, so you could try installing those from the gutsy repo's.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fr%2Fr-base%2Fr-base-core_2.5.1~20070618-1_i386.deb&md5sum=58e208e568b98aeeb40c9699e3fb1944&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fr%2Fr-base%2Fr-base-core_2.5.1~20070618-1_i386.deb&md5sum=58e208e568b98aeeb40c9699e3fb1944&arch=i386&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fr%2Frkward%2Frkward_0.4.7a-1_i386.deb&md5sum=7705ab0e239b55414035742334731373&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fr%2Frkward%2Frkward_0.4.7a-1_i386.deb&md5sum=7705ab0e239b55414035742334731373&arch=i386&type=main)

---

### Post by euler_fan on 2007-06-27
They have instructions posted on their website here: [http://rkward.sourceforge.net/?content=faq#n22]("http://rkward.sourceforge.net/?content=faq#n22")

They are more or less the same instructions you can get anywhere: resolve dependencies, download file, decompress to its own folder, configure, make, and make install.

---

### Post by edoviak on 2007-06-28
> **UbuWu said:**
> These are both in Gutsy, so you could try installing those from the gutsy repo's.

> **euler_fan said:**
> They have instructions posted on their website here:

Thanks guys! Looks like I have a project for the weekend. I appreciate your help and will keep you posted.
- Eric

---

### Post by edoviak on 2007-06-30
NOTA BENE: I wrote this message at 3:43 am and was quite tired. Things look a little different in the morning light. See "correction" below.

Thanks to the help of Euler_Fan and UbuWu, I successfully installed RKWard 0.4.7a

Here are the brutal details:

I started by trying to compile from source, but I didn't succeed because I couldn't install the **libqt3-mt-dev** package which depends on packages that depend on the older versions of two packages that Ubuntu upgraded (**libpng12-0** and **libfreetype6**).

Next I tried to install from the Gutsy repository. That worked too well. I upgraded to KDE 3.5.7 and quickly ran into this annoying: "Could not find mime type application/octet-stream" every time I opened a KDE application (with the suspicious exception of RKWard). I also lost the "System Settings" menu in the K Menu.

Fortunately, all of the "System Settings" can be accessed from the enormous "Lost & Found" menu that suddenly appeared in the K Menu.

Resolving the octet-stream mime-type was very difficult. After doing some internet searches, it appears that what solves the problem for one person, doesn't necessarily solve it for someone else. Here's what worked for me: 

To resolve the problem I opened the "File Associations" menu, added *.bin *.class *.dms *.exe *.lha and *.lzh to the filename patterns, set the "Description" to "octet-stream" and made "octet-stream" the first and only application in "Application Preference Order."

I also (as root) modified ** /home/eric/.kde/share/mimelnk/application/octet-stream.desktop ** to:
[B]
[Desktop Entry]
Comment=octet-stream
Hidden=false
MimeType=application/octet-stream
Icon=
Patterns=*.bin;*.class;*.dms;*.exe;*.lha;*.lzh
[/B]
After restarting the computer, the octet-stream problem disappeared.

As for RKWard ... Well, let's start with the good news: There are features to help you import SPSS files and it has a snazzy new welcome screen. Now the bad news: The "Edit," "View" and "Run" menus no longer function. Oops !!!

In summary, this was way too much work for too little benefit. Upgrade if you like, but you're better off waiting for the next release.

- Eric

CORRECTION: Things look a little different after a few hours of sleep. The "Edit," "View" and "Run" function properly. Depending on what you are trying to do they sometimes disappear. For example, there's nothing to run when you're in the help menu.

I'm going to spend some time playing with my new toy. Hopefully, all the effort will have been worth it.

---

