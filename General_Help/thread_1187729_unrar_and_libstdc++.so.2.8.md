---
title: "unrar and libstdc++.so.2.8"
date: 2009-06-14
forum: General Help
---

### Post by theluddite on 2009-06-14
Unrar seems broken.  Whenever I try to run it on a file I get this error:

> unrar: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory


I tried uninstalling and reinstalling various combinations of libstdc++5, libstdc++6 and libstdc++6.4.3-dev.  It's a key dependency for me.  I should mention I'm on an AMD64.  Any suggestions?

---

### Post by loomsen on 2009-06-15
Have you tried with any other rar extracting lib?

Like p7zip-rar?

If it fails, find your libstdc++ and see if it's linked in correctoly.

```
man ld
```

---

### Post by asmoore82 on 2009-06-15
[SIZE="5"]**+1**[/SIZE] for p7zip-rar

---

### Post by theluddite on 2009-06-15
Unrar is a dependency for hellanzb which I use frequently, so I rather fix it than use 7zip-rar.  But thanks for the suggestion.  

I've got libstdc++.so.5 and libstd++.so.6 in /usr/lib and I tried creating a symbolic link named libstdc++.so.2.8  to one of them in /usr/bin but that didn't work.  Any suggestions as to how I can link either of them in correctly?  Why the heck is unrar complaining about an old package anyway?

---

### Post by Databit on 2009-08-31
Ya was coming here hoping to find a fix. Hellanzb installs and runs just fine. Downloads the files and sticks the folder with all the rars in done. Just doesn't unrar them :(

update: I left off the part where I'm an idiot and hadn't enabled unrar in the config file...

---

### Post by theluddite on 2009-08-31
I actually found a workaround for this.  I discovered that it was rar that was giving me the error, not unrar.  I couldn't uninstall rar either so I deleted rar from /bin, /usr/bin and /usr/local/bin.  Then I just made a symbolic link in /bin using the code:

> ln -s /usr/bin/unrar-nonfree rar

Unrar takes all the same arguments as rar so Hellanzb calls unrar from bin using the symbolic link instead.  Finally, after months of having to manually unrar files using 7zip, then manually deleting the unwanted rars, Hellanzb is back to normal.

---

