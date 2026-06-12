---
title: "Saved playlist doesn't work when moved."
date: 2009-02-14
forum: General Help
---

### Post by Shadow12313 on 2009-02-14
I recently saved a playlist of my favourite songs in totem and when I move it to I different directory I get an error message saying object not found.  I haven't moved the songs, I only moved the playlist file.  When I move it back to the original directory it starts working again.

Any ideas?

---

### Post by ju2wheels on 2009-02-14
Its probably using relative paths for the files so when you move the play list it breaks the path.

Open the playlist with a text editor and make the paths absolute and then you should be able to move it. I would also check your preferences on the program you are using to see if theres an option for that as well...

[http://en.wikipedia.org/wiki/Absolute_path](http://en.wikipedia.org/wiki/Absolute_path)

---

### Post by Shadow12313 on 2009-02-14
Thanks it works :D

---

