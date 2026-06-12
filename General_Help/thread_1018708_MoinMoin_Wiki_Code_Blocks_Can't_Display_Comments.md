---
title: "MoinMoin Wiki Code Blocks Can't Display Comments"
date: 2008-12-22
forum: General Help
---

### Post by hyperboloid on 2008-12-22
Editing Ubuntu Wikis is based on something called moinmoin. To display code in a wiki, one surrounds it by {{{ }}}, but when the code contains embedded comments, those comments are NOT displayed on the wiki, because they are taken as comments themselves!

How does one get comments in code to diplay in the wiki? This is essential if one wants to display a script which has a first line of ```
#!/bin/bash
``` for example.

Anybody have a clue? To summarize: the problem is that when I type 
```

{{{
#!/bin/bash
printf "Hello, World!"
}}}

```
in an Ubuntu Wiki, ONLY the second line of the script is actually displayed in the Wiki.

---

