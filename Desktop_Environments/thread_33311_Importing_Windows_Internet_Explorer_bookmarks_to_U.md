---
title: "Importing Windows Internet Explorer bookmarks to Ubuntu Firefox"
date: 2005-05-10
forum: Desktop Environments
---

### Post by DaturaX on 2005-05-10
I am trying to import Windows XP internet explorer bookmark to Ubuntu firefox. I tried Bookmarks>Manage Bookmarks> Import>

By this only imports firefox bookmarks and does not import internet explorer as IE bookmarks are in the form of HTML.

Anyone have a solution on this?

---

### Post by egibbs on 2005-05-10
If you have a working Windows machine install Firefox under Windows and let it import your bookmarks, then copy the bookmarks.html file from the Windows machine to the Linux one.  Replace the current bookmarks.html file (under /.mozilla firefox/... in your home directory) with the imported one.

Ed Gibbs

---

### Post by derrick1985 on 2005-05-10
[QUOTE=egibbs]If you have a working Windows machine install Firefox under Windows and let it import your bookmarks, then copy the bookmarks.html file from the Windows machine to the Linux one.  Replace the current bookmarks.html file (under ./mozilla firefox/... in your home directory) with the imported one.

Ed Gibbs[/QUOTE]

Or, you could just import the bookmarks.html file in Firefox (linux) that always works too.

---

### Post by egibbs on 2005-05-10
You'ds think, wouln't you, but not for me.  But then most things don't work for me. . :-? 

When I tried to do that it actually opened the html file rather than importing the bookmarks.  Of course I'm noo to Linux and probably did something silly.  So I just brute forced it in the hard way.

Ed Gibbs

---

### Post by derrick1985 on 2005-05-10
[QUOTE=egibbs]You'ds think, wouln't you, but not for me.  But then most things don't work for me. . :-? 

When I tried to do that it actually opened the html file rather than importing the bookmarks.  Of course I'm noo to Linux and probably did something silly.  So I just brute forced it in the hard way.

Ed Gibbs[/QUOTE]

Whatever works, that's the best thing about linux.

for me, it would crash firefox, found out it was the theme I was using.

---

### Post by DaturaX on 2005-05-10
Thanks guys! Got it to work. As simple as doing an export of bookmarks in IE and importing it in firefox.

---

