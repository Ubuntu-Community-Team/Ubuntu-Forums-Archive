---
title: "ls -l across the entire terminal window"
date: 2009-01-07
forum: General Help
---

### Post by Squeegee_Joe on 2009-01-07
I feel silly posting this, but I can't find it in the man pages, and searching gets me no answers, so:

When I run ls -l, how can I make the results span more than just the default width?

For example:  When I maximize my terminal window, and run ls, it uses the entire width.  When I run ls-l it still uses the 80 character width.  Can it be changed, and how?  I've already tried the -w and -C options with no effect; it seems l overrides them.

Thanks!

---

### Post by -kg- on 2009-01-07
> I feel silly posting this, but I can't find it in the man pages, and searching gets me no answers

Open a terminal window and type in (or copy/paste) the following:

```
man ls
```

That will get you the man page for the "ls" command.

From what I read in the man, -w should be what you're looking for:

>  -w, --width=COLS
              assume screen width instead of current value


But you should probably note the following:

> DESCRIPTION
       List  information  about  the FILEs (the current directory by default). Sort entries alphabetically if none of -cftuvSUX nor --sort.

       **Mandatory arguments to long options are  mandatory  for  short  options too.** (Emphasis mine)


It may be that you need to specify column size.  I saw nothing that indicated a "word wrap" effect.

---

### Post by Squeegee_Joe on 2009-01-07
Perhaps I wasn't clear.  I've read the man pages.  I tried -w and -C, and yes, the arguments after the switches are mandatory.  They work perfectly without -l switch, but not when I use -l.

I'm not trying to be brusque, just clear. :)

I have long owner names (from my windows domain) on several files, and I can't see the names because the domain takes up 6 characters, so I get "$domain\$" instead of "$domain\$user".

---

### Post by -kg- on 2009-01-07
Can you pipe the output of the ls command into a file and read it from the file?

---

