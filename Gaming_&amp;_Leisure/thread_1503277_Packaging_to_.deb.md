---
title: "Packaging to .deb"
date: 2010-06-06
forum: Gaming &amp; Leisure
---

### Post by JakeFrederix on 2010-06-06
Hey everyone,

Just a quick question;
How do you package a .jar into .deb?

And I have already tried [http://mojo.codehaus.org/deb-maven-plugin/using-deb.html](http://mojo.codehaus.org/deb-maven-plugin/using-deb.html)
and it seems I'm simply incapable of changing my build-file without having my project crash on it (and I know it's probably me doing something wrong).

What I would like;

A program that opens a nice filedialog, I select the .jar, and after some processing, the given directory also contains  a .deb file.

The program I'm talking about can be found at
[jfdesigns.tk]("http://www.jfdesigns.tk") >> "hide and seek" (menu on the left) >> get it here

I'm the author of the site (and all programs on the site), so there are no copyright-issues. (It's not like I would distribute someone else's work.)

---

### Post by JakeFrederix on 2010-06-09
You know, what I'm asking can't be impossible.
In fact, you should be able to easily package programs as .deb (because it would encourage people to distribute their software that way).

---

### Post by Perfect Storm on 2010-06-09
Check here how to make a .deb: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by JakeFrederix on 2010-06-10
1) download your project source code
> I wrote the code, it's on my laptop, no need to download it. Also it's Java, not C

1.b) C/C++ compiles, Java runs (big difference, can't compile Java)

2) Making a configure-file
project does not have one yet, and it is not described in the article how to go about making one.

In short, I'm still as far away from the answer as in the beginning.
And again, one must wonder; Why is this so hard?

---

### Post by Simian Man on 2010-06-11
I recently packaged [my game]("http://ubuntuforums.org/showthread.php?p=9440795") as a .deb having never used this format before.  In looking for a guide I found several that were way too complicated and involved much more work than it should have taken (and way more than I spent on creating an rpm or even Windows installer).  Then I found [this guide]("http://ubuntuforums.org/showthread.php?t=910717") which is actually simple.  It's probably not the kosher Debian way to do things, but whatever it works :).

---

### Post by rizzeh on 2010-06-11
```
sudo apt-get install checkinstall 
```

use checkinstall instead of make install command after compiling. it'll do install and create a nice deb file. Can do just deb with it too, see man pages for that option.

---

### Post by JakeFrederix on 2010-06-11
Thanks Simian Man.
It really did the trick.
Now I'm out to find a way to get it into the "games" menu of ubuntu.
Perhaps have it execute a script when you install it so that a link is made.

Anyway, this part is solved.

---

### Post by Simian Man on 2010-06-11
> **JakeFrederix said:**
> Thanks Simian Man.
It really did the trick.
Now I'm out to find a way to get it into the "games" menu of ubuntu.
Perhaps have it execute a script when you install it so that a link is made.

Anyway, this part is solved.

That's easy and it's the same for all Linux systems - part of the FreeDesktop.org standards I think.  Just put a yourapp.desktop file in /usr/share/applications and a yourapp.png file in /usr/share/pixmaps.  Here is an example desktop file from my game (you have others to look at as well):

```

[ian@sanpedro ~]$ cat /usr/share/applications/ultrabear1.desktop 

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Ultra Bear 1
Type=Application
Icon=ultrabear1.png
Exec=ultrabear1
Terminal=false
StartupNotify=false
GenericName=Platform Game
Comment=A 2D side scrolling platform game 
Categories=Game;
X-Desktop-File-Install-Version=0.15

```

The "Categories=Game;" line is the one that makes it show up in the games menu.  For java, I suppose you'll need to put something like "java /path/to/app" on the Exec line.  If that doesn't work, putting a script that launches your program in /usr/bin would be my next attempt.

Hope that helps :).

---

