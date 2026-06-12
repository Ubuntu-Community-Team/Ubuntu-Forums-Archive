---
title: "Appending lines in *rc files"
date: 2009-02-25
forum: General Help
---

### Post by hardysummer on 2009-02-25
Is there a way I can append lines in *rc files? When I say "append" I mean break the line into 2 or more lines but still counts as a single line when read by the computer.

I do not like lines that are too long and require me to scroll. In bash, it allows me to append lines with "\".  Is there something similar that I can use in *rc files?

---

### Post by ibuclaw on 2009-02-25
What is your text editor?

[edit]
I say that because most text editors have a "wrap lines" option built in.
I know this is true for gedit, nano, and other socal wysiwyg editors.

Regards
Iain

---

### Post by hardysummer on 2009-02-25
> I say that because most text editors have a "wrap lines" option built in.
What is the point of it?  The wrapped line is counted as a separate line.  Thus the original line would be read as a broken line in the *rc files.

---

### Post by sgosnell on 2009-02-25
Displaying lines wrapped is **not** the same thing as inserting a newline in a file.  Don't confuse onscreen display with actual ASCII format.

---

