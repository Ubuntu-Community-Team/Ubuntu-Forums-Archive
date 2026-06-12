---
title: "aacgain installation and usage"
date: 2006-09-17
forum: Desktop Environments
---

### Post by the7trumpets on 2006-09-17
Has anyone used aacgain? - [http://altosdesign.com/aacgain/](http://altosdesign.com/aacgain/)

It's very symilar to mp3gain which is available via apt-get, but aacgain is not available with apt-get. This is the first thing I have ever installed from the source, but I think I did it right, I'm just not sure. It didn't spit out any errors when I ran:

./configure
sudo checkinstall

After that I was able to enter 'aacgain -h' and get the help screen.

The problem is the program simply doesn't do what it says it will. When invoking it on apple lossless .m4a files, I get the following response before it even tries to calculate the replaygain:

[INDENT]Error opening file: Track Name.m4a
Track Name.m4a is not a valid mp4/m4a file.[/INDENT]

When I run it on a 192kb/s AAC file it actually calculates the replay gain, but I get the following response error:

[INDENT]terminate called after throwing an instance of 'MP4Error*'
Aborted
[/INDENT]

After that, there is a temp file .m4a file in the directory, but it cannot be opened or played by anything.


Does anyone have any clue what is going on? I am at the mercy of the all knowing wise ubuntu people :)

Also, is there any chance that aacgain will find its way into the universe or multiverse repositories anytime soon? (soon enough that I can put this on hold for a few weeks and then install it from the repository and have it work right the first time?)

---

### Post by MGStreak on 2007-04-28
> **the7trumpets said:**
> 
Also, is there any chance that aacgain will find its way into the universe or multiverse repositories anytime soon? (soon enough that I can put this on hold for a few weeks and then install it from the repository and have it work right the first time?)
I have been having similar issues with aacgain... I gave up on trying to install it, instead booting up Foobar2000 in WINE, and using it to apply replaygain tags to all my m4a's... only problem is, without installing aacgain, Amarok can't read the tags... so I'm still stuck.  At least the files are tagged for whenever aacgain IS added to some repository...

Anyone know anything?

Perhaps a simple way to install it?

---

### Post by MGStreak on 2007-05-08
> **the7trumpets said:**
> Has anyone used aacgain? - [http://altosdesign.com/aacgain/](http://altosdesign.com/aacgain/)


Hi all... 

Aacgain has just been updated to version 1.7... but there's still no solution for installation (that I've found.)  Can anyone help out this n00b (as well as those others who are wondering the same thing?)

Thanks in advance :-)

---

### Post by jopsen on 2007-08-30
I've just done a little post about Amarok and ReplayGain:
[http://jopsen.dk/blog/2007/08/volume-normalization-with-amarok](http://jopsen.dk/blog/2007/08/volume-normalization-with-amarok)

There's a .deb package with AACGain too:
[http://jopsen.dk/blog/download-manager.php?id=4](http://jopsen.dk/blog/download-manager.php?id=4)

---

