---
title: "HOWTO:  Crossword download/print system"
date: 2007-02-12
forum: Gaming &amp; Leisure
---

### Post by Mateo on 2007-02-12
This system will automatically download and print the day's crossword puzzle from the Houston Chronicle.  It also saves an answer key to your home directory.  Alter as needed.

I had to modify the original source code to have it do the answer key.  That's the second program.  If you are a coder and know how to combine this into a single program, be my guest.  Credit to the author, I only hacked his code to make the second program and changed the script to bash (and used LPR instead of GS for printing):

[http://www.ctan.org/tex-archive/macros/latex/contrib/gene/crossword/AcrossLite/](http://www.ctan.org/tex-archive/macros/latex/contrib/gene/crossword/AcrossLite/)

This is my first HOWTO so it probably has mistakes; I'll correct as they're found.

**Step 1 - Create working directories**

We're going to create a temporary directory for setting everything up.

```
mkdir /tmp/crossword/
cd /tmp/crossword/
```

You should do everything else from this directory.

**Step 2 - Download and install components**

First make sure you have texlive.

```
sudo apt-get install texlive texlive-base texlive-base-bin
```

Then get the utilities necessary for compiling:

```
sudo apt-get install psutils build-essential
```

Next you want to download the file that is attached to this post.  Scroll down and get it  Then come back and run this:

```
tar -xf nytconv2.c.tar.gz
sudo mv nytconv2.c /tmp/crossword/
wget http://www.tug.org/tex-archive/macros/latex/contrib/gene/crossword/AcrossLite/nytconv.c
gcc -o nytconv nytconv.c
gcc -o nytconv2 nytconv2.c
sudo mv nytconv /usr/bin/
sudo mv nytconv2 /usr/bin/
wget http://ftp.inf.utfsm.cl/pub/tex-archive/macros/latex/contrib/gene/crossword/cwpuzzle.dtx
wget http://ftp.inf.utfsm.cl/pub/tex-archive/macros/latex/contrib/gene/crossword/cwpuzzle.ins
tex cwpuzzle.ins
sudo mv cwpuzzle.sty /usr/share/texmf-texlive/tex/latex/base/
```

This next step is very important, otherwise it will not all convert properly.  Run the following program and select "rehash".  This allows latex to use the cwpuzzle.sty (which tells it how crossword puzzles work).

```
sudo texhash
```

**Step 3 - Create script file**

The follow script file should be enough to get you going.  Replace YOURPRINTER with the name of your printer (as shown in System > Administration > Printing).  Name the script something like autopuz (that's what I used).

```
#!/bin/bash
mkdir /tmp/crossword
cd /tmp/crossword
todaydate=`date +%m-%d-%Y`

wget http://www.chron.com/content/fun/games/xword/puzzles/today.puz

#Processing unsolved puzzle
nytconv today.puz >today.tex
latex today.tex
dvips  -x 1400 today.dvi
psnup  -l -2 -pletter today.ps today.wps
echo \"quit\" >>today.wps
lpr -P YOURPRINTER today.wps

#Processing solved puzzle
nytconv2 today.puz >today2.tex
latex today2.tex
dvips  -x 1400 today2.dvi
ps2pdf today2.ps ~/$todaydate.pdf

rm -f /tmp/crossword/*.*
rmdir /tmp/crossword
```

then move it so it can be used from anywhere.

```
chmod +x autopuz
sudo mv autopuz /usr/local/bin/
```

**Step 4 - Decide how you want to run the script**

You can either create a launcher or run a cronjob (or both!).

For the launcher, I don't need to tell you how to do that.  Here's the icon I used:

```
wget http://www.shapefit.com/crossword_icon.gif
sudo mv crossword_icon.gif /usr/share/pixmaps/
```

For a cronjob, I think they update their crosswords pretty early, but I'm not sure when.  Either set it for when you know your computer will be on, or if you keep it on all the time, when you know you'll be asleep (unless the printer is in your bedroom).

---

### Post by wactuary on 2007-03-14
This is a great howto!  I have been looking for a way to do this.  It's been a major stumbling block in getting my folks over to Linux.  They couldn't understand why I would use an OS that couldn't print the morning crossword.  The ancient and unusable AcrossLite binary was really frustrating.

A few things I found on using the how-to:

Other packages to include in the apt-get install command:  psutils build-essential

psutils has the psnup command and build-essential to get the gcc to work properly.

I found that the texhash command had to be done as "sudo texhash".

Although I'm sure it is better to explicitly specify the printer, for me, just lpr today.wps was enough to make it work.

Also since I was looking for the NYT puzzle which requires a log-in, I'm not sure how to get wget to work.  And they name the puzzle with the date in the format mmmddyy.puz.  For me, it was simpler to comment out the wget in the shell and replace today.puz with $1 in the 2 locations it exist.  Then I can download the file manually and call the script as "autopuz.sh filename.puz" to run it.  I haven't ruled out automating the download as you have, but that will wait for another day.

Finally, maybe add a quick comment to the beginner (like myself) that the warnings when compiling are OK as long as the executable is created.  I had initially installed gcc instead of build-essential so I was getting compile errors.  Once I corrected the problem, it took me a while to realize it was fixed because the warnings still appeared.  Eventually I did an ls and realized I had the executables and all was good from there.

Thanks again.  This is a great fix to a niggle I've had for ages.

Chris

---

### Post by Mateo on 2007-03-14
Thank you very much, **wactuary**, I'm glad you liked it.  I will edit the howto for the mistakes you point out, thanks a bunch. I forgot which packages were necessary for the compile (since i installed them a long time ago), so I didn't include it.

Also, might i suggest that you uninstall tetex and instead get Texlive (it should be in synaptic).  Tetex is old and not maintained anymore, texlive is though.  When I update the howto later I'll change this part.

By the way, this page shows how to get the [NYT]("http://www.ctan.org/tex-archive/macros/latex/contrib/gene/crossword/AcrossLite/") puzzle. I'm not a subscriber so I can't try it.  Use this **instead of** the script I posted in the howto.

I don't know perl so I can't help modify it for you, but it doesn't look too difficult.  I'd remove the section on USA Today and also for the line that prints:

```
system("/usr/bin/gs -q -sDEVICE=laserjet -r300 -dQUIET -dNOPAUSE  -sOutputFile=$puzzle.lj $puzzle.wps ");
```

I'd put the LPR command in there instead.  That script is what I based the one in the howto off of.  I used lpr instead of gs because I couldn't get gs to work for some reason.  The reason I used the printer name in LPR is because I have multiple printers.  I didn't realize that people with 1 didn't have to put the printer name but that makes sense.

Also, that script doesn't create an answer key like mine does, but it probably wouldn't be hard to modify it so that it does.  Again, i'll take a look at it later and see if I can't make a script which works for people with a NYT subscription.

---

### Post by wactuary on 2007-03-15
Great.  Thanks for the additional info.  TeXlive going in now.

I did get wget to work for downloading the puzzle.  What you have to do is first log-in with firefox so that a cookie is left on the machine (check the "remember me" box).  Then

```

locate cookies.txt | grep firefox

wget --load-cookies *path-to-cookies.txt-from-last-step* [URL for Puzzle]

```

NYT names the puzzle files with the date.  I hadn't yet written the bit to create the puzzle names dynamically, but it looks like that Perl script does it already.  I'll look closer at that and post back if any changes were necessary.

---

### Post by Mateo on 2007-03-15
is there a particular pattern for the NYT dates?  You can use the 'date' program to get the day's date and get it to show up just write, that's what I did in the script to name the answer key.

I could convert that perl script to bash no problem, except for how runs a different procedure on sunday (because the puzzle is larger).

Did you try using the wget line in that perl script, by the way?  Just for testing try:

> wget --http-user=myname --http-passwd=secret [http://www.nytimes.com/partners/xword/WHATEVER.puz](http://www.nytimes.com/partners/xword/WHATEVER.puz)

replacing WHATEVER with the correct dating pattern (just for testing).  If that works we might be able to figure out how to get that all working in bash.

---

### Post by Mateo on 2007-03-15
I figured out how to convert that perl script to bash, wasn't a big deal.  I'm holding off finishing it because that wget command might not work.  If it does though, I'll do the bash script for NYT subscribers.

---

### Post by wactuary on 2007-03-17
I tried both forms of wget.  It does not work with passing the user name and password, but the load cookes switch does work.  If the locate function is standard, then this code snippet will find the cookies file:

```
locate cookies.txt | grep firefox
```

So if that could then be passed to the wget command like

```
wget --load-cookies path-to-cookies.txt URL
```

Then it would work.  Or since the path is static, it could be coded by the user as a variable at the top of the script.

---

### Post by el mariachi on 2007-03-31
isn't there a Picross system like this? i just love picross..

---

### Post by monkey89 on 2007-06-20
Just to let you know, there's a more modern program that can read Across Lite files available at [http://x-word.org/](http://x-word.org/).  That way, you can print them through a nice normal interface, or solve them on the computer like I like to do.

---

### Post by el mariachi on 2007-06-20
nothing on the picross? I haven't found any program to do picross on the computer... only sudoku damn

---

### Post by ShirishAg75 on 2007-09-08
Just a quick word. I dunno if you guys know but Ubuntu is using dash instead of bash nowadays. it just uses less resources. See if it can be done using dash. 

Regards,

---

### Post by jgordon510 on 2007-12-02
Here's my messy little script that works.

```
#create the filename for the current date
date="`date '+%b%d%y.puz'`"

cookie_loc="`locate cookies.txt | grep firefox`"
cd /tmp
wget --load-cookies $cookie_loc http://select.nytimes.com/premium/xword/$date
/home/jeffrey/.xword-1.0/xword $date
```

You'll have to alter the last line to point to wherever you have [xword]("http://x-word.org/") installed.

I put it in my nautilus scripts folder.

Of course, you'll need a NY Times crossword subscription with a current cookie for this to work.

---

### Post by BenSw on 2008-02-29
> **jgordon510 said:**
> Here's my messy little script that works.

```
#create the filename for the current date
date="`date '+%b%d%y.puz'`"

cookie_loc="`locate cookies.txt | grep firefox`"
cd /tmp
wget --load-cookies $cookie_loc http://select.nytimes.com/premium/xword/$date
/home/jeffrey/.xword-1.0/xword $date
```

You'll have to alter the last line to point to wherever you have [xword]("http://x-word.org/") installed.

I put it in my nautilus scripts folder.

Of course, you'll need a NY Times crossword subscription with a current cookie for this to work.

Does this actually work? I have been trying to do this on OSX and debian, and it just links me to the "glogin" page and downloads that instead.

---

