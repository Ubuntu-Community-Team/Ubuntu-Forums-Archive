---
title: "basic unix help"
date: 2009-04-10
forum: General Help
---

### Post by zebettra on 2009-04-10
Hi,

I have a text file with lines as follows
  foo bar
  blah blah
  FORMAT = RAM
  hello world
  KEY = RAM

Is there a way in command line to parse the file and change 'RAM' to 'ROM' but only in the line that begins with 'FORMAT'? (maybe with sed/awk/perl)

Thanks in advance for the help

---

### Post by tjwoosta on 2009-04-10
not sure about with the command line, but geany has a great replace feature


you could set it to search for FORMAT = RAM

and replace it with FORMAT = ROM

and it will do this for the entire document if you want it to

---

### Post by glotz on 2009-04-10
With sed it could be done for example with```
sed '/FORMAT/s/RAM/ROM/g' *input_file > output_file*
```

This actually changes RAM to ROM on any line containing (not beginning) with FORMAT.

---

### Post by ghostdog74 on 2009-04-10
> **zebettra said:**
> Hi,

I have a text file with lines as follows
  foo bar
  blah blah
  FORMAT = RAM
  hello world
  KEY = RAM

Is there a way in command line to parse the file and change 'RAM' to 'ROM' but only in the line that begins with 'FORMAT'? (maybe with sed/awk/perl)

Thanks in advance for the help

```

awk -F"=" '$1~"FORMAT"{$2="ROM"}1' OFS="=" file

```

---

