---
title: "restore Evolution to indicator applet"
date: 2010-05-11
forum: Desktop Environments
---

### Post by Docaltmed on 2010-05-11
On a fresh install of 10.04, I had to briefly uninstall Evolution. When I did that, it naturally disappeared from the indicator applet.

However, when I re-installed Evolution, it did not restore the application to the indicator applet. I still have the Chat and Broadcast options, but not the Mail option.

How do I restore Mail to the indicator applet?

---

### Post by Docaltmed on 2010-05-11
Found a partial solution here:

[http://ubuntuforums.org/showpost.php?p=9276206&postcount=19](http://ubuntuforums.org/showpost.php?p=9276206&postcount=19)

However, on the drop-down menu, it still says "Set up mail."

How do I fix that?

---

### Post by Eannes on 2010-07-27
> **Docaltmed said:**
> On a fresh install of 10.04, I had to briefly uninstall Evolution. When I did that, it naturally disappeared from the indicator applet.

However, when I re-installed Evolution, it did not restore the application to the indicator applet. I still have the Chat and Broadcast options, but not the Mail option.

How do I restore Mail to the indicator applet?
Right click on the top panel, click "Add to Panel" and scroll down to "Indicator Applet" and you're done

---

### Post by chunky bacon! on 2011-01-28
> **Eannes said:**
> Right click on the top panel, click "Add to Panel" and scroll down to "Indicator Applet" and you're done


I have experienced exact problem as original poster, and this does not fix it.  It only adds the Indicator Applet.

The applet itself is still missing the envelope.  Google and forum searches have frustrated.  Is there anyway to get it back?

---

### Post by Frogs Hair on 2011-01-28
Restore panels to default and see if that helps .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Krytarik on 2011-01-28
Try to add a file called "evolution" to the directory "/usr/share/indicators/messages/applications", with the following content:
```
/usr/share/applications/evolution-mail.desktop
```
Then restart gnome-panel, like *Frogs Hair* mentioned.

---

### Post by chunky bacon! on 2011-01-29
> **Krytarik said:**
> Try to add a file called "evolution" to the directory "/usr/share/indicators/messages/applications", with the following content:
```
/usr/share/applications/evolution-mail.desktop
```Then restart gnome-panel, like *Frogs Hair* mentioned.


I did the restart Frogs Hair mentioned, and also did the evolution file, and then the restart, and still no envelope.

Thanks for the replies, if you come up with any other ideas, please let me know.

---

### Post by Krytarik on 2011-01-29
Check if the package "indicator-messages" is installed at all. If it's not, install it:
```
sudo apt-get install indicator-messages
```

---

### Post by chunky bacon! on 2011-01-30
> **Krytarik said:**
> Check if the package "indicator-messages" is installed at all. If it's not, install it:
```
sudo apt-get install indicator-messages
```


well, that got "kind of" closer. 

there's now an evolution "envelope" as a separate applet, but it is still not in the indicator session applet.

---

### Post by chunky bacon! on 2011-01-30
well, hold on, perhaps we have finally got it.

i found an applet called "indicator applet complete," and added it to the panel.  the evolution part is right in there, along with the volume control, the "me" bit, and the power/log off options.

great, done, thank you all for your help.

---

### Post by yobach on 2011-07-13
you can install the evolution indicator that will be display in the indicator applet

# sudo apt-get install evolution-indicator

It seem that it is not installed by default.

---

### Post by frogotronic on 2011-07-29
These solutions didn't work for me.

The evolution mail icons are there when evolution is running, but not prior to it being started.

- CH

---

### Post by ZPField on 2012-06-09
Hey, just thought I'd add to this, I know it's an old post but it is still relevant.
I've just installed Ubuntu 12.04 with the gnome fallback (my nvidia graphics card is old and unsupported thus far, and I didn't like unity much anyway).  The default email client is Thunderbird but I'm used to using Evolution, and Thunderbird 12 doesn't support calendars as yet which I use quite a lot.  So I removed Thunderbird and installed Evolution, but this took the email launcher applet out of the messaging panel.  After following these instructions, (# sudo apt-get install evolution-indicator) I can say that it worked perfectly.  Thanks to yobach for that one!

---

