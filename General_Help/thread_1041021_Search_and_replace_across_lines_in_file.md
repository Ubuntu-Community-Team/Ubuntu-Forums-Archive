---
title: "Search and replace across lines in file"
date: 2009-01-16
forum: General Help
---

### Post by agep on 2009-01-16
I am looking to write a command to search and replace text matching a regular expression with a string. The added complication is that I want to do this where the text being replaced spans multiple lines. 

For example replace text matching the following regular expression: [0-9]*[a-z]*[0-9]* with 00000
from the following file content. The text that should be deleted is in bold.

```

lskfjlsdfsdffsdfsdfsd
sdfsdfkskd[B]79873918dss
sdsd23123[/B]ssdasdasdsdf
sdfkhsdfkjhsdfsdfsdfs
sdfhjsdkjfhsdfsdfsdfs

```

The result should be

```

lskfjlsdfsdffsdfsdfsd
sdfsdfkskd**00000**ssdasdasdsdf
sdfkhsdfkjhsdfsdfsdfs
sdfhjsdkjfhsdfsdfsdfs

```

I've seen **sed** used to search and replace, but as i understand it it only processes one line at a time.

Please can someone point me in the right direction to solve this one?

Thanks

---

### Post by mixmaster on 2009-01-16
I don't think your regular expression will do what you think it will -
I believe [0-9]* matches 0 or more numeric characters so I think you would get:
00000
00000dss
00000
00000

having said that, there are a number of binary search-and-replace tools available free (eg sfk replace).  You would need to look at them more carefully to see if they support enough regular expression parsing for your needs.  At first glance the BED binary editor will do what you want (you would simply have to add newline into each of the character matching patterns).

---

### Post by agep on 2009-01-16
I meant + not * in the reg exp. But in any case this isn't what i am running, but an example to illustrate the kind of thing I am trying to achieve. Thanks for help so far.

---

### Post by kitrule on 2011-01-17
```
cat 'a.file' | tr -d '\n' | sed 's/[0-9][0-9]*[a-z][a-z]*[0-9][0-9]*/00000/g'
```

Sorry, just realised the OP didn't want to strip the new lines, also sorry for reviving an old thread.

---

