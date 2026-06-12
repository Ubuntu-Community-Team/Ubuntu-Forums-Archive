---
title: "QtOctave is dead, almost a year ago"
date: 2012-05-30
forum: Education &amp; Science
---

### Post by PC_load_letter on 2012-05-30
This is one awesome app, a GUI (the only one I know of) for Octave. I just found out today that the dev behind it had stopped the development almost a year ago, here: 
[http://www.ohloh.net/p/qtoctave](http://www.ohloh.net/p/qtoctave)

This is really sad. If I were a better coder or had more time I would have volunteered. I hope someone does pretty soon.

---

### Post by PC_load_letter on 2012-05-30
Well, for those who are interested, it seems that GSOC 2012 has one project that will focus on the development of a native Octave GUI, it's in the news section at GNU Octave web site, more details on one of the devs blog:
[http://octave-gsoc2012.blogspot.com/](http://octave-gsoc2012.blogspot.com/)

Here is how it looks like:
[IMG]http://2.bp.blogspot.com/-eVo54m7KPzM/T7yXpYZs4jI/AAAAAAAAAmM/az6-Esy7U9s/s1600/screenshot.png[/IMG]

Looks very similar to QtOctave, let's hope it'll have some debugging capabilities.
The problem is until then, the only choice for a GUI is to install the QtOctave in the repos which depends on the ancient Octave 3.2 (latest version of Octave is 3.6.1).

---

### Post by PeterP24 on 2012-05-30
> **PC_load_letter said:**
> Well, for those who are interested, it seems that GSOC 2012 has one project that will focus on the development of a native Octave GUI, it's in the news section at GNU Octave web site, more details on one of the devs blog:
[http://octave-gsoc2012.blogspot.com/](http://octave-gsoc2012.blogspot.com/)

Here is how it looks like:
[IMG]http://2.bp.blogspot.com/-eVo54m7KPzM/T7yXpYZs4jI/AAAAAAAAAmM/az6-Esy7U9s/s1600/screenshot.png[/IMG]

Looks very similar to QtOctave, let's hope it'll have some debugging capabilities.
The problem is until then, the only choice for a GUI is to install the QtOctave in the repos which depends on the ancient Octave 3.2 (latest version of Octave is 3.6.1).

Oh, saddly I had to use matlab at work two months ago and ... the gui looks very similar to the matlab one - which is a little bit disturbing. What is wrong with the terminal based octave?

---

### Post by PeterP24 on 2012-05-30
don't get me wrong, I am a sucker for Scilab although I find it a little weird and not able to cope with some of the very basic tasks (like representing a color shade map taken from a FEA software in a form of - 2D point coordinate <-> physical quantity value pair -because it cannot manage - um RAM memory). But I don't see the point of an Octave GUI, as long as the terminal version does its job.

---

### Post by PC_load_letter on 2012-05-31
> **PeterP24 said:**
> Oh, saddly I had to use matlab at work two months ago and ... the gui looks very similar to the matlab one - which is a little bit disturbing. What is wrong with the terminal based octave?

Well, I prefer the terminal myself, even with Matlab, just type the following in a terminal.
```
matlab -nodesktop -nosplash
```

I appreciated the GUI when I was still a newbie to Linux in general and I always thought the GUI makes debugging code much easier, no? If you guys have suggestions about effective debugging from the terminal for Octave/Matlab, let me know.

---

### Post by mydebianblog on 2012-11-17
> **PC_load_letter said:**
> Well, I prefer the terminal myself, even with Matlab, just type the following in a terminal.

You can prefer whatever you like, but the important thing about GUI for Octave (and GUI in general) is to make the program more user-friendly, especially for beginners. The whole purpose of Octave is to be a cheap replacement for students to learn basics of MATLAB. In fact, Octave is merely a *companion to a chemical reactor design course.* [[Source.]]("http://en.wikipedia.org/wiki/GNU_Octave")

Octave is nowhere near to be a replacement of MATLAB (poor code quality, lots of bugs, poor documentation, no profiler, no working GUI). But it is a nice cheap replacement for students.

**_To recap:_** GUI for Octave is **important** and** very necessary** because it allows to make a learning curve more smooth.

The GSoC program (it does not even have a proper name!) right now is just a bucn of C++ files dumped into HG repo - no instructions for building, let alone build packages for major distros. Just in case somebody wants to build it (apart from the author), source code is  [here]("http://savannah.gnu.org/hg/?group=octave").

---

### Post by lad.kocb on 2012-11-19
I do not quite like the statements about all the "bad" aspects of Octave. like "poor coding", "bad documentation" etc. That is naturally not true. It might be discussed in some sense when comparing it to matlab, but it is no just comparison. Matlab is a big commercial project, Octave is not. There are also some few features of Octave which are more useful than matlab's often historically based limitations (funny, I do not remember any now, but  I am often surprised by something being possible in Octave and giving errors in Matlab) . And you can compile Octave for any device. I have compiled Octave 2.1 and it is running on my aging Nokia N800 internet tablet (debian-armel; compilation in a developer package that time freely available as Ubuntu virtual appliance). But that was without any GUI. Octave is not just cheap substitute for Matlab. It is what it says it is, a free GNU project attempting to provide functionality very close to Matlab. (I am in no way associated with the Octave project)

---

### Post by vinukn on 2013-02-21
Try DomainMath IDE.
[http://sourceforge.net/projects/domainmath/](http://sourceforge.net/projects/domainmath/)

---

### Post by Jsplinter on 2013-06-19
I too wish there was an IDE.  How does one step through a 200 line Octave script from the command terminal?  With an IDE it's as simple as 'F9.'

---

### Post by monkeybrain2012 on 2013-06-19
There is an IDE in the octave developmental version. See screenshot. I compiled Octave 3.7.5 from source in Ubuntu 12.04. It is pretty easy to compile though it takes a long time.

Alternatively, there is a ppa [https://launchpad.net/~octave/+archive/unstable](https://launchpad.net/~octave/+archive/unstable)

---

