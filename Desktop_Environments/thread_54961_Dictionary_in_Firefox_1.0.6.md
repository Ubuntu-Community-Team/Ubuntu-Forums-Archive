---
title: "Dictionary in Firefox 1.0.6?"
date: 2005-08-06
forum: Desktop Environments
---

### Post by erik-the-red on 2005-08-06
I installed Firefox 1.0.6 from source and now the dict feature in the address bar that I loved so much no longer goes to dictionary.com

How can I reconfigure this?

---

### Post by bored2k on 2005-08-06
[QUOTE=erik-the-red]I installed Firefox 1.0.6 from source and now the dict feature in the address bar that I loved so much no longer goes to dictionary.com

How can I reconfigure this?[/QUOTE]
 Go to $HOME/.mozilla/firefox/nameofyourprofile.default/search and delete the plugin (the .src and the .png).

Then go to [http://mycroft.mozdev.org/download.html?name=dictionary.com&submitform=Find+search+plugins](http://mycroft.mozdev.org/download.html?name=dictionary.com&submitform=Find+search+plugins) and add the one you want.

---

### Post by erik-the-red on 2005-08-13
[QUOTE=bored2k]Go to $HOME/.mozilla/firefox/nameofyourprofile.default/search and delete the plugin (the .src and the .png).

Then go to [http://mycroft.mozdev.org/download.html?name=dictionary.com&submitform=Find+search+plugins](http://mycroft.mozdev.org/download.html?name=dictionary.com&submitform=Find+search+plugins) and add the one you want.[/QUOTE]
 I did that, but the only plugin in the search folder was the google.src.

I did install a plugin for the "Google Toolbar" that involves dictionary.com, but I remember that one of the cool things about Firefox was that you could type "dict (word)" in the address bar, and it would lookup the word for you.

---

### Post by SGC on 2005-08-13
**The Dictionary.com Quick search comes with firefox, but if for some reason it does not works for you then, in firefox go to:**
Bookmarks -> Manage Bookmarks... -> New Bookmark...

**And add the following information:**
Name: Dictionary.com Quicksearch
location: [http://dictionary.reference.com/search?q=%s](http://dictionary.reference.com/search?q=%s)
keyword: dict

---

### Post by erik-the-red on 2005-08-15
[QUOTE=SGC]**The Dictionary.com Quick search comes with firefox, but if for some reason it does not works for you then, in firefox go to:**
Bookmarks -> Manage Bookmarks... -> New Bookmark...

**And add the following information:**
Name: Dictionary.com Quicksearch
location: [http://dictionary.reference.com/search?q=%s](http://dictionary.reference.com/search?q=%s)
keyword: dict[/QUOTE]
 Thanks. That worked!

---

