---
title: "Trusty, Gnome Metacity, XPlane10-Updated Install Data needed"
date: 2015-03-14
forum: Gaming &amp; Leisure
---

### Post by emarkay on 2015-03-14
Bought the 2 disc DVD recently. Thought it would be less hassle than getting v9 running a few years ago.  But...

Their install file has spaces in file name, I removed them and still no good. Copied file to desktop, and to a stand-alone direcctory, still no good. Nothing happens after I unzip it and run the resulting file. Tried Gdebi and it reports "Can not execute binary file. Exec format error". Their Wiki is for 9.04 “Jaunty Jackalope”. and the install page is for "8.10 Intrepid Ibex". I do have libopenal1 installed. I downloaded the apparently most recent file from here: [http://www.x-plane.com/downloads/x-plane_10_installer-updater/](http://www.x-plane.com/downloads/x-plane_10_installer-updater/), but per instructions elsewhere on their site, going to his page, it is for version 9: [http://wiki.x-plane.com/DVD_Installers](http://wiki.x-plane.com/DVD_Installers). 

I see some things on the web for  Ubuntu 12.02 or so, but have not been able to get a Google handle on a current standard Trusty install proccedure using the V10 DVD set.. See sig for details on the 32 bit Trusty PC.

Thank you!

---

### Post by oldrocker99 on 2015-03-17
I know it's too late to tell you now, but X-Plane is on Steam; it's expensive, but it is the finest flight simulator ever produced, and it's been that for over 15 years. I'm pretty sure that it runs just fine on Linux. I haven't seen too many complaints about it in the Steam forums. It **is** a 64-bit program, if that matters.

---

### Post by emarkay on 2015-03-17
Yea, I know, but I don't game, just fly.

Anyone else?

---

### Post by MikeCyber on 2015-03-18
Copy&Paste the terminal output so we see what you're trying to do.

Probably, simply put the cd in, cd to where the install is:
cd /media/michael/dvd
./x*installer

* is wildcard for use with spaces etc. No need to rename anything.
Probably it would be a good idea to use the latest installer from x-plane.com
and later update the demo with your cd. On the cds is mainly the scenery apart 
a older x-plane which you would need to update later anyway.

---

### Post by emarkay on 2015-03-20
Oh, run it in terminal? Gee, just what it says...

PCNAME:~/Downloads$ X-Plane 10 Installer Linux
X-Plane: command not found

Um, could it be the spaces?

MRK

PS: This is is using the downloaded installer, as the websitre here: [http://www.x-plane.com/downloads/dvd-installation/](http://www.x-plane.com/downloads/dvd-installation/)
States: 
***When you get your X-Plane DVDs, download and run the appropriate DVD installer below. *Do not** use the installer that comes on the Disc 1 DVD.

?????

---

### Post by MikeCyber on 2015-03-21
Yes spaces but that's no problem. Either do:
cd /home/downloads
./X-*install*
* stands for any character
or
./X
then press tab for autocomplete
or 
./X-Plane\ 10\ Installer\ Linux
which escapes spaces. So 3 ways to go without renaming. The ./ means execute in this directory.
You might need to set the installer to executable by right clicking on - permissions - execute 
or in terminal chmod +x instal*

Very, very basic stuff. How did you get that many beans...

---

### Post by emarkay on 2015-03-22
Using your text, in my directory (copied raw from ternimal):
NAME@COMPUTER:~?Downloads$

There is this file:
X-Plane 10 Installer Linux

Permissions on file are all Read and Write, and Execute is checked.
 
"Try:./X-*install*"
gets: bash: ./X-*install*: No such file or directory

"or ./X
then press tab for autocomplete"
gets:  ./X-Plane\ 10\ Installer\ Linux 
bash: ./X-Plane 10 Installer Linux: cannot execute binary file

"or ./X-Plane\ 10\ Installer\ Linux" 
also gets: bash: ./X-Plane 10 Installer Linux: cannot execute binary file

and: "chmod +x instal*"
gets: chmod: cannot access `instal*': No such file or directory

Again, "ls" shows: "X-Plane 10 Installer Linux"
Also have also tried the uppercase "Install*"


Thank you, Mike, for taking the time to assist, but still no go... 
Is this really this illogical, or what have I missed?
Please be kind;  I have beans for almost 9 years of learning...

---

### Post by emarkay on 2015-03-22
Now waitaminute - so there is a DIFFERENT installer, specifically for 32 bit Linux??? - (Thanks Google!)



Found :X-Plane 10 Installer Linux 32-bit, from Wed 03 Sep 2014 12:26:31 PM EDT

...and, it seems to be (at least installing now) working?



Absolutely bamboozled.....

---

### Post by MikeCyber on 2015-03-23
Yes those were examples, you need to take care of capitalization etc.
So ls -la shows:
X-Plane 10 Installer
do
./X-P*er
the er at the end is only needed if other similar named files are in the directory.

Good, after that put cd1 in and install your scenery. This is needed to get out of the demo mode.
Happy flying

---

### Post by emarkay on 2015-03-23
Yup, it was the wrong installer...

You will need to hunt down the 32 bit one for 32 bit systems.
Ignore everything about installing on their site. 

Find: X-Plane10InstallerLinux32.zip, from Wed 03 Sep 2014 12:26:31 PM EDT
Worked fine on Trusty and Precise.

Beyond bamboozled...
G'night!

MRK

---

