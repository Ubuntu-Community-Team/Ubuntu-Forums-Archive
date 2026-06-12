---
title: "Whatever happened to GPG?"
date: 2006-02-17
forum: Desktop Environments
---

### Post by thesnowysoviet on 2006-02-17
GPG, kgpg, gnupg, gpgme... only the last two are in the manifest when I check Adept, and even though they're flagged as "installed" they won't run.

What is Ubuntu's preferred PGP-esque encryption tool, and where can I get it?

---

### Post by GeneralZod on 2006-02-17
kgpg works fine here - try running it from the command-line and see if any errors are reported.  Or did you say that you can't find kgpg in the repos? If so, post your sources.list here, or use Synaptic :)

Also, if you are using KMail, check out this thread, especially Jon V's HOWTO:

[http://ubuntuforums.org/showthread.php?t=103699&highlight=kmail+gpg](http://ubuntuforums.org/showthread.php?t=103699&highlight=kmail+gpg)

---

### Post by mgor on 2006-02-17
afaik gpg = gnupg.

[http://www.gnulinuxclub.org/index.php?option=com_content&task=view&id=208&Itemid=31](http://www.gnulinuxclub.org/index.php?option=com_content&task=view&id=208&Itemid=31) might be helpful.

---

### Post by ryuko2002 on 2006-02-17
When i switched from Kubuntu i wanted a nice looking application to substitute kpgp and the answer was seahorse ;)

---

### Post by sweeney276 on 2006-02-18
The open source alternative to the Windows-only program Pretty Good Privacy (PGP) is the Gnu Privacy Guard, the name of which is most often shortened to gnupg or GPG. However, the developers install the package on the repositories as gnupg and you can see their site at [http://www.gnupg.org](http://www.gnupg.org) where other gnupg related software is to be found. 

The point to remember is that gnupg gives to other programs added facilities related to encryption when used as a plug-in, or be used on its own as a standalone program. Therefore what "is best" for you depends upon what you require. If you just want a GUI to manipulate your keyrings, there are a number around, such as Kgpg, Seahorse, Gpgp, and GPA (the Gnu Privacy Assistant). 

However, most people want encryption or verification of emails, and most include a "hook" to gnupg to use it. One exception to this is Mozilla-Thunderbird, which requires the extension Enigmail to operate the "hook" with gnupg. Its really a matter of which MUA (email program) you prefer. Its worth pointing out here that gnupg does NOT provide PGPMIME facilities. It is entirely the job of the MUA to provide these, linking with gnupg as it does, so if this is a particular concern of yours, try a number of MUAs to find out what is best for you. 

My favourite GUI interface to gnupg is Kgpg although I have to confess I generall use the command line. I prefer Kmail to Thunderbird so I use Kmail as my main MUA. The alternative one I use is Sylpheed-Claws. I have to say that the Enigmail extension for Thunderbird is well-maintained, and there is an active user list you can join at [http://enigmail.mozdev.org](http://enigmail.mozdev.org) 

If you want to join the gnupg email list, a link is available on the website. However, if you are a newb at public-key encryption, you might like to join the PGP-Basics yahoogroup. Replies like RTFM are outlawed and the Moderators there really try to help everyone. It covers gnupg as well as PGP, but it is a bit Windows-centric. Still there are very helpful Linux users who are part of the Help Team. You can join it at: [http://groups.yahoo.com/group/PGP-Basics/](http://groups.yahoo.com/group/PGP-Basics/)

To test whether gnupg is working properly on your system, type in at a console:

gpg --help

If you see something starting like this:

gpg (GnuPG) 1.4.1
Copyright (C) 2005 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512
Compression: Uncompressed, ZIP, ZLIB, BZIP2

you'll know its installed directly.  However, you will have to set up a gpg.conf file in your home /.gnupg directory to manipulate how you want the defaults to be set up.  Hope this helps!

---

### Post by thesnowysoviet on 2006-02-27
[QUOTE=sweeney276]wordswordswords[/QUOTE]

I know.  I'd prefer a GUI-based app - such as kgpg - over a command-line based app - such as gpg, which works - just on principle.  I cannot, however, find the package.  Likewise for any dependencies and libraries for video playback, but that's another story... Adept really isn't doing anything for me anymore.  Synaptic doesn't return anything either.  The contents of /etc/apt/sources.list:

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main


Those last two are for VLC, which didn't work anyway.  Grr.  Still better than Gentoo, though.  Damn you, Gentoo!

---

