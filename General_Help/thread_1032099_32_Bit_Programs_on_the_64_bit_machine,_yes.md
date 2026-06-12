---
title: "32 Bit Programs on the 64 bit machine, yes?"
date: 2009-01-06
forum: General Help
---

### Post by IKhider on 2009-01-06
Hello fellow Ubuntu Users, 

I have 64 bit Xubuntu/Ubuntu on my 64 bit processor machine. I am trying to install Skype but the installer says I need a 32 bit os to make it work. Therefore there surely must be an emulator out or a patch to get Skype fired up. 

Yes?

-I-

---

### Post by wolfen69 on 2009-01-06
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` then search synaptic for skype.

---

### Post by IKhider on 2009-01-06
Hello there Wolfen 69 and thanks for your prompt response. I followed your response and received the following error message on Synaptic 

"skype:
  Depends: lib32asound2 (>1.0.17) but 1.0.15-3ubuntu4 is to be installed
 Depends: lib32v4l-0  but it is not installable"

I guess I should add I am using Hardy as some programs like Kompozer will just not work on Intrepid. 

Any ideas?

-I-

---

### Post by IKhider on 2009-01-06
Hello again Wolfen69,

I tried to sub the 'intrepid' part of your command line code with "Hardy", but I got this error message when I tried to install Skype, an "unresolvable dependancy": 

"skype:
  Depends: skype-common (=2.0.0.72-0medibuntu1) but 2.0.0.72-0medibuntu4 is to be installed" 

Hmm, I'm not very clever here....

---

### Post by jerome1232 on 2009-01-06
Have you install ia32-libs?

```
sudo apt-get install ia32-libs
```

Also I find [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to be great for installing 32-bit programs that require 32-bit libraries.

---

### Post by IKhider on 2009-01-06
Hello Jerome, 

Apparently, I already have it. 

"ia32-libs is already the newest version."

Thanks for trying though. 

-I-

---

### Post by jespdj on 2009-01-06
You don't need an emulator to run 32-bit programs on a 64-bit operating system.

Installing Skype from the Medibuntu repository is the easiest way to do it and should not lead to dependency errors.

See [HOWTO: Install Skype on 64-bit Ubuntu](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by IKhider on 2009-01-06
Greetings Jespdj, 

I have followed the page, thank you--but that still leads to errors. I tried the Hardy Install commands on the link and got this on command line:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: skype-common (= 2.0.0.72-0medibuntu1) but 2.0.0.72-0medibuntu4 is to be installed
E: Broken packages"


Alternately, when I used Synaptic I got this after an "unresolvable dependency":

"skype:  Depends: skype-common (=2.0.0.72-0medibuntu1) but 2.0.0.72-0medibuntu4 is to be installed"


Where do you suppose I go from here?

-I-

---

