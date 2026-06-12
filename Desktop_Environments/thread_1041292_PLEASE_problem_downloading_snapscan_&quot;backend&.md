---
title: "PLEASE: problem downloading snapscan &quot;backend&quot;"
date: 2009-01-16
forum: Desktop Environments
---

### Post by PierreRussellStraddler on 2009-01-16
Hello

Another post about my scanner that doesn't work.

PLEASE, if anyone can PLEASE help!

the story--

the scanner isn't working.  it is an acer 1240.  everywhere I look it says that this scanner is supported, and should work with linux/ubuntu.

when I try to scan, I get this:

Failed to open device 'snapscan:libusb:003:003' invalid argument



so I went here:  [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

and got this info:



# untar sane sources
tar xvzf sane-x.x.x.tar.gz

-----this worked fine.  On my desktop, I now have

sane-backends-1.0.19




# move in the backend directory

cd sane-x.x.x/backend



----that seemed to work fine, too:

pierre@pierre-desktop:~/Desktop$ cd /home/pierre/Desktop/sane-backends-1.0.19/backend
pierre@pierre-desktop:~/Desktop/sane-backends-1.0.19/backend$ 





# untar snapscan sources

tar xvzf ../../snapscan-x.x.tar.gz

-------here is where the problems begin.  What is up with ../../ ?  What do I put in place of those ".."?  because when I type tar xvzf ../../snapscan-x.x.tar.gz

I get this:

tar: ../../snapscan-x.x.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
pierre@pierre-desktop:~/Desktop/sane-backends-1.0.19/backend$ 

please please what is the appropriate code! :cry:


and then the party stops there, and the frustration mounts, and the old lady says "you could scan perfectly fine in windows--what's so great about ubuntu if you can't scan, which is something you need to do all the time?" which begets more frustration and so on and so on.



Other web sites I have visited vis a vis this problem have been equally not helpful.  those sites include:

[http://www.blog.arun-prabha.com/2008/02/26/howto-setting-up-acer-320u-in-ubuntu/](http://www.blog.arun-prabha.com/2008/02/26/howto-setting-up-acer-320u-in-ubuntu/)

and

[http://www.vazfer.net/downloads/scanner.htm](http://www.vazfer.net/downloads/scanner.htm)


which is to say I am doing all the leg work and home work and smash my head against the wall work I can, but am failing constantly and in so doing, not scanning, which (in my narrow world) is a problem.



this shouldn't be too hard, I don't think, as the scanner seems to be supported.

P L E A S E H E L P M E A N Y O N E !


if this isn't an appropriate question for this section of the forum, PLEASE let me know and I will put this in the appropriate section.  Also, if these questions are better suited for another forum all-together, let me know and I will go there.



here is the rest of the code from the snapscan.sourceforge, none of which I was able to put into my computer with any success.



# (this will overwrite snapscan* files) as root, compile and install sane

machine# cd sane-x.x.x; ./configure; make; make install




--------what means this "machine#"?






# detect your scanner device

machine# tools/find-scanner
   find-scanner: found scanner "AGFA SNAPSCAN 310 1.20" at device
   /dev/XXXXX 

# if you want your scanner to be recognized easily, create a link:

machine# ln -s /dev/XXXXX /dev/scanner

# you should now scan using xscanimage

machine$ xscanimage





thank you again for any help, as I cannot scan and as such, cannot work, which is a problem.

thank you.

pierre russell straddler.

---

