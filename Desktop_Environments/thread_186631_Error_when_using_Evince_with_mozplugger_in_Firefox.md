---
title: "Error when using Evince with mozplugger in Firefox"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mikketeve on 2006-06-02
I've just installed Xubutu 6.06, and have problems with wiewing pdf's in Firefox.
First I chose 'Open with: evince' and this worked nicely, but it opened Evince in a new window. 

So I installed mozplugger via synaptic, and followed the [HowTo]("http://www.ubuntuforums.org/showthread.php?t=25685") on embedding Evince in firefox using mozplugger.

When I try to open pdfs, Evince opens embedded in the firefox window, but gives an error: "Unable to open document.  Unhandled MIME type." :confused: 

My /etc/mozplugger has this on pdf:

```
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
	repeat noisy swallow(evince) fill: evince "$file"
	repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"
```

Any suggestions?

---

### Post by msx2 on 2006-07-28
me too my friend :mad: 

whats happening??

---

### Post by dpm on 2006-07-28
I don't know if it will help, but I got mozplugger working in Epiphany and my /etc/mozpluggerrc looks like this:

```
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
    repeat noisy swallow(evince) fill: evince "$file"
    repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"    
    repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
    repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"
```

It seems to work with firefox as well.

Did you uninstall the mozilla-acroread package?

Cheers.

---

### Post by msx2 on 2006-07-28
sudo apt-get remove mozilla-acroread
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
El paquete mozilla-acroread no esta instalado, no se eliminará


Not installed!

:confused:

---

