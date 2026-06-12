---
title: "install of new flash player"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arvadawest on 2008-11-29
Good day to you all, we are trying to install the new flash player and we get the error message (this is after we have downloaded and clicked on the file called (install_flash_player_10_linux.deb))

Here's the error message:

Error: Dependency is not satisfiable: libcairo2

We tried (we are newbies still learning) to login as "su" but we get a failure even though we are administrators on this system.

Thanks for your help.  We need to find somebody to tutor us or some online tutoring because we are learning at a snails pace.  Thank you.  -aw

---

### Post by gbrainin on 2008-11-29
Two things:

First, rather than attempting to install the flash player by itself, you may want to install the meta-package of "restricted extras," which includes the flash player and other similar "non-free" extensions.  You install this by using the Synaptic Package Manager (System menu -> Administration -> Synaptic Package Manager) and installing the "ubuntu-restricted-extras" package.

You may need to enable the alternate depositories to make this package accessible.

If you don't want the other items, you can similarly use the package manager to install just the flash player.  In general, if you can install something via the package manager, I would recommend going that way rather than getting a *.deb package, if for no other reason than it's easier to maintain.

Second, Ubuntu does not, by default, have a root/superuser account enabled.  The things which you would do as su are done by prepending the "sudo" command.  There are several explanations why this system is considered better, or at least more secure; in any case, it's the default.

---

### Post by arvadawest on 2009-02-13
Hi can anyone help?  I'm a newbie to this and thought it would be easy.  I cannot install the latest version of flash.  I've been out on medical leave.  I find it frustrating as to why installing the latest version of flash doesn't work.  Thank you all.  -aw

---

### Post by ugm6hr on 2009-02-13
What version of Ubuntu are you running?

In case you haven't considered it - is Flash 9 not good enough?

EDIT: Just seen your other post - you are using 7.10

It is possible that Flash 10 requires a newer version of libcairo2 than Gutsy has available

Nevertheless - try:

```
sudo apt-get install libcairo2
```

Then try again.

---

### Post by arvadawest on 2009-02-22
> **ugm6hr said:**
> What version of Ubuntu are you running?

In case you haven't considered it - is Flash 9 not good enough?

EDIT: Just seen your other post - you are using 7.10

It is possible that Flash 10 requires a newer version of libcairo2 than Gutsy has available

Nevertheless - try:

```
sudo apt-get install libcairo2
```

Then try again.

Hello and thank you.  I do have the lastet libcairo, but still not sure where to go and installed the latest flash.  I believe we have flash 8.  Thanks for your help.  Due to medical issues, it makes it difficult to respond right away.  Any help would be appreciated.  I am a newbie.  Thanks.  -aw

---

### Post by arvadawest on 2009-02-22
I located this link:

[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

but not sure.  This is all so confusing as to how to install the latest flash.  We are running 7.10.

This is maybe is a bit frustrating is on windows, it's easier to install, but the line command are new to me (us).  Thanks to all again :)  -aw

---

### Post by ugm6hr on 2009-02-22
Exactly what happens when you follow the instructions?

Copy and paste here.

Also:

```
sudo apt-get install -f
```

---

### Post by arvadawest on 2009-02-22
> **ugm6hr said:**
> Exactly what happens when you follow the instructions?

Copy and paste here.

Also:

```
sudo apt-get install -f
```

We hope you are being kind?

There were multiple instructions to the link we provided so how are we supposed to know which one?

---

### Post by arvadawest on 2009-02-22
> **ugm6hr said:**
> Exactly what happens when you follow the instructions?

Copy and paste here.

Also:

```
sudo apt-get install -f
```

Ok, here is what we did...

Went to the instructions, right??
Then we followed these steps--
Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

but instead we loaded to /home/sector0/downloads area
we then typed--  ./flashplayer-installer
then it said--

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 10 now, press ENTER.

we hit "enter"

then it said--

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/sector0/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

And it still didn't work.

What we fail to understand is why should this be/could this be so difficult?  Can anyone help us?  Thank you.  Please respond professionally and know that we are newbies and I am disabled so it's difficult.  Thank you.  -aw

---

### Post by arvadawest on 2009-02-22
> **arvadawest said:**
> Ok, here is what we did...

Went to the instructions, right??
Then we followed these steps--
Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

but instead we loaded to /home/sector0/downloads area
we then typed--  ./flashplayer-installer
then it said--

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 10 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 10 now, press ENTER.

we hit "enter"

then it said--

Adobe Flash Player 10 will be installed in the following directory:

Mozilla installation directory  = /home/sector0/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

And it still didn't work.

What we fail to understand is why should this be/could this be so difficult?  Can anyone help us?  Thank you.  Please respond professionally and know that we are newbies and I am disabled so it's difficult.  Thank you.  -aw

***************
Also, here is what we got when we tried to install the .deb version we have the lastest liabcairo2 or something like that--

sector0@:~/downloads$ sudo dpkg --install install_flash_player_10_linux.deb
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 120586 files and directories currently installed.)
Unpacking adobe-flashplugin (from install_flash_player_10_linux.deb) ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 adobe-flashplugin depends on libnss3-1d; however:
  Package libnss3-1d is not installed.
 adobe-flashplugin depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin
sector0@:~/downloads$

---

### Post by ugm6hr on 2009-02-23
> **arvadawest said:**
> dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libcairo2 (>= 1.6.0); however:
  Version of libcairo2 on system is 1.4.10-1ubuntu4.4.
 adobe-flashplugin depends on libnss3-1d; however:
  Package libnss3-1d is not installed.
 adobe-flashplugin depends on libpango1.0-0 (>= 1.20.1); however:
  Version of libpango1.0-0 on system is 1.18.3-0ubuntu1.

This is why.

I can't remember why I thought libcairo2 was the problem - but it is.  As is libpango1.0-0.  The versions of these libraries in Gutsy are too old for Flash 10.

Gutsy will not be able to install this without serious installation of non-repository libraries (not recommended).  If you want a newer version of Flash, you'll need a newer version of Ubuntu.

Generally, a .deb is often a better option than .tar.gz for Ubuntu.  For Flash, it doesn't matter a great deal.

---

### Post by arvadawest on 2009-02-23
> **ugm6hr said:**
> This is why.

I can't remember why I thought libcairo2 was the problem - but it is.  As is libpango1.0-0.  The versions of these libraries in Gutsy are too old for Flash 10.

Gutsy will not be able to install this without serious installation of non-repository libraries (not recommended).  If you want a newer version of Flash, you'll need a newer version of Ubuntu.

Generally, a .deb is often a better option than .tar.gz for Ubuntu.  For Flash, it doesn't matter a great deal.

Thank you.  I had read another posting where someone had similar issues.  Would you recommend I update to 8.0.4 LTS or 8.10?  I really do not know the difference between the two, but I am very weak on line commands and have much to learn considering some major medical disabilities, but I'm trying really hard.  Any advice and "hand holding" would be so much appreciated and I want to offer my thanks to you and all those on this site.  -aw

---

