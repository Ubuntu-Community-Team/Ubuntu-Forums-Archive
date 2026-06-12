---
title: "PDF viewers for Firefox?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Sutekh on 2005-11-28
Currently Acrobat reader is displaying PDFs in Firefix for me, but I don't like the look of it (doesn't fit the theme).

Can I change the viewer to say evince?  How would I do this?

---

### Post by amohanty on 2005-11-28
In nautilus 
Places->Computer
Navigate to the pdf file

right click on the file and select properties
select the open with tab
click on Add
select the application you want to use
select its radio button and click ok

HTH
AM

---

### Post by Sutekh on 2005-11-28
Thanks but that only changes the program that views PDFs saved to my computer, I'm talking about viewing PDFs online in Firefox.  Is there anyway to change the program that views PDFs in Firefox?

---

### Post by Sutekh on 2005-11-28
Okay I found this HOWTO (amazing what happens with a change in search words) [HOWTO: Embed PDFs with Evince in Mozilla/Firefox]("http://www.ubuntuforums.org/showthread.php?t=25685&highlight=firefox+pdf+viewer")

It's for Hoary and requires mozpluggerrc, which is not in any Breezy repos that I could determine.  Is there anything like mozpluggerrc for Breezy?  Is there any other way to do what I want?

---

### Post by amohanty on 2005-11-28
I use the PDF file extension to at least get a choice and then usually download it to view the file separately.

If you put this in the Firefox location bar:
about:Plugins

can you find a handler for pdf? If so then go to Edit->Preferences->Downloads->Plugins 
and disable the plugin handler. Then the next time you click on a pdf file, it will prompt you where in you can specify that FF use an alternate program always.

HTH
AM

---

### Post by Sutekh on 2005-11-28
Yeah! Thanks! OK that half-worked, Firefox opens PDF with evince, but not inside Firefox, it opens a new window.  Is there a way to get evince (or other) to open the PDF in Firefox itself?

---

### Post by Sutekh on 2005-11-28
Ok I'm obviously not thinking straight, the answer was right in front of me.  Again changed the search words.  Searched for mozplug (not mozpluggerrc) in Synaptic and found mozplugger.  Installed that followed the HOWTO, and now have lovely embedded PDFs in evince.

Thanks for your quick responses amohanty.  I actually was lookg for that info for some other default apps that need changing.  Thanks again!

---

### Post by sabitha on 2005-11-28
why dont u try with mozilla-acroread
that's work for me on hoary 5.04 i dont know if there program list on breezy ;)

---

### Post by Sutekh on 2005-11-28
I had been using mozilla-acroread but it didn't look very nice with the rest of my theme.  Where as evince fits right in being a GTK application.

Should have taken a screenie with the acroreader to illustrate.

---

