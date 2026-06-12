---
title: "trying to install canon pixma ip1800 printer"
date: 2008-12-20
forum: General Help
---

### Post by Raichu on 2008-12-20
I have a Canon pixma ip1800 printer that I used to use on Windows XP. I am trying to install it on my new PC that runs Kubuntu.

When I connected the printer, it seemed to recognize it. If I go to System Settings / Printers, it is listed as "Canon iP1800 series".

If I try to print, however, I get this error and to be honest I have no idea what it means:
> cupsdoprint -P 'iP1800_series' -J 'xx' -H '/var/run/cups/cups.sock:631' -U 'george' -o ' copies=1 multiple-document-handling=separate-documents-collated-copies orientation-requested=3' '/tmp/kde-george/kdeprint_ZWfORabu' : execution failed with message:
client-error-document-format-not-supported 

I tried doing a search with Google and on this forum as well but I couldn't find anything both relevant and understandable apart from a Canon site that provides a driver:
[http://support-au.canon.com.au/contents/AU/EN/0900718601.html](http://support-au.canon.com.au/contents/AU/EN/0900718601.html)
I downloaded it and it's an rpm that I don't know what to do with.

I tried going to System Settings / Printers / Add Printer Wizard but when I got the printer model selection, the iP1800 was not there. I tried opening the rpm file using the "other..." button but it rejected it.

Can anyone help?

---

