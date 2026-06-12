---
title: "Tab completion in gnuplot, and my solution"
date: 2009-04-19
forum: General Help
---

### Post by Yoshis88 on 2009-04-19
I really wanted tab completion in gnuplot, and perhaps this post is more for myself than for anyone else, but upon searching of these forums, you learn that tab completion libraries cannot be linked to the gnuplot because of the way GPL works.  You may find some people opting for sidestepping the issue by installing a different program which will wrap the tab functionality in.
```
sudo apt-get install rlwrap
Then add the following line in the ~/.bashrc
alias gnuplot='rlwrap -a -c gnuplot'
```Now, this solution doesn't really taste good to me.  I haven't tried it though.  But I don't know how it would handle piping, which I have come to value.  It also has the qualification that it will only work with names surrounded by double quotes(") and not those surrounded by the single dingles('). Also, the alias needs added to every user on the system.
While most people will consider it a hassle to compile from source, I find these drawbacks the greater hassle.

So! Compiling from source doesn't have to be scary.  You can cut and paste the following commands into terminal, and you will have Tab completion functionality regardless of user and quotation type!
```

sudo apt-get purge gnuplot
sudo apt-get build-dep gnuplot
cd `mktemp -d`
apt-get source gnuplot
cd gnuplot*
./configure --with-readline=gnu
make
sudo make install

```Some caveats:
[LIST]
[*]You must have sudo priviledges
[*]I have only tried it on Intrepid Ibex (8.10)
[*]This will install the version associated with your ubuntu.  If you need the newest version, get the newest .tar.gz from the [Gnuplot website]("http://www.gnuplot.info/"), unpack it, get into a terminal into the directory in which you unpacked it, and just execute the first two commands, then skip to the ./configure and down.
[*]It installs to /usr/local/bin for me and works, which some people reported issues with, though I might suggest doing "sudo ln -s /usr/local/bin/gnuplot /usr/bin/gnuplot"
[*]There is still no direct PDF support.  I would suggest "sudo apt-get install texlive-extra-utils" and write eps output ("set terminal postscript eps enhanced color") then use epstopdf to make a pdf.  Anyone else up for adding a little addendum to this to have direct PDF output supported using only that which can be apt-get'ed from the Ubuntu repositories?
[/LIST]

---

