---
title: "Firefox mime types on KDE"
date: 2008-04-29
forum: Desktop Environments
---

### Post by swistakers on 2008-04-29
Does anybody know if there's a way to make Firefox recognize KDE mime types? Or just any mime types. Maybe it would be possible to install some packages from Gnome or insert something in the home directory.
I'm using Kubuntu 8.04 with Firefox 3 beta 5.

Thanks in advance.

---

### Post by swistakers on 2008-05-10
bump

---

### Post by Xiong Chiamiov on 2008-05-10
What exactly are you trying to do?  Could you give me a more concrete example?

---

### Post by takowl on 2008-05-10
Guessing at what the poster probably meant:

Firefox largely works nicely in KDE. However, when you download a file and it offers you "open in ..." or "save file", it doesn't recognise the default program it should use to open a file--e.g. I have to use the file dialogs to find the executable file for Okular, or OpenOffice, or whatever is appropriate to open the file type. I can then click "remember this" and it will do so for all, say, PDF files. It would be nice, however, if it could tap into KDE's file associations so that it would automatically select Okular to read PDF files, and so on.

I hope that all makes sense...

---

### Post by swistakers on 2008-05-16
> **takowl said:**
> Guessing at what the poster probably meant:

Firefox largely works nicely in KDE. However, when you download a file and it offers you "open in ..." or "save file", it doesn't recognise the default program it should use to open a file--e.g. I have to use the file dialogs to find the executable file for Okular, or OpenOffice, or whatever is appropriate to open the file type. I can then click "remember this" and it will do so for all, say, PDF files. It would be nice, however, if it could tap into KDE's file associations so that it would automatically select Okular to read PDF files, and so on.

I hope that all makes sense...

That is exactly what I meant.

---

### Post by luisfpg on 2009-04-26
Take a look at my post at [http://luisfpg.blogspot.com/2009/04/making-firefox-open-files-honoring-kdes.html](http://luisfpg.blogspot.com/2009/04/making-firefox-open-files-honoring-kdes.html)
It shows an easy way on how to do this.

---

### Post by lodp on 2009-12-13
Thank you so much, luisfpg. This got rid of a major firefox annoyance for me, bad KDE integration in this regard has been bothering me for years.

It's weird though -- there's a difference in file associations in the download dialogue as opposed to the list of finished downloads. It seems when I double-click or right-click open a file in the list of finished downloads, firefox will always open that file with the application that's associated with the mimetype "file", regardless of the actual mimetype or extension of the file. Why is that? It works perfectly after using the above script if you just once choose "/usr/bin/xdg-open" when first prompted for an association for the mimetype "file". But still, that's some weird firefox behavior.

---

### Post by Zorael on 2009-12-13
There's [an effort](http://en.opensuse.org/KDE/FirefoxIntegration) going on to increase KDE integration in Firefox, but packages with the fruits of that effort aren't part of the Karmic release. See that link for a table of what has been accomplished so far.

If you still want to try it out, you can get unofficial packages from [Felix Geyer](https://launchpad.net/~debfx)'s PPA ([ppa:debfx/firefox-kde](https://launchpad.net/~debfx/+archive/firefox-kde)).

```
*[...]*
Mimetype handling	 done (11.2)	 KDE file associations are read and used
*[...]*
```

---

### Post by lodp on 2009-12-13
Sweet! Thanks for posting man, I'm sure going to try this.

Is there a push to get this into the next Kubuntu release?

---

### Post by Zorael on 2009-12-13
```
[19:45] <zorael> Will kmozillahelper and a KDE-friendly Firefox be in Lucid main? I don't see the package currently on packages.ubuntu.com.
[19:54] <JontheEchidna> zorael: it's being worked on, yes
```

---

### Post by lodp on 2009-12-13
I just installed it and I'm amazed. No more browsing through the endless list in /usr/bin when opening a file. Brilliant stuff, hope to see it in the next release too. Thanks again!

---

### Post by Lord Blackadder on 2009-12-14
Thanks for posting the link to that PPA.  I had just switched back to Kubuntu from openSUSE because I was sick of openSUSE's repositories always screwing up... then I installed openSUSE 11.2 on another machine and saw how great their Firefox implementation was and was like "D'oh!"

Someone posted a link to the KGTK PPA which was a life-saver, at least giving me the KDE file picker back (and without having to compile it myself since that doesn't always like to work), but having the buttons in the wrong order always annoyed me, since I'm used to OK being first in both KDE and Windows.

Hopefully they'll be able to make this standard in Kubuntu 10.04 :)

---

