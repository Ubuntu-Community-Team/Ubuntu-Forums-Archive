---
title: "Collecting and analysing data from publicly accessible sources..."
date: 2014-10-18
forum: Education &amp; Science
---

### Post by sgofferj on 2014-10-18
Hi,

I'm looking for some kind of "poor man's CIA"... I'm pretty active in nature conservation and I'm looking to build a system which automatically collects information from publicly accessible sources, say press, publicly visible forums, etc. and analyses the data for certain connections and relations. Specifically, I'm looking to discover information which could help prevent poaching of endangered species.
I already have a very simple system in place that regularly pulls RSS feeds from certain news sources and websites and if an article or post contains certain keywords, those are stored in a database. That's a good start but the analysis is still a major task and it's not always easy to see connections.
Does anybody know any open source software which could help us analyze this kind of information? What would this kind of software be called (English isn't my native language)?

-S

---

### Post by tgalati4 on 2014-10-18
Normally, this activity would be called a Clipping Service.  Here's an example:  [http://www.burrellesluce.com/services/media_monitoring/full_service](http://www.burrellesluce.com/services/media_monitoring/full_service)

There are not many open source projects:  [http://newsclipper.sourceforge.net/](http://newsclipper.sourceforge.net/)

Your current data format is RSS feeds which are HTML or XML text files.  So you would need an HTML/XML data miner to pull out key phrases from your feeds.  Then you would need to review them to determine if they are relevant to your purpose.  To automate this process would require a Big Data infrastructure and some sort of artifical intelligence framework that learns over time.  This is not trivial.

Do you have some small example datasets that you can attach?

I would keep your pets inside.

---

### Post by sgofferj on 2014-10-18
So THAT is "Big Data"...? I do have written a Perl script which pulls RSS feeds from a number of local and national news sites and if an article contains certain (hardcoded) keywords, it's pushed into a mysql database. To prevent duplicates, I also hash the description text and store the hash, so that part is already working. My next step would be to have a second table for the keywords with some easy "pull keyword out of text into table" function in the GUI. The acquisition and filtering of relevant articles isn't that hard.

The analysing is the hard part. As I wrote, it's fairly hard to see patterns or relations if you look at all those articles manually, e.g. recognize names, locations, etc. Simply spoken, I would like to have a flag popping up if e.g. a certain place occurs repeatingly in connection with reports about poaching. If it's not like every day or every week, something like that is hard to catch when looking at a ton of daily articles manually.

Sample dataset - not yet... But you can basically create or imagine some yourself. Just grab every article which contains e.g. "bear", "wolf", "lynx" and "poaching" from all relevant national and local news services. Then you have an idea of the amount of information I have to process...

Pets?

---

