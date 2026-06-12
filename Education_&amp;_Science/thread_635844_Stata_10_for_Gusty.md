---
title: "Stata 10 for Gusty"
date: 2007-12-09
forum: Education &amp; Science
---

### Post by shuttleworthwannabe on 2007-12-09
Just curious if anyone has installed Stata 10 for Unix systems (tested on RH, Suse, Fedora, but no mention of Ubuntu) on the official [Stata]("http://www.stata.com/products/unix.html") web-pages.

---

### Post by chrisby on 2008-04-02
I have stata 10 installed on ubuntu and it works perfectly.  Here is how I got it to run:

mkdir /usr/local/stata10
cd /usr/local/
chmod a+rx /usr/local/stata10
cd /usr/local/stata10
mkdir /tmp/statainstall
cp -r /media/cdrom0 /tmp/statainstall
/tmp/statainstall/cdrom0/install

follow prompts

now xstata-se does run because it is looking for libtiff.so.3

This is old so make a symbolic link to your current version 

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

now stata should run fine.

---

### Post by buntu_hugenewbie11 on 2008-04-24
Have you been able to use the MP version? If so, any huge differences?

---

### Post by chrisby on 2008-04-25
I don't have a license for the multiprocessor version, so I haven't tried it.  The special edition works very well, and with Ubuntu's low ram usage you can allocate a lot to stata. If you get the multiprocessor version let me know how it works.

---

### Post by liuzerus87 on 2008-04-30
I have Stata 10 running in Hardy, and it runs pretty well (I have the standard version running on a Pentium IV). My only concern is that Stata graphs ridiculously slowly (like one data point every 2 seconds), so I'm going to try running the same commands on my Windows copy on the same pc in a few days (when I actually have to do this problem set) and see if its a problem that I need to investigate.

---

### Post by chrisby on 2008-05-02
liuzerus87,

I don't have that problem with se, are you using intercooled?

---

### Post by liuzerus87 on 2008-05-07
I am. And it does run much faster under Windows. I have no idea why that is the case. I might try running it from terminal.

---

### Post by chrisby on 2008-05-10
How many observations, and what kind of plot are you doing?

---

### Post by gatorbrit on 2008-05-15
I'd be interested to hear other folks views on benchmarking stata in windows vs ubuntu.  I had read somewhere that it was faster in linux.  Anyone else have any experience?

Thanks

---

### Post by chrisby on 2008-05-16
Just in terms of system resources, it is better for Linux.  Vista alone was using around half of my ram. Since Stata pulls the data into ram, and doesn't actually work with it on the hard drive, using Linux frees up a lot of resources for stata.  Hardy with compiz extra affects enabled is only using 23%.  With the size of datasets I am working with this helps out greatly.


I think its a good question though.  Does any have Stata 10 for both so that we can compare benchmarks on a single machine?

---

### Post by PGScooter on 2008-12-15
any updates on those benchmarks or further issues with Stata 10 and ubuntu?

Thought I would add a link to a guide I found: "INSTALLING STATA 10 UNDER UBUNTU 8.04
Kristian Koerselman, september 2008"
[http://www.abo.fi/public/media/12450/stata.txt](http://www.abo.fi/public/media/12450/stata.txt)

---

