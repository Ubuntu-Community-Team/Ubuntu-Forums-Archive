---
title: "Flash Issues"
date: 2008-12-06
forum: General Help
---

### Post by Zyferian on 2008-12-06
You know, I'm aware that there are billions of topics out there to cover this and I thought that I could figure it out form those, but I'm having some issues. 

I can't get flash player installed for Firefox. I know that you're supposed to use ```
sudo apt-get install flashplugin-nonfree
``` and that's having issues. When it goes to download the file from Adobe, it can't find it and so doesn't install it. 

The same thing happens when you try to let Firefox install it itself. Any ideas? Thanks!

---

### Post by thegreenblob on 2008-12-06
Have you tried downloading and installing the ubuntu .deb on adobes site?

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Zyferian on 2008-12-06
I'm not sure I know how to install a .deb file... but I can try that.

---

### Post by thegreenblob on 2008-12-06
> **Zyferian said:**
> I'm not sure I know how to install a .deb file... but I can try that.

Simply double clicking it after downloading it in the more recent ubuntu versions. ;)

---

### Post by Zyferian on 2008-12-06
Okay, I tried that... and it said that it worked and the package was installed, but after rebooting Firefox, I still can't view anything Flash oriented...

---

### Post by thegreenblob on 2008-12-06
> **Zyferian said:**
> Okay, I tried that... and it said that it worked and the package was installed, but after rebooting Firefox, I still can't view anything Flash oriented...

Hmm... not quite sure why it wouldn't work after that. :-k Might wanna try rebooting. Other than that not sure what to do. Sorry I couldn't be of more help. :???:

---

### Post by Zyferian on 2008-12-07
Okay, some new updates on my progress here... 

And I have made progress, isn't that wonderful!?

So, I figured out that it's only a problem that I'm having with Firefox. I installed Seamonkey, to see if it was going to be an issue there too, and I found that it wasn't. Sooo... here's what I did. 

I removed Firefox with apt-get, also removing the configuration files for it and the plugins folder. Then, I re-installed it... with apt-get. Then, I reinstalled Flash from the .deb file... and then tried it again, and nothing helped. 

Any ideas? Just Firefox is messing up... I'm using Mozilla Firefox 3 Beta 5.

---

### Post by phantomjoker on 2008-12-07
Well I got

> apt-get install flashplugin-nonfree

to work a few days ago - and it did nothing - firefox freezes when attemping to view ANY flash media... its useless

---

### Post by Zyferian on 2008-12-07
When trying that command, I get an error because it can't find the file to download from somewhere. Not sure why that is...

---

