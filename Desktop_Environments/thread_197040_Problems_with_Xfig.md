---
title: "Problems with Xfig"
date: 2006-06-15
forum: Desktop Environments
---

### Post by hutxubix on 2006-06-15
Hello,

I have had problems with Xfig. I've seen things in other threads but nothing work for me. This is what I get:

alberto@portatil01:~$ xfig
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,*--16-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
alberto@portatil01:~$

and this continue when I work with it. 


Any idea?

Thanks
I have ubuntu updated on a laptop Acer TravelMate 4001WLMi

---

### Post by taurus on 2006-06-15
I am glad to see another soul using xfig besides me around here!!!  Well, I get the same warning, not error, message when I run xfig but as far as I know, xfig is working just fine on my Dapper.  It just complains about some missing fonts or strings so nothing to worry about.  If you don't want to see that warning message, start it from Applications -> Graphics -> Xfig.

---

### Post by hutxubix on 2006-06-15
Well, in my case, when I work with text, I really have problems with things that dissapear or so. A warning always means a problem. Doesn't it?

---

### Post by taurus on 2006-06-15
What text are you talking about?  Maybe I can see if I have the same problem as yours.  By the way, warning is not always a problem.  Error message is a problem...  

I assume you have also installed transfig as well!

---

### Post by hutxubix on 2006-06-19
Well, I hadn't transfig installed. I have just do it, but nothing has changed.

The text I was talking about was any text I want to write, I have problems with it. For example, I have just opened something made in another machine, in Debian, and it gave me an ' arror massage: Can't find times-medium-r ... ' and then, the text in the figure was very small, and nothing to do with what I had previously done.

Any Idea?

Thanks.

---

### Post by fast1 on 2006-06-19
I have the same problem both with xfig and with xemacs.

---

### Post by enemorales on 2006-06-26
Hi,

I'm new to the forums. I have the same problems. Fonts that are not found and therefore badly displayed (very small, for instance) in the screen.

Has anyone found a solution for this? Using DAPPER from 2 weeks now and it is great, so far only this (annoying) xfig bug...

Thanks in advance for any feedback!

EDIT: BTW, when I export to ps anything works fine. The problem is only whie editing with xfig...

---

### Post by therrmann on 2006-07-07
I have the same problem with xfig under Dapper, and so far have not been able to fix it.  With Hoary (I skipped Breezy), the problem was solved by downloading a ghostscript fonts package, ghostscript-fonts-std-8.11.tar.gz from an ftp mirror and installing it in /usr/X11R6/lib/X11/fonts/Type1, but this does not work under Dapper.  For one thing, that directory does not exist, and I have not found another place to put it that works.    It's a pain since I use xfig all the time for making embedded eps figures in LaTeX.    Anyone?

---

### Post by bigM on 2006-09-14
I had this problem with xfig. (Ubuntu 6.06 LTS - the Dapper Drake.) I installed the following packages:

tkfont (1.1-12)
ttf-xfree86-nonfree (4.2.1-3)
unifont (1:1.0-1ubuntu2)

and now it works fine, apart from a few font selections. I haven't investigated which package was the necessary one. I assume it wasn't the first.

---

### Post by hollowhead on 2007-04-26
Tried downloading the above passages this didn't work.  Any other suggestions?


Can't find -*-times-medium-r-normal--13-*-*-*-*-*-ISO8859-*, using 6x13
Can't find -*-times-medium-i-normal--13-*-*-*-*-*-ISO8859-*, using 6x

Ta. Hollowhead

---

