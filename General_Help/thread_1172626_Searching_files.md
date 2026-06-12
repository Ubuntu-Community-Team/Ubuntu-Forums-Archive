---
title: "Searching files?"
date: 2009-05-28
forum: General Help
---

### Post by PerfectReign on 2009-05-28
I am using the file browser (ubuntu 9.04, gnome 2.261) and trying to find files in my home folder.

I want to find files that contain a specific string.

There doesn't seem to be a method to do this from the file browser. In searching the intraweb, I see there's a search tool - gnome-search-tool - that does find text in files. However, it doesn't allow me to double-click on the files. For example, I'm searching on a string inside of .php files. I want to open them with text editor.

What can I do?

Sorry if this seems silly, I'm coming from a Windows and KDE world.

---

### Post by fatality_uk on 2009-05-28
Have you tried the search option from the places menu?

---

### Post by elysianfields44 on 2009-05-28
The grep command can search for files based on their contents.

For example, if you wanted to search all files in the current directory for *string* (where you replace *string* with the expression you want), type from terminal:

```
grep -l string *
```

Note that *string* is case-sensitive. To search subdirectories as well you could use grep with find, like this:

```
find . -name '*.txt' | xargs grep -l string
```

The above will search the current directory (.) for files with any filename ending in .txt, which contain the expression *string*.

For more information on searching files based on a number of criteria, see:

```
info find
```

---

