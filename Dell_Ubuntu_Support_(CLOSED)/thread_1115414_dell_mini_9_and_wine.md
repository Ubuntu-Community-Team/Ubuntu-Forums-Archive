---
title: "dell mini 9 and wine"
date: 2009-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 2roombas on 2009-04-03
I am wanting to install wine on my new dell mini that has ubuntu 8.04 pre-loaded, but the checkbox for wine in the repository "will not" check? Is this a common problem on the preloaded software? I had no trouble at all getting wine installed on my Inspirion that has Jaunty (9.04) that I loaded myself.

---

### Post by Cowchip7 on 2009-04-03
Must have something to do with the lpia. Another reason why I will updating to Jaunty UNR when I get my mini.

---

### Post by Cowchip7 on 2009-04-03
Do you guys think a terminal install would work?

---

### Post by 2roombas on 2009-04-03
Thiw is what I get from a terminal install...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
E: Broken packages

---

### Post by GenericGuy on 2009-04-03
you could try getting a more current version of libasound on the intrepid repos, or even on the debian ones (they work)

---

### Post by 2roombas on 2009-04-03
> **Cowchip7 said:**
> Must have something to do with the lpia. Another reason why I will updating to Jaunty UNR when I get my mini.

  I was actually considering an upgrade to Jaunty on this machine, as it's been running so nicely on my other laptop.  Do you think that will be OK to do?  I do not have an external drive so I'm bit worried about doing that bc I can't just re-install 8.04 if I make a mess.

---

### Post by 2roombas on 2009-04-03
> **GenericGuy said:**
> you could try getting a more current version of libasound on the intrepid repos, or even on the debian ones (they work)

and I do this how???

---

### Post by Ryback on 2009-04-03
> **Cowchip7 said:**
> Must have something to do with the lpia. Another reason why I will updating to Jaunty UNR when I get my mini.

That's an incorrect assumption.  I have an absolutely bog-standard lpia dell install of 8.04 on my mini9 and wine installed without a problem via synaptic, and is running fine.  Sorry I can't help troubleshoot this problem but it's not a general problem with the lpia kernel per-se.

---

### Post by anjilslaire on 2009-04-04
> **2roombas said:**
> I was actually considering an upgrade to Jaunty on this machine, as it's been running so nicely on my other laptop.  Do you think that will be OK to do?  I do not have an external drive so I'm bit worried about doing that bc I can't just re-install 8.04 if I make a mess.

I'm running the standard i386 Intrepid just fine, and early reports show that Jaunty is good, too:
[http://www.ubuntumini.com/2009/03/ubuntu-904-jaunty-jackalope-beta-on.html](http://www.ubuntumini.com/2009/03/ubuntu-904-jaunty-jackalope-beta-on.html)

---

### Post by shiningkenmonster on 2009-04-05
i have the dell pre-installed ubuntu 8.04 on a dell mini 9. I got wine installed by using this website:

[http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

I followed the examples with the pictures. 

 For some reason on the section of:
Alternative command Line Instructions for Installing Wine:

it gave me an error on the 

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

or the 

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

I had to use the Graphic User Interface to add the WineHQ APT Repository and Authenticate the key. (like the examples of the pictures of the website)

and than I installed it on the terminal with the:

```
sudo apt-get update
```
```
sudo apt-get install wine
```

wine worked perfectly afterwards

---

### Post by 2roombas on 2009-04-05
I was able to get it all to work just fine. On another board in this forum they mentioned having to edit a word the source.list. That did it.

unfortunately the program I wanted wine installed for will not even work!  Bookworm Deluxe is the game I'm addicted to and I cannot find a native linux equivalent.  Sigh...  guess I'll keep a Windows dual-boot after all.:(

---

### Post by Cowchip7 on 2009-04-15
I just got my mini 9 in the mail yesterday. Wine was available using synaptic and it installed like a charm... but I don't have a reason to use it yet! :lolflag:

---

