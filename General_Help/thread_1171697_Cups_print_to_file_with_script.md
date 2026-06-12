---
title: "Cups print to file with script"
date: 2009-05-27
forum: General Help
---

### Post by jukka2 on 2009-05-27
Hello!

Been using ubuntu couple years now with little tweaking and alot of using which is good.

Now I have a problem:
I have old text only thermal printer with no linux driver
it works when writing echo test >/dev/ttyS0
But i need it to work from firefox with one special web page with couple of varying words!
Couldnt get the generic printer work so how could i make it to print to file or pipe where my scrit would clean the text and echo it to serial port? This should be possible!

---

### Post by jukka2 on 2009-05-28
Any idea of this ?

---

### Post by jukka2 on 2009-06-01
Got this working by using pdf-printer and pdftotext.
It had option to put script at the end.

Script didn't work well but it was that old ubuntu did reset the serial port after every boot so that script couldn't write to it.

---

