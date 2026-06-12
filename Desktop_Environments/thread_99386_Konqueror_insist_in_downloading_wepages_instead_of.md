---
title: "Konqueror insist in downloading wepages instead of serving them"
date: 2005-12-05
forum: Desktop Environments
---

### Post by michux on 2005-12-05
When I use Konqueror it works fine, but when I click on some link from an outside app, like amaroK, for example (in the Wikipedia tab), Konqueror launches itself and starts downloading the requested webpage to /var/tmp/cache...something, and then proudly opens it. Of course this behavior is completely nonsense and I'd like to change it to "show me the webpage, my friend". When do I set it? No idea whatsoever...

---

### Post by stimpack on 2005-12-05
I had a similer problem where it kept asking if I wanted to download or open with kate. Somehow the html association had screwed up.

If its the same problem then:

In Konq: configure->file associations->text/html bump konq to the top.

---

### Post by michux on 2005-12-05
[QUOTE=stimpack]I had a similer problem where it kept asking if I wanted to download or open with kate. Somehow the html association had screwed up.

If its the same problem then:

In Konq: configure->file associations->text/html bump konq to the top.[/QUOTE]

No, it's not it. I have Konqueror at the top and KHTML at the top in "embedded".

---

### Post by Ptero-4 on 2005-12-05
AFAIK, it's normal. Konq is made of several pieces called IO Slaves. When one ioslave needs to send processed information to another (for example the web browsing ioslave to the amarok library ioslave) it puts the data in /var/tmp/cache so that whichever ioslave needs it can access that data (/var/tmp/cache is a temporary central cache that all kde ioslaves can access) from there. Every KDE app access that cache but sometimes the retrieval is so fast that you don't even see the download dialog. But other times, especially when downloading contents from the web, the dialog may appear and even stay there for some time.

---

### Post by michux on 2005-12-05
[QUOTE=Ptero-4]AFAIK, it's normal. Konq is made of several pieces called IO Slaves. When one ioslave needs to send processed information to another (for example the web browsing ioslave to the amarok library ioslave) it puts the data in /var/tmp/cache so that whichever ioslave needs it can access that data (/var/tmp/cache is a temporary central cache that all kde ioslaves can access) from there. Every KDE app access that cache but sometimes the retrieval is so fast that you don't even see the download dialog. But other times, especially when downloading contents from the web, the dialog may appear and even stay there for some time.[/QUOTE]

Well all nice but you missed my problem. The webpages are cached and opened LOCALLY. This means when I click any link on the downloaded page, 404 error shows up because it cannot find the page it links to. 

I just need Konqueror to open the freaking webpage when I click on any link in my system (like from amarok or thunderbird) instead of downloading the page and opining it locally.

I cant believe that this is the default behavior for KDE...

---

### Post by michux on 2005-12-06
[QUOTE=michux]Well all nice but you missed my problem. The webpages are cached and opened LOCALLY. This means when I click any link on the downloaded page, 404 error shows up because it cannot find the page it links to. 

I just need Konqueror to open the freaking webpage when I click on any link in my system (like from amarok or thunderbird) instead of downloading the page and opining it locally.

I cant believe that this is the default behavior for KDE...[/QUOTE]

So... anybody?

---

### Post by enkryptor on 2007-03-17
first check your "Settings" -> "KDE Components" -> "Component chooser" -> "Web Browser"
select "in the following browser" instead of "in an application based on the contents" and enter "konqueror" in the text field. restart KDE

if the problem persist, open "KDE Components" -> "file association" and then check "text/html" option. in "Application preference order" select "Konqueror", click "Edit" and enter "konqueror %u" in the "command" field. "%u" means url, and "%f" means a file (that opened from the cache)

sorry for bad English, i'm a Russian in fact %)

---

