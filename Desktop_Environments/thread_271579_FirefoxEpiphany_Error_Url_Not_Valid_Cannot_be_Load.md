---
title: "Firefox/Epiphany Error: Url Not Valid Cannot be Loaded on Localhost"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Burgresso on 2006-10-04
I'm creating a web page on localhost but for some reason when I load a page in Epiphany or Firefox, the page loads, and a moment later a window pops ups saying "The URL is not valid and cannot be loaded." It's pretty annoying becuase I often need to refresh the page. IE under wine does not do this. Some urls on my local host are fine; some are not. Any ideas?

Gracias,

burgresso

---

### Post by Burgresso on 2006-10-05
Update:

apparently the browsers are trying to forward to "http:/". I figured this out b/c I tried opera.

Directories on my localhost server that have been around a while do not have this error.

How can I stop it? Any advice?

gracias

burgresso

---

### Post by Burgresso on 2006-10-05
Arg! I've just gutted and reinstalled the apache server and many related packages - no luck!

:-k

---

### Post by odinfromvalhalla on 2006-10-05
installing apache is not enough.

try creating a folder called public_html in your home folder (i.e.: in terminal type: cd ~; mkdir public_html) then copy the files of the website to that folder.

now make sure apache is started (i.e.: in terminal type: sudo /etc/inid.d/apache2 start (that considering you have installed apache2, else the path will end with apache)).

now point your browser to: http://localhost/~<your_username_here>

---

### Post by Burgresso on 2006-10-05
thanks for your help odinfromvalhalla - unfortunatly, the page loads fine, then the warning comes up again. 

I wonder whats going on here?

:)  :-k

---

### Post by Burgresso on 2006-10-06
Alas, I did a complete system reinstall.

---

