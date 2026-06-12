---
title: "desktop icon I can drag&amp;drop TEXT to"
date: 2008-08-18
forum: Desktop Environments
---

### Post by drsar on 2008-08-18
Hi,
I'd like to be able to drag and drop text onto an icon on the desktop. 

The point of this exercise is to be able to highlight a telephone number on a web page (firefox) and let my internal fax+voice modem do the dialing. I can do this from the commandline with a self-written script a la: 
```
~/bin/dialthisnumberplease 18001231234
```
but would like to be able to this from the comfort of my browser.

I suspect for this to work I need the script behind said icon to receive the text in some variable and hand it over to my above shell script.

Thanks for your help.
DRSAR

---

### Post by Redmumba on 2008-08-18
You _can_ do this with a simple shell script (say, test.sh) as follows:

```

#!/bin/sh

~/bin/dialthisnumberplease $1

```

> 
chmod a+x test.sh


HOWEVER, you're probably going to run into a problem with Nautlius wanting to CREATE a text file when you drag raw text onto the desktop.  As to how to prevent Nautilus from doing this, I have no idea.

---

### Post by drsar on 2008-08-18
Well, precisely my problem. As you are pointing out, it doesn't work (nautilus creates a textfile with the text in it).

I can also create a launcher which allows me to accept *files* to be dragged onto it. I could then use the filename with referencing it with %f or so.

But I want **text** handed over. And I don't want it dropped in a text file.

Cheers, Stefan.

---

