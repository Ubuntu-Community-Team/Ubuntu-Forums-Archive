---
title: "Update symlinks"
date: 2009-01-26
forum: General Help
---

### Post by bobbob1016 on 2009-01-26
Is there a way to update symlinks?

I did "ln -s /var/lib/mythtv/videos/Movies /path/to/movies/*" (I linked the files so I would have all movies listed, and not have to navigate "Movie folder 1" "Movie folder 2").

When I did "ls" in /var/lib/mythtv/videos/Movies it showed the correct list.  However, I added a movie in /path/to/movies/ and it isn't showing up in /var/lib/mythtv/videos/Movies.

I guess a script could, but would it duplicate if I ran it again?
Could anyone help me with said script?  Since I'm not that good at writing them.

Edit:  I found out I can just re-symlink it, as in just do "ln -s /var/lib/mythtv/videos/Movies /path/to/movies/*" again, and it gives errors for the duplicates, but how do I have it auto-remove files that aren't there anymore?  They show up as red in the terminal, but don't go away without "unlink file" which can take a while with lots of files.

---

### Post by ajcham on 2009-01-26
This command will remove dead links:
```
find -L -maxdepth 1 -type l -delete

```

That said, you could just **rm** all the links before you run **ln**.
ln will recreate the live links anyway, and the dead links will be gone.

---

