---
title: "what does ~ mean after the filenames???"
date: 2006-07-15
forum: Desktop Environments
---

### Post by chingazo on 2006-07-15
thanks to anybody who can help me out with this little problem.  i have searched the forums, but can't seem to find out what this means, mainly because i don't know what words to use for the search.

whenever i edit a file, say "sources.list" through vi, gedit, whatever, i always get a second copy of the file named "sources.list~".  i have no idea what is going on other than the second file seems to be identical to the first, just with a ~ at the end.

so my question is first, what is that file supposed to do, and secondly, how do i get my editors to stop making this file?  i delete them all the time, and it doesn't seem to cause any problems.

thanks again.

---

### Post by vigleik on 2006-07-15
Gedit is being "helpful" by making a backup for you. It's not dangerous, and it has no adverse effect on your system other than taking up a tiny little bit of more space.

I believe edit->preferences->editor and then unchecking the box that says "create a backup copy of files before saving" should turn it off.

Vigleik

---

### Post by chingazo on 2006-07-15
thanks for the explanation, and it does seem to only happen when i use gedit vs. vi.  i was able to disable that feature by opening up gedit, and going to the preferences, and under the editor tab, i unchecked "create a backup copy of files before saving".  i can  see where this is useful though.

---

