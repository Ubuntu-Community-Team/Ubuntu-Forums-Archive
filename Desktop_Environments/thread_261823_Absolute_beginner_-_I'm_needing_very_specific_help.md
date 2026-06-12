---
title: "Absolute beginner - I'm needing very specific help..."
date: 2006-09-20
forum: Desktop Environments
---

### Post by r2builder on 2006-09-20
Hi guys, I just installed Ubuntu tonight, and it's the first distro of linux I've used. I am a total novice.

The reason for the installation is because I came across Dr Roland Shregle's website:
[http://www.ganjatron.net/misc/scanjet/scanjet.html](http://www.ganjatron.net/misc/scanjet/scanjet.html)
which deals with using his program along with SANE backends to make a specific scanner - (The HP 4c) make music.

As soon as I saw his webpage, I knew I needed to acheive this somehow.  So, I heard that Ubuntu was the most popular distro of linux, and downloaded it - but I'm completely out of my depth.  I was wondering if anyone could give me a really dumbed down version of how to get this to work.

Are the required SANE backends already installed in my version of ubuntu? (I used the Ubuntu Live CD, then installed it to my HD)  Note that his readme says: "Note that
libsanei and its header files is not installed per default, and must be done
manually."

I've got the SANE backend files downloaded to my Ubuntu desktop, along with the source code for the scanjet program, but I have no idea what to do now.

I know how to get into the terminal, but I don't know any commands or what to do with tar.gz files.

It looks as though after the SANE backends are installed, I need to edit the scanjet makefile and then compile it?  Does the fresh install of Ubuntu come with a compiler?

If anyone could create a complete walkthrough on how I can get this working I'll be forever greatful.  I bought the specific scanner from ebay, and installed Ubuntu JUST to get this to work.  I've invested a lot of time & money into getting this to work, and I'm not going to give up now.  Pretty desperate guys.

Thanks in advance everyone, 
-James

PS: wow, this is the first post I've ever written under Linux ;)

---

### Post by Odinist on 2006-09-20
Wow! Not only is that scanner trick amazing, so is the fact that you bought the scanner and installed Linux just to recreate it! Kudos!!

You should be able to double click the tar.gz file, and it will open in Archive Manager. You and then extract the file to wherever you want. Then, using the terminal, you can navigate to where you extraced it, and compile/install it.

---

### Post by r2builder on 2006-09-20
Cool thanks, I've got the scanjet package extracted to a folder on my desktop.

Now, before I compile & install this, it says I need those backends..

Does anyone know if the fresh install of Ubuntu has those backends (even libsanei and its header files?)

If it's not, can someone walk me through installing it all?

Thanks, and sorry to do this - but as I said I'm a complete newbie and have resorted to posting a message on this forum after days of searching google for support.

I'm quite frustrated with it all, but I'm determined to learn to get it to work.

Thanks again.

---

### Post by odinfromvalhalla on 2006-09-20
libsane - API library for scanners
libsane-dev - API development library for scanners [development files]
libsane-extras - API library for scanners -- extra backends
libsane-extras-dev - API development library for scanners [development files]

you can install those (you might not need all of them) like this in a shell:

sudo apt-get install libsane libsane-dev libsane-extras  libsane-extras-dev

---

### Post by PriceChild on 2006-09-20
you will also need to ```
sudo apt-get install build-essential
``` before you can build from source.

Check out the readme for specific instructions, but it will be something along the lines of ```
./configure
make
sudo checkinstall
```

---

### Post by r2builder on 2006-09-20
Thanks everyone, I've done everything posted here - and now I'm at:
> Edit the Makefile to reflect your C compiler's flags and the locations of
the SANE libraries and header files, then run make.

The makefile as it is says:
```
#CFLAGS = -O
CFLAGS = -g
#LDFLAGS = -s

all: sjetplay sjetnasm

sjetplay: sjetplay.c
	$(CC) $(CFLAGS) sjetplay.c -o sjetplay $(LDFLAGS) -lsanei

sjetnasm: sjetnasm.c
	$(CC) $(CFLAGS) sjetnasm.c -o sjetnasm $(LDFLAGS)	

```

I'm pretty much clueless.

was "sudo apt-get install build-essential" to install a compiler?
If so, how do I find out the flags?  or whatever they are.

Thanks a BUNCH for the help so far!!

---

