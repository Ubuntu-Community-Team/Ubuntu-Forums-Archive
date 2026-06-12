---
title: "Conky Rss"
date: 2009-05-18
forum: General Help
---

### Post by merlin_ie on 2009-05-18
Hey everyone. I'm trying to set up (as title says) an rss feed in conky. I've found a code, but I'm not sure how to make it work (still getting used to conky/Ubuntu) Here is the code
> ${rss [http://website.com/feeds](http://website.com/feeds) 10 feed_title}
${rss [http://website.com/feeds](http://website.com/feeds) 10 item_title 1}
${rss [http://website.com/feeds](http://website.com/feeds) 10 item_title 2}
${rss [http://website.com/feeds](http://website.com/feeds) 10 item_title 3}

Does anyone know if this would work or is there a better/easier one (idiot proof springs to mind lol)

I would like to get the feed for the site below and if possible, to show the top 10 - 15 headlines

> [http://www.premierleague.com/rss/ptv/page/ArticleIndex/0,,12306~2233528,00.xml](http://www.premierleague.com/rss/ptv/page/ArticleIndex/0,,12306~2233528,00.xml)

Any help would be greatly appreciated :D

---

### Post by iiska on 2009-05-19
Put following in your .conkyrc below the line TEXT. If you don't have .conkyrc file in your home dir you can copy it from /etc/conky/conky.conf.

```

${rss http://example.com/feed 10 feed_title}
${rss http://example.com/feed 10 item_titles 15}

```

That will fetch 15 latest titles every 10 minutes.

---

