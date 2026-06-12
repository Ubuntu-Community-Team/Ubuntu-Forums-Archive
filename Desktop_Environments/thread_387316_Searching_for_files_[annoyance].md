---
title: "Searching for files [annoyance]"
date: 2007-03-18
forum: Desktop Environments
---

### Post by phansiizwe on 2007-03-18
When trying to search for some files on a DVD I was pretty annoyed by the implemented search options.

Going to Places -> Search fires up beagle, but beagle only indexed my home directory, so it won't even search the DVD drive.
When pressing the Search button in nautilus and typing in what to search for, my home directory is search again. When the results are shown, I can press the "+" button and specify a location. I point to the DVD and press search again, though, no results are found.

The only GUI search program that finds something (but I have to start it via the terminal) is gnome-search-tool.

Is there any possibility to let Search use gnome-search-tool instead of beagle?!

---

### Post by moshuptrail on 2007-03-18
I'm using Dapper, and when I search I get the gnome-search-tool, and I can't find beagle so it must be new.

However, I can go to a command line and get help on command line options for gnome-search-tool.  I looked for an option having to do with indexes a found none.  But maybe beagle has such an option...??

Try typing man beagle from the command line and see if you can search one directory but place the index somewhere else.  I'm guessing, but perhaps beagle tries to build an index on the same place it's searching.

---

