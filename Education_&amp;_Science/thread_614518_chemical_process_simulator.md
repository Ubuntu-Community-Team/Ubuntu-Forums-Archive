---
title: "chemical process simulator"
date: 2007-11-16
forum: Education &amp; Science
---

### Post by armin_ahmadi on 2007-11-16
Hi everyone
I want to know if there is any linux software for CHEMICAL PROCESS SIMULATOR like HYSYS in windows

or if I can use WINE to setup HYSYS in ubuntu??
if anyone knows anything that can help me,PLEASE HELP ME
thanks

SOMEBODY PLEASE HELP ME,PLEASE

---

### Post by zadig on 2007-12-08
There might be something here at the chemistry section 
[https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

I havent used any of it though.

---

### Post by jjgomera on 2009-01-26
one years later ...

chemcad run perfect in wine

---

### Post by blizzn01 on 2011-04-14
Did you just install it via wine, then install XML Core Services via winetricks and the VB for Chemcad and VSTfA 2005 were included in the package. Is that right?

I can execute the Demos for the debutanizer but chemcad isnt loading. It's got problems with some .dll's

Did you have the same problems? I'm using wine1.3 on ubuntu 10.10.

Es fehlen/kann nicht darauf zugreifen (keine Ahnung)
error: failed to import

MFC42.DLL
ccxdlg.dll
Ppdb.dll

and some others. .. . 

Got a Solution for that

---

### Post by blizzn01 on 2011-04-14
> **blizzn01 said:**
> Did you just install it via wine, then install XML Core Services via winetricks and the VB for Chemcad and VSTfA 2005 were included in the package. Is that right?

I can execute the Demos for the debutanizer but chemcad isnt loading. It's got problems with some .dll's

Did you have the same problems? I'm using wine1.3 on ubuntu 10.10.

Es fehlen/kann nicht darauf zugreifen (keine Ahnung)
error: failed to import

MFC42.DLL
ccxdlg.dll
Ppdb.dll

and some others. .. . 

Got a Solution for that

_______________________________________

Ok i installed MFC42.dll via winetricks then mdac25.dll and it worked. Took a while to load but there it is.

---

### Post by mips on 2011-04-14
> **blizzn01 said:**
> 
MFC42.DLL
ccxdlg.dll
Ppdb.dll

and some others. .. . 

Got a Solution for that

Do you actually have those dll files in wine? If not download them or copy them from a windows install cd.

---

### Post by blizzn01 on 2011-04-14
> **mips said:**
> Do you actually have those dll files in wine? If not download them or copy them from a windows install cd.

Hi, yes loaded them via winetricks and it worked but it took 3 minutes to load the CC6 Window and it doesn't seem stable to me.
And Aspen Suite isn't working on Linux either so for job issues i'm going back to windows.

---

