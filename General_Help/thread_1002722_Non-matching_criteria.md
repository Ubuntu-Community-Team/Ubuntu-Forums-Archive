---
title: "Non-matching criteria"
date: 2008-12-05
forum: General Help
---

### Post by jehaboth on 2008-12-05
Is there a way to search (using nautilus) for non-matching criteria? For example, I want to search an entire hard drive for files that aren't either mp3 or m4a.

---

### Post by ajcham on 2008-12-05
Hi, I thought I had the answer but it didn't work as I had expected.  In the Gnome search tool (Places > Search for Files) you can toggle 'Select more Options' and there will be a drop down box from which you can select 'Name Does Not Contain'.  From here you can, for example, enter *.mp3 to exclude mp3 files from your search, but unfortunately, I haven't yet figured out how to get this command to accept multiple search terms.

I'm going to keep trying to find the answer, so please let me know if you figure it out.

---

### Post by ajcham on 2008-12-05
Hmm... I have a way of achieving the result you want. It's an ugly kludgey solution, and far from ideal, but may be okay for now.

If you enter as a search term in the Name Does Not Contain box:
[B]*.m[p4][3a]
[/B]

It's not perfect, and will also exclude .mpa files from your search if you have any (and also .m43, but I'm not aware that that is a valid file extension).

---

