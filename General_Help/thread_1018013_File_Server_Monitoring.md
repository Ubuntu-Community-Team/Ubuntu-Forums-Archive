---
title: "File Server Monitoring"
date: 2008-12-21
forum: General Help
---

### Post by Kissell on 2008-12-21
I have been lacking something in the past year or so I've been using Ubuntu full-time for one of my file servers...  That's a good way to see who's doing what on my server.

What I am envisioning, is an easy and nice GUI program that shows me what's up with users and connections on the file server...  

For christmas, I want a program that shows me "Mary is editing a file at "/media/Data/Users/Mary/christmaslist.doc" using a Samba share" and "Joseph is using FTP to upload a file at "/media/Data/incoming/Kung Fu Christmas.mkv at 30kbps"

Currently I have no idea what's going on with the file server, if people are using it, they are, i'm unaware of it...  i can login to webmin and take a look at who's got what open on the samba shares, but that doesn't include other methods of connection, and even if it only showed me samba that would be nice, but i'd rather have a desktop GUI app only for this instead of having to login to webmin and browse to the correct page.

What I'd really like is a extra tab in SYSTEM MONITOR similar to, oh god, windows...  that tells me what users are doing what with what files where.

Anyone know of any good apps for this in Ubuntu?

---

### Post by jimmy the saint on 2008-12-21
you could ssh in to the machine and type the "users" command
I know it isn't a gui command, but it is pretty easy.

---

### Post by Kissell on 2008-12-21
When i type in "users" it just tells me what users are logged in...  I really need it to tell me what files they have open.

Also, I would prefer a GUI solution for this particular issue.

---

### Post by dcstar on 2008-12-22
> **Kissell said:**
> 
.......
What I'd really like is a extra tab in SYSTEM MONITOR similar to, oh god, windows...  that tells me what users are doing what with what files where.

Anyone know of any good apps for this in Ubuntu?

lsof and:

[http://glsof.sourceforge.net/](http://glsof.sourceforge.net/)

---

### Post by Kissell on 2008-12-22
ah, thanks, lsof looks good, was already installed...

but, I am having trouble getting glsof to work.  

Is there a repository i can add to sources.list or a .deb file?

When I unarchive the source and run .configure I get:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found
No package 'gconf-2.0' found

But when I type in "apt-get install glib-2.0" and the others it can't find them by those names... :(

---

