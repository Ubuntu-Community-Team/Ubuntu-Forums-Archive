---
title: "Konqueror"
date: 2006-03-14
forum: Desktop Environments
---

### Post by eriefisher on 2006-03-14
Why is the "K" browser not supported by Gmail. I use Thunderbird to retrieve messages from Gmail and no problem. However today I went to Gmail through Konqueror to change some account settings and could only view as plain html. I could not make any changes to my account. What other sites don't support it and why? I hope this is changed in the future.

eriefisher

---

### Post by skymt on 2006-03-14
Obviously, Gmail sniffs the browser you're using and compares it to a list. If it's not on the list, you're stuck with the plain interface. It makes sense, really. Gmail uses some of the fanciest Javascript on the web, so they want to make sure it doesn't malfunction because you're using a browser that doesn't run it properly.

You could probably send them an email asking them to add Konqueror to the list. It probably works, since it uses the same engine as Safari. Or you can change user agent strings, to make it look like you're using a supported browser. I don't know how to do that, since I don't have Konqueror installed, but it shouldn't be hard to find.

---

### Post by Jucato on 2006-03-14
How to change user agent strings in Konqueror for Gmail:
1. Go to Settings > Configure Konqueror > Browser Identification
2. In the Site Specific Identification part, click on New
3. enter the site name (I entered "gmail.com")
4. In the Use the following identification drop-down list, choose something that Gmail supports (I used Mozilla 1.7.3)

Here's some thoughts of a KDE dev about Gmail and Konqueror:
[http://www.kdedevelopers.org/node/1195]("http://www.kdedevelopers.org/node/1195")

I think that the problem lies on both sides: Gmail not actually wanting to support Konqueror and Konqueror having problems with Javascripts. I wonder if Konqueror is the only non-standard browser having the same problems. what about Dillo?

---

### Post by firephoto on 2006-03-18
It might work a little better if you identify:

google.com as safari
and
mail.google.com as firefox

Also some of the other google services ignore the user agent and do a javascript check of somesort (googlepages). The khtml in konqueror (3.5.1) is pretty close to the what apple has right now so there's not much point in it being blacklisted but I guess google is a big company so you have to jump though the hoops. Kopete and gtalk is in the same boat.

I'm new to kubuntu so I'm not all up to speed on the kde layout with breezy but as long as you're using 3.5.1 konqueror (3.5.0 was buggy) it should do pretty good on most sites.

---

