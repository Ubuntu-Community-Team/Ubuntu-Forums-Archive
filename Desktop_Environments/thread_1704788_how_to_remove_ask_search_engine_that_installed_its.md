---
title: "how to remove ask search engine that installed itself as default"
date: 2011-03-11
forum: Desktop Environments
---

### Post by mimmo.marozzi on 2011-03-11
I found that "ask search engine" installed as default web search engine instead of google in firefox. Now it's impossible to go back to google search engine as "ask" always remains as default search and no other search engins are shown in the firefox list.
Any idea about how to get rid of "ask"? I managed to install another "unofficial google" search plugin but if i click on restore default search engine "ask" will be restored.
Thanks in advance.

---

### Post by Krytarik on 2011-03-11
I would search for packages related to "ask" in Synaptic.

The system-wide default search engines are stored in "/usr/lib/firefox-3.6.15/searchplugins/en-US" (in my case).

These are mine, these are also the default ones:

amazondotcom.xml
answers.xml
creativecommons.xml
eBay.xml
google.xml
wikipedia.xml
yahoo.xml

You can restore them by re-installing Firefox, or by extracting them from here:
[http://packages.ubuntu.com/maverick-updates/firefox](http://packages.ubuntu.com/maverick-updates/firefox)

---

### Post by Frogs Hair on 2011-03-11
Firefox > Edit > Preferences > General Tab . Where you see home page select restore to default. To restore the search engine list use the arrow in the right search box and drop down to manage search engines and restore defaults.

---

### Post by Davaross on 2011-03-11
I personally had this issue last week (albeit in windows 7) and found I had to change the default search keyword in the firefox about:config page. 
Hope that helps!

---

### Post by Deeday on 2011-03-11
This is **RIDICULOUS**: if I highlight a word and right click on it, now I get "Search Ask.com for <word>", instead of "Search Google" as before, but I've never changed any search engine option!!!

This must have happened within last week. I've just updated to Firefox 3.6.15 (Maverick x64).

My about:config **DOES NOT RETURN ANYTHING** if I filter for ask.com

keyword.URL contains ```
http://www.google.co.uk/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=
```

[SIZE="3"]**WTF IS GOING ON HERE?**[/SIZE] Please somebody help. I don't want Ask.com. I want to set whatever search engine I wish!!

---

### Post by MartyBuntu on 2011-03-12
> **Deeday said:**
> This is **RIDICULOUS**: if I highlight a word and right click on it, now I get "Search Ask.com for <word>", instead of "Search Google" as before, but I've never changed any search engine option!!!

This must have happened within last week. I've just updated to Firefox 3.6.15 (Maverick x64).

My about:config **DOES NOT RETURN ANYTHING** if I filter for ask.com

keyword.URL contains ```
http://www.google.co.uk/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=
```

[SIZE="3"]**WTF IS GOING ON HERE?**[/SIZE] Please somebody help. I don't want Ask.com. I want to set whatever search engine I wish!!

Firefox...

Top-Right drop down box for search engines...

Change it to Google or whatever you want...

Next time you highlight and right-click, it should offer the chance to search with whatever search engine is currently in the default spot.

---

### Post by Frogs Hair on 2011-03-12
More Information
This may be due  to the isp switching you to its default search provider . I don't know if it was intensional or not. [http://forums.mozillazine.org/viewto...&sd=a&start=15](http://forums.mozillazine.org/viewto...&sd=a&start=15)
[http://slashdot.org/article.pl?sid=08/02/26/1741253](http://slashdot.org/article.pl?sid=08/02/26/1741253)

---

### Post by gmargo on 2011-03-12
Ubuntu has "helped" you by including ask.com in the **xul-ext-ubufox** package.  You can remove it as described above, or you can remove the xul-ext-ubufox package.

---

### Post by Deeday on 2011-03-12
> **MartyBuntu said:**
> Firefox...

Top-Right drop down box for search engines...

Change it to Google or whatever you want...

[SIZE="3"]**Thanks!**[/SIZE] ):P I've always removed the search bar from my Firefox, as I prefer to use Quick Searches via keywords in the address bar, and  that's why I didn't spot it. I'm surprised that those settings are not reflected in the about:config and also that Ubuntu rather sneakingly _replaced_ the existing engine with Ask.com, instead of just adding it (if they really felt the urge to promote Ask).

---

### Post by Krytarik on 2011-03-12
> **gmargo said:**
> Ubuntu has "helped" you by including ask.com in the **xul-ext-ubufox** package.  You can remove it as described above, or you can remove the xul-ext-ubufox package.
Ah, I always disable those extension right after installation, that's why I didn't notice a change. Maybe I should remove it at all, but I want to take a look into its other "functions" before. Do you know, what it also includes?

---

### Post by texpat on 2011-03-12
Here's what I did:

Located "/usr/lib/firefox-3.6.15/searchplugins/en-US/" and copied the xml files (see Krytarik's post above) to "/usr/share/xul-ext/ubufox/searchplugins/"

If you don't like ask.com I suppose you could remove the ask.xml file from that directory.

Re-started Firefox and they appeared on the list.

---

### Post by XsheepX on 2011-03-12
Have you tried uninstalling Firefox and reinstalling it?

---

### Post by Krytarik on 2011-03-17
I should mention that the OP of another thread regarding those issue found a bug report earlier, it seems to get fixed in the near future, it also includes a temporary workaround:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768](https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768)

---

