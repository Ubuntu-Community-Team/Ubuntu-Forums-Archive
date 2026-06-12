---
title: "How Do I Make DVD Backups In Linux?"
date: 2009-03-15
forum: General Help
---

### Post by s1mp13m4n on 2009-03-15
Hello everyone.  I have a young daughter and want to make backups of legal dvd's that I own.  I am trying to switch from Windows to Linux thus do not want to use Windows to do this any more.  In Windows I used DVD Shrink, DVD Decrypter, and DVDFab to make backups.  I have Wine installed with all three of those programs installed on Wine as well, but they do not work.  DVD Decrypter and Shrink do not see my dvd drive and DVDFab does not load at all.  I have K9copy but do not know how to use it to do what DVD Decrypter and Shrink do.  
     Where do I start in making DVD backups in Linux?  Which programs should I use?  How do I use them?  Thank you for the help.  :)

---

### Post by .nedberg on 2009-03-15
K9Copy is "the way to go" I think. I found a how-to here:
[http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/)

It should do just as good as Shrink.

---

### Post by s1mp13m4n on 2009-03-15
Thank you for taking the time to look.  I am headed there now to check out the webpage.  :)

---

### Post by binbash on 2009-03-15
there is a new deb file at getdeb.net for k9copy.You can also use acidrip or dvd:rip

---

### Post by s1mp13m4n on 2009-03-15
None of the programs are working.  K9copy  just sits in the authering stage but does nothing and DVDRip and AcidRip are beyond what I know at the point.  I am looking for a simple tool to just get the job done.  I will certainly keep trying but for now I need to newbie tools for the beginner.  I am not sure why K9copy is not working...I did use that helpful webpage.  :)

---

### Post by Altay_H on 2009-03-15
If you don't mind using the terminal, you can try this command:
```

dd if=/dev/dvd of=~/Desktop/dvd.iso

```

Replace /dev/dvd with the location of your dvd and ~/Desktop/dvd.iso with the location you want it to be copied to. My dvd drive is located at /dev/sr0. If you're not sure where it is, you can use this command to find out:

```

mount | grep media

```

---

### Post by mc4man on 2009-03-15
If you want to try your win progs then go Applications -> wine -> configure wine.
In the config. click on 'drives' tab and click the 'autodetect' box.
Make sure on 'applications' tab that the windows version is set to either windows xp or windows nt 4.0


The k9 copy in intrepid is a 2.x.x version that uses kde4, it's somewhat flaky when run on ubuntu (vs. kubuntu

Your dvdfabhd.... should also work, I just dl'ed it and it worked right away. (the free version

Using dd is ok but if you burn the.iso to a disk it will not work in a standalone dvd player

If there is no structure protection (will be on disney titles) the vobcopy works very similar to dvddecrypter. (command line only, basic command (outputs to movie named folder in your home folder

```
vobcopy -v -m -F 16
```

---

