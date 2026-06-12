---
title: "Problem printing to a postscript printer"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jasonmartens on 2005-10-26
Hey all, 
   I've got a Hoary client system set up as a cups client printing to a Debian Sarge system as the cups server.  The printer I'm using is a HP Laser Jet 1200.  Most things are working fine.  I can print a test page from the ubuntu system; but when I try to print out a web page, I get the following page printed instead of the web page:

The Postscript interpreter in your printer is 2014.116
This printout requires at least version 2015 or greater

Then it has some instructions for how to change the browser to use ghostscript to convert the output down to basic level 2. It says to change this:
lpr [OPTIONS]
to this:
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | lpr [OPTIONS]

However, I don't know where to change this line.  What would be the "proper" ubuntu way to fix this?

I should note that I can print from a debian etch system without a probem from browsers.  

Thanks!

---

### Post by Alexander Kirillov on 2005-10-27
> **jasonmartens]Hey all, 
   I've got a Hoary client system set up as a cups client printing to a Debian Sarge system as the cups server.  The printer I'm using is a HP Laser Jet 1200.  Most things are working fine.  I can print a test page from the ubuntu system said:**
> 
to this:
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | lpr [OPTIONS]

However, I don't know where to change this line.  What would be the "proper" ubuntu way to fix this?

I should note that I can print from a debian etch system without a probem from browsers.  

Thanks!

Open the web browser (firefox?) and enter 
about:config
Search for print_command
Find the print command for the printer in question; right-click, then select Modify and replace the original print command (usually lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}) by the new one, adding 
gs -q -sDEVICE=pswrite -sOutputFile=- -dNOPAUSE -dBATCH -dMozConvertedToLevel2=true - | in front of it. Do not forget the vertical bar | (pipe symbol).

---

