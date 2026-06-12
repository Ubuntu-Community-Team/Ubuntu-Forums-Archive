---
title: "Need help printing - Canon MP600R on network?"
date: 2009-03-13
forum: General Help
---

### Post by Xero Xenith on 2009-03-13
**_NOTE. THE GUIDE BELOW DOES NOT WORK IN KARMIC/LUCID DUE TO [THIS ISSUE]("https://bugs.launchpad.net/ubuntu/+bug/458445"). Workaround: INSTALL [THIS PACKAGE]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download"). Then it works 100% perfectly :)_**

I have a Canon MP600R printer connected to the network, and am dual-booting Jaunty alpha 6 and standard 8.10, both 64-bit. I simply need to be able to print from it - which is causing quite a lot of frustration: there are no official Linux drivers for it.

[There's this thread]("http://ubuntuforums.org/showthread.php?t=604748"), but the instructions don't seem to work - after adding the extra repo I still get the message "E: Couldn't find package libcnbj-2.6". Oddly enough, on my old 32-bit PC this guide worked just fine - albeit many *many* months ago. [This looks promising]("http://mp610.blogspot.com/2008/10/canon-pixma-scanners-are-now-network.html"), but I don't really understand it. 

**_NOTE. THE GUIDE BELOW DOES NOT WORK IN KARMIC/LUCID DUE TO [THIS ISSUE]("https://bugs.launchpad.net/ubuntu/+bug/458445"). Workaround: INSTALL [THIS PACKAGE]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download"). Then it works 100% perfectly :)_**

As you can tell, I'm really confused. Any help would really be appreciated :)

---

### Post by Xero Xenith on 2009-03-14
bump...

---

### Post by Xero Xenith on 2009-03-16
I hate to be "that guy", but here's another bump. Any help at all?

---

### Post by Xero Xenith on 2009-03-18
my last bump before I give in...

---

### Post by Xero Xenith on 2009-03-20
That is, unless this is my last bump. :P

---

### Post by Xero Xenith on 2009-03-21
Can anyone help at all?

---

### Post by Xero Xenith on 2009-03-23
bump

---

### Post by SSamiK on 2009-04-01
I'm trying to get the same printer going, I'm at no help to you at this point, but I'll post back if I'm having any success. And please, if you have gotten this sortet, please share how you did it.

---

### Post by SSamiK on 2009-04-01
I've got it up and running! 

1: Download and install cnijfilter-common-2.80-1.i386.deb
cnijfilter-mp600series-2.70-3.i386.rpm

cnijfilter-common_2.80-1_i386.deb you'll find [here]("http://support-au.canon.com.au/contents/AU/EN/0100083403.html")


cnijfilter-mp600series-2.70-3.i386.rpm you'll find [here]("http://software.canon-europe.com/software/0027403.asp")

The last one you'll have to convert to a deb with alien.
```
sudo aptitude install fakeroot alien
fakeroot alien -i cnijfilter-mp600series-2.70-3.i386.rpm

```

then install them both with ether gdebi or dpkg 
```
sudo dpgk -i cnijfilter-common_2.80-1_i386.deb cnijfilter-mp600_2.70-3_i386.deb
```

Then you'll have to install the cups-bjnp driver witch is available [here]("http://sourceforge.net/project/showfiles.php?group_id=234369&package_id=284515").
You'll have to compile it from source- 
First, satisfy a dependency: 
```
sudo aptitude install libcups2-dev 
```

Unpack the cups-bjnp you downloaded and enter that folder. 
To compile type:
```

./configure --prefix=/usr
make
```
Then we can test to see if it will work: ```
./bjnp 

```

If it's working it will print out something, in my case with a MP600R:
```
./bjnp 
network bjnp://192.168.0.104:8611 "Canon MP600R" "Canon MP600R 192.168.0.104" "MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe;SOJ:TXT01,BJNP2;MDL:MP600R;CLS:PRINTER;DES:Canon MP600R;VER:1.01;STA:10;FSI:03;WCH:00000000;HRI:OTH;MSI:DAT,E3;"

```

Now to install the driver: ```
sudo make install
```
And restart cups:
```
sudo /etc/init.d/cups restart
```

Now add your printer as normal under [System - Administration - Printing] Your printer should sow up under search for printers, add it and choose the PIXMA MP610 Gutenprint driver. If all went well, as it did for me, happy printing! ):P

---

### Post by Xero Xenith on 2009-04-01
Fantastic, I'll give that a go now! Only thing is, I removed Intrepid once Jaunty hit beta, but if it means being able to print I'll be more than happy to install again. Also I'm running 64-bit, so let's see what happens... but thanks so much for posting :D

EDIT: hit a snag, I can't find "cnijfilter-mp600series-2.70-3.i386.rpm" so instead I got "cnijfilter-mp600-2.70-2.i386.rpm". I hope this still works, but I'm going ahead with it anyway (Jaunty is meant for breaking ;))

NOTE TO MODS/ADMINS: this isn't a topic specifically for 9.04, it's about getting this printer working full stop - like I said, I'm going to test this in 8.10 if 9.04 doesn't work. So please don't move this to the ubuntu+1 forum.

EDIT 2: hit another snag; 64-bit alien doesn't like 32-bit RPMs. [However this page]("http://inst.eecs.berkeley.edu/~scheme/precompiled/Linux/") provides a solution:
> 	Use a 32-bit computer to 'alien STk-4.0.1-ucb1.3.6.i386.rpm'
	On the 64-bit computer, run 'apt-get install ia32-libs'
	copy the $STK.deb file from the 32-bit computer to the local amd64, ie:
	'scp [email]user@32bHost:~/$STK.deb[/email] root@local64bHost:~/.'
	On the 64-bit computer, run 'dpkg --force-architecture $STK.deb'

...so I'm running it through a VM with 32-bit Ubuntu, and I'll upload the resulting file. Let's see how this plays out...

EDIT 3: OK, that's done - got my two .debs. Now I'm gonna try and install them with dpkg's --force-architecture flag on the 64-bit machine.

EDIT 4: Done, but one depended on libcupsys2, but that's in the repos. Both are now installed.

EDIT 5: I assume you mean to download the file "cups-bjnp-0.5.tar.gz". That's the one I'm using.

EDIT 6: My output for ./bjnp :

```
chris@chris-desktop:~/Downloads/printubuntu/cups-bjnp-0.5$ ./bjnp
network bjnp://192.168.0.8:8611 "Canon MP600R" "Canon MP600R 192.168.0.8" "MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe;SOJ:TXT01,BJNP2;MDL:MP600R;CLS:PRINTER;DES:Canon MP600R;VER:1.01;STA:10;FSI:02;WCH:00000000;HRI:OTH;MSI:DAT,E3;"

```

This looks very promising :D

EDIT 7: System-Administration-Printing found the printer; it's searching for drivers...

EDIT 8: The printer is added!

EDIT 9: Tried two test pages: no error messages either side, yet no output and no sign of the printer receiving the job... :S

EDIT 10: D'ohh!! Stupid. I'd picked the wrong driver; I just charged ahead with what was instantly recommended, instead of going for the Pixma MP610 Gutenprint driver *you* recommended. Now I can print! Yay! :D Thank you SO much :D

EDIT 11: Hmm... another D'oh. Text comes out fine, but all images (including the Ubuntu test page) have a very weird blue "shadow" - I'll try and scan some to show you...

EDIT 12: Attached an image (scaled down to fit forum requirements) and a PDF (zipped to fit forum reqs). This is very strange, but I'm still very happy I can print text :)

EDIT 13: Posting just this edit from an 8.10 32-bit liveCD, which I've just set up to print as per your instructions. I still suffer the same problem down do the pixel, so it can't be a 9.04 problem.

EDIT 14: YES!!! Got it fixed! The trick is to use the MP**500** drivers, not MP610. I can now print perfectly from this LiveCD - now to reboot into Jaunty and try the same. Thanks so much for your guide, btw! :D

EDIT 15: WOOHOO!! Works fine on my installed 64-bit Jaunty. Thank you so SOOO much :D

And [here's the .deb from Edit 2]("http://rapidshare.com/files/216282565/cnijfilter-mp600_2.70-3_i386.deb"). It's only required for 64-bit users, as they can't alien the RPM to a DEB themselves. Sorry about the RapidShare, but at least the file should stay up that way; I have a premium account with them.

---

### Post by SSamiK on 2009-04-02
I'm so glad to hear that you got it working! I was not aware of the picture print problems, but just as you suggested, the MP500 driver fixed this. So thank you for that one! :D

---

### Post by Xero Xenith on 2009-04-30
A little update - I've just confirmed it working perfectly with Kubuntu 9.04 Jaunty 64-bit, exact same method, though instead of System -> Administration -> Printing, it's under K menu -> Computer -> System Settings -> Advanced -> Printer Configuration. A bit more of a mouthful :)

EDIT 05/May/2010: This continues to work in Lucid, even 64-bit, as long as the extra package is installed (and special measures are taken to install the 32-bit packages, as I explained on the first page). :)

---

### Post by edubidu on 2010-12-31
Hello!

I tryed to apply the tutorial. My problem is that i can't do this:
[HTML]fakeroot alien -i cnijfilter-mp600-2.70-2.i386.rpm [/HTML]it begins, I see it begins to creates a .deb package. But Then this output:

[HTML]error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package cnijfilter-mp600: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
    dpkg --no-force-overwrite -i cnijfilter-mp600_2.70-3_i386.deb
(Reading database ... 219620 files and directories currently installed.)
Preparing to replace cnijfilter-mp600 2.70-3 (using cnijfilter-mp600_2.70-3_i386.deb) ...
Unpacking replacement cnijfilter-mp600 ...
Setting up cnijfilter-mp600 (2.70-3) ...[/HTML]... then it deletes the .deb package it wanted to create.

It even won't with 

[HTML]fakeroot alien -i --scripts cnijfilter-mp600-2.70-2.i386.rpm 
error: incorrect format: unknown tag
    dpkg --no-force-overwrite -i cnijfilter-mp600_2.70-3_i386.deb
(Reading database ... 219620 files and directories currently installed.)
Preparing to replace cnijfilter-mp600 2.70-3 (using cnijfilter-mp600_2.70-3_i386.deb) ...
Unpacking replacement cnijfilter-mp600 ...
Setting up cnijfilter-mp600 (2.70-3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/HTML]
Using Ubuntu 10.04 LTS (lucid lynx) on a i386

What's going wrong?? 

Thanks for help

---

### Post by edubidu on 2010-12-31
Ah, what i see: 

the -d option generates the package, the -i option installs...

[HTML]fakeroot alien -d --scripts cnijfilter-mp600-2.70-2.i386.rpm [/HTML]

---

### Post by edubidu on 2010-12-31
Me again.

Finally, the only thing that seems to work is the Canon Pixma MP830 Cups+Gutenprint driver, included in the lucid lynx installation.

Dear, I tried for some 5 hours to find out that. I post it here, for some other people....

I installed with the Ubuntu Software Center the packages needed for canon. Type "canon" into the search field.
Some packages seem not to be authenticated. If you want them, use apt-get install.

Here all the packages I installed (maybe some are even not needed, I'm too tired to test this now):


[LIST]
[*]libcnbj-2.6
[*]bjfilter-2.6
[*]cnijfilter-common
[*]jsgutenprint
[*]cupsys-driver-gutenprint
[*]gimp-gutenprint
[*]libgutenprintui2-1
[*]libgutenprint-dev
[/LIST]
:lolflag:

---

### Post by SSamiK on 2012-03-11
A small little update, if someone still finds this thread useful. 

I've just used my initial guide to get my MP600R working in Linux Mint 12, and it still works. But some updates are due. 

Hints: Fix for libcupsys2 dependencie: [http://ubuntuforums.org/showpost.php?p=10864432&postcount=7](http://ubuntuforums.org/showpost.php?p=10864432&postcount=7)


Newer cnijfilter-common: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html")

Will make an updated post if anyone craves it.

---

### Post by shawkes on 2012-05-13
The link to the French website is broken. ERREUR 404 - Document non trouvé
Do you have a new link or alternative source to resolve the libcupsys2 dependency?

---

### Post by SSamiK on 2012-09-30
The code you want is in the post, just make the file by copy/pasting the text. ;-)

---

