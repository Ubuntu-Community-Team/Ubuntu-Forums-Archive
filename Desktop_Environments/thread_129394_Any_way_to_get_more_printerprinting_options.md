---
title: "Any way to get more printer/printing options?"
date: 2006-02-13
forum: Desktop Environments
---

### Post by naked on 2006-02-13
I miss having a rediculus amount of printer/printing options.  One of the two things that I think M$ does a better job of (#2 is gui to display properties).

I'm printing from OpenOffice and I want to be able to print 2-4 pages per page.

Seems like there are a lot options missing as well.  I don't know if this is an OO2 problem or a gnome/over all ubuntu problem.

Abiwords print 'box' allows me the option to print multiple pages per page.  But Abiword's print dialogue lacks some of the options that I get when I print via OO2.

So any way to change things?  Does Abiword and OO2 call on another program to print?  Meaning is each programs print box different?  Or do they call on a printing program to do the job and I just need to redefine what program calls which printing program?

Thanks for the help!

L

---

### Post by wrtrdood on 2006-02-13
Most of those options are dependent on the printer drivers.  Check out linuxprinting.org.  With some effort, you can generate a ppd that will let your printer do a lot more than it does now.

The printing program is dependant on what you're using but most likely it will be CUPS.  I like KDE's kprinter program better than anything I've used for my printing interface.  It's an extra hoop but often gives me much better control over what I want to print.  I just enter (or replace) on the line that most printing interfaces offer for "printing program" kprinter --stdin and I'm in business.

---

