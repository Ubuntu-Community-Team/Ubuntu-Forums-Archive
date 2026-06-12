---
title: "Viewing html in mutt"
date: 2006-09-24
forum: Desktop Environments
---

### Post by mark_g on 2006-09-24
I've recently switched to mutt as my main MUA and set it up to automatically render html using lynx, but I'd much rather like to view the html-mails in links2 using the framebuffer, so I've added the following lines to my .mailcap file:

> text/html; links2 -g -mode 1024x768x32K '%s';copiousoutput;description=HTML;nametemplate=% s.html
text/html; /links2 -g -mode 1024x768x32 '%s';needsterminal;description=HTML;nametemplate=% s.html

Unfortunately this opens links2 which just displays the html as <HTML><BODY> etc... What am I doing wrong?

---

### Post by mark_g on 2006-09-24
Just found that I needed to add the parameter '-force-html', because links2 normally looks at the extension to determine how to display the file.

---

