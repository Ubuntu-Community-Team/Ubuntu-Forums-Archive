---
title: "How do I get a list of subkeys from Gnome configuration?"
date: 2009-01-20
forum: Desktop Environments
---

### Post by rrwo on 2009-01-20
I am looking to programmatically (either in a shell script, or a Perl script) get a list of subkeys from a key.  I can't find anything in the documentation or web searches on how to do this.

Specifically, I want to get the names of Gnome Terminal Profiles from /apps/gnome-terminal/profiles, e.g. all of the /apps/gnome-terminal/profiles/*/visible_name keys.

How do I do this, without using an evil hack like

```
gconftool-2 --search-key visible_name /apps/gnome-terminal/profiles \
 | grep -e \ /apps/gnome-terminal/profiles/.*/visible_name\ \=\ .*$ \
 | cut -d "=" -f 2 \
 | sed 's/^\s\+/\"/' |sed 's/\s*$/\"/'
```

Update: I've found that the Gnome2::GConf Perl module has an (undocumented!) method get_dirs() that does what I need.

Update #2: from the command-line, I use gconftool --all-dirs.

---

