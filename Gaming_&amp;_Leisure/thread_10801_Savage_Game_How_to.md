---
title: "Savage Game How to"
date: 2005-01-11
forum: Gaming &amp; Leisure
---

### Post by puzzledm on 2005-01-11
Has anyone got savage the game working?  And how did you do it?

After not getting anywhere with the demo I thought I would try the full game as I found it for a £5 however I have come across the same problems.

Something to do with the updater not working?

---

### Post by puzzledm on 2005-01-11
It has something to do with links to new libs or something ... I am quite new to linux.  When I run the game binary I get this error message:

ImportError: libssl.so.0.9.6: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  
bailing out.

I have libssl 0.9.7 installed and so i think I need to link to that how do I do that?

---

### Post by Perfect Storm on 2005-01-12
I'm downloading the demo now and i'll report back if I experience the same problem.

---

### Post by valadil on 2005-01-13
If you're trying to run it on a 64bit system make sure you do a 32bit chroot.  Savage can run in 64bit mode, but I haven't gotten it to do that reliably.

Make sure you install the SEP patch.  S2games' linux developer left, so when savage got updated to 2e the linux version didn't get updated.  The people over at SEP grabbed all the content and packaged it up for us linux folks.  [http://notforidiots.com/SEP](http://notforidiots.com/SEP)

Just copy the sep tarball into ~/games/Savage and untar it there.  I'm not sure if you need the other savage patches installed first.  

Savage generally complains about a few dependcies.  They should all be in apt.  I'm pretty sure it'll bitch about libtiff.so.3 but Ubuntu doesn't want to run anything older than libtiff4.  You can symlink the libs and savage will run fine.

---

### Post by Perfect Storm on 2005-01-13
Libtiff.so are complaining LOL rather than that when you made the symblinks it runs perfect (for me atleast)


.:=The AI Dude=:.

---

### Post by puzzledm on 2005-01-13
Probably simple question ... but how do you create a symlink?

---

### Post by puzzledm on 2005-01-13
I have installed the files from the cd into a folder called ~/Games/Savage.  I then run "chmod 755 -R ~/Games/Savage" to remove the root priveledge thing.  

And straight away the savage.bin won't run - Gnome telling me that it is an executable and I have to rename it to something (who knows what?).  

So I open a terminal and run savage.bin from there (which works so why can't gnome do the same!).  The savage.bin doesn't work saying "error running updater bailing out!" 

so I run the updater the same way, in a terminal, and it says something about not being able to find libcrypto.so.0.9.6.  

So I followed the above instructions and unzipped the file SEP-1.2e.tar.gz into the Savage folder.  

And nothing has changed!!

---

### Post by valadil on 2005-01-14
puzzledm,

Savage includes its own libs folder.  These libs need to be loaded for savage to run.  The savage executable (which is just a shell script) loads all those and then calls savage.bin.  Try running savage instead of savage.bin.

Symlinks are created with ln.  They're kind of like shortcuts in windows but more powerful.  If savage is bitching about libtiff.so.3 not existing, I would run ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3.  This makes a file called libtiff.so.3 that points to libtiff.so.4 and says 'use that guy over there.'  The -s option makes a soft symlink I think.  Not quite sure why but that's what I always use.

---

### Post by Perfect Storm on 2005-01-15
Know I've playing around with the demo, I've decided to buy the game!!!  =D>
Excellent gameplay! and diffently a worthy game and recommendable!

---

### Post by puzzledm on 2005-01-19
So I have it working ... eventually!  Hurrah!

It is a very cool game I shall have to get into it more.  However one annoying thing ... 

to get it running I have to open a terminal 'cd' to the directory and run './savage.bin' 

making a shortcut doesn't work ... running it from anywhere else doesn't work (i.e. running '/home/matthew/games/savage.bin') ... and double clicking on it doesn't work (gnome just says it is executable and I should either rename it properly (which i don't understand) or just not load it) 

anybody have any ideas?!!?

---

### Post by valadil on 2005-01-20
Try running savage with the absolute path instead of savage.bin.

If that doesn't work you can put multiple lines into one shortcut, just separate them by semicolons.

cd /home/matthew/games/Savage/ ; ./savage

If that doesn't work, drop the above lines in a text file, name it start_savage.sh, chmod it a+x, and point your launcher to the text file.

---

### Post by puzzledm on 2005-01-20
I followed your instructions made a text file and even copied it into /usr/bin so now I can just alt-f2 and type savage and it loads ... how good is Linux!

---

### Post by ming0 on 2005-02-23
[QUOTE=valadil] The -s option makes a soft symlink I think.  Not quite sure why but that's what I always use.[/QUOTE]

As far as I understand, a soft symlink is basically the same as a windows 'shortcut' and a hard symlink is sort of a real copy of the file that mirrors the original.

I'm sure there's a better explanation somewhere :)

---

### Post by menachem on 2005-03-03
[QUOTE=ming0]As far as I understand, a soft symlink is basically the same as a windows 'shortcut' and a hard symlink is sort of a real copy of the file that mirrors the original.

I'm sure there's a better explanation somewhere :)[/QUOTE]
 Check out: [http://www-rohan.sdsu.edu/doc/debian/ch-advanced.html#s-advanced-files](http://www-rohan.sdsu.edu/doc/debian/ch-advanced.html#s-advanced-files)

---

