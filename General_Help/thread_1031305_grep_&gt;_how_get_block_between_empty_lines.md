---
title: "grep &gt; how get block between empty lines?"
date: 2009-01-05
forum: General Help
---

### Post by gaiterin on 2009-01-05
Hi!
Can I get a complete block between empty lines in a file with the grep command?

Example: If I have this file test.txt:
test1
test2

test3
test4
test5
test7
test8

test6
test7

If I'm searching est3 or st4 or test5..., get the complete block:
test3
test4
test5
test7
test8

Thanks very very much!

---

### Post by northern lights on 2009-01-05
I figured grep wouldn't act this way and upon testing, cannot confirm this behavior.
I created an exact copy of your txt file.

This is the result```
pille@jox:~$ cat test.txt
test1
test2

test3
test4
test5
test7
test8

test6
test7
pille@jox:~$ grep st4 test.txt
test4
pille@jox:~$ cat test.txt | grep est3
test3
pille@jox:~$ 

```

---

### Post by Slim Odds on 2009-01-05
> **gaiterin said:**
> Hi!
Can I get a complete block between empty lines in a file with the grep command?

grep is the wrong tool for this job. grep is a line by line type tool. You need something that reads multiple lines and evaluates the contents.

You could write a bash shell script or use something like awk.

---

### Post by gaiterin on 2009-01-05
How can I do with awk? :)
Thanks

---

### Post by northern lights on 2009-01-05
> **gaiterin said:**
> _Can_ I get a complete block between empty lines in a file with the grep command?
Now I got it.

Misread and figured *grep* was doing this for you. Which would have been very weird.

---

### Post by Slim Odds on 2009-01-05
> **gaiterin said:**
> How can I do with awk? :)
Thanks

I'm not an awk guru, but you might try these:
[http://en.wikipedia.org/wiki/Awk](http://en.wikipedia.org/wiki/Awk)
[http://www.vectorsite.net/tsawk.html](http://www.vectorsite.net/tsawk.html)
[http://www.gnu.org/software/gawk/manual/gawk.html](http://www.gnu.org/software/gawk/manual/gawk.html)
[http://www.grymoire.com/Unix/Awk.html](http://www.grymoire.com/Unix/Awk.html)

(google: awk)

Your example should be pretty easy to do.

---

### Post by dagnabit dang doohickey on 2009-01-05
```

#!/usr/bin/awk -f

# this_script.awk
# usage: this_script.awk -v PATTERN="*pattern*" < *input-file*

BEGIN {
	RS="\n\n"
	FS="\n"
#	PATTERN="*pattern*"
}
{
	if ($0 ~ PATTERN)
	{
		print $0;
	}
}

```

One-liner:
```
awk 'BEGIN { RS="\n\n"; FS="\n"; PATTERN="*pattern*" } { if ( $0 ~ PATTERN ) print $0; }' *input-file*
```


If interested in learning about awk, the [Grymoire Awk Tutorial]("http://www.grymoire.com/Unix/Awk.html") is a great place to start. [Grymoire]("http://www.grymoire.com/Unix/") also has a fantastic [Sed tutorial]("http://www.grymoire.com/Unix/Sed.html").

---

