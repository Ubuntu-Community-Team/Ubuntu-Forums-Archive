---
title: "&quot;Find all my posts&quot; returns stale results"
date: 2013-03-13
forum: Forum Feedback &amp; Help
---

### Post by SeijiSensei on 2013-03-13
Even after clearing my browser cache, if I click on "find all my posts" in the Quick Links drop-down, I get results that are marked with "Search took 0.04 seconds; generated 56 minute(s) ago."  I cannot seem to force vB to include the posts I made just now.

i wonder if this is related to another anomaly I noticed last night where some posts can have zero views but multiple replies.  It's as if there's some delay in posting to the database.

While I have your attention, is there any chance that the Quick Links menu item could appear at the top of every page? It's unavailable on pages like search results which means returning first to the main page before being able to go to "mark forums read" or "show all my posts".

---

### Post by coffeecat on 2013-03-13
> **SeijiSensei said:**
> Even after clearing my browser cache, if I click on "find all my posts" in the Quick Links drop-down, I get results that are marked with "Search took 0.04 seconds; generated 56 minute(s) ago."  I cannot seem to force vB to include the posts I made just now.

I'm not seeing this. "Find all my posts" in Quick Links is giving me recent results reliably. However, this may be an issue that is affecting some accounts and not others. It would be helpful if other members would say if they are seeing the same problem as SeijiSensei.

> **SeijiSensei said:**
> i wonder if this is related to another anomaly I noticed last night where some posts can have zero views but multiple replies.  It's as if there's some delay in posting to the database.

We have noticed some oddities with regard to searches, which elude solution at the moment. This is being investigated.

> **SeijiSensei said:**
> While I have your attention, is there any chance that the Quick Links menu item could appear at the top of every page? It's unavailable on pages like search results which means returning first to the main page before being able to go to "mark forums read" or "show all my posts".

The main problem is that "Forum" and "Latest Activity" (above where quick links appears) are two tabs, and any search causes the "Latest Activity" tab to be made live - which is what you are seeing with advanced search. The search items in quick links - find all my threads, find all my posts, unanswered posts and new posts - all cause the live tab to switch from Forum to Latest Activity too. The only solution I can see at the moment is to have a duplicate set of quick links under the "Latest Activity" tab, which would be clumsy. The layout of the navigation manager is not fixed in stone and it's quite likely that we'll be adding or changing things. We'll keep this in mind.

---

### Post by SeijiSensei on 2013-03-13
Thanks!  While I can't say I'm a big fan of the current layout, which I see as having much too much inefficient empty space, I'm trying to limit my comments to functionality.  I suspect the layout issues have as much to do with changes to vBulletin as with anything you folks have done.

---

### Post by matt_symes on 2013-03-13
> i'm not seeing this. "Find all my posts" in Quick Links is giving me  recent results reliably. However, this may be an issue that is affecting  some accounts and not others. It would be helpful if other members  would say if they are seeing the same problem as SeijiSensei.

Neither am i seeing this.

---

### Post by coldcritter64 on 2013-03-13
Did a search, result 0.03 seconds last post 9 hrs ago. Posted in the "Ban the user above you" cafe thread. Repeated the search and last post was 10 hours ago. My last posting is not currently being found. Confirmed here. Cleared my browsers cache leaving cookies etc for maintaining a login, repeated the search, same result.

Edit: if it matters, I'm using Dolphin Browser, the "jetpack" version, on an android tablet. Edit2: I do force the site to supply the desktop layout, does not seem to matter anywhere else though.

---

### Post by SeijiSensei on 2013-03-13
Just clicked "find all my posts now" and got back " Search: Search took 0.04 seconds; generated *27 minute(s) ago*. ".

Here are some symptoms.  First, if i run "find all my posts" again after having run it a while ago, the URL shows the same searchid as before.  Even clearing my browser cache does not change that.  I'm using Firefox, and I allow cookies. I'm also connecting directly rather than though a proxy like Squid, so there isn't any upstream caching either.  

When I build sites with PHP, I explicitly forbid caching with header() calls like these:

```

# force page refresh
header("Pragma: no-cache");
header("Cache-Control: no-cache; must-revalidate");
header("Expires: -1");

```

that run ahead of every page I send to the user's browser.  That might be extreme, but it does avoid some caching problems I've experienced running scripted websites.  On text-heavy sites like this one, I don't see any reason to deny caching.  Sure peoples' browsers then won't cache graphic objects like the buttons below, but that's a pretty small price to pay.

---

### Post by sandyd on 2013-03-14
Problem has been located - working on it

---

### Post by SeijiSensei on 2013-05-13
I just encountered this issue again and tried a different solution.  I ran the built-in search for unanswered posts to force the server to update my most recent search ID.  Then I again ran the search for all my posts, and a newly-entered post now appeared.  Apparently the server caches the search ID for a while and refuses to run another search with the same parameters until the cached entry expires.  It does seem that the default cache length is a bit conservative, though.  In my first post above, I reported getting back the same results as long as 56 minutes later.  I understand the need to protect against denial-of-service attacks against the search engine, but perhaps a cache length closer to 10-15 minutes might make more sense?

And while I'm at it, **thank you so much for adding the Quick Links menu to search results**.  I use it all the time!

---

