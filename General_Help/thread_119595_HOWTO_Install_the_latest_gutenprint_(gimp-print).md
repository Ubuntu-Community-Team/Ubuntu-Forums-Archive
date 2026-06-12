---
title: "HOWTO: Install the latest gutenprint (gimp-print)"
date: 2006-01-19
forum: General Help
---

### Post by fubarbundy on 2006-01-19
WARNING: DON'T BLAME ME IF YOUR COMPUTER EXPLODES, YOUR HOUSE BURNS DOWN AND THE APOCALYPSE ARRIVES AS A RESULT OF USING THIS GUIDE!

Now, on with the good stuff! Here's how to get the latest gutenprint (pre-5.0.0rc2) installed and working on Breezy, nice and clean like :-)

1. Open gnome-terminal

2. Create a build directory:

```
mkdir ~/gutenprint
cd ~/gutenprint
```

3. Get Ubuntu sources for gutenprint:

```
wget ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_4.3.99+cvs20051122.dfsg.1.orig.tar.gz ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_4.3.99+cvs20051122.dfsg.1-2.diff.gz ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_4.3.99+cvs20051122.dfsg.1-2.dsc
```

4. Install build dependencies:

```
sudo apt-get install libcupsys2-dev libcupsimage2-dev libgtk1.2-dev libgimp2.0-dev libreadline5-dev libijs-dev debhelper zlib1g-dev flex gettext foomatic-db-engine chrpath dpatch
```

5. Install other needed packages:

```
sudo apt-get install build-essential dpkg-dev fakeroot
```

6. Extract the sources:

```
dpkg-source -x gutenprint_4.3.99+cvs20051122.dfsg.1-2.dsc
```

7. Compile gutenprint:

```
cd gutenprint-4.3.99+cvs20051122.dfsg.1
dpkg-buildpackage -rfakeroot -uc -b
cd ../
```

-------------Now, EITHER install the lazy way (a) or the cracktastic way (b)----------------

THE LAZY WAY (UNTESTED!!! You will probably need to fix broken packages in Synaptic afterwards - I think it's just the removal of cupsys-driver-gimpprint-data but I can't say for sure):

8a. Install packages:

```
dpkg -i *.deb
```

9a. Fix any broken packages in Synaptic and you're done!

-------------OR------------

THE CRACKTASTIC WAY (through Synaptic by creating a local repository - replace i386 with amd64/powerpc/ia64/sparc as appropriate):

8b. Create local repository directories:

```
mkdir -p ~/gutenprint-packages/dists/breezy/local/binary-i386
mkdir ~/gutenprint-packages/binary-i386
```

9b. Move the packages into the repository and change directory:

```
mv *.deb ~/gutenprint-packages/binary-i386
cd ~/gutenprint-packages
```

10b. Scan the new packages and create a package list for dpkg:

```
dpkg-scanpackages binary-i386 /dev/null | gzip -9c > dists/breezy/local/binary-i386/Packages.gz
```

11b. Edit your repositories:

```
sudo gedit /etc/apt/sources.list
```

12b. Add the following line to the end of the file:

**deb file:///home/[your username]/gutenprint-packages breezy local**

13b. Refresh your package list:

```
sudo apt-get update
```

14b. Install or upgrade the following through synaptic (you may have to remove cupsys-driver-gimpprint-data):

[B]cupsys-driver-gimpprint
foomatic-db-gimp-print
ijsgimpprint
cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2[/B]

15b. Done!

---

### Post by brucetan on 2006-02-14
dear fubarbundy,

I ve followed instruction and installed gutenprint successfully! Many thanks.:) 

By the way, can delete away the subdirectories in my home directory:
~/gutenprint and ~/gutenprint-packages?

My printer is EPSON STYLUS CX4100, gutenprint detected correctly when I did a 'add a new printer'.   The print function is 100% ok.

However,CX41000 also has a scanner built-in.  How can I use the scanner function?

Hope you can help & many thanks.

---

### Post by gremlin hunter on 2006-02-14
[QUOTE=brucetan]
However,CX41000 also has a scanner built-in.  How can I use the scanner function?[/QUOTE]

You would be wanting to use SANE. Although your device is not listed the 4200 is. Would be worth a shot.

---

### Post by brucetan on 2006-02-14
Thanks for your prompt advice. I'll try it shortly.

What about those 2 subdirectories from gutenprint installation, can they be deleted?

---

### Post by fubarbundy on 2006-02-27
[QUOTE=brucetan]Thanks for your prompt advice. I'll try it shortly.

What about those 2 subdirectories from gutenprint installation, can they be deleted?[/QUOTE]


Yes you can. The gutenprint folder is for building and the gutenprint-packages is for the deb packages. But I suggest you keep the deb packages in case you want to reinstall later (move them wherever you want).

---

### Post by fubarbundy on 2006-02-27
[QUOTE=brucetan]dear fubarbundy,

I ve followed instruction and installed gutenprint successfully! Many thanks.:) 

By the way, can delete away the subdirectories in my home directory:
~/gutenprint and ~/gutenprint-packages?

My printer is EPSON STYLUS CX4100, gutenprint detected correctly when I did a 'add a new printer'.   The print function is 100% ok.

However,CX41000 also has a scanner built-in.  How can I use the scanner function?

Hope you can help & many thanks.[/QUOTE]

See my post here: [http://ubuntuforums.org/showthread.php?t=94064](http://ubuntuforums.org/showthread.php?t=94064)


p.s.: Some other tips.

--For anyone wanting to print in GIMP, you will (probably) need to do this:

1. Open a picture
2. Click File/Print
3. Make sure your printer is in the Printer Name box and click "Setup Printer"
4. Postscript Level 2 should be selected.
5. Remove the -oraw option from the end of the print command in the Command box
6. There should be a PPD file for your printer in /etc/cups/ppd/ (mine's called Stylus-DX4200---CUPS+Gutenprint-v5.0.0-rc2.ppd)
7. Click OK and click Save Settings

--I had a problem with Firefox (1.5) using an old style print dialogue and refusing to print because my "paper size wasn't supported" which I solved by deleting my profile and restarting Firefox. YMMV.

---

### Post by brucetan on 2006-03-01
Thanks.  I will try it this weekend and will update the result on this thread.

---

### Post by jmullagh on 2006-03-12
Damn... I used your method and went the 'Non-Lazy Way' and my Epson CX7800 came up like a dream! Thank You so much!

---

### Post by mrcaseyj on 2006-03-14
Thanks fubarbundy, I probably couldn't have got my Epson Stylus CX3810 working without your procedure. Your procedure worked almost as listed but there was one snag. It may have been because I'm running Kubuntu (5.10 Breezy Badger). At the dpkg-source command it came back with the error:

Unmet build dependencies: libcupsys2-dev libcupsimage2-dev libgtk1.2-dev libreadline5-dev libijs-dev (>= 0.35-1) flex chrpath (>= 0.12) dpatch
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

All I had to do was copy and paste the list of packages from the error message to the end of a sudo apt-get install command and then edit out the parts in parenthesis. So the command I used was this:

```
sudo apt-get install libcupsys2-dev libcupsimage2-dev libgtk1.2-dev libreadline5-dev libijs-dev flex chrpath  dpatch
```

I doubt anyone would want to copy that command exactly, you should customize it according to your error message if you get one.

I used your lazy method for the last part and it worked fine. At first I didn't see any indication that I needed to remove cupsys-driver-gimpprint-data, but the next day when I started Synaptic it said I had one broken package. It said to use the filter to find the broken package, but the filter didn't seem to work, so I just searched for the name cupsys-driver-gimpprint-data and found a red box next to it. I right clicked on it, selected remove, and clicked apply to remove it.

The good news is my printer makes beautiful prints. The Bad news is I have to put it in at least 1440x720 mode or my printouts have faint streaks in them. They look just like a clogged nozzle. I know there are no clogged nozzles because the streaks are through all the colors on the cups test page, the nozzle test print has no missing parts, and the printer prints perfectly from windows or when doing copies. I think this may be a lack of head alignment in the gutenprint driver. In 1440x720 mode my cx3810 prints unidirectional and pretty slowly. Changing the setting to bidirectional seems to be ignored, and doesn't speed it up. I've played with the dither, interleave, printing direction, and resolution settings, and only found the resolution setting to solve the streak problem. I've tried aligning the print heads in Windows and then printing in Kubuntu without turning the printer off, but there was no noticeable improvement.

---

### Post by campidg on 2006-04-26
Hi Fubarbundy,

I tried your instructions and got as far as point 3 when these error messages appeared:
[I]No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.dsc'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.diff.gz'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1.orig.tar.gz'.
[/I]
I pressed on regardless but to no avail.  

I have the cheap and nasty CX1500 which does not work at all with the installed drivers aprt from printing a blank test page.  linuxprinting.com says it should work perfectly well with gutenprint.  What am I doing wrong?

Thanks Cam

ps I have downloaded gutenprint-5.0.0-rc2 as a ppc.dmg file and a tar.bz2 file.  Any advice on who to install them would be greatly appreciated.

---

### Post by sunshine on 2006-05-10
I'm having the same problem as campidg, any advice would be great.

---

### Post by fubarbundy on 2006-05-11
[QUOTE=campidg]Hi Fubarbundy,

I tried your instructions and got as far as point 3 when these error messages appeared:
[I]No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.dsc'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1-2.diff.gz'.
No such file `gutenprint_4.3.99+cvs20051122.dfsg.1.orig.tar.gz'.
[/I]
I pressed on regardless but to no avail.  

I have the cheap and nasty CX1500 which does not work at all with the installed drivers aprt from printing a blank test page.  linuxprinting.com says it should work perfectly well with gutenprint.  What am I doing wrong?

Thanks Cam

ps I have downloaded gutenprint-5.0.0-rc2 as a ppc.dmg file and a tar.bz2 file.  Any advice on who to install them would be greatly appreciated.[/QUOTE]
That's because these are the sources for the Dapper release, which have now been updated. At least at the moment, the working line would be: 
```
wget ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_5.0.0~rc2.orig.tar.gz ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_5.0.0~rc2-0ubuntu6.diff.gz ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/gutenprint_5.0.0~rc2-0ubuntu6.dsc
```

You can find the appropriate versions by visiting [ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/](ftp://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/) in your browser and looking for the latest *orig.tar.gz, *diff.gz and *dsc files.

Keep up now ;)

---

### Post by gigigentoo on 2006-05-13
1_:D  tx for the howto , my epson stylus DX4250 now prints ok 
2_:-k  FYI, I had an error with the cupsys when trying to build the packages.
 It was complaining about the cupsys version. So I basically followed the same steps to download , build the packages, add  a repository to the local files.

Thankx again
I now have to install last gutenprint version under my gentoo box ;)

---

### Post by marcw on 2007-07-09
Even though this thread was started more than 1.5 yrs ago, it helped me greatly.  I acquired a newer Epson printer (R380) whose drivers weren't included in Feisty.  However I did find out that they are to included in Gutsy.  This is because Gutenprint recently had a new release - 5.0.1.  Using your guide and making the obvious name changes I was able to get these latest drivers installed without a hitch.  Thanks!

p.s. Can anyone can tell me why, when using the new driver, things will print just fine but the paper won't eject when finished?

---

