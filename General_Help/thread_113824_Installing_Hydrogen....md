---
title: "Installing Hydrogen...???"
date: 2006-01-07
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-01-07
I tried installing the drum program Hydrogen using

sudo apt-get install hydrogen

and was SHOCKED when it actually installed something... but then I found that there were no shortcuts to it (I had to search my entire hard drive for file named hydrogen), and when I finally did manage to launch it, it spat out unintelligible error messages as I worked, which I attributed to its being an unstable version... basically, it wasn't very pleasant to use.

So I decided to compile the stable version using the directions at [http://www.hydrogen-music.org/content/tutorial/manual_en.html]("http://www.hydrogen-music.org/content/tutorial/manual_en.html").  I got past the downloading part, but when I saw

"Compiling Hydrogen depends on the following libraries:"

I wasn't quite sure what to do... I guessed that "libraries" would equate to "packages" managed by Synaptic (forgive me for having grown up with Windows).  The first library on the list was something called libsndfile... I opened Synaptic and did a search for libsndfile, and found
[LIST]
[*]libsndfile0 (the check box beside this one looked empty)
[*]libsndfile0-dev (also empty)
[*]libsndfile1 (this one had a green check box beside it)
[*]libsndfile1-dev (empty)
[*]mffm-libsndfilew-dev (empty)
[/LIST]

I didn't know if that meant I had it or not (is libsndfile the same as libsndfile1?) so I decided I'd just follow the link [http://www.mega-nerd.com/libsndfile/]("http://www.mega-nerd.com/libsndfile/") and install it from there... I downloaded libsndfile-1.0.12.tar.gz, extracted it into my home folder, and opened the README file.  The first thing it told me to do was

./configure

so I typed that in, and things started scrolling by.  Then it stopped by telling me

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

so, out of nowhere, I thought I'd try sudo apt-get install gcc... that seemed to work, but when I did ./configure again, it gave me

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Can anyone help me...?

---

### Post by akiro.yamamoto on 2006-01-07
Install build-essentails.

---

### Post by akiro.yamamoto on 2006-01-07
That was a little cryptic...
Use Synaptic to install build essentials.
Or you can use apt-get install build-essential
This is a meta package that should install the required packages for building software from source.
For more info check the links in my sig..
Hope that helps

---

### Post by akiro.yamamoto on 2006-01-07
You can search in Synaptic for the required libraries....
If they are available from the repository that would save you quite a bit of time....

---

### Post by mztriz on 2006-01-07
>     * libsndfile0 (the check box beside this one looked empty)
    * libsndfile0-dev (also empty)
    * libsndfile1 (this one had a green check box beside it)
    * libsndfile1-dev (empty)
    * mffm-libsndfilew-dev (empty)
Everything that is empty is not installed; so check them (mark for installation) and then click apply. 
> libsndfile the same as libsndfile1 no.
> ./configure

so I typed that in, and things started scrolling by.  Then it stopped by telling me

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
 Go to terminal and type in ```
 sudo apt-get install build-essential
``` and then try ./configure again.
good luck :)

---

### Post by akiro.yamamoto on 2006-01-07
BTW:
What were the error messages that recieved when trying to run the app.
What file did you use to run the app with....

---

### Post by mztriz on 2006-01-07
Also when you are looking for programs, most programs are installed in /usr/bin
so check there first.

---

### Post by jmxhgyZN8wK7 on 2006-01-08
to akiro.yamamoto... i don't know what the error messages were exactly, it just looked like a whole bunch of random crap - COULDN'T DO THIS, COULDN'T DO THAT

hold on, i'm going to try that build-essentials thing (now how was i supposed to know about that?  :-(

thanks guys

---

### Post by Havoc on 2006-01-08
Ummmmm....Why don't you download the binary installer? :confused: 

It works great for me.Try that.

---

### Post by jmxhgyZN8wK7 on 2006-01-08
to Havoc... I tried the binary installer.  First I downloaded the file hydrogen-linux-installer-0.9.2-x86.run to my home folder, then I ran it using

sh hydrogen-linux-installer-0.9.2-x86.run

After it said "Done!", I clicked on the desktop icon and got a little "Starting Hydrogen..." thing in my taskbar (is that what you call it in GNOME)?  Then it disappeared.  So I went to the hydrogen-0.9.2-x86 folder in my home folder and did

sh hydrogen

but it gave me "./bin/hydrogen-0.9.2: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory"

---

### Post by jmxhgyZN8wK7 on 2006-01-08
I tried

sudo apt-get install build-essential

and went back to the first step:

./configure

It gave me

checking whether QTDIR environment variable is set... no
configure: WARNING: QTDIR must be properly set.
 * Searching for Qt library
   |-> searching QT in /usr/share/qt *** Not found ***
   |-> searching QT in /usr/share/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt-3.1 *** Not found ***
configure: WARNING: Qt library not found. Maybe QTDIR isn't properly set.
checking for qmake... no
configure: error: qmake not found in current PATH. Maybe QT development environment isn't available (qt3-devel).

So I tried

sudo apt-get install qt3-devel

and got "E: Couldn't find package qt3-devel"

tried

sudo apt-get install qt3

and got "E: Couldn't find package qt3"

tried sudo apt-get install qt

and got "E: Couldn't find package qt"

(I'd already added the Universe and Backports repositories and done sudo apt-get update, if that helps...)

---

### Post by pandionknight on 2006-02-03
I just used Synaptic to install Hydrogen and couldn't find it in the Applications menu or with Find Files. Though as mentioned in a previous post I was able to it in Usr/bin, I double-clicked  what I presume is the binary file and it opened up fine. Now I just need to find the Hydrogen Icon?

---

