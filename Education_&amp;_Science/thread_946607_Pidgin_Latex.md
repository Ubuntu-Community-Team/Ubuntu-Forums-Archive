---
title: "Pidgin Latex"
date: 2008-10-13
forum: Education &amp; Science
---

### Post by quazi on 2008-10-13
If you want to be able to chat over IM with math equations, a latex plugin for Pidgin exists which makes this quite easy.

The plugin's hosted by sourceforge [_here_](http://sourceforge.net/project/platformdownload.php?group_id=117582&sel_platform=5789). Unzip the contents of the archive into a directory.

Before installing it, you need to replace the LaTeX.c file with a newer one in the CVS: [_LaTeX.c_]("http://pidgin-latex.cvs.sourceforge.net/viewvc/*checkout*/pidgin-latex/pidgin-latex/LaTeX.c?revision=1.12")

Now, before installing run ```
sudo apt-get install libpurple-dev
```.  Browse to the directory where the files are and run the commands
```
$ make
$ sudo make install

```
and the plugin should be installed for Pidgin.  To enable go to the plugins menu under tools and check the box next to LaTeX.

Note: for images to properly be displayed the texlive and imagemagick packages must both be installed.  To do this run ```
sudo apt-get install texlive imagemagick
```

Now it should be much easier to communicate in mathematics over the internet.

---

### Post by mrgnash on 2008-10-13
The latest Gajim build also has this feature built in. Wouldn't both clients need to have the same setup in order to be able to communicate the formulas with one another, though?

---

### Post by quazi on 2008-10-13
Yea, both parties need the LaTex plugin as it simply translates $$code$$ into the appropriate latex image and displays that in the chat window.  The actual image isn't sent.

It would be nice if this was included by default and present in other commonly used clients.

---

### Post by mathfeel on 2008-10-22
I actually needed pidgin-dev to compile correctly.

How is that this plug-in not in the official repository?

---

### Post by boblemur on 2008-10-25
Im currently using this as well, i to needed pidgin-dev in order to make it work...

however i also needed to add:
```
<delegate decode="dvi" command="&quot;dvips&quot; -q -o &quot;%o&quot; &quot;%i&quot;"/>
```

to my "/usr/lib/ImageMagick-<INSERT VERSION HERE...JUST PRESS TAB :p>/config/delegate.xml"

however i think that the confusion arises because there is actually 2 different projects that seemingly at exactly the same, 
the one on source forge is not the same as the one on [http://www.unfreeze.net/?page_id=78](http://www.unfreeze.net/?page_id=78)

i found the later much better my latex images came out all blotchy and bold with the one off source forge

---

### Post by myle on 2008-10-28
Great news. Usually it is a pain in the neck to write a formula in msn. Very useful when we are chatting with colleagues.

---

### Post by niaz11 on 2008-10-28
LaTex plugin as it simply translates $$code$$ into the appropriate latex image and displays that in the chat window.

---

### Post by biscmal on 2008-11-02
Hi,
I just installed pidgin tex and it works, which is quite an achievement after about a hundred different other im progs with at least 200 plugins :?
Ok I admit it wasnt that difficult. But now I got it to work, my font when I type TeX symbols is pretty ugly, a bit like _[this]("http://img90.imageshack.us/my.php?image=sampleuglyfonted8.png")_.

Since I used _[this guide]("http://wangtang.de/pidgin-latex/")_ for my installation, the screenshot gives me the impression there could a better font for the TeX symbols.

I guess the problem has to be related to the moment when the TeX-symbols/image is created by one of these programs (ImageMagick or MikTeX) but I have no idea on how to change any parameters which the programs are fed with when they are asked to build the image.
Since I'm using Windows maybe the solution to that problem is quite different from the solution to a similar problem with ubuntu and I'd also understand if you didnt want to help me (shame on me, I even use vista) ^^
But not having to look at that ugly font would definitely cheer me up.
Thanks for your help,
bisc

(Can anyone recommend a good alternative to imageshack which has less/no ads?)

---

### Post by apricode.net on 2008-11-03
> **quazi said:**
> If you want to be able to chat over IM with math equations, a latex plugin for Pidgin exists which makes this quite easy.

The plugin's hosted by sourceforge [_here_](http://sourceforge.net/project/platformdownload.php?group_id=117582&sel_platform=5789). Unzip the contents of the archive into a directory.

Before installing it, you need to replace the LaTeX.c file with a newer one in the CVS: [_LaTeX.c_]("http://pidgin-latex.cvs.sourceforge.net/viewvc/*checkout*/pidgin-latex/pidgin-latex/LaTeX.c?revision=1.12")

Now, before installing run ```
sudo apt-get install libpurple-dev
```.  Browse to the directory where the files are and run the commands
```
$ make
$ sudo make install

```
and the plugin should be installed for Pidgin.  To enable go to the plugins menu under tools and check the box next to LaTeX.

Note: for images to properly be displayed the texlive and imagemagick packages must both be installed.  To do this run ```
sudo apt-get install texlive imagemagick
```

Now it should be much easier to communicate in mathematics over the internet.

Thank you very much for your help
IT WORKS FINE

---

### Post by quazi on 2008-11-06
> **biscmal said:**
> Hi,
I just installed pidgin tex and it works, which is quite an achievement after about a hundred different other im progs with at least 200 plugins :?
Ok I admit it wasnt that difficult. But now I got it to work, my font when I type TeX symbols is pretty ugly, a bit like _[this]("http://img90.imageshack.us/my.php?image=sampleuglyfonted8.png")_.

Since I used _[this guide]("http://wangtang.de/pidgin-latex/")_ for my installation, the screenshot gives me the impression there could a better font for the TeX symbols.

I guess the problem has to be related to the moment when the TeX-symbols/image is created by one of these programs (ImageMagick or MikTeX) but I have no idea on how to change any parameters which the programs are fed with when they are asked to build the image.
Since I'm using Windows maybe the solution to that problem is quite different from the solution to a similar problem with ubuntu and I'd also understand if you didnt want to help me (shame on me, I even use vista) ^^
But not having to look at that ugly font would definitely cheer me up.
Thanks for your help,
bisc

(Can anyone recommend a good alternative to imageshack which has less/no ads?)

Did you replace the LaTeX.c file with the one from the link given?  It improves the anti-aliasing of the images.

More info here: [http://sourceforge.net/forum/forum.php?thread_id=2046453&forum_id=401996](http://sourceforge.net/forum/forum.php?thread_id=2046453&forum_id=401996)

Reading your post though, it seems you're running Windows and this is a cure for Ubuntu (so maybe it won't work for you).

---

### Post by biscmal on 2008-11-08
Thanks for your advice, I think I'll just be patient and wait until I get kubuntu, at least I can IM with TeX =)

---

### Post by guitarboy on 2009-04-17
HI,
I've just installed the plugin, but i still have some problems. If i send a message like 
$$TeXcodehere$$
the message i see is not an image, but the code itself (i.e. $$TeXcodehere$$). Howewer, if i browse my history of sent messages, i'm able to see the image i wanted to see. Here a screenshot to understand what i'm saying:
[[IMG]http://img165.imageshack.us/img165/8599/screenshotwmx.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshotwmx.png)
Any idea?

---

### Post by quazi on 2009-04-18
> **guitarboy said:**
> HI,
I've just installed the plugin, but i still have some problems. If i send a message like 
$$TeXcodehere$$
the message i see is not an image, but the code itself (i.e. $$TeXcodehere$$). Howewer, if i browse my history of sent messages, i'm able to see the image i wanted to see. Here a screenshot to understand what i'm saying:
[[IMG]http://img165.imageshack.us/img165/8599/screenshotwmx.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshotwmx.png)
Any idea?

The new version of this plugin uses dvipng to convert images, so make sure you have that installed.

---

### Post by elliottb on 2009-06-11
This worked for me fine.  I took the source from this link at source forge which was version 1.3 at the time:
[http://sourceforge.net/project/showfiles.php?group_id=117582]("http://http://sourceforge.net/project/showfiles.php?group_id=117582")

Following other instructions running around I 'apt-get install'ed libpurple-dev pidgin-dev texlive imagemagick and dvipng

then, just use make to compile and make install to copy the library to the plugin directory.

Elliott

---

### Post by fesghelbahal on 2009-12-30
When I enter the make command, it says: ```
gcc  -fPIC -c LaTeX.c -o LaTeX.o -D_REENTRANT -I/usr/include/pidgin -I/usr/include/gtk-2.0 -I/usr/include/libpurple -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DHAVE_CONFIG_H
LaTeX.c:310: error: conflicting types for &#8216;latex_to_image&#8217;
LaTeX.h:103: note: previous declaration of &#8216;latex_to_image&#8217; was here
LaTeX.c:386: error: conflicting types for &#8216;analyse&#8217;
LaTeX.h:110: note: previous declaration of &#8216;analyse&#8217; was here
make: *** [LaTeX.o] Error 1

```I've replaced the Latex.C file with the new one.
What does it mean by "previous declaration"?
What should I do?

---

