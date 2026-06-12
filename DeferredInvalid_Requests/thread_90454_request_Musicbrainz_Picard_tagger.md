---
title: "request: Musicbrainz Picard tagger"
date: 2005-11-15
forum: Deferred/Invalid Requests
---

### Post by brian g on 2005-11-15
[http://musicbrainz.org/wd/PicardDownload](http://musicbrainz.org/wd/PicardDownload)

```
MusicBrainz Tagger NG (picard) Install Instructions
---------------------------------------------------

OS Support: 

    Linux: Works.
    Windows: Works.
    Mac: Has many horrible bugs due to wxWindows. :-(

Prerequisites:

(Please don't ask for help if you're not will to install *ALL* the prerequisites!)

1. Python 2.4

    If you don't have Python 2.4 installed, grab it from http://python.org

2. wxPython 2.6.1.x or higher UNICODE version

    Grab wxPython from http://wxpython.org/download.php#binaries 

    Make sure you get the UNICODE version -- if you don't the tagger won't run. Currently
    2.6.1.x/UNICODE is not available in binrary form for Linux. You'll have to compile it
    yourself -- I've created a script that allows me to compile picard in one easy step:

      http://musicbrainz.org/~robert/build_wx.sh

    Be sure to take a look at the build script and change the version number or install
    paths. I use a non-standard /opt install path to not conflict with the normal 
    wxWidgets/wxPython install. In order to run the tagger using the wxPython install
    from the /opt install path, start it with a script like this:

        #!/bin/sh
        export LD_LIBRARY_PATH=/opt/wx/2.6.1.0/lib
        export PYTHONPATH=/opt/wx/2.6.1.0/wxPython
        python tagger.py 

    Again, adjust paths as necessary.

3. libmusicbrainz

    You will need to install libmusicbrainz 2.1.1:

      http://musicbrainz.org/products/client/download.html

    Follow the instructions in INSTALL

4. libmusicbrainz python bindings

    These bindings require the ctypes (0.9.6) package from python:

       http://starship.python.net/crew/theller/ctypes/

    The python bindings are now included in the libmusicbrainz 2.1.2 package. If you have libmusicbrainz 2.1.1
    and don't want to install the new 2.1.2 version, download and install these bindings:

       ftp://ftp.musicbrainz.org/pub/musicbrainz/picard/python-musicbrainz-1.0b3-picard.tar.gz

    Regardless of where you get the bindings, follow the instructions in README

5. libtunepimp

    Install this version of libtunepimp:

      ftp://ftp.musicbrainz.org/pub/musicbrainz/libtunepimp-0.4.0.tar.gz

    Follow the instructions in INSTALL

6. libtunepimp python bindings

    In the python directory of libtunepimp (downloaded from above) are the python tunepimp 
    bindings. After installing libtunepimp, do this from the python directory:

       python setup.py build
       sudo python setup.py install

7. Once you've installed this long list of software packages, run the tagger from this directory:

       ./tagger.py

8. Read the README file to get a clue how to use it and to let me know about problems in the tagger.

Good luck!

rob@eorbit.net

```

---

### Post by macleod199 on 2005-11-15
I've been waiting for this too. It hasn't been updated in a long while, though, and I don't think debian has the Unicode version of wxPython required. For a while they even reverted to 2.4 from 2.6

---

### Post by souled on 2005-11-15
When I tried to run this I got some error about UTe8 or something like that.

---

### Post by 23meg on 2005-11-15
I'd like this too but I can't see it in Dapper. You should bug the MOTU instead.

---

### Post by brian g on 2005-11-18
[QUOTE=macleod199]I've been waiting for this too. It hasn't been updated in a long while, though, and I don't think debian has the Unicode version of wxPython required. For a while they even reverted to 2.4 from 2.6[/QUOTE]new version released 3 days ago. 0.5.0 i believe.
[QUOTE=23meg]I'd like this too but I can't see it in Dapper. You should bug the MOTU instead.[/QUOTE]MOTU? I don't know who/what that is..


John Dong told me to make requests for extras in the request forum...:? :confused:

---

### Post by johnio on 2005-12-12
I would like to request this one too.

I tried to manually install it and after I installed all the required software it crashes like this: 

Traceback (most recent call last):
  File "./tagger.py", line 67, in ?
    from browser import browser, filelookup, launch
  File "/home/johnio/tmp/picard-0.5.0/browser/browser.py", line 57, in ?
    from lib import events, util
  File "/home/johnio/tmp/picard-0.5.0/lib/util.py", line 73, in ?
    class ConfigSettings(object):
  File "/home/johnio/tmp/picard-0.5.0/lib/util.py", line 95, in ConfigSettings
    settingID3Encoding = tunepimp.eUTF8
AttributeError: 'module' object has no attribute 'eUTF8'

---

### Post by jdong on 2005-12-12
Extras has been closed in favor of MOTU.

---

### Post by brian g on 2006-03-29
[QUOTE=macleod199]I've been waiting for this too. It hasn't been updated in a long while, though, and I don't think debian has the Unicode version of wxPython required. For a while they even reverted to 2.4 from 2.6[/QUOTE][http://wiki.musicbrainz.org/PicardLinuxInstall](http://wiki.musicbrainz.org/PicardLinuxInstall)

---

### Post by dsvensson on 2006-04-17
[QUOTE=johnio]I would like to request this one too.

I tried to manually install it and after I installed all the required software it crashes like this: 

Traceback (most recent call last):
  File "./tagger.py", line 67, in ?
    from browser import browser, filelookup, launch
  File "/home/johnio/tmp/picard-0.5.0/browser/browser.py", line 57, in ?
    from lib import events, util
  File "/home/johnio/tmp/picard-0.5.0/lib/util.py", line 73, in ?
    class ConfigSettings(object):
  File "/home/johnio/tmp/picard-0.5.0/lib/util.py", line 95, in ConfigSettings
    settingID3Encoding = tunepimp.eUTF8
AttributeError: 'module' object has no attribute 'eUTF8'[/QUOTE]


You're missing recent versions of required libraries. Read the install documentation.

---

