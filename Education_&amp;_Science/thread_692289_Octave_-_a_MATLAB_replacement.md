---
title: "Octave - a MATLAB replacement"
date: 2008-02-09
forum: Education &amp; Science
---

### Post by rye_ on 2008-02-09
Just my thoughts....
I write this as a a civil engineer with a leaning toward dynamics which MATLAB is suited to;

I can honestly say that Octave 3.0, when used in conjunction with gedit, with snap open, snippets, and side pane brower, and terminal plugins offers a programming experience superior to matlab.  
The only areas which matlab (not inclu. simulink) excels over Octave its ability to construct GUIs and its video capture abilities, none of which are really necessary for core work.



For those students and professionals amongst you who have learned to use matlab, yet do not wish to part with £1000, $2000 (much less for students); or for those who use illegal  copies and feel uncomfortable about this; Octave is well worth a go, and is very, very compatible with MATLAB.

Ryan

---

### Post by thisismalhotra on 2008-02-13
Octave is defnitely great speciallly the new 3.0 is very very good, coming from matlab one will not have to learn almost anything it&#347; quite compatible to matlab. Also, if you add qtoctave 0.7.1 GUI to it and EasyPlot 1.1 as you plotting program, BAM, you have a matlab like GUI/IDE and same plotting application 

HERE IS A SCREENSHOT TO DEMONSTRATE!!

---

### Post by Wolf-Ekkehard on 2008-02-13
very impressive!!

I have been using Octave for quite a while and have meanwhile even convered all of my Matlab mex files to Octave - it looks like qtmatlab and 3.0 is all that I am missing (I already knew I was missing 3.0 for graphics).

But I have a question: neither Octave 3.0 nor qtmatlab are in the standard (K)ubuntu repositories.  Am I missing a repository?  Where is the best place to get both, or simpler: where did you get yours :-)

Many thanks in advance

Ekkehard

---

### Post by militem on 2008-02-13
I heartily agree with the above posts.  I am proud to say Octave was created at my school in the cs department.  The only possible drawback for me would be the lack of signal and image processing toolboxes.  As a imaging student, I use those functions quite frequently.  I think I am going to bite the $100 bullet and get the student version with the 2 toolboxes included.

---

### Post by thisismalhotra on 2008-02-14
> **Wolf-Ekkehard said:**
> very impressive!!

I have been using Octave for quite a while and have meanwhile even convered all of my Matlab mex files to Octave - it looks like qtmatlab and 3.0 is all that I am missing (I already knew I was missing 3.0 for graphics).

But I have a question: neither Octave 3.0 nor qtmatlab are in the standard (K)ubuntu repositories.  Am I missing a repository?  Where is the best place to get both, or simpler: where did you get yours :-)

Many thanks in advance

Ekkehard

Qtoctave (not qtmatlab) is not in standard repos so you have to build it from source, the same goes for easy plot too. Alslo, Octave 3.0 came out a month ago and will be included in repos of Ubuntu 8.04 Hardy, but for now you have 
to build it from source..

This thread will help too..
[http://ubuntuforums.org/showthread.php?t=680690&highlight=octave](http://ubuntuforums.org/showthread.php?t=680690&highlight=octave)

You will get octave source from here: -
[http://www.gnu.org/software/octave/download.html](http://www.gnu.org/software/octave/download.html)

Qtoctave and Easyplot from here:-
[https://forja.rediris.es/frs/?group_id=60&release_id=298](https://forja.rediris.es/frs/?group_id=60&release_id=298)

Here is instructions how to build from source: -
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Bythe way if you dont want to get into all this trouble, I have deb file for Octave 3.0 and all others, send me your e-mail in a message and I will send you the file.

TC

---

### Post by thisismalhotra on 2008-02-14
> **militem said:**
> I heartily agree with the above posts.  I am proud to say Octave was created at my school in the cs department.  The only possible drawback for me would be the lack of signal and image processing toolboxes.  As a imaging student, I use those functions quite frequently.  I think I am going to bite the $100 bullet and get the student version with the 2 toolboxes included.

I am not 100% sure about this, but if you install octave-forge with octave, you will get all you need and you don't have spend $100 on matlab... double chek on that 
here is the website;

[http://octave.sourceforge.net/](http://octave.sourceforge.net/).

TC:)

---

### Post by Wolf-Ekkehard on 2008-02-14
Ooops - Freudian slip, yes I meant qtoctave - shows you how much I think of them interchangeably.

Thanks a bunch for the links!!

---

### Post by Wolf-Ekkehard on 2008-03-04
Thanks to thisismalhotra for pointing me to qtoctave!  qtoctave makes a great environment for octave and m-file development! Very nice piece of work!!

I installed octave 3.0.0 and qtoctave from source (I'm way behind in my Ubuntu installation, so I couldn't use the packages that thisismalhotra was kind enough to send to me).  They compiled and installed just fine after I had taken care of some dependencies (latest version of qt).

Have any of you guys had any luck with installing octave-forge packages, though?  Somehow the pkg command in octave 3.0.0 does not work for me - complains that the COPYING file is not there.  It is there, though...

Also, the commands imshow and imagesc start putting up a gnuplot window, as they should in 3.0.0, but then they put the image still in a imagemagick window. Very weird :confused:

Anybody had any more luck than I did?

---

### Post by thisismalhotra on 2008-03-04
> **Wolf-Ekkehard said:**
> Thanks to thisismalhotra for pointing me to qtoctave!  qtoctave makes a great environment for octave and m-file development! Very nice piece of work!!

I installed octave 3.0.0 and qtoctave from source (I'm way behind in my Ubuntu installation, so I couldn't use the packages that thisismalhotra was kind enough to send to me).  They compiled and installed just fine after I had taken care of some dependencies (latest version of qt).

Have any of you guys had any luck with installing octave-forge packages, though?  Somehow the pkg command in octave 3.0.0 does not work for me - complains that the COPYING file is not there.  It is there, though...

Also, the commands imshow and imagesc start putting up a gnuplot window, as they should in 3.0.0, but then they put the image still in a imagemagick window. Very weird :confused:

Anybody had any more luck than I did?

Hey Wolf;

Good to know everything is working out for you. I think I have seen this issue floating around on octave forums and I feel that is a better place to ask question about techni9calities of octave. There is a web based view of forums here... 

[http://www.nabble.com/Octave-f1895.html](http://www.nabble.com/Octave-f1895.html)


but you can subscribe to mailing lists here

[http://www.gnu.org/software/octave/archive.html](http://www.gnu.org/software/octave/archive.html)

Good Luck:KS

---

### Post by Wolf-Ekkehard on 2008-03-04
Completely agree - that's a much better place to ask...  I just hadn't found it yet ;-)

Thanks again Guarav!!

---

