---
title: "Genealogy layout help"
date: 2009-01-30
forum: General Help
---

### Post by YigalB on 2009-01-30
I have a complicated family tree (13 generations) which I need to print by tomorrow.
So far I was working with FTW on M$ (please don't judge me for that :)

However, FTM 2006 wont let me play  with the layout in "all tree" mode (only in descended mode).

the layout chosen by the software is very bad.
I need a software that will let me import the Gedcom (or .FTW), including hebrew characters, and let me modify the layout.

By layout I mean the ability to move individuals, yet keep the lines that connect them.

Any idea of such software?

---

### Post by FluffyElmo on 2009-01-30
I think your best plan of action would be to export the data as GEDCOM and then import it into whatever program you choose. I've only done this once before for a friend so I'm not an expert, some features are apparently not supported by GEDCOM but I didn't have a problem.

[http://www.ancestry.com/share/awt/ftwftm.htm](http://www.ancestry.com/share/awt/ftwftm.htm)

There are a few free programs out there, GRAMPS was pretty good, but if your needs are more complicated you may want to Google and try a few.

[http://www.gramps-project.org/wiki/index.php?title=Main_Page](http://www.gramps-project.org/wiki/index.php?title=Main_Page)

---

### Post by YigalB on 2009-01-30
> **FluffyElmo said:**
> I think your best plan of action would be to export the data as GEDCOM and then import it into whatever program you choose. I've only done this once before for a friend so I'm not an expert, some features are apparently not supported by GEDCOM but I didn't have a problem.

[http://www.ancestry.com/share/awt/ftwftm.htm](http://www.ancestry.com/share/awt/ftwftm.htm)

There are a few free programs out there, GRAMPS was pretty good, but if your needs are more complicated you may want to Google and try a few.

[http://www.gramps-project.org/wiki/index.php?title=Main_Page](http://www.gramps-project.org/wiki/index.php?title=Main_Page)

I tried GRAMPS - it didnt process the Hebrew names. In addition - it doesn't allow the layout capabilities.

No much luck with google search as well.

---

### Post by FluffyElmo on 2009-01-30
I saw it supported Hebrew calendars and thought it might handle the text conversion as well. Are you sure FTM is outputting Unicode text? If not maybe you could try converting the file to Unicode first, I don't know how to do that with text files but have done it with databases.

Sorry it didn't work out and hope you find something. Good Luck!

---

### Post by YigalB on 2009-01-31
> **FluffyElmo said:**
> I saw it supported Hebrew calendars and thought it might handle the text conversion as well. Are you sure FTM is outputting Unicode text? If not maybe you could try converting the file to Unicode first, I don't know how to do that with text files but have done it with databases.

Sorry it didn't work out and hope you find something. Good Luck!

Thank you!

My conclusion is that making family trees should be separated into two different tasks: data collection and output processing.
The output should be processed by software designed to place and route, such as Visio in M$ (what is the compatible software in Linux world?)

---

### Post by FluffyElmo on 2009-02-02
I'm not sure if there is a direct replacement for Visio. Inkscape has some shape and connector tools, so you could probably start there even though it's more of a general Vector drawing tool.

[http://inkscape.org/](http://inkscape.org/)

The Inkscape file format is text/xml as well, so it's possible that you could automate some of the original data import and then use the more advanced tools to tweak the layout to your liking.

---

