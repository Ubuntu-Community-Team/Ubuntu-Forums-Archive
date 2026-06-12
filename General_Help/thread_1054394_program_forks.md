---
title: "program forks"
date: 2009-01-29
forum: General Help
---

### Post by josefnpat on 2009-01-29
So, I use terminal a lot. Love it. When I used windows, I killed the explorer.exe and went on in terminal until I needed simple thumbnails.

This is what i like to do:

> 
cd /<folder where my music is>
vlc <best album on earth>

... and I get to hear my music (yay!)

So, now I have to wait for my vlc to close before I can use terminal again. I don't like starting new terminals. How can i simply fork it so I don't have to deal with this?

-Seppi

---

### Post by harlan on 2009-01-29
type $vlc file &

---

### Post by josefnpat on 2009-01-29
I tried vlc [file] &, vlc file & [file], it's still not forking.

Edit:

Thanks for telling me that the & forks it but doesn't show the command line after words. A description of ps, gb fg, etc would have helped a lot.

---

