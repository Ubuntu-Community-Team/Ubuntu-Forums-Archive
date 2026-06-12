---
title: "How to change pdf printing defaults in Firefox"
date: 2009-01-18
forum: General Help
---

### Post by Starbuck13 on 2009-01-18
Just an easy question, I can't find an answer to: How do you change the default printing options, for "print to file" in Firefox? I'm referring to printing options like saved location, pdf or ps, what headers and footers are used. Any help is much appreciated---Thanks!

---

### Post by kaibob on 2009-01-18
You can set the default save path and file type by changing the following Firefox about:config preferences:

```
print.printer_PDF.print_to_filename
```

```
print.printer_Print_to_File.print_to_filename
```

The following is an example of the value that I use:

/home/kaibob/pdf/mozilla.pdf

The headers and footers are set in the options tab of the print dialog. By default, these settings stick from session to session.

As an aside, I have compared the output created by cups-pdf and by the Firefox print-to-file pdf option, and cups-pdf produces clearer output and smaller file sizes on my machine. Also, PDF documents created with the Firefox print-to-file pdf option do not print reliably for me. So, you may want to try both to see which works best for you.

---

### Post by patspam on 2009-11-24
I found that I had to change print_to_filename for *all* printers for this to work (as suggested [here]("http://ubuntuforums.org/showthread.php?t=1228123")).

---

### Post by NikUAE on 2010-05-03
BUMP
All well and good in Firefox what about other browsers :confused:

---

### Post by Elfy on 2010-05-03
> **NikUAE said:**
> BUMP
All well and good in Firefox what about other browsers :confused:

Rather than hijacking a thread about firefox you would be better served starting your own thread.

---

### Post by blitzter47 on 2011-07-16
@Starbuck13 : I think it's time to write [SOLVED] in the title...

---

