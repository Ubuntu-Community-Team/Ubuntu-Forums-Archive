---
title: "Epson Stylus C84 - working, but Not working."
date: 2006-04-27
forum: Desktop Environments
---

### Post by nismoskys on 2006-04-27
im trying to get my Epson Stylus C84 to work and it just wont.
It **works** in the sense that the computer recognizes it and sends it something to print, but all that comes out are blank pages. the printer 'thinks' it's printing but i only get blank pages. im sure there's ink in there because you can shake around the cartradges and hear the ink splash around, and escputil tells me i have 34% remaining..
```
           Ink color    Percent remaining
               Black     34
                Cyan     50
             Magenta     41
              Yellow     43
```
does anyone know why it doesnt actually print anything out?

-I'm using the Stylus C84 driver in gimpprint.

thannks.

---

### Post by nismoskys on 2006-04-27
i cant even get it working on Windows..
i performed 'print head nozzle cleaning' several times through the Windows driver from epson.com, but no effect, i dont even get a drop of ink on the paper when it comes out.

---

### Post by Sef on 2006-04-28
This is from LinuxPrinting.org

> Epson printers has permanent piezo nozzles. As you cannot change them the printer will get unusable if it is so heavily clogged that the printer-internal cleaning mechanisms do not work any more. To initiate the nozzle cleaning Gimp-Print includes command-line-based cleaning/loading/testing software and an alternative software with graphical user interface is available: MTink. Furthermore, for many Epsons alternative special-purpose inks are available (archival, greyscale, altered gamuts, etc), as well as more options for refilling and continuous-feed systems. In most cases, the Epson arrangement is better; at the cost of some simple regular maintenance you get a more flexible and capable device.

LinuxPrinting.og:

[http://linuxprinting.org/suggested.html]("http://linuxprinting.org/suggested.html")

MTINK:

[http://xwtools.automatix.de/]("http://xwtools.automatix.de/")

---

### Post by nismoskys on 2006-04-28
thanks alot, but im not home right now though, so i'll try it when i get back.

---

