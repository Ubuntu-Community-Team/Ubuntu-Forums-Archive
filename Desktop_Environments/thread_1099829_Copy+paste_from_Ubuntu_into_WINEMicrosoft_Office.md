---
title: "Copy+paste from Ubuntu into WINE/Microsoft Office"
date: 2009-03-18
forum: Desktop Environments
---

### Post by O-pos on 2009-03-18
Hi,

When I work in Windows, whatever picture I like online, or on the desktop, I would usually just copy & then paste into Microsoft PowerPoing or Word. Or if I would crop an image in Photoshop, then copy it - I could easily paste it in Microsoft Office.

In Ubuntu office works fine, but I can't paste what I copy. Only time it works is when I copy something which is already in office. Say, there is already a picture in powerpoint presentation - then I can copy and paste it as many times as I want. Even that does not work if I try to copy & paste between different microsoft office application (powerpoint and word, excel and powerpoint) - it should be exactly same application (word with word only, powerpoing with powerpoint only). 

That's a major disatvantage, any ideas how can I deal with that?

Thanks :(

---

### Post by Rotaj on 2009-03-18
Unless there is something I am not understanding, can't this be done with OpenOffice, and then saved as a Word, Excel or PowerPoing document?

---

### Post by O-pos on 2009-03-18
Generally yes, but when you want to prepare a powerpoint presentation and then run it from a computer with microsoft powerpoint in the conference room, fine details are not always the same.

---

### Post by sreeslinux on 2010-11-30
Did you ever fix this? I am having the exact same problem.

---

### Post by uriel1998 on 2010-11-30
I'm able to copy and paste between linux apps and ones in Wine (10.04, and the same behavior in both Wine 1.2 & 1.3) - but only if the application I'm copying *from* is still open.

For example, I can use **gnome-screenshot** to capture my desktop.  I click "Copy to clipboard" *and leave gnome-screenshot open*.  I then open **IrfanView** (EoG is great for viewing, but my basic editing needs are above F-Spot and below Gimp most days), and can Ctrl-V paste with no problem.

If I close gnome-screenshot *before* I paste, the data in the clipboard is cleared.  (If it makes a difference, this is also the case when using linux apps -  I just tested it with The Gimp as well.)

This is *totally* different than Windows (and apparently has been annoying people since [before Ubuntu 8.04]("http://www.feedelite.com/92/how-to-fix-the-ubuntu-clipboard-problem")).  There's several clipboard managers out there, but none seem to handle images well, if at all.  

So, workaround is to keep the copying *from* application open until after you've pasted.

I think that's as close to "solved" as you're going to get right now...

---

### Post by uriel1998 on 2010-11-30
> **uriel1998 said:**
>   There's several clipboard managers out there, but none seem to handle images well, if at all.  


And of course, I now [stumble across Glippy]("http://www.omgubuntu.co.uk/2010/06/glippy-simple-clipboard-manager-with-image-support/"), which proports to handle images as well.

---

### Post by sreeslinux on 2010-12-01
Was using Parcellite but the only issue seemed to be it wouldn't copy images from Okular (KDE) to Microsoft Office (wine). I had to copy to Open Office first then from Open Office to Microsoft Office - real pain. Didn't have this issue with other PDF readers but Okular is by far the fastest. 
I am a teacher and use Microsoft Office (Yuk) for compatibility for .docx, pptx.
Tried Glippy and it seems to do everything I want from a Clipboard manager.  I can copy images from any app and paste into Microsoft Office (wine).
Many thanks.

---

