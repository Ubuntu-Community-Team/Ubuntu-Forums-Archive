---
title: "Help with XQF Game Server Browser?!"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by andy- on 2007-02-08
First time installing it and running it worked fine,can see my installed games etc. Then after getting disconnected from a Quake server because PunkBuster wants a manual upgrade, XQF broke down on me. I can't get Quake 3 Arena in there as a category any more, won't let me reinstall either, it's just an empty window now, with all the options still showing, none of which I can use. If anyone has any experience with this software, please help.

```
andy@home:~$ xqf

Gtk-WARNING **: Unable to locate loadable module in module_path: "libraleigh.so" ,
WARNING 06:42:11 loadpixmap.c:213 load_pixmap_as_pixmap() - Error loading pixmap  file: share/xqf/default/splash.png
WARNING 06:42:11 loadpixmap.c:213 load_pixmap_as_pixmap() - Error loading pixmap  file: share/xqf/default/xqf_48x48.png
```

That's what I'm getting in term. (It still starts, but nothing works inside, and Q3A is gone from the listing.)

---

### Post by glotz on 2007-02-19
I just installed XQF 1.0.5 and Qstat 2.11 and GeoIP 1.4.2. It's a beautiful combo.

Here's how to do it. First make sure you've got the needed development packages installed:

**sudo aptitude install libgdk-pixbuf-dev libglib1.2-dev libgtk1.2-dev libxml-parser-perl gtk-engines-raleigh libx11-dev**

That will probably suggest a few other dependencies to be installed. Accept the suggestions.

Then acquire the source codes for the three packages:

[http://prdownloads.sourceforge.net/xqf/xqf-1.0.5.tar.gz?download](http://prdownloads.sourceforge.net/xqf/xqf-1.0.5.tar.gz?download)
[http://downloads.sourceforge.net/qstat/qstat-2.11.tar.gz?use_mirror=heanet](http://downloads.sourceforge.net/qstat/qstat-2.11.tar.gz?use_mirror=heanet)
[http://www.maxmind.com/download/geoip/api/c/GeoIP.tar.gz](http://www.maxmind.com/download/geoip/api/c/GeoIP.tar.gz)

Then, extract the tarballs, and goto each folder and **./configure**, **make**, **sudo make install**. Do GeoIP first so it will be included in the XQF configure.

Now if you excuse me, I'll go play Tremulous using XQF to find me a proper geoflagged server! :D

---

### Post by jdarias on 2007-03-28
Glotz, I had to install zlib1g-dev. all 3 packages asked me for this.

```
sudo aptitude install libgdk-pixbuf-dev libglib1.2-dev libgtk1.2-dev libxml-parser-perl gtk-engines-raleigh libx11-dev zlib1g-dev
```

Another easier way to get this working without compilin anything (and getting the same not-so-cute-as-the-one-in-the-repository-but-up-to-date XQF) is to 1) download the RPMs for xqf, qstat and geoip, 2) convert to DEB with alien, and 3) install the resulting debs.

These are the rpm's:

[http://prdownloads.sourceforge.net/xqf/xqf-1.0.5-1.i586.rpm?download](http://prdownloads.sourceforge.net/xqf/xqf-1.0.5-1.i586.rpm?download)
[http://prdownloads.sourceforge.net/xqf/qstat-2.11-1.i586.rpm?download](http://prdownloads.sourceforge.net/xqf/qstat-2.11-1.i586.rpm?download)
[http://prdownloads.sourceforge.net/xqf/GeoIP-1.4.0-1.i586.rpm?download](http://prdownloads.sourceforge.net/xqf/GeoIP-1.4.0-1.i586.rpm?download)

Btw, when i try to connect to a Tremulous server, it just loads the game as normal. Doesn't try to connect to any server, like ET does. How do i fix that?

---

### Post by glotz on 2007-03-28
Trem connects for me normally. I have no idea why it wouldn't for you.

---

### Post by jdarias on 2007-03-28
Mine isn't working. :(
Can you post your config?

---

### Post by glotz on 2007-03-28
Uhm, sure, what file do you want?

---

### Post by jdarias on 2007-04-29
@Glotz
Plz tell me how is trem configured in your preferences/games dialog box.
I just have "tremulous" in "command line". nothing more.

---

### Post by glotz on 2007-04-30
I have the full path to the executable. /home/username/tremulous/tremulous.x86

You can use **updatedb** and **locate tremulous.x86** to find the location of the exe.

---

### Post by MadMacaco on 2007-05-01
Hi to all,

I have a little problem regarding XQF (cedega 6 and Call of Duty United Offensive 1.51).
XQF-s command line look like this : *command line: cedega --run call CoDUOMP*, and then XQF starts the game and connects to a specified server but then the CoDUOMP shuts down, the same thing happens with launcher on the Desktop (*command line: cedega --run call CoDUOMP +connect 195.228.155.158:28964*).

Please help I'm out of ideas.

Cheers!

---

