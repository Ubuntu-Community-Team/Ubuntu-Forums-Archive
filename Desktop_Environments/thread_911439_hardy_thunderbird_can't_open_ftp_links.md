---
title: "hardy: thunderbird can't open ftp:// links"
date: 2008-09-05
forum: Desktop Environments
---

### Post by david_lynch on 2008-09-05
Back when I was running SuSE, I could click on an ftp link in an email message in thunderbird, and it would grab the file and save it to the desktop.

When I attempt the same thing in ubuntu hardy, thunderbird just hangs forever. A look at the processes shows that it's launching "xdg-open" with the ftp url as argument, and xdg-open is hanging. 

Any idea how to configure this to work? The gnome "preferred applications" menu only allows web and email URLs, so how to handle ftp is apparently indeterminate.:(

---

### Post by david_lynch on 2008-09-05
Following up, it seems that xdg-open calls gnome-open, which apparently can't properly parse ftp urls. Too bad I can't just tell thunderbird to use firefox for ftp urls...

If anyone's already conquered this beast, feel free to advise...

---

### Post by david_lynch on 2008-09-08
(bump)

anybody?

---

### Post by david_lynch on 2008-10-22
(bump) anybody?

---

### Post by lorebett on 2008-10-23
I had a similar problem also with http links (not only ftp), take a look here: [http://tronprog.blogspot.com/2007/10/thunderbird-wont-open-http-links.html]("http://tronprog.blogspot.com/2007/10/thunderbird-wont-open-http-links.html")

hope this helps...

---

