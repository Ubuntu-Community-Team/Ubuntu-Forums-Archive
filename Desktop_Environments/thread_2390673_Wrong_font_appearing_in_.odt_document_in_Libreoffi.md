---
title: "Wrong font appearing in .odt document in Libreoffice"
date: 2018-05-01
forum: Desktop Environments
---

### Post by GwibberFooey on 2018-05-01
I have recently installed ubuntu 18.04. When I go to Show Application - Utilities - Fonts, it is indicated that the Courier 10 Pitch font is installed. There exists a .odt document that contains text in the Courier 10 Pitch font. When I open this document using Libreoffice, the text does not appear as Courier 10 Pitch. How can I modify this system such that the correct font gets displayed in Libreoffice?

---

### Post by Claus7 on 2018-05-01
Hello,

from a quick search it is supposed to be a bug for libbreoffice >=5.3. Download the font from [here]("https://www.fontsmarket.com/font-download/courier-10-pitch") and place it under .fonts folder in your ubu system (mind the dot in front of the name, which means that is a hidden folder inside your home folder). If this folder does not exist, just create it.
Open libbreoffice writer and it will be there.

Regards!

---

