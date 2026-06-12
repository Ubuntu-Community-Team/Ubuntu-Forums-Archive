---
title: "How to adblock in Opera Linux."
date: 2009-01-29
forum: General Help
---

### Post by Tomatz on 2009-01-29
**Download the attachment** (below) and extract the **urlfilter.ini** file to your **Desktop**.

Open a terminal:

```
cd ~/Desktop
```

```
cp ~/Desktop/urlfilter.ini ~/.opera/urlfilter.ini
```

**_Restart opera_**

Done

*All credit goes to **fanboy** for his great content blocking list (urlfilter.ini). *

[SIZE="1"]Newer releases of urlfilter.ini can be downloaded here: [http://www.fanboy.co.nz/adblock/opera/](http://www.fanboy.co.nz/adblock/opera/).[/SIZE]

---

### Post by beerguzzler on 2009-01-29
Brilliant.

Exactly what I've been after and works a treat. \\:D/

---

### Post by Tomatz on 2009-01-29
To disable ad-blocking on a per site basis do this (in opera):

***F12**, Edit Site Preferences, Content **then uncheck** Enable content blocking.*

---

### Post by Lampi on 2009-05-06
Great Howto, thanks! Tomatz

---

### Post by Arup on 2009-05-06
Fanboyz works quite well, I have been using it since its early days and it has never let me down.

---

### Post by shane2peru on 2010-03-04
This is a bit of an old thread, but I thought I would pitch in.  This seems to be a decent way of adblocking in Opera.  What I did was made an easy script to do this on a regular basis for me.  You can do it like this:

```

#!/bin/bash
#This script will download the latest ad filter set from http://www.fanboy.co.nz/adblock/opera/urlfilter.ini
cd /home/$USER/.opera/
wget -c http://www.fanboy.co.nz/adblock/opera/urlfilter.ini
exit

```

Copy that into a text editor (gedit)  and save it in a folder called bin in your home directory.  Then make it executable with:
```
chmod +x /home/$USER/bin/[COLOR="Red"]scriptname[/COLOR]
```

Now we will set a crontab to update your filter on a regular basis.
In the terminal put:
```

crontab -e
```

and you can put this in the last line:

```

0 12 * * 1,3,5 /home/$USER/bin/[COLOR="Red"]scriptname[/COLOR]

```

Then hit ctrl-x to exit and y to save changes.

**NOTE:**
The first number is for the minutes, the second is for the hour, notice I have 12 therefore at 12PM mine will update.  Then the * is for Day of Month in our case any day of the month, next * is month, we want every month, then we have 1,3,5 which is for day of week, Sunday being 0 we have Mon, Wed and Fri that it will update at noon.  You can adjust those numbers accordingly.

Enjoy your Opera with automated updating of the url.  

Here is a link on the urlfilter:

[http://my.opera.com/Tamil/blog/ad-block](http://my.opera.com/Tamil/blog/ad-block)

Much info there.

Shane

---

