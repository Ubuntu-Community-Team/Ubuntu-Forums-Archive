---
title: "Howto: Expand Lessfile/lesspipe"
date: 2009-01-07
forum: General Help
---

### Post by christopherolah on 2009-01-07
I recently posted an idea about expanding lessfile/lesspipe on Ubuntu Brainstorm. To my surprise, no one seemed to have heard of it, let alone expanding it. Having used many great howtos from this site, I though it might be a good idea to put one here.

**Introduction:**

On Ubuntu when you use BASH, any use of less through "less $filename" is preprocessed by a program called lessfile/lesspipe. 

Lessfile is a symbolic link to lesspipe. Lesspipe is a shell script that can run various commands on a file, the output of which are piped to less.

**Modification:**

For the purposes of modification, the most important part of lesspipe's structure is a case. The input to the case is a filename. When it finds a rule that matches the filename, it runs the commands in this rule.

The case begins with:

```
		case `echo "$1" | tr '[:upper:]' '[:lower:]'` in
```

After that we can add whatever we want.

For example, if we want to run ls when the file is a directory:

```
			*/)
				ls --color='always' "$1" ;;
```


[I]Note: If you are using escape sequences, make sure you have aliased less as less -R or it will block your escape sequences.
[/I]


**Potential Applications**

At this point, the ideas that me and other people on Brainstorm have come up with for this are:

*/ : ls
source : source-highlight
*.html : html2text
*.[123456789].gz : man -u (see my idea about exploiting the LESS_TERMCAP_* variables for an improvement on this...) 
*.doc : antiword
*.odt : odt2text 

From [http://brainstorm.ubuntu.com/idea/17063/]("http://brainstorm.ubuntu.com/idea/17063/")

---

