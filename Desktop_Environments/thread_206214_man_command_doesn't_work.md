---
title: "man command doesn't work"
date: 2006-06-29
forum: Desktop Environments
---

### Post by grizzly on 2006-06-29
man anycommand gives:
```
ni-desktop% man dd                                                                                             ~/
No manual entry for dd
See 'man 7 undocumented' for help when manual pages are not available.
ni-desktop%
```

However man /ust/share/man/man1/something.1.gz works.

Heres my manpath.config:
> # manpath.config
#
# This file is used by the man-db package to configure the man and cat paths.
# It is also used to provide a manpath for those without one by examining
# their PATH environment variable. For details see the manpath(5) man page.
#
# Lines beginning with `#' are comments and are ignored. Any combination of
# tabs or spaces may be used as `whitespace' separators.
#
# There are three mappings allowed in this file:
# --------------------------------------------------------
# MANDATORY_MANPATH			manpath_element
# MANPATH_MAP		path_element	manpath_element
# MANDB_MAP		global_manpath	[relative_catpath]
#---------------------------------------------------------
# every automatically generated MANPATH includes these fields
#
#MANDATORY_MANPATH 			/usr/src/pvm3/man
#
MANDATORY_MANPATH			/usr/man
MANDATORY_MANPATH			/usr/share/man
MANDATORY_MANPATH			/usr/X11R6/man
MANDATORY_MANPATH			/usr/local/man
#---------------------------------------------------------
# set up PATH to MANPATH mapping
# ie. what man tree holds man pages for what binary directory.
#
#		*PATH*        ->	*MANPATH*
#
MANPATH_MAP	/bin			/usr/share/man
MANPATH_MAP	/usr/bin		/usr/share/man
MANPATH_MAP	/sbin			/usr/share/man
MANPATH_MAP	/usr/sbin		/usr/share/man
MANPATH_MAP	/usr/local/bin		/usr/local/man
MANPATH_MAP	/usr/local/bin		/usr/local/share/man
MANPATH_MAP	/usr/local/sbin		/usr/local/man
MANPATH_MAP	/usr/local/sbin		/usr/local/share/man
MANPATH_MAP	/usr/X11R6/bin		/usr/X11R6/man
MANPATH_MAP	/usr/bin/X11		/usr/X11R6/man
MANPATH_MAP	/usr/games		/usr/share/man
MANPATH_MAP	/opt/bin		/opt/man
MANPATH_MAP	/opt/sbin		/opt/man
#---------------------------------------------------------

#
# In a per-user configuration file, this directive only controls the
# location of catpaths and the creation of database caches; it has no effect
# on privileges.
#
# Any manpaths that are subdirectories of other manpaths must be mentioned
# *before* the containing manpath. E.g. /usr/man/preformat must be listed
# before /usr/man.
#
#		*MANPATH*     ->	*CATPATH*
#
MANDB_MAP	/usr/man		/var/cache/man/fsstnd
MANDB_MAP	/usr/share/man		/var/cache/man
MANDB_MAP	/usr/local/man		/var/cache/man/oldlocal
MANDB_MAP	/usr/local/share/man	/var/cache/man/local
MANDB_MAP	/usr/X11R6/man		/var/cache/man/X11R6
MANDB_MAP	/opt/man		/var/cache/man/opt
#
#---------------------------------------------------------
# Program definitions.  These are commented out by default as the value
# of the definition is already the default.  To change: uncomment a
# definition and modify it.
#
#DEFINE 	pager	/usr/bin/pager -s
#DEFINE 	cat	/bin/cat
#DEFINE 	tr	/usr/bin/tr '\255\267\264\327' '\055\157\047\170'
#DEFINE		grep	/bin/grep
#DEFINE 	troff 	/usr/bin/groff -mandoc
#DEFINE 	nroff 	/usr/bin/nroff -mandoc
#DEFINE 	eqn 	/usr/bin/eqn
#DEFINE 	neqn	/usr/bin/neqn
#DEFINE 	tbl 	/usr/bin/tbl
#DEFINE 	col 	/usr/bin/col
#DEFINE 	vgrind 	/usr/bin/vgrind
#DEFINE 	refer 	/usr/bin/refer
#DEFINE 	grap 	/usr/bin/grap
#DEFINE 	pic 	/usr/bin/pic -S
#
#DEFINE		decompressor	/bin/gzip -dc
#DEFINE		compressor	/bin/gzip -c7
#---------------------------------------------------------
# Misc definitions: same as program definitions above.
#
#DEFINE		whatis_grep_flags		-i
#DEFINE		apropos_grep_flags		-iEw
#DEFINE		apropos_regex_grep_flags	-iE
#---------------------------------------------------------
# Section names. Manual sections will be searched in the order listed here;
# the default is 1, n, l, 8, 3, 2, 5, 4, 9, 6, 7. Multiple SECTION
# directives may be given for clarity, and will be concatenated together in
# the expected way.
# If a particular extension is not in this list (say, 1mh), it will be
# displayed with the rest of the section it belongs to. The effect of this
# is that you only need to explicitly list extensions if you want to force a
# particular order. Sections with extensions should usually be adjacent to
# their main section (e.g. "1 1mh 8 ...").
SECTION		1 n l 8 3 2 3posix 3pm 3perl 5 4 9 6 7

Help please.

kubuntu dapper, i386 PIII.

---

### Post by mlind on 2006-06-29
man dd works for me on Ubuntu.

You could try re-creating mandb cache
```

sudo mandb

```

---

### Post by grizzly on 2006-06-29
sudo mandb gives:
```
Updating index cache for path `/usr/share/man/man1'. Wait...mandb: warning: /usr/share/man/man1/plucker-prc-install.1.gz: whatis parse for plucker-prc-install(1) failed
done.
Checking for stray cats under /usr/share/man...
Checking for stray cats under /var/cache/man...
Purging old database entries in /usr/local/man...
mandb: can't update index cache /var/cache/man/oldlocal/index.db: No such file or directory
Processing manual pages under /usr/local/man...
Purging old database entries in /usr/local/share/man...
[COLOR="Red"]mandb: can't update index cache /var/cache/man/local/index.db: No such file or directory[/COLOR]
Processing manual pages under /usr/local/share/man...
1 man subdirectories contained newer manual pages.
4 manual pages were added.
0 stray cats were added.
63 old database entries were purged.

```

Still not working, though I think that missing indexdb file could be the culprit.

---

### Post by mlind on 2006-06-29
[QUOTE=grizzly]sudo mandb gives:
```
Updating index cache for path `/usr/share/man/man1'. Wait...mandb: warning: /usr/share/man/man1/plucker-prc-install.1.gz: whatis parse for plucker-prc-install(1) failed
done.
Checking for stray cats under /usr/share/man...
Checking for stray cats under /var/cache/man...
Purging old database entries in /usr/local/man...
mandb: can't update index cache /var/cache/man/oldlocal/index.db: No such file or directory
Processing manual pages under /usr/local/man...
Purging old database entries in /usr/local/share/man...
[COLOR="Red"]mandb: can't update index cache /var/cache/man/local/index.db: No such file or directory[/COLOR]
Processing manual pages under /usr/local/share/man...
1 man subdirectories contained newer manual pages.
4 manual pages were added.
0 stray cats were added.
63 old database entries were purged.

```

Still not working, though I think that missing indexdb file could be the culprit.[/QUOTE]

I get the same output, so I guess it's normal.. Sorry, can't help you more.

---

### Post by grizzly on 2006-06-30
Anybody else?

---

### Post by mlind on 2006-06-30
Does /usr/share/man/man1/dd.1.gz file exist though?
Did you try reinstalling coreutils package that provides dd?
```

sudo aptitude reinstall coreutils

```

---

### Post by grizzly on 2006-06-30
[QUOTE=mlind]Does /usr/share/man/man1/dd.1.gz file exist though?
Did you try reinstalling coreutils package that provides dd?
```

sudo aptitude reinstall coreutils

```[/QUOTE]


the problem is not only with dd, but with "man anything"

---

### Post by grizzly on 2006-06-30
Good news! I found the problem :)

thanks to this thread [http://ubuntuforums.org/showthread.php?t=51901&highlight=manpath](http://ubuntuforums.org/showthread.php?t=51901&highlight=manpath) 

Most probably my manpath got changed by the app trayer ( This is most probably true, coz the same problem in the above link was caused by alltray or something) .

If someone can confirm this for a bug report. OR just tell me how to search the output of "man -d anycommand"

---

