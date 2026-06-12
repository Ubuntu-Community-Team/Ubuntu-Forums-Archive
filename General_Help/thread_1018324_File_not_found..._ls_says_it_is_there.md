---
title: "File not found... ls says it is there"
date: 2008-12-22
forum: General Help
---

### Post by igknighted on 2008-12-22
So, I am trying to install Adobe AIR.  I downloaded the installer, made it executable with chmod +x, and tried to run it with ./AdobeAIRInstaller.bin.  See the results:

```
(fitz@lappy: ~/Desktop)$ ls -al | grep Adobe
-rwxr-xr-x  1 fitz fitz 13553300 2008-12-05 20:51 AdobeAIRInstaller.bin
(fitz@lappy: ~/Desktop)$ ./AdobeAIRInstaller.bin 
zsh: no such file or directory: ./AdobeAIRInstaller.bin

```

I tried using the bash shell, I tried creating a copy and putting it in a different folder... nothing seems to work.  It lets me do other operations on the folder though:

```
(fitz@lappy: ~/Desktop)$ cp AdobeAIRInstaller.bin ../Documents 

```

Any ideas on what is happening?

---

### Post by jerome1232 on 2008-12-22
Perhaps you're missing a dependency, and when adobe goes to grab that dependency and not finding it, it's echoing to the screen "no such file, blah blah"


Well that was the problem for me on a whole different program once, baffled me for hours. Might want to use getlibs on it to make sure you have all the dependencies installed.

---

### Post by igknighted on 2008-12-22
> **jerome1232 said:**
> Perhaps you're missing a dependency, and when adobe goes to grab that dependency and not finding it, it's echoing to the screen "no such file, blah blah"


Well that was the problem for me on a whole different program once, baffled me for hours. Might want to use getlibs on it to make sure you have all the dependencies installed.

Hmm, oh well.  I really have no need for it, so the idea of adding a bunch of 32bit libs really doesn't appeal to me.  Adobe just pumped out 64bit flash, so maybe Air will follow.

EDIT: There is nothing on Adobe's site to indicate that it is 32bit only, so maybe that isn't the issue?

---

### Post by jerome1232 on 2008-12-22
getlibs grabs 64 bit dependencies too, it's not just for installing 32 bit binaries with 32 bit dependecies.

It's just the only reason I can possibly think of for getting that message.

---

### Post by dcstar on 2008-12-22
> **igknighted said:**
> So, I am trying to install Adobe AIR.  I downloaded the installer, made it executable with chmod +x, and tried to run it with ./AdobeAIRInstaller.bin.  See the results:

```
(fitz@lappy: ~/Desktop)$ ls -al | grep Adobe
-rwxr-xr-x  1 fitz fitz 13553300 2008-12-05 20:51 AdobeAIRInstaller.bin
(fitz@lappy: ~/Desktop)$ ./AdobeAIRInstaller.bin 
zsh: no such file or directory: ./AdobeAIRInstaller.bin

```

I tried using the bash shell, I tried creating a copy and putting it in a different folder... nothing seems to work.  It lets me do other operations on the folder though:

```
(fitz@lappy: ~/Desktop)$ cp AdobeAIRInstaller.bin ../Documents 

```

Any ideas on what is happening?

Look inside the file and see what the script is trying to do.

The default Ubuntu shell is bash, so if this is using zsh then it could be "assuming" other things as well, or changing to directories that don't exist.

---

### Post by igknighted on 2008-12-22
> **dcstar said:**
> Look inside the file and see what the script is trying to do.

The default Ubuntu shell is bash, so if this is using zsh then it could be "assuming" other things as well, or changing to directories that don't exist.

1) It's a binary, not a script.

2) I tried using bash as well, same error.

---

### Post by Altimac on 2009-01-09
FWIW, Adobe's instructions worked perfectly for me on 64-bit Intrepid:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1)

---

### Post by LateNiteTV on 2009-01-09
try running it without the "./"

---

### Post by hyperdude111 on 2009-01-09
To install adobe air re-name the installer "a.bin" and place it in your home. This removes any need to cd or type out a long name. 
Once you have done that its easy.

Go to terminal and

chmod +x a.bin

then

sudo ./a.bin

You do not need dependencies for air so ignore that one. This worked perfectly for me.

---

