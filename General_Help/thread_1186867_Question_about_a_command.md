---
title: "Question about a command"
date: 2009-06-13
forum: General Help
---

### Post by ReyJavikVI on 2009-06-13
A tutorial I read says to use the command "tar cf - . | (cd / ; tar xf - )". How is that different from "cp -r * /"?

---

### Post by Frenziefrenz on 2009-06-13
Do you mean aside from the [tarring](http://en.wikipedia.org/wiki/Tar_(file_format))?

---

### Post by ReyJavikVI on 2009-06-13
This may be kind of dumb, but I tested it with a sample directory and I didn't see any tar files.

---

### Post by PureLoneWolf on 2009-06-14
Simply put, cp will copy the files as they are and tar will compress them to an archive (think zip if you come from MS)

If you follow the link that Frenziefrenz specified, you will get a full explanation of tar

Hope that helps

---

### Post by ReyJavikVI on 2009-06-14
What I mean is that tar and cp have the same result: all files are copied to the target directory, no tarballs anywhere. If you're telling me that the difference is that tar first archives them and then extracts them, I understand that, but I don't see the point. AFAIK, tar alone doesn't compress files, just archives them.

---

### Post by Girya on 2009-06-14
> **ReyJavikVI said:**
> What I mean is that tar and cp have the same result: all files are copied to the target directory, no tarballs anywhere. If you're telling me that the difference is that tar first archives them and then extracts them, I understand that, but I don't see the point. AFAIK, tar alone doesn't compress files, just archives them.

I think the difference is in the speed in which the commands work. On my box tar is about 3 times faster than cp. try this experiment:

> ~$ time tar -cvf Documents.tar Documents


> ~$ time cp -r Documents/ Documents.bak

and note the output. on my box, from tar:
real	0m0.046s :D
user	0m0.000s
sys	0m0.036s

from cp: 
real	0m1.382s :(
user	0m0.000s
sys	0m0.052s

---

### Post by ReyJavikVI on 2009-06-14
I see, thanks.

By the way, "tar cf - ." means to tar everything in the current directory?

---

### Post by Girya on 2009-06-14
> **ReyJavikVI said:**
> I see, thanks.

By the way, "tar cf - ." means to tar everything in the current directory?

don't know what the "- ." does. I use file and directory paths.

---

### Post by MaxIBoy on 2009-06-14
"-" is the previous working directory, I believe. "cd -" takes you back to the previous working directory.

"." is the current working directory, of course.

---

### Post by Girya on 2009-06-14
> **MaxIBoy said:**
> "-" is the previous working directory, I believe. "cd -" takes you back to the previous working directory.

"." is the current working directory, of course.
 
thanks!

---

### Post by pizmooz on 2009-06-14
ReyJavikVI:

actually in tar the "-" means to read from stdin or write to stdout depending on if you are compressing or extracting, respectively.  This is essential to how the command is working.

so for the command you stated:
[FONT="Courier New"]tar cf - . | (cd / ; tar xf - )[/FONT]

It is converting the contents of the current directory into a tar formatted stream, changing the directory and untarring the stream in the new directory, achieving the same result as a cp.  For an action this simple there isn't mush benefit to using it instead of cp.  However it is useful to understand because you can use the pipe concept with tar to achieve more powerful things, for instance to simulate [FONT="Courier New"]scp -r SRC_DIR REMOTE_HOST : DST_DIR[/FONT] use:

[FONT="Courier New"]tar cf - SRC_DIR | ssh REMOTE_HOST "cd DST_DIR; tar xf -" [/FONT]

---

### Post by ReyJavikVI on 2009-06-14
Thanks.

---

