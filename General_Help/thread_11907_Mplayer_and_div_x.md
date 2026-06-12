---
title: "Mplayer and div x"
date: 2005-01-20
forum: General Help
---

### Post by new2linux on 2005-01-20
Hi,

   I just installed linux for the first time on my computer.  I had used the live cd of 
ubuntu a bunch of times, and I liked it so much I decided to put it onto one of my computers.  It installed fine and was working great.  Then I tried to watch some divx and mpg. files.  Obviously they didn't work, so I looked around and discovered mplayer.  However, when I ran the installer, it came up with a bunch of errors saying that some packages were missing.  I don't have that computer hooked up to the internet, so I decided to try to download the packages, burn them, and then install them.  I soon discovered that this doesn't work.  When you install one package, it wants you to install another and so on.  

   Is there any way that I could figure out all the packages that it could possibly need and their dependencies and download them?  
    I would love to keep Linux on my computer bcause I really like it, but if I can't get things like this working, I may need to switch back.

Thanks for any help,
EHD

---

### Post by Ste on 2005-01-20
[QUOTE=new2linux]Hi,

   I just installed linux for the first time on my computer.  I had used the live cd of 
ubuntu a bunch of times, and I liked it so much I decided to put it onto one of my computers.  It installed fine and was working great.  Then I tried to watch some divx and mpg. files.  Obviously they didn't work, so I looked around and discovered mplayer.  However, when I ran the installer, it came up with a bunch of errors saying that some packages were missing.  I don't have that computer hooked up to the internet, so I decided to try to download the packages, burn them, and then install them.  I soon discovered that this doesn't work.  When you install one package, it wants you to install another and so on.  

   Is there any way that I could figure out all the packages that it could possibly need and their dependencies and download them?  
    I would love to keep Linux on my computer bcause I really like it, but if I can't get things like this working, I may need to switch back.

Thanks for any help,
EHD[/QUOTE]
 Most of the packages are available here.
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

Use synaptic to tell you what it's going to install then take a note of the packages, download them then install.

---

### Post by new2linux on 2005-01-20
Thanks for responding,

Is there a version of synaptic for windows?  The computer I have connected to the internet is a win 98, or I can also get onto a win xp.

I did try connecting the ubuntu box, but it wasn't finding my modem, and when I tried to plug in a crossover cable that is connected to an xp box which is sharing a connection, it didn't work.  So I figured that the easiest thing to do would be to d-load it on my 98 box and burn the files


EHD

---

### Post by jonny on 2005-01-20
mplayer is apparently easy to install if you have a recent Pentium.  If you have an Athlon or older Intel chip, you'll need to compile it yourself, and that will increase the number of dependencies dramatically; I have an Athlon, so haven't bothered myself.  There's more advice in [this thread](http://www.ubuntuforums.org/showthread.php?t=9850) or, alternatively, in the [unofficial how-to guide](http://ubuntuguide.org/)  - an awesome resource.

If the computer's not connected to the internet, things get a bit trickier.  It might be quicker to physically move the machine to a convenient broadband connection, or to beg / steal / borrow an external serial modem (these almost always work with Linux) but you can download packages the hard way if that's impossible.

I can't test this approach (my office is an ubuntu free zone) but, working from memory, you need use Firefox to navigate to ftp site containing the packages you want (try looking in the repositories list in Synaptic Package Manager to find out the url) and download all of the packages onto a CD.  Synaptic will also tell you the dependencies for a package, so you can build up a full recursive list by searching on them, too... but this might take some time if you're doing it by hand.

Once you have the packages on your ubuntu box, you need to open up a terminal session, navigate to the appropriate directory (use CD to change directory) and use the command dpkg to install them one at a time, starting from the bottom of your list.  I seem to remember that the syntax is
```
dpkg -i <filename>
```
but you can always type
```
man dpkg
```
to get the full syntax.

This approach is not for the faint hearted.  Be ready to meet lots of obstacles and hit a steep learning curve.  Good luck!

---

### Post by new2linux on 2005-01-20
Thanks
Well, here goes.

---

### Post by Rule on 2005-01-20
good luck :smile:

---

### Post by jdodson on 2005-01-20
i have a AMD chip, albiet it is much newer so it plays stuff fine.  though you are right and older system does bog down using mplayer.  i had a 900MHZ p3 and i could play dvds with some minimal skipping.  i could watch smaller frame videos 300x240 with no worries.  anything larger really bogs down specially if it is a .wmv or .ra or .qt because of the way mplayer plays them.

anyways, to check it out, [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has good info on it.  if you cant play them fast at least you can do it.  

to answer the question on synaptic for windows, suffice it to say it wouldnt work well as synaptic is a package manager for a unix like OS, windows does not fit that bill.

---

### Post by Ste on 2005-01-20
[QUOTE=jdodson]windows does not fit that bill.[/QUOTE]

Nice pun :)

---

