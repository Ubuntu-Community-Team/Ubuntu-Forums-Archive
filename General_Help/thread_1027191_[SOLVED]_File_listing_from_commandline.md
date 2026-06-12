---
title: "[SOLVED] File listing from commandline"
date: 2009-01-01
forum: General Help
---

### Post by dwasifar on 2009-01-01
This is going to seem like a dumb question.

When using ls, how do I combine a wildcard file specification with the -R flag?  Say for instance I want to see a listing of just the mp3 files within a directory structure.  The top directory of the structure is ~/mp3, and all the actual mp3 files are in folders below that level.

If I do
```
cd ~/mp3
ls -R
```
I get a recursive listing of everything below that level, whether it is mp3 file or not.  But if I try to restrict it to just mp3s, like so:
```
cd ~/mp3
ls -R *.mp3
```
I get nothing, apparently because the wildcard file specification causes it not to look deeper.

Surely this is possible to do and I'm just not seeing it.

---

### Post by adult swim on 2009-01-01
in mp3 directory try ```
ls | grep mp3
```

---

### Post by dwasifar on 2009-01-01
I actually have to pipe it to grep?  Wow.  As flexible as ls is, you'd think there'd be a switch for this.

---

### Post by dagnabit dang doohickey on 2009-01-01
```
find . -name '*.mp3' -printf '%f\n'
```

---

### Post by snova on 2009-01-01
> **dagnabit dang doohickey said:**
> ```
find . -name '*.mp3' -printf '%f\n'
```

Or:

```
find -name '*.mp3' -print
```

:P

Depending on the shell, you could also do:

```
ls **/*.mp3
```

But although this works with Zsh, it's not part of Bash.

If all your mp3's are at the same folder depth, you could also do something like this:

```
ls */*/*.mp3
```

Add and remove wildcards as necessary.

---

### Post by ghostdog74 on 2009-01-01
> **adult swim said:**
> in mp3 directory try ```
ls | grep mp3
```

you don't have to pipe to grep when listing file names of directories. Just use shell expansion
```

ls *.mp3

```
many people forgot that.

---

### Post by dagnabit dang doohickey on 2009-01-02
```

#!/usr/bin/env bash

function lr ()
{
	local default_format format options search_dir usage OPTIND
	default_format='%f\n'
	usage="Usage: ${FUNCNAME[0]} [-fph] [-d DIRECTORY] PATTERN
 -d   specify directory to search, else current directory
 -f   print file names omitting path (default)
 -p   print file names including path
 -h   display this help and exit\n
Try quoting the pattern, if getting unexpected results.\n"

	OPTIND=1
	while getopts ":d:fph" options
	do
		case $options in
			d	)	search_dir="$OPTARG"; [ ! -d "$search_dir" ] && echo -e "${FUNCNAME[0]}: $search_dir: directory does not exist\n$usage" && return 1;;
			f	)	if [ -z "$format" ]; then format='%f\n'; else echo -e "$usage"; return 1; fi;;
			p	)	if [ -z "$format" ]; then format='%p\n'; else echo -e "$usage"; return 1; fi;;
			h	)	echo -e "$usage"; return 0;;
			?|:	)	echo -e "$usage"; return 1;;
		esac
	done
	shift $((OPTIND-1)); OPTIND=1

	[ -z "$1" ] && echo -e "${FUNCNAME[0]}: missing pattern\n$usage" && return 1
	find "${search_dir:-.}" -name "$1" -printf "${format:-$default_format}"
}

```

---

### Post by dwasifar on 2009-01-02
See, this is what I love about this place.  All sorts of different answers, and most of them useful.  :)

Thanks guys!  Special thankyou to dagnabit who apparently wrote me an entire function.  :)

---

