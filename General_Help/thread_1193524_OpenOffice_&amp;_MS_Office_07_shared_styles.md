---
title: "OpenOffice &amp; MS Office 07 shared styles?"
date: 2009-06-21
forum: General Help
---

### Post by sandman3838 on 2009-06-21
QUESTION:

I have a dual boot system with Winxp & Ubuntu 904.
My issue have to do with the page size or scale of the page when printing between Office 2007 and Open Office.

Although, both are accessing the same document (spreadsheet), and they are both set to auto-scale or &#8220;fit page to Width/Height&#8221;,  the Office 2007 print job is perfect.  However the Open Office print out of the same page is about 10% less.

I know that there are some discrepancies between the size and font style between Winxp and Ubuntu.  However, would any of you have any suggestions for a fix or possibly a more compatible default font that I can setup on each Offce package?

Any suggestions or tweaks between the two packages would be great!

Thanks for all you help and time.

---

### Post by blueridgedog on 2009-06-21
Have you installed the MS fonts?

---

### Post by sandman3838 on 2009-06-21
I'm not sure!

That's Ms Fonts in Ubuntu, right?

Is there a way to check.

---

### Post by blueridgedog on 2009-06-22
Well, assuming you have installed the medibuntu repositories documented at:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

In addition to the normal:
```

sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
```

Most setups require:
```
sudo apt-get install ttf-xfree86-nonfree
```

You can also add in:
```

sudo apt-get install msttcorefonts
```

I doubt it will fix your problem, but it is worth a shot anyway as it improves the appearance of your desktop.

In the long run, I suggest you realize that the applications are different and will produce different results.

---

### Post by sandman3838 on 2009-06-22
Thanks for the help.
Looks like I'll have to do some adjusting.

I already had:
libdvdcss2
w32codecs
msttcorefonts

But I didn't have was ttf-xfree86-nonfree

Again thanks for the help.

---

### Post by blueridgedog on 2009-06-22
Keep in mind that the process is young still and in the big picture it is pretty amazing to be as far along as OpenOffice is.

---

### Post by jsoellner on 2009-06-22
Have you checked that the margins and page size are the same when you open the file in both MS Excel and OOo?

You could also define the print range in OOo manually to be sure that no extra cells are being output (highlight cells to be printed and Format-->Print Ranges-->Define)

May not help but worth a try

---

