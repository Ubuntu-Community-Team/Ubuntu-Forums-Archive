---
title: "specify application for a particular file extension"
date: 2007-04-01
forum: Desktop Environments
---

### Post by Bloch on 2007-04-01
Greetings;

I am a dapper 6.06 user.

I have various  files that gnome all treats as plain text files (I presume gnome decides from the content and not the file extension).

These include .ram files, .cfg files, .pac files and of course .txt.

The .ram files I want to open with realplayer
The .cfg are records of Go games that I want to open with glGO
The .pac files  I want to open with Bluefish

Now when I click the properties tab on a .ram file for example and change the default to realplayer, then realplayer attempts to open ALL plain text files. This is not a satisfactory solution.

How can I change settings so that these files (and others) open with my application of choice?

---

### Post by TerryNewton on 2007-04-01
ROX Mime Editor...
[http://rox.sourceforge.net/desktop/MIME-Editor](http://rox.sourceforge.net/desktop/MIME-Editor)
[http://rox.sourceforge.net/desktop/ROX-Lib](http://rox.sourceforge.net/desktop/ROX-Lib) (required library)

Put the ROX-Lib2 dir in a dir named lib in your home dir, the mime editor itself
can be anywhere, run AppRun to start. Add new type, call it what you want
after the /x- part, specify extension (*.red etc) and comment, close. Close and
restart any open Nautilus windows, specified file extension should now have a
generic icon. Right-click properties and add what you want to the open-with tab.
Very nice! Without this program, every script I had showed for every text-based file,
now I can separate files by extension according to my needs.

Hope this helps,
Terry

---

### Post by Bloch on 2007-04-02
Thanks Terry,

your solution worked perfectly.

I see on the gnome project home website that the GNOME 2.2.1 desktop has exactly the capability that I described above: 
(the ability to choose what application is to open what files based on the file extension e.g some text files ending in .cfg  I want to open with my go-board program.)

[http://www.gnome.org/learn/users-guide/2.2/ch07s07.html](http://www.gnome.org/learn/users-guide/2.2/ch07s07.html)

If someone could confirm that GNOME on the latest Ubuntu version has this capability,  it would close this topic.

---

