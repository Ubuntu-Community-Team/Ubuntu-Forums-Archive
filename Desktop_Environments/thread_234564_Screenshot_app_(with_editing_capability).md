---
title: "Screenshot app (with editing capability)"
date: 2006-08-11
forum: Desktop Environments
---

### Post by cjraven on 2006-08-11
I'm an ubuntu convert, the past 24 hours has been an utterly amazing experience. No other possible way to put it.

What I'm honestly missing however, is a SnagIt equivalent, meaning; a screenshot app which can do some really basic editing (placing an arrow on a screenie, or putting a circle around something of interest, or putting some text in a textbox on top of the image).

That is perhaps the *one* and *only* Windows piece of software that I have not seen an equivalent for - thus far at least. There appear to be numerous kde and gnome screenshot apps - I've installed one of each - BUT both do a screenie, and then you have to perform some kind of black magic on the image with the GIMP. I just can NOT handle the GIMP...sorry...if that tags me a helpless or lazy newbie, so be it...I'm neither, and although willing (and eager) to learn - and help others - GIMP is "too much and way too soon". So that's why I'm looking for an app of the kind I described above.

Suggestions would be most gratefully received.

Regards,
-Colin

---

### Post by ardchoille on 2006-08-11
> **cjraven said:**
> I'm an ubuntu convert, the past 24 hours has been an utterly amazing experience. No other possible way to put it.

What I'm honestly missing however, is a SnagIt equivalent, meaning; a screenshot app which can do some really basic editing (placing an arrow on a screenie, or putting a circle around something of interest, or putting some text in a textbox on top of the image).

That is perhaps the *one* and *only* Windows piece of software that I have not seen an equivalent for - thus far at least. There appear to be numerous kde and gnome screenshot apps - I've installed one of each - BUT both do a screenie, and then you have to perform some kind of black magic on the image with the GIMP. I just can NOT handle the GIMP...sorry...if that tags me a helpless or lazy newbie, so be it...I'm neither, and although willing (and eager) to learn - and help others - GIMP is "too much and way too soon". So that's why I'm looking for an app of the kind I described above.

Suggestions would be most gratefully received.

Regards,
-Colin

I wrote a bash script for taking a screenshot and I feel that it is much better than the default screenshot app in gnome:

[http://ubuntuforums.org/showthread.php?t=223758](http://ubuntuforums.org/showthread.php?t=223758)

You could always add a line to the bottom of the script once you found a nice app you like to use to edit the screenshot:

```

appname $mypath"/"$myfilename

```

and that would open the screenshot in appname, where appname is the app you prefer.

Bash scripts are quite powerful :)

---

### Post by loserboy on 2006-08-11
well in add/remove theres something called gnu paint, haven't used it though, i think its suppose to be like mspaint.

Edit: i just tested it... yea it doesn't get any easier than that, although i couldnt find a screencap and editor in one

---

