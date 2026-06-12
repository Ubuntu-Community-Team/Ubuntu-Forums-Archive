---
title: "Openoffice hyperlinks always open in Konq and freeze openoffice"
date: 2006-02-09
forum: Desktop Environments
---

### Post by jetpeach on 2006-02-09
When I click a hyperlink in Openoffice, the following happens: Konqueror opens the link, Openoffice freezes UNTIL I close Konqeror.  The problems is I want to use Firefox anyway (and I don't like the freezing of OO either...).

So I tried going into Kcontrol->Kde comp->file associations and changing html files so Firefox is the default.  Doesn't change anything though.
So digging around more, I also found kcontrol->"component chooser"->web browser and in there it says, "firefox %u"
So everything looks like it's set to firefox, why the hell does openoffice open konq??  Driving me nuts...

THANKS FOR ANY HELP!!! jet

Specs: 32bit Kubuntu w/ KDE 3.51 (previously a gnome installation upgraded to Kubuntu) 
Openoffice 2.01

---

### Post by treris on 2006-02-10
Yeah same problem here, it's been happening for as long as I remember and nowadays I've gotten used to just copying and pasting the url to FF

---

### Post by jetpeach on 2006-02-10
Maybe I'll post this over at the other Kubuntu forums as well, see if anybody there has any ideas...

---

### Post by Jucato on 2006-02-10
Ok, I think this is a an OOo bug rather than a KDE bug. Here are the things I tested that lead me to that conclusion:

1. Konqueror as default browser: OOo opens link in Konqueror and freezes until the opened link is closed, then OOo returns to normal.
2. Konqueror as default browser: KWord opens link in Konqueror, does not freeze, operates independently of Konqueror
3. Firefox as default browser: OOo opens link in Konqueror and freezes until opened link is closed, then OOo returns to normal.
4. Firefox as default browser: KWord opens link in Firefox, does not freeze, operates independently of Konqueror.

So as you can see, KWord operated in the way it was expected to, while OOo had a few quirks. Perhaps OOo opens the browser like a modal dialog box, one that you must dismiss first before it returns control to the calling app. I'm not really sure, but I really think that this is a problem with OpenOffice rather than KDE.

Specs: KDE 3.5.1, KOffice 1.5 beta, OpenOffice 2 (from the repositories)

---

### Post by Ramses on 2006-02-11
I think OO looks default browser from /etc/alternatives. So you can change that with:
```
sudo cp /etc/alternatives/x-www-browser /etc/alternatives/x-www-browser.bak
```
```
sudo ln -sf /usr/bin/mozilla-firefox /etc/alternatives/x-www-browser 
```

It still seems that OO freezes with firefox too.

---

