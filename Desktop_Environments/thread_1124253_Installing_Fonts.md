---
title: "Installing Fonts"
date: 2009-04-13
forum: Desktop Environments
---

### Post by blindape on 2009-04-13
Hi, I'm looking for a simple way to add/install fonts into Ubuntu and manage them.  In an earlier thread (dated 2006) on a similar subject, one of the replies said to use >system>preferences>fonts.  However I don't have a fonts item on my preferences menu.  Is there something missing in my installation, are things done differently now as Intrepid Ibix was not in use in 2006 or is there a better more efficient way of installing fonts?

Regards,

John Curwood

---

### Post by hw-tph on 2009-04-13
While it might not be quite the solution you're looking for, I'm very content with simply copying new fonts to ~/.fonts/ and then running **fc-cache -v** to make them accessible.

To change font rendering options, including subpixel smoothing and setting the level of hinting for Truetype fonts, use System menu/Preferences/Appearance and then select the Fonts tab.

---

### Post by vrezic on 2009-04-13
Try:
[http://www.zolved.com/synapse/view_content/28550/How_to_Install_Fonts_on_Ubuntu]("http://www.zolved.com/synapse/view_content/28550/How_to_Install_Fonts_on_Ubuntu")

Veselin

---

