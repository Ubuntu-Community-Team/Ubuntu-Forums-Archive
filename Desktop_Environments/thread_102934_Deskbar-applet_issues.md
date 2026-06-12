---
title: "Deskbar-applet issues"
date: 2005-12-13
forum: Desktop Environments
---

### Post by DaMasta on 2005-12-13
My deskbar-applet use to have the option to search google for whatever I was typing in. For some reason, it has ceased providing me with that option. I've dpkg-reconfigured and removed and installed. Any ideas?:confused: Screeny attached.

---

### Post by 23meg on 2005-12-13
Maybe you removed google from your list of search engines (the search bar ones) in firefox?

---

### Post by DaMasta on 2005-12-13
Well, I recently changed my browser preference to epiphany within preferred applications. I just checked firefox and I can still search google in the search bar. I tried changing epiphany back to firefox, removed and then added the applet but still no go.

---

### Post by 23meg on 2005-12-13
Did you upgrade to Firefox 1.5? Did you try a dpkg-reconfigure after changing the default browser?

---

### Post by DaMasta on 2005-12-13
No, haven't upgraded to 1.5. Yeah, I've reconfigured a couple of times.

---

### Post by 23meg on 2005-12-13
Try adding another engine and see if that's cached. Then remove the google search item (.src file in your profile folder I think) and reinstall it and see if that helps. Also try reinstalling deskbar altogether.

---

### Post by DaMasta on 2005-12-13
Ok, I added imdb to firefox. Is that where you're talking about adding the search engine? Not sure how to add one to deskbar. Nothing different in deskbar. And where should I remove the google engine from?

---

### Post by 23meg on 2005-12-13
Yes, I meant adding to the Firefox search bar. Does deskbar offer an IMDB search now?

The search engine items should be in /usr/lib/mozilla-firefox/searchplugins . If not, check the "search" folder in your profile folder which is in ~/.mozilla/firefox .

---

### Post by DaMasta on 2005-12-13
Yeah, imdb showed in my local firefox searchplugins directory. I reinstalled firefox, moved my .mozilla temporarily it'd create a new one and still no go. I'm not going to worry about it right now since I really only use the deskbar to launch apps. Hopefully, a new release will resolve the issue. Thanks for your help 23meg.:KS

---

### Post by 23meg on 2005-12-13
You're welcome. If you're sure this happened only after changing to Epiphany, you should submit it as a bug report.

---

### Post by jannol on 2005-12-16
I have never coded python before but I did attempt to create a temporary 'solution' since I did not get Google Live to work.

I basically copied web_address.py and modified it in a quick and ugly way.

The methods I use is
[b]g for Google
i for Google Image
w for Wikipedia
imdb for IMDB movie database
[/b]

you can get the handlers with >
```
wget -nc shr.jannol.com/ubuntu/handlers.tar.gz ; tar xvf handlers.tar.gz -C ~/.gnome2/deskbar-applet/handlers/
```

and the art >
```

wget -nc shr.jannol.com/ubuntu/icons.tar.gz ; sudo tar xvf icons.tar.gz -C /usr/share/deskbar-applet/art/
```

Restart deskbar-applet and then go to deskbar prefs. and enable them.

if you builded deskbar from cvs the paths might differ, then you can download the files, untar and put them where they belongs.

[handlers](shr.jannol.com/ubuntu/handlers.tar.gz)

[art](shr.jannol.com/ubuntu/icons.tar.gz)

I also made a quick demo 5.4 mb
Get it here > [deskbar google demo](shr.jannol.com/ubuntu/deskbar.mpg)

I hope the handlers work ok but please let me know if they fail... or not :rolleyes:

<edit>
Added imdb
</edit>

---

### Post by songochain on 2006-03-08
It doesnt work for me :( Also deskbar doesnt work when i try to open a web page, what's the problem?
PD: using deskbar coming from gnome 2.13.9 (dapper)

---

### Post by jannol on 2006-03-08
Alot has updated in dapper so it might be a bit broken in dapper for now, I haven't tried to make it work in dapper very much and as for my quick and dirty hack, it was ment for breezy and is probably outdated by now, deskbar supports your quick search bookmarks from your browser.

Maybe building deskbar from cvs could work...

---

