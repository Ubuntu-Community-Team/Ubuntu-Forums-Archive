---
title: "Changing Names of Directorys in Root"
date: 2009-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dave30c on 2009-05-02
I'm a complete Newbie to Linux and Ubuntu, having just bought a Dell Mini.  Am currently listening to VTCs tutorials, and had this question.  

What happens if I change the names of the directories in the Root Directory?  For example, I change "bin" to "Applications."  

I don't want to do anything until I know I won't screw up the system.

Thanks

Dave

---

### Post by unutbu on 2009-05-02
Changing /bin to /Applications would be very bad, I think.
Many scripts call programs in /bin, and they reference the apps using a full path name like "/bin/sh". If you move bin to Applications, then all scripts that reference "/bin/sh" would break.

---

### Post by dave30c on 2009-05-02
> **unutbu said:**
> Changing /bin to /Applications would be very bad, I think.
Many scripts call programs in /bin, and they reference the apps using a full path name like "/bin/sh". If you move bin to Applications, then all scripts that reference "/bin/sh" would break.

I was afraid of that.  

Then, why are the names nothing but jargon?

---

### Post by unutbu on 2009-05-02
Jargon? I don't understand what you mean.

The Linux filesystem hierarchy is an agreed-upon convention. To read about it, open a terminal and type
```

man hier
```

---

### Post by dave30c on 2009-05-02
> **unutbu said:**
> Jargon? I don't understand what you mean.

The Linux filesystem hierarchy is an agreed-upon convention. To read about it, open a terminal and type
```

man hier
```

"Bin" for "binaries" might as well be in Esperanto, totally foreign to almost everybody.  It's real meaning is "Applications," or so I understand.  

That's "jargon."  Just like lawyers sometimes lapse into inscrutable Latin -- Res ipsa loquitor, coram nobis, habeas corpus, ...

---

### Post by unutbu on 2009-05-02
LOL, no matter what the Linux developers chose, someone would call their choice inscrutable. :)

To me, /bin res ipsa loquitor.

If you'd like to call /bin, /Applications, then 
open a terminal (Applications>Accessories>Terminal) and type
```

sudo ln -s /bin /Applications
```

Error coram nobi, we can create a "symlink" (symbolic link) from /Applications to /bin.
The actual programs will remain in /bin, but you can access them through /Applications.

If you'd prefer making the symlink with a GUI, here are instructions:
[http://linux.about.com/library/gnome/blgnome6n6l.htm](http://linux.about.com/library/gnome/blgnome6n6l.htm)

---

### Post by dave30c on 2009-05-03
Thanks for all the suggestions, but they look much too complicated for Newbie me.  

Dave

---

### Post by dave30c on 2009-05-03
> **dave30c said:**
> "Bin" for "binaries" might as well be in Esperanto, totally foreign to almost everybody.  It's real meaning is "Applications," or so I understand.  

That's "jargon."  Just like lawyers sometimes lapse into inscrutable Latin -- Res ipsa loquitor, coram nobis, habeas corpus, ...

I went into terminal, entered "man hier" and got the message "No manual entry for hier"

???

---

### Post by unutbu on 2009-05-03
Edit: Second response:
If you are new to Ubuntu (or Linux), I would recommend reading the free book mentioned in this forum sticky:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

It will give you a better introduction than reading man pages.

------------------------------------------------------------
First response:

The command "man hier" should work if you have the manpages package installed. I thought this package was installed by default, but for some reason it does not appear to be true on your system. 

If you have the hard drive space (~7MB), it would be good to install the manpages package. 

On the other hand, if you don't have the hard drive space, or do not intend to use the command line often, then you can look up man pages here:

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

Just type "hier" into the search form near the top of the page.

By the way, (speaking of jargon), manpages is jargon for manual page.

---

### Post by gbrainin on 2009-05-03
> **dave30c said:**
> "Bin" for "binaries" might as well be in Esperanto, totally foreign to almost everybody.  It's real meaning is "Applications," or so I understand.  

That's "jargon."  Just like lawyers sometimes lapse into inscrutable Latin -- Res ipsa loquitor, coram nobis, habeas corpus, ...

Of course it's jargon.  But then again, so is "application."  Not so long ago, "application" was a word meaning a written request for admission to a school (among other things).

Yes, there's a learning curve when you go from one area to another, where a different jargon applies.  Most people find that the learning curve isn't all that steep for what they're actually trying to do.  If you're just running programs from the GUI, you won't spend much time on the command line, and most of the time don't need to care whether your programs are in a directory ("folder") called /bin or /Applications or /qwrfldu.

If you really care what your program directory is called, as noted above, you can create a symbolic link ("Shortcut") which gives the directory a second name, rather than a new name.  That way, the programs can call it /bin and you can call it /Steve, and both of you are happy.

---

