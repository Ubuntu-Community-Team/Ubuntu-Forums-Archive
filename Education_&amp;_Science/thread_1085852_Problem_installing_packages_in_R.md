---
title: "Problem installing packages in R"
date: 2009-03-03
forum: Education &amp; Science
---

### Post by sarahmander on 2009-03-03
Hi all-

I am working on an Intel MacBook, and I am trying to install the package Proxy in the program R. I just installed the newest version of XCode, but I am still getting the following message when I try to use the GUI to install this or any program:

==================================================
downloaded 34Kb

* Installing *source* package 'proxy' ...
** libs
** arch - i386

The downloaded packages are in
	/private/var/folders/GF/GFf1cNBZGFmcoJzQINUQf++++TI/-Tmp-/RtmpaZ7qck/downloaded_packages
** arch - ppc
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/i386/*: No such file or directory
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/ppc/*: No such file or directory
ERROR: compilation failed for package 'proxy'
** Removing '/Library/Frameworks/R.framework/Resources/library/proxy'

It says that the make command is not found, and make does not seem to work inside of terminal either.. but I just installed XCode. Why isn't it working? Will I have to reinstall R?

Thanks so much for any advice you can give!!
Sarah

---

### Post by earlycj5 on 2009-03-03
> **sarahmander said:**
> Hi all-

I am working on an Intel MacBook, and I am trying to install the package Proxy in the program R. I just installed the newest version of XCode, but I am still getting the following message when I try to use the GUI to install this or any program:

==================================================
downloaded 34Kb

* Installing *source* package 'proxy' ...
** libs
** arch - i386

The downloaded packages are in
	/private/var/folders/GF/GFf1cNBZGFmcoJzQINUQf++++TI/-Tmp-/RtmpaZ7qck/downloaded_packages
** arch - ppc
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/i386/*: No such file or directory
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/ppc/*: No such file or directory
ERROR: compilation failed for package 'proxy'
** Removing '/Library/Frameworks/R.framework/Resources/library/proxy'

It says that the make command is not found, and make does not seem to work inside of terminal either.. but I just installed XCode. Why isn't it working? Will I have to reinstall R?

Thanks so much for any advice you can give!!
Sarah

It sounds like you don't have Make installed.

You might try installing r-base-dev, that will cover alot of the dependencies you need to compile packages for R.  Be sure that you have make installed after that.

---

### Post by favilac on 2009-03-03
---------------------
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/i386/*: No such file or directory
/Library/Frameworks/R.framework/Resources/bin/SHLIB: line 122: make: command not found
chmod: /Library/Frameworks/R.framework/Resources/library/proxy/libs/ppc/*: No such file or directory
ERROR: compilation failed for package 'proxy'
** Removing '/Library/Frameworks/R.framework/Resources/library/proxy'
----------------------

That looks like the OS X enviroment.
Are you trying to install R on Ubuntu or on OSX?

---

### Post by NikoC on 2009-03-04
If you are running R under Mac OS, maker sure you download the correct package!

If you are using Ubuntu and the 'missing' make is the problem, type in a terminal:
sudo apt-get install make

For both operating you can always manually install packages via:
sudo R CMD INSTALL package.name

Cheers,

Niko

---

### Post by ahmatti on 2009-03-05
> **sarahmander said:**
> Hi all-

I am working on an Intel MacBook, and I am trying to install the package Proxy in the program R. I just installed the newest version of XCode, but I am still getting the following message when I try to use the GUI to install this or any program:

==================================================
downloaded 34Kb

* Installing *source* package 'proxy' ...
** libs
** arch - i386


Hi Sarah,
I guess you are running OSX, since you're talking about Xcode...  I'm not sure why your Mac is trying to install the source package, because for me the binary installs just fine (using install.packages('proxy')).

Try installing with R using:
install.packages('proxy',type='mac.binary')

OR

Download the proxy binary package [http://cran.r-project.org/bin/macosx/universal/contrib/r-release/proxy_0.4-1.tgz](http://cran.r-project.org/bin/macosx/universal/contrib/r-release/proxy_0.4-1.tgz) and run the command R CMD INSTALL proxy_0.4-1.tgz from the terminal.

---

