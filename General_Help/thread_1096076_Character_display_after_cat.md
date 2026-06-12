---
title: "Character display after cat"
date: 2009-03-14
forum: General Help
---

### Post by georgestan on 2009-03-14
Hi,

Under the terminal, if one types 

cat <any executable>

like

cat ls

the character display will be corrupted. Could anyone give a suggestion? Thanks.

Regards,

---

### Post by Slim Odds on 2009-03-14
> **georgestan said:**
> 
the character display will be corrupted. Could anyone give a suggestion?

Don't cat executables

---

### Post by flyingbrass on 2009-03-14
Type reset and hit enter.

---

### Post by Iowan on 2009-03-14
Listing (via **cat**, **less**, etc.) executables or other binaries can issues codes that put your graphics display in modes you didn't know you wanted.  As mentioned, sometimes a reset is required.

---

### Post by Slim Odds on 2009-03-14
> **Iowan said:**
> Listing (via **cat**, **less**, etc.) executables or other binaries can issues codes that put your graphics display in modes you didn't know you wanted.  As mentioned, sometimes a reset is required.

Which is why it's best not to cat an executable in the first place.

You could make an alias or shell script that checks the file first and only cats non-executable ones.

```
#! /bin/bash

if [ -x $1 ]; then
    printf "cat with executable is not good\n"
    exit
fi

cat $1

```

---

### Post by heindsight on 2009-03-14
> **Slim Odds said:**
> Which is why it's best not to cat an executable in the first place.

You could make an alias or shell script that checks the file first and only cats non-executable ones.

```
#! /bin/bash

if [ -x $1 ]; then
    printf "cat with executable is not good\n"
    exit
fi

cat $1

```

Just relying on whether the file has execute permission doesn't help much. Firstly, many executable files are shell/python/perl/etc. scripts - nothing wrong with catting those. Secondly, many non-executable files can also screw up the terminal display.

The problem is caused by printing the ASCII code 0x0E (016 in octal or 14 in decimal) known as the Shift out character. It can usually be fixed again by echoing the shift in character (0x0F):
```
echo -e \\0017
```

A possibly better (but not necessarily foolproof) way of testing would be:
```
#!/bin/sh
if file -b "$1" | grep -iq "text"; then
    cat $1
else
    echo "Not a text file"
fi

```

Another approach would be:
```
#!/bin/sh
T=$(sed -n '/\o016/i\SO' $1)
if [ -z $T ]; then
    cat $1
else
    echo "Don't cat this file"
fi

```

EDIT:
I just realised for the first test I proposed I did:
```
grep -iq "text" $(file -b "$1")
```
which is wrong. it should be
```
file -b "$1" | grep -iq "text"
```

---

### Post by Slim Odds on 2009-03-14
Good point [heindsight]("http://ubuntuforums.org/member.php?u=222765")

But my original point still stands that it's best to make sure not to cat a "problem file", than to just reset the terminal if you do.....

---

### Post by heindsight on 2009-03-14
> **Slim Odds said:**
> Good point [heindsight]("http://ubuntuforums.org/member.php?u=222765")

But my original point still stands that it's best to make sure not to cat a "problem file", than to just reset the terminal if you do.....

I don't disagree with that. I just disagree with the method you suggested for testing whether it's OK to cat a file...

---

### Post by Slim Odds on 2009-03-15
> **heindsight said:**
> I don't disagree with that. I just disagree with the method you suggested for testing whether it's OK to cat a file...

No argument there.... ;)

---

