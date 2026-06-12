---
title: "[SOLVED] Koctave instead of MATLAB........."
date: 2008-02-25
forum: Education &amp; Science
---

### Post by Immolatus on 2008-02-25
I was just wondering if anyone here had experience with both MATLAB and Koctave. My questions are 1. can Koctave handle "mesh"? and 2. what are the major differences in syntax? any thoughts would be greatly appreciated.

---

### Post by graham-cracker on 2008-02-26
I don't have too much experience with koctave, although I used octave for a bit after leaving matlab. It is surprisingly similar, although the graphing capabilities were pretty bad when I used it (~1 year ago).

I'm really impressed with python and matplotlib:
[http://matplotlib.sourceforge.net/](http://matplotlib.sourceforge.net/)
I've found python to be pretty useful because it seems much closer to a traditional programming language (I'm actually taking a break from analyzing some electrophysiological as I write this).

I imagine that the biggest deciding factor may be whatever toolkits or libraries you use. If they are few or small enough (or if you're lucky) you could either rewrite them in python or find a suitable alternative.

To get back to your original questions. I'm sure there are quite a few sites out there that compare octave and matlab, such as this one:
[http://en.wikibooks.org/wiki/MATLAB_Programming/Differences_between_Octave_and_MATLAB](http://en.wikibooks.org/wiki/MATLAB_Programming/Differences_between_Octave_and_MATLAB)

---

### Post by thisismalhotra on 2008-02-26
To answer both the post above: -

1. It is not Koctave which handles mesh, Koctave just a GUI which helps you program using Octave. Octave is the one which handles plotting and graphing commands. Usually the default plotting manager with octave is Gnuplot but now you can easily use jhandles or EasyPlot which offer diffrent functionality.

2. Octave has just released Octave 3.0 which added a lot of plotting and graphing capability to it. I can say now it easily rivals with Matlab if used along with octave-forge packages/toolboxes.

3. I have used matlab quitre a lot and is now using octave quite frequently and to your surprise there is almost no diffrence in syntax for the most part. 

4. Octave is a better way to go that writing your own libraries beacuse somebody has done the work for you ans there is enough help and support in the community.

5. Also, for GUI I would suggest Qtoctave 0.7.1 with EasyPlot  and Octave 3.0, and you have your matlab clone (if thats what you are used too). Here is screen shot of my installation just to have a look. Also, I have .deb for each if you need them.

---

### Post by Immolatus on 2008-02-26
I would love .deb's for this if you have them. I was actually clued in to the idea of using Qtoctave in place of koctave, but was under the impression it required QT4lib to run so ( this will make you laugh) I broke my system trying to install the kde4 live cd and had to start over. For what ever reason Kubuntu will not install on my machine now with out crashing half way through. So now I run ubuntu with kde installed from repo and ripped out gdm replaced with kdm......close enough. I digress....I'll deffinately look into your suggestions and await your response. thank you.:guitar:

---

### Post by thisismalhotra on 2008-02-27
no, with qtoctave you can use qt3 or qt4 which ever you have installed on your system. The screenshot above uses qt4.

Also, regarding you kubuntu issue. if you install a pakage called kubuntu-desktop from ubuntu and then lof out and chage session to kde you will have full fledged kubuntu in you ubunt installation. One thing which I really dont like with that installtion is you menus will show both gnome application and kde application which makes it a real clutter.

I will send th .deb as soon as I get a chance

---

### Post by jlawrence on 2008-02-27
thisismalthora,

can you please send to me the debs as well or upload the debs somewhere (rapidshare) ?

Thank you in advance,

---

### Post by thisismalhotra on 2008-03-02
> **jlawrence said:**
> thisismalthora,

can you please send to me the debs as well or upload the debs somewhere (rapidshare) ?

Thank you in advance,

Thanks dude I was looking for a place to upload these files for few months now...

 Here is the link to OCtave 3.0 Deb

[http://rapidshare.com/files/96432442/octave_3.0.0-1_i386.deb.html](http://rapidshare.com/files/96432442/octave_3.0.0-1_i386.deb.html)

I am doing others as I am posting this...:popcorn:

---

### Post by thisismalhotra on 2008-03-02
Qtoctave 0.7.1 here:-

[http://rapidshare.com/files/96433471/qtoctave_0.7.1-1_i386.deb](http://rapidshare.com/files/96433471/qtoctave_0.7.1-1_i386.deb)

---

### Post by thisismalhotra on 2008-03-02
EasyPlot 1.1

[http://rapidshare.com/files/96434443/src_20080123-1_i386.deb](http://rapidshare.com/files/96434443/src_20080123-1_i386.deb)

---

### Post by Immolatus on 2008-03-02
thanks for the .deb's but....qtoctave dumped itself in my home folder claiming there was no suitable app. for installing it. I assume I should do this manually. so .....how and where??:confused:

---

### Post by thisismalhotra on 2008-03-03
> **Immolatus said:**
> thanks for the .deb's but....qtoctave dumped itself in my home folder claiming there was no suitable app. for installing it. I assume I should do this manually. so .....how and where??:confused:

I think you are missing Qt libraries and install cmake too from synaptic and run it again.

post back if it does not work

---

### Post by Immolatus on 2008-03-03
Grrrr.... I've installed cmake and all the libqt"s I could find that looked relevant. A point of interest though, I have been using and automated installer So, where do I install each of these manually? .

---

### Post by thisismalhotra on 2008-03-03
could you please tell what error message you get when you try to install using Qtoctave .deb..

Thanks, It might take me some time to reply as I am kinds tie up tomorrow but I will surely rply by day's end !!

---

### Post by Immolatus on 2008-03-03
OOOO.....k. so scratch that last I guess. I've found qtoctave installed in /usr/local/share, problem is it wont run when called in a terminal

 rooster@kurgan:~$ qtoctave
qtoctave: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory
rooster@kurgan:~$ 

Also there is no menu entry to run from either. What do you make of that?
It's not the end of the world though I've been using octave/gnuplot/koctave in the mean time.

---

### Post by thisismalhotra on 2008-03-06
Sorry I am kinda tied up with stuff, I will try to work on your solution over the weekend adn see if I can help you out !!

---

### Post by Immolatus on 2008-03-06
:guitar:Thanks for the help.

---

### Post by thisismalhotra on 2008-03-07
> **Immolatus said:**
> OOOO.....k. so scratch that last I guess. I've found qtoctave installed in /usr/local/share, problem is it wont run when called in a terminal

 rooster@kurgan:~$ qtoctave
qtoctave: error while loading shared libraries: libQtXml.so.4: cannot open shared object file: No such file or directory
rooster@kurgan:~$ 

Also there is no menu entry to run from either. What do you make of that?
It's not the end of the world though I've been using octave/gnuplot/koctave in the mean time.

Please install following from synaptic...

libqt4-core
libqt4-gui
libqt4-qt3support

It should do the job

---

### Post by Immolatus on 2008-03-09
:popcorn:Yup. That did it. Just one more silly question though. It's telling me to choose my version of Octave then "reload" qtoctave. I couldn't find the option to reload, how does one go about "reloading" qtoctave?

---

### Post by Immolatus on 2008-03-09
Doh!! Never mind that last post. I fixed it, the octave version it's looking for is in /usr/bin. pointed it there, quit, restart and golden.
thanks for your help.:guitar:

---

### Post by thisismalhotra on 2008-03-10
> **Immolatus said:**
> :popcorn:Yup. That did it. Just one more silly question though. It's telling me to choose my version of Octave then "reload" qtoctave. I couldn't find the option to reload, how does one go about "reloading" qtoctave?

FYI, by reloading it means close all the Qtoctave session and start them again.

If you are done can you mark the thread solved using thread tools s that other people may find it useful.

TC

---

### Post by Immolatus on 2008-03-10
:)

---

### Post by thisismalhotra on 2008-03-21
> **Immolatus said:**
> :)

Cool !!:popcorn:

---

