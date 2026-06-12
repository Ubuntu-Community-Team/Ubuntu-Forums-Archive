---
title: "Firefox can't install extensions."
date: 2006-06-10
forum: Desktop Environments
---

### Post by Belathor on 2006-06-10
Hi,

I'm having difficulty installing firefox extensions on my laptop. No matter which extension I try, I keep getting the same error:

> Firefox could not install the file at

http://releases.mozilla.org/pub/mozilla.org/extensions/<extension name>/<extension file name>.xpi

because: Unexpected installation error
Review the Javascript console log for more details

I've gotten this error with:
[LIST]
[*]Google notebook
[*]adblock plus
[*]geckotip
[*]forecastfox enhanced
[/LIST]

Is there any way I can get this resolved?

Thanks for the help!

EDIT: add ScrapBook to the list as well.

---

### Post by FredB on 2006-06-10
Can you copy / paste the content of javascript console in order to help us ? Thanks.

---

### Post by Belathor on 2006-06-10
I will once I can find it. I "unhid it", but I still don't know where it is.

EDIT: I found it...

EDIT: I've been trying to post the content of the java script console, but Firefox keeps freezing whenever I try to paste the 3000 lines of code in there. :(

---

### Post by FredB on 2006-06-10
[QUOTE=Belathor]I will once I can find it. I "unhid it", but I still don't know where it is.

EDIT: I found it...

EDIT: I've been trying to post the content of the java script console, but Firefox keeps freezing whenever I try to paste the 3000 lines of code in there. :([/QUOTE]

Copy it in Gedit, and then, cut the error lines to paste them there.

Thanks

---

### Post by Belathor on 2006-06-10
```
     // An item entry is valid only if it is not disabled, not about to 
      // be disabled, and not about to be uninstalled.
      var installLocation = this.getInstallLocation(item.id);
     ** if (installLocation.name in StartupCache.entries &&**
          item.id in StartupCache.entries[installLocation.name] &&
          StartupCache.entries[installLocation.name][item.id]) {
        var op = StartupCache.entries[installLocation.name][item.id].op;
        if (op == OP_NEEDS_INSTALL || op == OP_NEEDS_UPGRADE || 
            op == OP_NEEDS_UNINSTALL || op == OP_NEEDS_DISABLE)
          continue;
      }
      // Suppress items that have been disabled by the user or the app.
      if (ds.getItemProperty(item.id, "disabled") != "true")
        activeItems.push({ id: item.id, location: installLocation });
```

The bold line is the line javaconsole highlighted as the problem.

---

### Post by Belathor on 2006-06-10
I also tried uninstalling and reinstalling. It didn't work, I still get the same error.

---

### Post by Belathor on 2006-06-10
anyone have any ideas?

Thanks!

---

### Post by TOPPEL on 2006-06-10
for 3000 lines of text you could use pastebin.com to and have the url linked here on the forum.  you may or may not have known that however please give me a hard time about that.   or who knows -- maybe pastebin.com doesn't work with 3000 lines of text.

---

### Post by Belathor on 2006-07-11
I think that little chunck that I posted is all that is wrong. But thanks for the pastebin tip! 

Still looking for ideas on how I'm supposed to get extensions? I've been using Opera 9 and like it, but I miss my Scrapbook!

---

### Post by Aulden on 2006-09-23
Hey I've got the same problem I think... But... I opened firefox with sudo and installed an extension no problems... but when I open it normally it doesn't show up. With sudo the extension works perfect. 

Anyone figure this out?

thanks

---

### Post by lekikui on 2006-09-23
Nevermind, cleared up when I restarted Firefox.

---

### Post by Gnub_Daemon on 2008-04-13
I had this same problem with a fresh install of Hardy Heron Beta.  I had to delete my .Mozilla file in my user folder.  Seems to be a conflict between Firefox2 and 3...

---

### Post by Dark Laith on 2008-04-29
> **Gnub_Daemon said:**
> I had this same problem with a fresh install of Hardy Heron Beta.  I had to delete my .Mozilla file in my user folder.  Seems to be a conflict between Firefox2 and 3...

Thank you for that comment, just to confirm i had the same problem and this fixed it :)

---

