---
title: "Strange thing with syntax highliting,"
date: 2005-08-22
forum: Desktop Environments
---

### Post by Shutdownrunner on 2005-08-22
After I upgraded to breezy I began having strange problems with syntax higlighting in gphpedit and anjuta. I think that's got something to do with syntax highliting, but I'm not 100% sure. Nevertheless I see strange things in both of these programs. Here's a [screenshot](http://abtei.republika.pl/kicha.png). Has anyone out there had a similar problem and solved it? When I try to select a piece of text everything begans to move, some parts of text dissapear, some appera or move from left to right.

---

### Post by KingBahamut on 2005-08-22
Screen refresh mebbe....that looks weird. 

That or Video.

---

### Post by Shutdownrunner on 2005-08-22
Ok. I found sth like this [http://bugzilla.gnome.org/show_bug.cgi?id=312075](http://bugzilla.gnome.org/show_bug.cgi?id=312075). According to this bug report there's a bug in pango. Could anyone responsible for pango package try to fix it somehow?

---

### Post by student on 2005-08-23
yeah, I've got this problem too!
I finally find a good IDE in anjuta 2.0.1, and now this :(

---

### Post by student on 2005-08-23
ok, i managed to fix the problem with the pangomeasure patch  O:)

---

### Post by Shutdownrunner on 2005-08-24
[QUOTE=student]ok, i managed to fix the problem with the pangomeasure patch  O:)[/QUOTE]
Yeah, me too, I installed anjuta from cvs:)

---

### Post by Ricapar on 2005-10-16
I'm having this same problem as well, where would I be able to find this pangomeasure patch?

---

### Post by Shutdownrunner on 2005-10-16
[QUOTE=Ricapar]I'm having this same problem as well, where would I be able to find this pangomeasure patch?[/QUOTE]
It depends on the program. There were changes in one of the libraries required by anjuta and gphpedit. The latest anjuta from cvs works. I don't know about gphpedit, but it should also work. Maybe you should upgrade your ubuntu and see what happens.

And you have problems with which program?

---

### Post by synergynova on 2006-03-15
how do you apply the patch? I've got the .bin file?

---

### Post by andyjeffries on 2006-06-29
This bug was fixed in the latest gPHPEdit (0.9.80), it needed an upgraded GtkScintilla.

Cheers,


Andy

---

