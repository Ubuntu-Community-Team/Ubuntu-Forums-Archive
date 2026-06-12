---
title: "Save web page as PDF using CUPS-PDF"
date: 2009-04-17
forum: General Help
---

### Post by jsdegard on 2009-04-17
Hello

I have installed cups-pdf on Hardy.  I am starting to wonder if it is what I need, though.  I was hoping that from a client machine I can save a web page as a pdf from the server using cups-pdf.  Now I'm not sure that will work.  Does cups-pdf only work on the local machine, like how Acrobat Distiller works on Windows?  Or do I just need to add remote access permissions to the /etc/cups/cupsd.conf or something?  I was trying to steer away from things like fpdf if I could.  Thanks in advance for any advice.

---

### Post by reeseslover531 on 2009-04-17
I am not sure I understand what you are looking for. Are you just trying to "print" the webpage to a pdf, and then uploading it to the server? Is that kind of what you are looking for?

---

### Post by jsdegard on 2009-04-17
Yes, I have a headless server and need to save web pages as pdf's remotely.  Once i installed cups-pdf I was hoping it would be easy like clicking print in FF, then have the option to save as pdf.  The cups-pdf printer that is created on the server can print a test page to the home directory from the cups web manager at 'http://192.168.30.30:631/'.  However, remotely I don't see how this can be done.  I can't even print a test page from Webmin remotely.

---

### Post by jsdegard on 2009-04-17
'... 
Are you just trying to "print" the webpage to a pdf, and then uploading it to the server? Is that kind of what you are looking for? 
...'

To answer this question, yes.  Except it doesn't necessarily have to be uploaded to the server.  Preferably saved to client desktop, actually.  Why, have you done this?  How??  I'm open to other solutions.

It seems I'm asking for much.  I want to solve the problem for those who do not have Acrobat Distiller or such capability in their printer options.  What I'm asking is if they could use the cups-pdf printer on the server somehow.

---

### Post by jsdegard on 2009-04-17
Well, I might give up on this.  It doesn't seem like you can save a web page as pdf client side using a driver on server side, probably for security reasons.  It should be easier than this (?).

---

