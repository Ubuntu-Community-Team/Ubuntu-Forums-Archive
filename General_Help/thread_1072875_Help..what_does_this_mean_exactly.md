---
title: "Help..what does this mean exactly?"
date: 2009-02-17
forum: General Help
---

### Post by casmok on 2009-02-17
Hi,

I'm following the Medibuntu instructions for installing the codecs to play non native media formats in MPlayer. Specifically to install the w64codecs.

I've followed the instructions to the letter but I get this error when I enter it in Terminal. What should I do next? 

Thanks, Mike

mbdb@M2000:~$ sudo apt-get install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w64codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w64codecs has no installation candidate
mbdb@M2000:~$

---

### Post by Titan8990 on 2009-02-17
It means there is no package called w64codecs. Usually an indication that the guide you are reading is out-dated.

---

### Post by casmok on 2009-02-17
> **Titan8990 said:**
> It means there is no package called w64codecs. Usually an indication that the guide you are reading is out-dated.

Oh wonderful! just when I thought I got it sorted! 

The Medibuntu site does have the codecs available for download on the page but it prompts me to choose which directory to install them to? If I do it under terminal "sudo apt-get install w64codecs" So which directory do I use?

Or... (and this was why I started going through all this to begin with)
can anyone recomend an easier way of playing RealMedia videos under Linux?

---

### Post by yther on 2009-02-17
The package is correct, but might not be available to you depending on your architecture.  If you're on a 32-bit system, you'll need "w32codecs" instead, or if it's a (non-Intel) Mac I believe it's "ppccodecs".  Does either of those work for you?

---

### Post by casmok on 2009-02-17
> **yther said:**
> The package is correct, but might not be available to you depending on your architecture.  If you're on a 32-bit system, you'll need "w32codecs" instead, or if it's a (non-Intel) Mac I believe it's "ppccodecs".  Does either of those work for you?

Well I'm using AMD Turion 64 so I assumed this was the correct one!

---

### Post by Matsukaze on 2009-02-17
Did you add the Medibuntu repository to your apt sources?

---

### Post by casmok on 2009-02-17
> **Matsukaze said:**
> Did you add the Medibuntu repository to your apt sources?

yes I did :confused:

mbdb@M2000:~$ #
mbdb@M2000:~$ 
mbdb@M2000:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for mbdb: 
--16:47:45--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[=================================================================================>] 226           --.--K/s             

16:47:46 (15.74 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

---

### Post by yther on 2009-02-17
> **casmok said:**
> Well I'm using AMD Turion 64 so I assumed this was the correct one!

Did you install the 64-bit version of Ubuntu?  It may be a silly question, but since the 32-bit version will happily install and run on a 64-bit platform such as yours, I have to ask.  If you're running 32, then the system won't want to show you 64-bit packages.

I don't know the official way to check Ubuntu release or version but I did this:

```
$ file `which bash`
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
```

If yours comes back with "ELF 32-bit" then I think we have the answer to the question.  ;)

---

### Post by casmok on 2009-02-18
I thought I installed the 64 bit version and this confirms it. :confused:
hmmmm...


mbdb@M2000:~$ file `which bash`
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
mbdb@M2000:~$

---

### Post by wildman4god on 2009-02-18
try going to packages.medibuntu.com and download the deb manually and install it.

edit:

also try sudo apt-get update and see if all the repos are downloading, on the network I'm on it blocks the public keys so I can get some software through the repos.

---

### Post by Therion on 2009-02-18
Simply do the following:```
sudo apt-get install ubuntu-restricted-extras
```

Problem solved.

---

### Post by casmok on 2009-02-18
> **wildman4god said:**
> try going to packages.medibuntu.com and download the deb manually and install it.

edit:

also try sudo apt-get update and see if all the repos are downloading, on the network I'm on it blocks the public keys so I can get some software through the repos.

OK two things here:

I ran apt-get update and it updated except for the following error msg at the end. Does this explain anything? 

"Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
mbdb@M2000:~$" 

I did go to medibuntu yesterday and found the deb manually...BUT where do I download it to? It defaulted to my home directory but thats not where I want it?

---

### Post by casmok on 2009-02-18
> **Therion said:**
> Simply do the following:```
sudo apt-get install ubuntu-restricted-extras
```

Problem solved.

OK will try that
Thanks!

and does this install all restricted or give me a choice of what I need?

---

### Post by wildman4god on 2009-02-18
> **casmok said:**
> OK two things here:

I ran apt-get update and it updated except for the following error msg at the end. Does this explain anything? 

"Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
mbdb@M2000:~$" 

I did go to medibuntu yesterday and found the deb manually...BUT where do I download it to? It defaulted to my home directory but thats not where I want it?

yeah I get that error alot on my network, it maybe a problem with the network, you'll haver to contact your network supervisor or isp. but it doesn't matter where you download the deb once you have it just double click it (like an exe in windows) and it should open up in gdebinstaller and install, I will research the public key error.

---

### Post by casmok on 2009-02-18
> **wildman4god said:**
> yeah I get that error alot on my network, it maybe a problem with the network, you'll haver to contact your network supervisor or isp. but it doesn't matter where you download the deb once you have it just double click it (like an exe in windows) and it should open up in gdebinstaller and install, I will research the public key error.

Thanks! I just downloaded and installed the deb.

Now it doesnt resolve my original problem on playing realmedia files but I'm going to post that as a seperate thread.

Thanks
Mike

---

