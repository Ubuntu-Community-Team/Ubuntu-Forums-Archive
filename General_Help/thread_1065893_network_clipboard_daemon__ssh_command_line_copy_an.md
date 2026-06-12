---
title: "network clipboard daemon / ssh command line copy and paste to client"
date: 2009-02-10
forum: General Help
---

### Post by shrift on 2009-02-10
In OSX I figured out a way to make the clipboard daemon listen on a localhost network socket, then I could forward the port of that to to a remote server when I ssh and do something like "cat filename | nc localhost 9999" to send the contents of "filename" to my local clipboard. This is much nicer than having to cat a file and highlight it in your terminal then copy it.

Does anyone know how I could do something like this in ubuntu?

---

