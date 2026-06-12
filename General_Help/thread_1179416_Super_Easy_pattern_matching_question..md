---
title: "Super Easy pattern matching question."
date: 2009-06-05
forum: General Help
---

### Post by jimmyhilldrix on 2009-06-05
I'm looking for a command that will match all occurrences of a regex pattern in a file and print the matching string.

grep insists on printing the entire line the match was found in while /pattern/ { print $1 } in gawk only matches the first pattern in the line.

For example if the input where

the cat had a bat and
a hat

and I matched /.at/

I want 

cat
bat
hat

This seems like it should be really easy to do but I haven't figured out how.

Is there anything that will do this?

---

### Post by Celauran on 2009-06-05
grep -o?

---

### Post by jimmyhilldrix on 2009-06-05
Thank you!

I knew it had to be something simple.

---

