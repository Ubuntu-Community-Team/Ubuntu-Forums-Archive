---
title: "Font Manager not showing complete font family"
date: 2013-01-09
forum: Desktop Environments
---

### Post by Nick Payne on 2013-01-09
I'm running 12.10 amd64 and have font-manager 0.5.7-4 from universe installed. The Adobe font family Myriad Pro (opentype format) is installed in my ~/.fonts folder. The fonts are all visible and useable in Libreoffice writer - Myriad Pro, Myriad Pro Black, Myriad Pro Black Condensed, Myriad Pro Condensed, Myriad Pro Light, Myriad Pro Light Condensed, and gnome-font-viewer shows them all, but Font Manager only shows Myriad Pro as existing in Bold, Bold Italic, Italic, and Regular. I have a couple of other Adobe font families installed in ~/.fonts - Caslon Pro and Jenson Pro - and font manager shows the complete font families for both of those ok.

I've attached a couple of screen shots of the font viewer and font manager windows.

---

### Post by vasiliscnisrok on 2013-01-09
1) run font-manager in Terminal
2) Give the output of the program

---

### Post by Nick Payne on 2013-01-09
Running font-manager from terminal and then closing it doesn't show anything unexpected:
```
nick@nick ~ $ font-manager
INFO    :  Verified /home/nick/.fonts.conf
INFO    :  Font Manager is now starting
INFO    :  Finished loading 73 families
INFO    :  Saving configuration
INFO    :  Exiting...
nick@nick ~ $ 

```

---

### Post by vasiliscnisrok on 2013-01-11
reading configurations from ~/.fonts.conf now is deprecated.

try
```
mkdir -p ~/.config/fontconfig
mv ~/.fonts.conf ~/.config/fontconfig/fonts.conf
```

---

### Post by Nick Payne on 2013-01-11
Font Manager recreates ~/.fonts.conf:
```
nick@nick ~ $ mkdir -p ~/.config/fontconfig
nick@nick ~ $ mv ~/.fonts.conf ~/.config/fontconfig/fonts.conf
nick@nick ~ $ font-manager
INFO    :  Updating /home/nick/.fonts.conf
INFO    :  Font Manager is now starting
INFO    :  Finished loading 73 families
```
When I have a look, Font Manager has recreated ~/.fonts.conf. And it's still showing only a small subset of the installed Myriad Pro fonts.

---

