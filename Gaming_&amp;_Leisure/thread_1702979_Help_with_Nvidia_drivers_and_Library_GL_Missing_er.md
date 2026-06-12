---
title: "Help with Nvidia drivers and Library GL Missing error?"
date: 2011-03-08
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2011-03-08
Im compiling Danger from the deep from SVN, and when i try to build it i get this error...



```
 Install binary path: /usr/local/bin
Using data dir: /home/dlambert/dangerdeep/data
Checking for C library GL... no
Library GL is missing, it must be installed!
```

---

### Post by Dlambert on 2011-03-09
Im using the latest Nvidia drivers on an GTS 450

---

### Post by Perfect Storm on 2011-03-09
Try with:
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```

---

### Post by Dlambert on 2011-03-11
> **Artificial Intelligence said:**
> Try with:
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```
 
Will let you know how it goes.

---

### Post by realzippy on 2011-03-11
Let us know when you get danger from the deep running (longer than 5 minutes),..we still
have [no success]("http://ubuntuforums.org/showthread.php?t=1674479").

---

### Post by Dlambert on 2011-03-12
> **realzippy said:**
> Let us know when you get danger from the deep running (longer than 5 minutes),..we still
have [no success]("http://ubuntuforums.org/showthread.php?t=1674479").

Im going to try on this laptop, since I have no access to my desktop. Ill be on later.

---

### Post by Dlambert on 2011-03-12
The game runs, but when i try to play it, it crashes. I believe the reason is the Intel GMA 45 on this laptop. all settings on low and it says segmentation fault.

---

### Post by realzippy on 2011-03-12
..here it crashes after few minutes,no matter if intel or nvidia graphics,where everything else works flawlessly.

---

### Post by Dlambert on 2011-03-13
Im going to try on my Nvidia GTS 450 when i get home. Ill let you know.

---

### Post by Dlambert on 2011-03-17
My monitor went out. :( wont be able to test for a while.

---

### Post by Dlambert on 2011-03-18
Its building! ill let you know.

---

### Post by Dlambert on 2011-03-18
> **Artificial Intelligence said:**
> Try with:
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```

I already had them installed, but after updating Driver to latest it worked! Doesn't crash either, after 10 mins on MAX on Nvidia GTS 450.

---

### Post by realzippy on 2011-03-19
Not crashing?
Reached the convoy?

---

### Post by Dlambert on 2011-03-19
Haven't played that much, ill do it now. Diving doesn't work though...and some textures disappear..it is testing software though.

---

### Post by Dlambert on 2011-03-19
It freezes, i get about 200 yards away, then fire a torpedo, and it freezes...They have alot of work to do on this game...too bad it almost seems dead.

---

### Post by NM5TF on 2011-05-10
> **Dlambert said:**
> It freezes, i get about 200 yards away, then fire a torpedo, and it freezes...They have alot of work to do on this game...too bad it almost seems dead.

at least you get close enuff to fire torpedo.....I never seem to come close
to convoy B 4 it freezes...

I have talked to DEV on IRC #dangerdeep....he claims that he cannot
duplicate the problem...:confused::confused:

---

### Post by realzippy on 2011-05-10
...do they run windows or linux version? :P

---

### Post by NM5TF on 2011-05-10
> **realzippy said:**
> ...do they run windows or linux version? :P

don't know....I did ask them what distro & hardware platform they use...
still waiting for response...they sometimes take days to respond...:(

will post here when they respond...:P

---

### Post by NM5TF on 2011-05-10
> **NM5TF said:**
> don't know....I did ask them what distro & hardware platform they use...
still waiting for response...they sometimes take days to respond...:(

will post here when they respond...:P

he responded amazingly fast today...:P

here is his response:

using Gentoo OS...

graphics cards he has used are: ATI 4250, Nvidia 8600GT, INTEL 4500 with
both INTEL & AMD 64 bit

he also said that if he "gets time this weekend, he will run an UBUNTU VM
to see if he can duplicate the problem"....

now he wants to know if I am running 32 or 64 bit....I am running 32 bit
at this time...that may be a problem...waiting for response now...

---

### Post by realzippy on 2011-05-10
[I]...he will run an UBUNTU VM.
[/I]
:confused:
.... in a VM he won't be able to get 3D hardware acceleration !?

---

### Post by NM5TF on 2011-05-12
MAJOR NEWS this AM..:D

yesterday I downloaded the 64 bit version of 10.04.2 & installed a dual-boot
system to take advantage of my AMD K8-64 dual-CPU hardware...

I then downloaded the files from SVN, not the "easy" version...the"long"
version...I then compiled it & ran it this morning...

the game has been working for over 15 minutes now with NO problems...NO
freezing/crashing...:P:P

now I will need to read the manual to learn how to play this brilliant game
to the fullest...

if your machine has 64 bit capability, but you're only using a 32 bit OS, this just may solve your problem also...:P

---

### Post by NM5TF on 2011-05-12
just talked with the DEV on IRC...

he says that he had a 32 bit 10.04 VM running last night for over 1 hour
with no problems...

i am wondering if it is maybe a memory problem...may machine only has 1 GB
of RAM installed....

what about you other guys...how much RAM do you have???

---

### Post by Dlambert on 2011-05-14
I have a 64bit dual core phenom II. and 4 Gigs of DDR3 1600 in dual channel

---

### Post by ubudog on 2011-06-02
I've got 6 gigs, 2.53 GHz here and it still crashes.  (using latest svn)

---

### Post by Dlambert on 2011-06-03
And my phenom 2 is 4 GHz

---

