---
title: "Creating screensaver with SWF file"
date: 2009-09-28
forum: Desktop Environments
---

### Post by tnsmart on 2009-09-28
Hi.

I have an swf file which I am trying to make a screensaver out of by following these instructions:

[http://www.linuxquestions.org/questi...savers-515495/](http://www.linuxquestions.org/questi...savers-515495/)
and
[http://www.jwz.org/xscreensaver/faq.html#mpeg](http://www.jwz.org/xscreensaver/faq.html#mpeg)

Unfortunately, I get pretty lost in them. I have xscreensaver and adobe flash player installed, but that’s as far as I’ve gotten.  If there’s a different way to do this, I can convert the swf file into any other media file if necessary.  Can anyone help me?  Thanks.

---

### Post by tnsmart on 2009-09-29
Can anybody help me?

---

### Post by tnsmart on 2009-10-01
Anybody?

---

### Post by slidersv on 2011-01-08
> **tnsmart said:**
> Hi.

I have an swf file which I am trying to make a screensaver out of by following these instructions:

[http://www.linuxquestions.org/questi...savers-515495/](http://www.linuxquestions.org/questi...savers-515495/)
and
[http://www.jwz.org/xscreensaver/faq.html#mpeg](http://www.jwz.org/xscreensaver/faq.html#mpeg)

Unfortunately, I get pretty lost in them. I have xscreensaver and adobe flash player installed, but that’s as far as I’ve gotten.  If there’s a different way to do this, I can convert the swf file into any other media file if necessary.  Can anyone help me?  Thanks.

Maybe a bit late, but I wrote the guide on how to do it and posted it here:
[http://www.bitsonwire.com/?p=209]("http://www.bitsonwire.com/?p=209")

Here is an excerpt for people that are searching:
Step 1. Extract/Get SWF file you intend to use as a screensaver. If you have a MacOS screensaver, search the installation folder for SWF files using search tool. Put SWF file somewhere safe, where you won’t accidentally delete it. For example:
```
cd ~
mkdir .screensavers
copy flash_screensaver.swf ~/.screensavers
```

Step 2. Remove/Disable/Adjust your default screen saver so it does not conflict with xscreensaver. On ubuntu this can be accomplished using:
```
sudo apt-get remove gnome-screensaver
```

Step 3. Install xscreensaver and check if it works.
```
sudo apt-get install xscreensaver
```
On ubuntu: System > Preferences > Screensaver
And try setting some screensaver, click preview, and if it works, close the window.
(Note: this is important, launching xscreensaver for the first time will create configuration file in your home directory)

Step 4. Install Opera and Flash plugin, if you haven’t already
```
sudo apt-get install opera
sudo apt-get install flashplugin-nonfree
``` 
(Note: Opera can be substituted for any other browser that supports Kiosk Mode. Firefox for example can be used with R-kiosk plugin. Important thing is to use the browser that you won’t be using for anything else but the screensaver)

Step 5. Edit xscreensaver setting and create your own Flash screensaver.
For example, if your SWF file is located at
/home/user/.screensavers/flash_screensaver.swf
then add the following line to ~/.xscreensaver after “programs:”
```
"My Flash Screensaver"	opera -kioskmode /home/user/.screensavers/flash_screensaver.swf	\n\
```

Step 6. Set your screensaver as default in xscreensaver, and check how it works by clicking on preview.
(Note: Opera might take about 4-5 seconds to close after mouse move. You can press ALT+F4 to speed up the process. Other browsers might be quicker)

That’s it. Now you should have fully functional flash screensaver in linux. This method can be used to put up any web page as a screensaver. This method can also be used to install windows screensavers on linux by using wine and /s switch. Although that might require some tweaking because xscreensaver draws a root window over everything, and sometimes has problems drawing over wine.

---

### Post by CHEWS on 2012-02-14
Help I did this but every-time the daemon is running or I start it it removes the entry from the file so I can't set it as my default screensaver or even select it. I am on ubuntu 11.10 64bit or at least autocreates a new file it uses instead.

---

### Post by CHEWS on 2012-02-14
Actually now I just only have audio not video >.>

---

