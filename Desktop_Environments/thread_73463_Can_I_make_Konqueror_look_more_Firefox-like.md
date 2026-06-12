---
title: "Can I make Konqueror look more Firefox-like?"
date: 2005-10-09
forum: Desktop Environments
---

### Post by Karaoke on 2005-10-09
Having installed Kubuntu Hoary 5.04, I found that browsing the web with Konqueror is less convenient than with Firefox:

(1) Is there any way to close tabs with one click? If I middle-click a tab, Konqueror assumes I want to insert the currently saved text (the copy-and-paste text) into the address bar of that bar - most of the time, this gives a "Bad URL" reply.

(2) How do I add new search engines to the search field? Using the pre-defined menu only seems to allow to choose ONE engine. Using the short-cuts in the address field (like "gg: search term" or whatever) is powerful indeed -  but being very forgetful, I prefer having some icons instead. Furthermore: Can you change the size of this search field (like in Firefox by editing userChrome.css)?

(3) Why does Konqueror sort of forget what I have looked for in this search field? It's just displayed on double-clicking regardless of the options I've chosen before ("automatically complete" or similar).

(4) Is it possible to change the looks/the behaviour of the bookmarks? I find the bookmarks are to high - my folders from Firefox didn't fit completely into Konqueror. Furthermore: Can you permanently open a folder (and display it in the bookmarks column) instead of just opening it like a menu (ie have a behaviour like in IE, Firefox, Mozilla...)?

(5) A GOOD pop-up blocker (I found the setting "intelligent java behaviour" (or similar...) is firstly not very well placed within the menu and secondly does not do its job as well as other pop-up blockers (including the blocker in IE, I have to say...) and something excellent like Adblock-Plus is not to be expected before KDE 3.5, is it?

Unfortunately, installing Firefox with Synaptic is not a solution to this - it looks ugly, it's much slower to start, and I think Konqueror is just much better integrated into KDE. Do you have any ideas how to deal with the above problems?

Many thanks,
Karaoke

---

### Post by localzuk on 2005-10-09
There are a variety of themes available for firefox from [http://addons.mozilla.org](http://addons.mozilla.org).

IMHO you will have a better browsing experience with firefox as it is more popular and therefore some websites now cater for it - but not khtml...

---

### Post by manicka on 2005-10-09
Installing gtk2-engines-gtk-qt should improve the look of Firefox.

---

### Post by Segovia on 2005-10-09
[QUOTE=manicka]Installing gtk2-engines-gtk-qt should improve the look of Firefox.[/QUOTE]
I noticed just yesterday that this is installed by default in Breezy.  :-)

---

### Post by ltmon on 2005-10-09
The ones I can answer off the top of my head:

(2) This is forthcoming in KDE 3.5.  You can install that right now if you want, or just wait a month or so for Kubntu 5.10.  Also, the new version has an "adblock" filter as well which works pretty much the same as the firefox extension.

(4) Hit "F9" to display a sidebar.  There should be a bookmarks tab there (as well as history and some other stuff).

L.

---

### Post by One Quick Question on 2005-10-10
1. Add the following text to your ~/.kde/share/config/konquerorrc and clicking on a tab with the middle mouse button will close it.
 
[FMSettings]
 MouseMiddleClickClosesTab=true

And more cool info here: [http://wiki.kde.org/tiki-index.php?page=Secret+Config+Settings](http://wiki.kde.org/tiki-index.php?page=Secret+Config+Settings)

3.  Right-click on an one-line text field thing and you can change the text completion behavior ... if that's what you were asking.

---

### Post by Segovia on 2005-10-10
[QUOTE=ltmon]or just wait a month or so for Kubntu 5.10[/QUOTE]
Have I missed something?  I know Ubuntu is scheduled for release on the 13th (3 days from now).  Will Kubuntu not be released on the same day as Ubuntu?

---

### Post by Karaoke on 2005-10-10
Thanks to all of you for your advice! I think I will switch to Firefox for the moment - it is much better using gtk2-engines-gtk-qt now. But as soon as KDE 3.5 is released, I will give Konqueror another try - I wonder why such essential things like an ad-blocker or better integration of various search engines have not yet been included in a programme that might be very powerful as a file manager (or something else), but is most commonly used as a web browser.

---

### Post by ltmon on 2005-10-10
[QUOTE=Segovia]Have I missed something?  I know Ubuntu is scheduled for release on the 13th (3 days from now).  Will Kubuntu not be released on the same day as Ubuntu?[/QUOTE]

I think I probably meant "wait a month or so for KDE 3.5 to be released properly."  :)

L.

---

### Post by Segovia on 2005-10-10
[QUOTE=ltmon]I think I probably meant "wait a month or so for KDE 3.5 to be released properly."  :)

L.[/QUOTE]
Ah, OK.  :)  Well after reading your message I went to the Kubuntu site and forums, trying to find out if Kubuntu Breezy had been delayed!  You sent me on a wild goose chase for nothing!  ;)

---

### Post by Brando569 on 2005-10-11
i think kde 3.5 should be out by the end of this month, im probly gonna download breezy as soon as its final, then wait till kde 3.5 is out, buy the ubuntu dvd (if there is such a thing, i heard there would be) and then add 3.5 to it so i dont have to keep downloading it everytime i wanna do an install

---

