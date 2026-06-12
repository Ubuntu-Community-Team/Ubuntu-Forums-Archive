---
title: "LibreOffice Writer Won't Open"
date: 2017-10-26
forum: Desktop Environments
---

### Post by electrosteam on 2017-10-26
Running Lubuntu 17.04 on an old Dell laptop.
AbiWord did not impress so installed LibreOffice.
All the components except Writer open Ok.
Tried re-installing Writer and re-booting without success.

Any suggestions ?
John.

---

### Post by vanadium on 2017-10-27
Try opening writer from the terminal to see if eventually error messages may point to the problem.

---

### Post by electrosteam on 2017-10-28
Thanks for the suggestion,

Could not find the way to attempt to open Writer on its own, but got LibrOffice to open from the command line.
Got errors, 10 warnings and 2 critical, typical as shown:

(soffice:2860): Gtk-WARNING **: Theme parsing error: gtk-lubuntu.css:252:14: Expected a string.

(soffice:2860): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed

I think it is time to re-install LibreOffice.
John

---

### Post by electrosteam on 2017-10-30
Did a re-install cycle of LibreOffice, but no improvement, Writer is still no-show.

Searching has revealed a reported history of this problem, with configuration possibly part of the problem.
I will settle in for some digging.
John.

---

### Post by vasa1 on 2017-10-30
> **electrosteam said:**
> ...
Searching has revealed a reported history of this problem,  ...
Could you share the link(s)?

Also, have you tried after renaming (temporarily) *~/.config/libreoffice*. First close all running instances of any LibreOffice components.```
pgrep soffice
```should come up empty. Then do the renaming.

---

### Post by electrosteam on 2017-10-30
vasai,
you solved (indirectly) the problem.

Your suggested    pgrep soffice   didn't seem to do anything.
But, your request for a link made me search for details.
There are many references to configuration problems, but I eventually got to :
            [http://forums.debian.net/viewtopic.php?f=6&t=133566#p648049](http://forums.debian.net/viewtopic.php?f=6&t=133566#p648049)

The suggested :
           apt-get remove --purge libreoffice-wiki-publisher
did the trick.
The other component, nlpsolver, was not present.
Writer now opens, saves and re-opens a document.
But ---- the document shows the same annoying flickering in the upper part of the sheet that initiated the change from AbiWord  !!!!

John

---

### Post by vasa1 on 2017-10-30
> **electrosteam said:**
> ... But ---- the document shows the same annoying flickering in the upper part of the sheet that initiated the change from AbiWord  !!!!
...
That's the first time I've read this complaint regarding LibreOffice. Can you please post the image you see when you open any LibO application and go to Help > About LibreOffice?

Re. Abiword, see [https://ubuntuforums.org/showthread.php?t=2321942&p=13514069#post13514069](https://ubuntuforums.org/showthread.php?t=2321942&p=13514069#post13514069)

---

### Post by electrosteam on 2017-10-30
vasa1,
I have to withdraw my comment about Writer flickering, I cannot reproduce it now.

AbiWord flickers, Writer does not.

I was trying various combinations at the time, perhaps I simply launched AbiWord by mistake (it was very late in the evening here).

But, my test document is filed as an 'odt', not an 'abw', with the Writer default font, not the AbiWord default font.

Testing shows that an odt document is opened by AbiWord on my system, then saved as an odt.
This is probably the confusion not realised at the time.

Probably prudent to remove AbiWord and Gnumeric to avoid problems in the future.

John.

---

