---
title: "Walk me through the Beryl Installation | Im a couple molicules short of a full bean"
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by Hymn on 2007-04-05
As corny as the title sounds, its true.  I haven't the slightest clue on Linux or Ubuntu, and I'm absolutely lost when it comes to installing programs for this system.  I've always said and believe that the best way to learn anything with the computer is to completely immerse yourself in it, find one thing you understand, then work from there.  So far, I understand that the Terminal is about the equivilent of Windows Dos Prompt, except with 100 times more functionability and such.  I started to read the guides you have at the top about installing Beryl, and of course the confusion set in.

^_^ I did learn a command though...  sudo gedit [path] is to edit data... always useful information.

Ok... one of the concerns I have is that this laptop is rather shitty, as in the Video Card is an Intel mobile something or other which I heard wasn't highly supported by Beryl in general.

Anyone wanna inturpret the stickies at the top so I can start learning?  I did manage to get through all of the "installation" up to where it asks me to install emerald packages, but I think I screwed something up because it wont let me run the Beryl-Manager.

---

### Post by cantormath on 2007-04-05
not that I have a problem with debian or prefer gentoo, but if all you are looking for is the gu in gui, you might like the Sabayon Linux, it comes with all the beryl stuff and its pretty easy to install.  There is a DVD with everything or a cd for those who just want the basics......I dont like all the gui, so I use debian and slackware.......its all a preference.

---

### Post by Hymn on 2007-04-05
Well, as I'm stuck with this install until I can find another way to install another OS (which I don't want to do)

I don't mind the functionability of Ubuntu, its just a large part of it confuses me because its new.  I'm not actually all that foriegn to computers, I just like having a buddy show me the ropes.

---

### Post by eentonig on 2007-04-05
> gksudo gedit /path/to/text

Is only needed if you want to modify files as root. otherwise, you can leave the gksudo part away.

concerning your Beryl install and problems. How did you install it? If you try to run Beryl from the console, do you see error messages?

> beryl-manager

---

### Post by Hymn on 2007-04-05
Excuse me if I speak in lamens terms.


First, I was following the guide on this page 
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
Which you link to in the sticky.  Looking at the history of the wiki, it hasn't changed much recently, so its either really outdated or upto date.


I started down here
[http://doc.gwos.org/index.php/BerylOnEdgy#Intel](http://doc.gwos.org/index.php/BerylOnEdgy#Intel)
Which is the intel 3d driver install

Everything seemed to work out perfectly, I was able to navagate my way through it and finish the 3d driver install (quite easy)


I got down to the beryl install inpeticular...
[http://doc.gwos.org/index.php/BerylOnEdgy#Install_Beryl](http://doc.gwos.org/index.php/BerylOnEdgy#Install_Beryl)

added
```
deb http://ubuntu.beryl-project.org/ edgy main
```
to
```
/etc/apt/sources.list
```
Which my best guess is that it enables installation from that website, using those... I dunno what the edgy and main are called exactly?


> Run the command for authentication, update, then install Beryl:
This is where I got confused.

It asks you to run three commands through the terminal, which I followed to a Tee...

Then it gets a bit hazy from there.

---

### Post by eentonig on 2007-04-05
I didn't follow those procedures, as I installed Beryl from the official repo's. But I'm running on Feisty.

Which commands are the ones it asks you to run? Can you copy and paste their output?

Regards,

---

### Post by nsleiman on 2007-04-05
updating the sources means: sudo apt-get update
installing beryl can be done wit: sudo apt-get install beryl

the repo must be added in /etc/apt/sources.list before performing those 2 steps.

---

### Post by Hymn on 2007-04-05
```
hymn@hymn-laptop:~$ sudo apt-get install beryl
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: emerald but it is not going to be installed or
                  aquamarine but it is not going to be installed or
                  heliodor but it is not going to be installed or
                  yawd but it is not installable or
                  compiz-gnome but it is not installable
         Depends: beryl-manager but it is not going to be installed
E: Broken packages

```

??

---

### Post by nsleiman on 2007-04-05
once you add

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

to the sources.list, type from the konsole:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

and retry to re-install

if it doesnt work with it try to download manually the *.deb files marked as dependent from:
[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

hope this will work

---

### Post by Spr0k3t on 2007-04-05
> **Hymn said:**
> ^_^ I did learn a command though...  sudo gedit [path] is to edit data... always useful information.

If you are launching a GUI based application such as gedit from the terminal with root privileges, make sure you use **gksudo** instead of sudo.  There is a difference.  If you don't use gksudo, there will be a time when gnome will fail to launch.  There's a very easy solution to the problem, but why worry when you can avoid the issue up front.

sudo for terminal

gksudo for GUI apps

---

### Post by Hymn on 2007-04-05
Grr this is getting more and more irritating.  I downloaded the deb packages, and the installer is telling me it can't install them.


why?


Oh, and I do appreciate all your guys help :)

---

### Post by Spr0k3t on 2007-04-06
What are you using to download deb packages?  Are you trying to add them to your existing repositories or are you using apt-get through the terminal?

---

### Post by siefer132 on 2007-04-06
can anyone tell me what the repo's are for Feisty(to install Beryl), and is it still sudo apt-get install beryl?

---

