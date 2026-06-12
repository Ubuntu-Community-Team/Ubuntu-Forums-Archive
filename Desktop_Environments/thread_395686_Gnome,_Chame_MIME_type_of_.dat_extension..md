---
title: "Gnome, Chame MIME type of .dat extension."
date: 2007-03-28
forum: Desktop Environments
---

### Post by Timtro on 2007-03-28
Hi all.

How would I change gnome/nautilus so that it doesn't think .dat files are MPEG video? I want it to show as text/plain.

Thank you.

Cheers,


Tim.

---

### Post by ComplexNumber on 2007-03-28
a shortcut is to do the following: right click on a dat file, select properties. then choose to Open With an editor such as gedit by default.

---

### Post by Timtro on 2007-03-28
> **ComplexNumber said:**
> a shortcut is to do the following: right click on a dat file, select properties. then choose to Open With an editor such as gedit by default.

Thank you complex number, but no.

I really do wish that people would read the problem a little more closely. This is the second time I've had to repost the problem because I keep getting the same answer. This is not an open with problem. 

Once again, gnome internally understands that a file with a .dat extension should be an MPEG file. Once it takes a closer look with a file sniffer, it realizes that the MIME type is text/plain, and gives and error when I try to open it.

Of course, I can open it if I select 'open with' every time, but I use far too many dat files for that to be a practical solution.

I've tried modifying /usr/share/mime-info/gnome-vfs.mime, but it does not seem to change anything, even after a restart.

Since I don't really know what I'm doing (I know very little about gnome's internal workings), I don't want to muck about. I'd much rather hear from someone who knows what they're doing.

Thanks again, and thank you Complex Number for your reply.

---

### Post by ComplexNumber on 2007-03-28
it would have been more useful to people if your 2nd post had have been your 1st post instead. then people know where you're coming from and what you're trying to achieve. otherwise, people responding to your post are merely firing in the dark.

so when you edited the following files, what did you change them to?

text/plain
    ext: asc txt TXT

video/mpeg
    ext: mp2 mpe mpeg mpg vob dat

---

### Post by Timtro on 2007-03-28
> **ComplexNumber said:**
> it would have been more useful to people if your 2nd post had have been your 1st post instead. then people know where you're coming from and what you're trying to achieve. otherwise, people responding to your post are merely firing in the dark.


I regret that my second may seem a little abrasive. It has just turned into a very frustrating problem. I'm sorry. Any frustration was not directed at you, ComplexNumber.

Of course, you're right. I could have been more clear in my first post. Although I think if you don't read into it as a 'noob' question, it is clear that I'm not asking how to change the program used to open the file. I specify that I wish to change how gnome/nautilus recognizes the file, not the default opening action. Also, aside from my embarrassing misspelling of 'change'  ('chame') It is evident from the title of my most that I want to modify the linkage between the .dat extension and the MIME type. 

Also, I didn't know about /usr/share/mime-info/gnome-vfs.mime when I had made my first post. I knew less about the problem when I first posted.

---

### Post by Timtro on 2007-03-28
I canged

```


text/plain
\text: asc txt TXT

video/mpeg
\text: mp2 mpe mpeg mpg vob dat

```

(note: I added the \t as a tab character. I read that it was important.)

to

```


text/plain
\text: asc txt TXT dat

video/mpeg
\text: mp2 mpe mpeg mpg vob


```

In fact, let me take a moment to actually copy the code from my files so that I can be sure of exactly what I did.

```

text/plain
	ext: asc txt TXT dat
.
.
.
video/mpeg
	ext: mp2 mpe mpeg mpg vob

```

The above is copied and pasted from an open gvim of said file. Currently, .dat files are still being 'guessed' at initially to be video files, but once highlighted, are changed. Double clicking brings a popup error telling me about the whole mismatch.

Thank you ComplexNumber.

---

### Post by Timtro on 2007-03-30
* bump *

---

### Post by Timtro on 2007-03-31
*bump*

---

### Post by ComplexNumber on 2007-04-02
you may like to try [this]("http://www.kdau.com/projects/assogiate/screenshots.html").

---

### Post by kdau on 2007-04-04
Hello, I'm the author of assoGiate, the MIME types editor that was linked from the last message. /usr/share/mime-info is deprecated, and GNOME now uses the shared-mime-info database at /usr/share/mime/packages. The default MIME data come from the shared-mime-info package.

Its developers agree with you that *.dat shouldn't be assumed to be MPEG, and they removed that association in shared-mime-info-0.19. According to the package database, feisty will have 0.20, so the problem should be resolved then.

If you do use assoGiate to fix the problem, edit either "text/plain" (as you mentioned) or "application/octet-stream" (which 0.19+ uses) and add "*.dat" in the "Name matching" tab.

---

### Post by oomingmak on 2007-07-09
> **ComplexNumber said:**
> you may like to try [this]("http://www.kdau.com/projects/assogiate/screenshots.html").
That program looks amazing (and just what I need). However, I haven't a clue how to install it. 

:confused:

I've followed guides for configure, make, install before, but not when there has so much dependency stuff to take into consideration. I can't even find half the stuff the author is talking about, because the versions are so new.

Can someone talk me through how to install this on 7.04 Feisty please?

---

### Post by kdau on 2007-07-12
> **oomingmak said:**
> Can someone talk me through how to install this on 7.04 Feisty please?

To install any missing build dependencies on Feisty, run:

```
sudo aptitude install g++ libgtkmm-2.4-dev libgnome-vfsmm-2.6-dev libxml++2.6-dev gettext gnome-doc-utils
```

After that, the regular configure/make process should work fine.

Note that assoGiate is on track for inclusion in Gutsy, so it should be much more convenient then.

---

### Post by oomingmak on 2007-07-13
Thank you so much for your help [kdau]("http://ubuntuforums.org/member.php?u=267404")!

:grin:

To my complete and utter surprise, the whole process went without a hitch (which I think is a first for me on Linux).

It was well worth me asking how to install this program, because it really has lived up to my expectations and it will make a huge difference to me and how I use Ubuntu. I practically live in Regedit on Windows (constantly making various customised file types and tailor-made context menus) so being on Ubuntu and not being able to control a single thing was like going back to square one. 

I did manage (after much trawling around the net looking for guides) to make a MIME type association by hand, through editing the XML database manually. That part was ok, but no matter what I did, I just couldn't get any icons to associate with my new file type. 

However with Assogiate it was quick and effortless. I even created some new file types from scratch within seconds of opening the program (and I didn't even need to look at the Help once).

I think this will be an fantastic addition to Gutsy.

Thanks for helping me get access to this program now (rather than having to wait till October).

---

### Post by oomingmak on 2007-07-13
OMG!

I just realised that you are the author of the program! -lol

I didn't even know that until just now (when I was looking through my bookmarks, and I saw the domain name of your site).

:lolflag:

---

