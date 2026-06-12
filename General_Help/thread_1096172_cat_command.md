---
title: "cat command"
date: 2009-03-14
forum: General Help
---

### Post by blairm on 2009-03-14
Hi,

I'm combining file a and file b to create file c using the cat command; is it possible to do this so a blank line is inserted between file a and b? 
Feel I'm not explaining what I'm after too well so probably best to give an example.

File A: This is the text of file A
File B: This is the text of file B

Desired outcome for file C is below:
 
This is the text of file A
                         
This is the text of file B    

Cheers,

Blair

---

### Post by LegendofTom on 2009-03-14
you could append a newline to the first file and then concatenate.

---

### Post by Rackstar on 2009-03-14
Or if you don't wish to edit file a. Create a file d which only has an empty line, then cat a b d > c

But there should be a more elegant way.

---

### Post by snova on 2009-03-14
```
{cat first-file; echo; cat second-file} > third-file
```

This particular form of redirection will redirect all output generated from within the { } block.

Which, with the empty echo statement, will be the first file followed by a blank line, followed by the second file.

---

### Post by munishvit on 2009-03-14
> **blairm said:**
> Hi,
Desired outcome for file C is below:
 
This is the text of file A
                         
This is the text of file B    

Cheers,

Blair

Try this:
> $ cat A - B > C
hit ENTER two times and then type Ctrl-D. 

---

### Post by blairm on 2009-03-15
Thanks everyone, knew there would be an answer somewhere!

Blair

---

