---
title: "Exile III on Edgy Kubuntu"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by obsidion on 2007-01-12
HI,

 Any help here would be welcome.
Have recently upgraded to edgy, actually fresh install but no matter.
Any way been trying to get exile III to run.

[http://www.spiderwebsoftware.com/productsOld.html](http://www.spiderwebsoftware.com/productsOld.html)

It ran no problems on dapper but won't even fire up and crash on edgy using alt-F2
I have tried it from a terminal both the symlink and using ./ from the install directory.
I get nothing, no output even to complain about a missing library or some such.

 It could be something about xorg in edgy I suppose but surely I should get some sort of error message so I know how to start solving. I suppose if all else fails I could use wine and run the windows version but really don't want to go that route.

---

### Post by Perfect Storm on 2007-01-13
Check if there's a log file in the ~/.exile folder.

---

### Post by obsidion on 2007-01-13
> **Artificial Intelligence said:**
> Check if there's a log file in the ~/.exile folder.

  Good thought, but no joy just the .dat file that should be created there.
The thing I have noticed that is a little different from other installs. The exile3-fullscreen-binary is in red like something is logging on to it. Even tried delting this as I usually don't run it fullscreen anyway. Top isn't showing anything running, it's the sort of problem I have never had before ie the no output from a terminal bit. So I am at a bit of a loss where to even start looking
  Ah...getting somewhere now the exile3 symlink is pointing at the fullscreen. Ran exile3-binary instead and got an error message of no libtwin32.so which seems a little strange but I will go see what I can find

---

### Post by obsidion on 2007-01-13
I'm giving up with this, finally found twin32 lib in an older rpm then it wanted another library that is only in an old winex. I'm begging to think it is some sort of half windows half linux hybrid

---

### Post by Githlar on 2007-11-26
Same Problem under Ubuntu Gutsy. I did a little looking around. The reason that it gave you the missing library is because the exile3 program is a script that loads some environment variables before starting exile3-binary. One of those variables points to several locations where that library could be.

As far as getting fullscreen mode working, I'm in the same boat. However, I did a little editing of the exile3-fullscreen script so that it would print the errors encountered instead of sending them to /dev/null (which is what it does by default). This is the error that it won't show you:

The X Window System does not appear to be
running. Although exile3-fullscreen runs a separate
X server, it is designed to be run from an icon or
console in the X environment, in order to provide
a convenient 'Switch to Desktop' button which
returns there. Launch exile3-fullscreen from
your X environment, such as KDE or GNOME.

But that's weird. I am running GNOME when I call that script...

---

