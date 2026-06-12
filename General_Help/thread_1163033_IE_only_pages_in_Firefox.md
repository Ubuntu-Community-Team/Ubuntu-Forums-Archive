---
title: "IE only pages in Firefox"
date: 2009-05-18
forum: General Help
---

### Post by lsemmens on 2009-05-18
My bank claims to support firefox for windoze but will not come at a secure OS, so that does not help me. Even FF 4 Windoze does not work so their claim is a load of you know what! End of winge!

Can anyone suggest a way of convincing a site that is IE specific to load in FF or another browser. IE view works fine for me in Windoze but not in Jaunty. I am a complete novice in things Linux, but am comfortable digging around in the Windoze registry, so am willing to try. Please excuse what may be dumb questions.(If any of the mods think this is better in absolute beginner forum - I'm happy about that.)

---

### Post by Sidewinder1 on 2009-05-18
Don't think you'll have much luck convincing a financial institution to alter their web server to accommodate FF. Although I can't give you any specific instructions on "how to", have you tried installing IE through Wine and running it that way?
HTH, Side

---

### Post by Tibuda on 2009-05-18
Have you tried with the user agent switcher extensions? It will only work if the site does not uses ActiveX (which is one of the main IE vulnerabilities).

---

### Post by Sidewinder1 on 2009-05-18
If you're interested in installing IE through Wine, read this:
[http://ubuntuforums.org/showthread.php?t=1003201&highlight=Internet+Explorer](http://ubuntuforums.org/showthread.php?t=1003201&highlight=Internet+Explorer)
Side

---

### Post by lsemmens on 2009-05-18
I cant seem to convince Wine to run IE. If I open Browse C:\ Drive in Wine and navigate to home/me/.wine/dosdevices/c:/Program Files/Internet Explorer and double click on iexplore.exe as I could in Windoze all I get is a blank window titled "Wine Internet Explorer" The only option there is to minimise/maximise/Close the window.

---

### Post by ljk on 2009-05-18
You might try installing IE Tab, a Firefox Add-On.

[https://addons.mozilla.org/en-US/firefox/addon/1419?id=1419](https://addons.mozilla.org/en-US/firefox/addon/1419?id=1419)

A tiny icon appears in the bottom right hand corner of the Firefox window. Click on it and the icon changes from Firefox to IE or vice versa. This has worked on my computers, mainly when I want stuff from Microsoft (not often) and their website insists that only IE can be used.

---

### Post by Sidewinder1 on 2009-05-18
I don't use Wine but you might want to post this in the Wine forum:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
HTH,
 Side

---

### Post by lsemmens on 2009-05-18
Thanks for the help.
ljk - IE Tab is not supported in Linux, IE view is, however it needs to point to a working copy of IE to work. 

SW - I've read through the links that you posted, most of which was over my head, but from what I could make out, I thought that all that would be needed was to attempt to re-install IE through WINE.

I run into problems again in that I get a pop-up saying "Unable to find a volume for file extraction. Please verify that you have proper permissions."

I thought that I could work around that using Terminal "sudo wine IE8-WindowsXP-x86-ENU.exe" and I get a message saying "wine: /home/me/.wine is not owned by you" and here I run into my kack of knowledge.

---

### Post by Sidewinder1 on 2009-05-18
Like I said above, start a new thread in the Wine forum, listing your specific problem and I'm certain that they will solve this for you.
Good luck,
Side

---

### Post by Legace on 2009-05-18
Try this: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by lsemmens on 2009-05-18
Thanks for the assistance, the Wine forum looks like the way to go.

User agent switching didn't work either.

---

### Post by Sidewinder1 on 2009-05-18
My pleasure...

---

### Post by bacardiandwatermelon on 2009-05-18
You could try ies4linux if it is easier... IE6 works pretty well.
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by lsemmens on 2009-07-03
> **bacardiandwatermelon said:**
> You could try ies4linux if it is easier... IE6 works pretty well.
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)I might look into that, thanks.
FYI: I did a work around by setting up a virtualbox with Windoze and IE, the bank seems happy with that, so WINE got the flick, too, as it wouldn't run some of my more Windoze specific apps. When I get time, I'll re-write them to an Open Standard.

---

