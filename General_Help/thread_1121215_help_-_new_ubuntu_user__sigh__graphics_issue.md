---
title: "help - new ubuntu user  ::::sigh::::  graphics issue"
date: 2009-04-09
forum: General Help
---

### Post by vjmerc on 2009-04-09
Hey folks. Thanks in advance for whatever help you can provide. I recently purchased a Dell Mini 9 with Ubuntu 8.04.  Guess I should have made sure I was good friends with a local brain surgeon before I did that....lol.   I am having a few problems wrapping my head around all the differences between windows and ubuntu.

I am slogging through all the documentation and websites trying to understand how it all works.  Right now, the main issue I am having is that the graphics on some websites (ie:pogo) are not loading. I only get a giant X in the upper left hand corner.  I am sure there is a simple install that will resolve it but, after reading documentation for a few days, I haven't found it.  I have a very basic understanding of how this all works but, I
am trying to figure it out.  Any help would be greatly appreciated.... bribery is also not out of the question at this point.

thanks!

Vicky

---

### Post by Vaphell on 2009-04-09
you mean images are missing? or flash parts?
some examples of such websites?

---

### Post by phantom3113 on 2009-04-09
If you just got your laptop and Ubuntu is pretty fresh (i.e. you've only been using it for a day or two) you'll need to run "sudo apt-get install ubuntu-restricted-extras" (without the quotes) in a terminal which can be found under applications>>accessories>>terminal. the restricted extras package contains all the different file formats and such, like java, flash, .wmv, .avi, etc., which ubuntu doesn't come with by default. Also, when the terminal asks for the sudo password, it's the same password you use to log in with.

P.S.: Be careful when running anything with sudo! It gives you temporary god-like powers over your computer enabling you to do ANYTHING (as long as the computer understands you). apt-get install is the command to download and install programs.

---

### Post by FrankT-Qc on 2009-04-09
phantom3113 Is right, but if you're new to Ubuntu, there's also a thing called "Add/Remove Applications" that sits in the Application menu..


If you start this, it will show you a (huge) list of everything you can install on your system... Among them, you'll find "Ubuntu restricted extras" that is at a click's distance... The missing images are most likely Flash... You'll be able to see them after installing the extras... 

If you're trying to relate to your Windows experience, you might remember having Internet Explorer telling you "You're missing a plugin to display this..." and then you would click to install the plugin...

In Ubuntu, every piece of software is "centralized" in repositories (Add/Remove Application is a graphical user interface front end to it, apt-get is a command line one). Your plugins are in there with the rest !

You should take time to investigate what piece of software you can find in there... One of the "greatest" challenge of the transition is realizing how much software you now have access to !!!

---

### Post by phantom3113 on 2009-04-09
I guess I've gotten too used to using the terminal :P

---

### Post by vjmerc on 2009-04-18
OK, I tried installing Ubuntu restricted extras and I get the following:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Help! LOL.....will I ever get this unit up and running?  How do I manually run this?  I am totally lost but determined to stick with this until I have an understanding of what I am doing.

Thanks again,
Vic

---

### Post by Aizawa on 2009-04-18
Try this:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

...from a terminal. :)

EDIT: And then try to install the restricted extras, that is.

---

### Post by vancouverite on 2009-04-18
Hey vj,
The error you are getting suggests that dpkg was interrupted at some point.  dpkg is a program to monitor and administer the package system on your computer. It'll be a new idea coming from Win, but it's not that complicated.  It helps install and keep track of programs that you have installed on your system.  You know on a Win machine when you install something, decide that you don't want it and uninstall it, then you find that you have left over files and registry keys.  Oh, that's frustrating! Well dpkg helps keeps track of all that stuff on your new machine.

To orient you, Linux uses on-line repositories of available libraries and programs.  You can access these repositories in two ways: 1) you can use *apt* in the terminal, or you can go to "System > Administration > Synaptic Package Manager". If you search Synaptic for "restricted extras" you will find "ubuntu-restricted-extras" and a short description. Checking box next to it and hitting apply will do the same thing as typing *apt-get install ubuntu-restricted-extras* in terminal.

You will come to love the repositories.  They are safe (no viruses) and _full_ of great programs.  They act a lot like a huge, online install CD, all you have to do is select things you want installed, check apply and it will take care of the rest.  Same with uninstalling.

Occasionally, you will want to use software not in the repositories.  This happens when you want the newest version of some software, or are using a program that is just not in there.  Here there are three options 1) the software you want may have it's own repositories that you need to add (like medibuntu - a repository for stuff like encrypted DVD software and Adobe Reader that is illegal to distribut with Ubuntu, or requires subscribing to a license agreement respectively). 2) installing from a *.deb* file (ie if you want the newest OpenOffice) and 3) building from source.

I won't tell you about building from source, but adding repositories can be done through terminal (of course) or through "Software Sources" in the same menu as Synaptic. Most websites that have you add repositories will walk you through the steps, or more likely will have text that you just cut and paste into terminal to do it for you.

*.deb* files are Debian package files and are installed using the command *sudo dpkg -i [filename].deb* in a terminal. If you type *dpkg --help* in a terminal it will explain that command to you. If you want to know more, type *man dpkg* and it will give you the manual entry for *dpkg*. Press *q* when you are done looking at the manual to return to the command line.

So, to get you on your way, do as it recommends with the *dpkg --configure -a* (this installs and configures packages that have been downloaded, but not fully setup) and then just go into Synaptic, search for the restricted extras package and install it from there.  Synaptic's a much more user friendly way to manage your computer.  Lets face it, the command line has its place (and, believe it or not, you will come to actually like it ;)), but an effective GUI is just easier to get a fast handle on!

Hopes this helps.  I'll watch this thread, so post again if it worked or if not!

Cheers,
Van

PS I thought the Dell computers came with the restricted packages and DVD decoder installed - strange that they aren't working out of the box. If you can't play DVDs for some reason, surf to [www.medibuntu.org](www.medibuntu.org) and follow the directions there to add their repository and install libdvdcss2.

---

