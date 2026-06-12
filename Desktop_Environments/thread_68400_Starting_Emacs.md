---
title: "Starting Emacs"
date: 2005-09-23
forum: Desktop Environments
---

### Post by CaptainMorgan on 2005-09-23
Hi,

I just installed Ubuntu and I love it. I need to run Emacs but I can't figure out how. At the terminal I enter emacs and I get bashed. I navigated to find the folder labelled emacs in /etc/emacs/site-start.d/50dictionaries-common.el 

Where do I go from here?

Thank you

---

### Post by frodon on 2005-09-23
to install emacs (not installed after a fresh install) use this command : ```
sudo apt-get install emacs
```To use emacs type in a terminal :```
 emacs file_path
```

---

### Post by CaptainMorgan on 2005-09-23
Excellent. 


Thanks! 


 :)

---

### Post by STINGRAY on 2005-09-25
What am I doing wrong here? I type the above and get:
"[I][B]Reading package lists... Done
Building dependency tree... Done
Package emacs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs has no installation candidate[/B][/I]" ](*,) 

I need to install emacs, ghc6 and haskell-mode but keep getting the above message. :---) 

Any help would be greatly appreciated!

---

### Post by bongobonga on 2005-09-25
Emacs comes in the package name 'emacs21'. 
So what you are looking for is the package named emacs21
so just do 

apt-get install emacs21 ghc6 haskell-mode

---

### Post by STINGRAY on 2005-09-25
[QUOTE=bongobonga]Emacs comes in the package name 'emacs21'. 
So what you are looking for is the package named emacs21
so just do 

apt-get install emacs21 ghc6 haskell-mode[/QUOTE]

Thanks a lot, emacs is now installed. :grin: 
However, ghc6 and haskell mode still wont be installed and I get the same message as above. Any ideas?

---

### Post by bongobonga on 2005-09-25
I've just installed 'ghc6' and 'haskell-mode' with no problems. 

The only reason I can think of that you are having problems with the packages is that they are not part of the official distribution, so you probably just have to change your '/etc/apt/sources.list' file to include additional source locations. Here is my source files.


> deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted


deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by David Marrs on 2005-09-25
[QUOTE=bongobonga]I've just installed 'ghc6' and 'haskell-mode' with no problems. 

The only reason I can think of that you are having problems with the packages is that they are not part of the official distribution, so you probably just have to change your '/etc/apt/sources.list' file to include additional source locations. Here is my source files.[/QUOTE]
 It's probably easiest to do this from within synaptic. Enable the universe and possibly multiverse repositories from the settings menu.

---

