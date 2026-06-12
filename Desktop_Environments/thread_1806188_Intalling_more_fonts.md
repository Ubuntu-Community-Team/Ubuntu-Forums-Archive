---
title: "Intalling more fonts"
date: 2011-07-17
forum: Desktop Environments
---

### Post by manolomanolo on 2011-07-17
Hi to all.

I am trying to install windows fonts on my Ubuntu 11.04
In detail, I wish I could install Calligraph412 BT and Book Antiqua fonts.

Any help, please?
Thanks.

---

### Post by howefield on 2011-07-17
This page should sort you out.

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by grahammechanical on 2011-07-17
@howefield

as a mater of curiosity and interest, how did you find that link? Whenever I tried to use the Ubuntu wiki to find information like that I always drew a blank. It is not obvious how to find that page from the wiki home page.

The official documentation still has the old style look, whereas that page is new style and some pages are now in fact links to the Gnome Library and not to a Ubuntu Wiki page.

I do hope that the Ubuntu Wiki is being transformed into the usual type of Wiki and away from its present use as a communication link for Ubuntu developers.

Or, do forum staff have special access to documents that are hidden from the rest of us.

Regards.

---

### Post by manolomanolo on 2011-07-17
Thanks.

However, that did not solve my problem. I had already installed that package before posting here, as well as other ttf-* packages from Synaptic but the fonts I have been requesting for (Calligraph412 BT and Book Antiqua) have not been installed.

In detail, the ttf-mscorefonts-installer description says 

> This package allows for easy installation of the Microsoft True Type
Core Fonts for the Web including:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

You will need an Internet connection to download these fonts if you
don't already have them.

NOTE: the package ttf-liberation contains free variants of the Times,
Arial and Courier fonts. It's better to use those instead unless you
specifically need one of the other fonts from this package.

which clearly shows that the requested fonts are not included.
Any other suggestion, please?
Thank you.

---

### Post by oldos2er on 2011-07-17
[s]Do you mean Calligraph421? It's not freeware:[/s] [http://new.myfonts.com/fonts/tilde/calligraph-421/](http://new.myfonts.com/fonts/tilde/calligraph-421/)

I take that back, I found some sites where Calligraph421 can be downloaded for free.

---

### Post by howefield on 2011-07-17
> **manolomanolo said:**
> 
In detail, the ttf-mscorefonts-installer description says 
<snip>
which clearly shows that the requested fonts are not included.
Any other suggestion, please?
Thank you.

I wasn't referring you to the ms-corefonts-installer package. There are a few methods of installing fonts described on the wiki. 

Is your problem finding fonts or installing ?

---

### Post by manolomanolo on 2011-07-17
A strange effect happens with LibreOffice.

I discovered that when selecting a text written in "Book Antiqua" font from a windows machine I can do see the "Book Antiqua" font selected into the text formatting bar. However, the effective font of the text is not "Book Antiqua". Also, when trying to search for "Book Antiqua" font into the fonts list of the text formatting page, it does not appear.

So, it recognises that that font should be shown but it does not shows that since it is not actually installed (I suppose).

Any clue?
Thanks again.

---

### Post by manolomanolo on 2011-07-17
> **howefield said:**
> 

Is your problem finding fonts or installing ?

At the moment, the problem is finding the Book Antiqua and the Calligraph412 BT fonts.

---

### Post by manolomanolo on 2011-07-17
> **oldos2er said:**
> 
I take that back, I found some sites where Calligraph421 can be downloaded for free.

Which sites?

---

### Post by oldos2er on 2011-07-17
[http://www.font-zone.com/download.php?fid=394](http://www.font-zone.com/download.php?fid=394)

---

### Post by Luke M on 2011-07-17
Install font-manager.

---

### Post by manolomanolo on 2011-07-17
> **oldos2er said:**
> [http://www.font-zone.com/download.php?fid=394](http://www.font-zone.com/download.php?fid=394)

Ok, that worked!
I tried to download the fonts with Firefox and it downloaded them without adding the .tff extention.
The workaround has been: rename the downloaded file and adding the .tff extention or downloading the file with Chromium.

After that, I created a new folder into the /usr/share/fonts/truetype folder by running
```
gksu nautilus /usr/share/fonts/truetype
```
and then copying the .tff file into it.
At the end, I run the following command to update the list of fonts recognized by the system
```
sudo fc-cache -f -v
```

The wonderful thing is that I did not need to restart my system to make the fonts be available suddenly! I just started the LibreOffice application (it was closed during the font installation) and that's it!

Thanks!

---

