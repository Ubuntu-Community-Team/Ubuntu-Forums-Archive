---
title: "Installing Downloaded Program - TrueCrypt"
date: 2009-05-10
forum: General Help
---

### Post by dave30c on 2009-05-10
I want to be able to download and install TrueCrypt so that I can open files encrypted from my MacBookPro onto a flashdrive 16G and then  use them on the Dell Mini w-Ubuntu

The tutorial I was following VTC did not cover this issue.  On the Mac, one just downloads the file to Downloads, then drags the file to Applications, then double clicks it and installs.  Just like that.  So, in Ubuntu Linux on this Dell Mini, where does the downloaded file go?  Where should it next go? the Bin folder?  And then double-click the file to install?  

I tried setting up two windows to accomplish this and just don't know how.  

I tried finding something in the Ubuntu Pocket Guide and found nothing about this subject at all. The word "download" does not even appear in the Index, and "Installation" covers only of the OS. I also note that the word "applications" also does not appear in the index.

Thanks for the help.

Dave

---

### Post by dave30c on 2009-05-10
I found a piece of jargon named "Software Management" buried deep in the booklet, so I need to read that.

---

### Post by paradigm2 on 2009-05-10
> **dave30c said:**
> I found a piece of jargon named "Software Management" buried deep in the booklet, so I need to read that.

Here.  I have to install Truecrypt anyway and will do it now and give you a step by step in a second after i do it.

---

### Post by paradigm2 on 2009-05-10
I just finished my install of Truecrypt and here are my notes on how to do it-



How to install Truecrypt (This assumes Gnome and Firefox as well as the current version.  It is not the point and click way either)
-----------------------

1. Go to: [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
2. Under "Linux" select "Ununtu x86" (assuming you are not using 64bit -- you would know)
3. Click Download right under what you selected.
4. up comes a box (in firefox) "You have chosen to open...", select SAVE FILE.
5. If it lets you choose where to put it, put it in your home folder.  If not it will probably just go on your desktop.

6. Open up a terminal. (Applications -> Accessories -> Terminal)
7. type "ls -l" without the quotes. (Note: this is the lowercase letter L, not the number one)
8. You should see a file like: "truecrypt-6.1a-ubuntu-x86.tar.gz" listed.
9. If so type:

```

tar xvf truecrypt-6.1a-ubuntu-x86.tar.gz

```

10. Now do:

```

sudo ./truecrypt-6.1a-setup-ubuntu-x86

```

11. Select "Install Truecrypt"
12. Ok to the agreement(s)
13. click "Install Package"

14. Look for it in Applications -> Other -> Truecrypt.

God luck. :)

---

### Post by sgosnell on 2009-05-10
It's in the repositories.  You should be able to simply type "sudo apt-get install truecrypt", or open Synaptic, find it in the list, mark for installation, and then click Apply.

---

### Post by Sandworm on 2009-08-03
Its not in any of the basic repos.  If I remember correctly there are some licensing issues with it.

---

### Post by MadHatter21 on 2009-08-03
If you want you can go to Sys Package Manager and install easy crypt, works for me. Mounts quickly and easily.

---

### Post by mcfion on 2009-09-16
> **paradigm2 said:**
> I just finished my install of Truecrypt and here are my notes on how to do it-



How to install Truecrypt (This assumes Gnome and Firefox as well as the current version.  It is not the point and click way either)
-----------------------

1. Go to: [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
2. Under "Linux" select "Ununtu x86" (assuming you are not using 64bit -- you would know)
3. Click Download right under what you selected.
4. up comes a box (in firefox) "You have chosen to open...", select SAVE FILE.
5. If it lets you choose where to put it, put it in your home folder.  If not it will probably just go on your desktop.

6. Open up a terminal. (Applications -> Accessories -> Terminal)
7. type "ls -l" without the quotes. (Note: this is the lowercase letter L, not the number one)
8. You should see a file like: "truecrypt-6.1a-ubuntu-x86.tar.gz" listed.
9. If so type:

```

tar xvf truecrypt-6.1a-ubuntu-x86.tar.gz

```10. Now do:

```

sudo ./truecrypt-6.1a-setup-ubuntu-x86

```11. Select "Install Truecrypt"
12. Ok to the agreement(s)
13. click "Install Package"

14. Look for it in Applications -> Other -> Truecrypt.

God luck. :)

I tried this, but the "Install Package" is in grey and nothing happens when i click it =/

Also Truecrypt is not in the repositories, at least not those that i have here (the ones that comes with ubuntu plus the amsn repo)

Any solution?

---

### Post by Albert2009 on 2009-09-20
Hi,
- check your /tmp folder. You will find there a ??truecrypt??.deb file.
- use: sudo dpkg -i ??truecrypt??.deb
- run truecrypt.

---

