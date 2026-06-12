---
title: "gnome-dictionary and dictd"
date: 2006-01-15
forum: General Help
---

### Post by jofre on 2006-01-15
Hi lads,

I have been using the gnome-dictionary (Application -> Accessories -> Dictionary), but it needs Internet to work, so I decided to have a look with Synaptic to setup an offline methode, and I found the "dictd" package, I installed along with "dict-moby-thesaurus". I did not see any new program added anywhere. If I do man dict in a terminal, staff appear about servers. I am not an expert about Linux. I guess that i have to change something in "gnome-dictionary-> Preferences -> server and port" so it uses just the locals thesaurus. Has anybody an idea of how to do this?

If anybody knows how to setup a decent offline dictionary also works. ;-)

Thanks a million, Jofre.

---

### Post by markovuc on 2006-01-15
After you install dictd package, in Preferences of gnome-dictionary change Server from dict.org to localhost (don't change the Port, because dictd listens on 2628 by default). Runing dictd should be safe, as it only allows connections from localhost by default (I read it in /etc/dictd/dictd.conf file).

After that, install more dictionaries (packages dict-gcide, dict-jargon etc.), try with searching for 'dict' in synaptic.

It worked immediately for me.

Marko

---

### Post by jofre on 2006-01-15
Thanks a million!!!!:p 

Or in other words: It work perfectly!

If i can abuse a bit...

You would not know how to set-up a translator tool like Spanish-English?

Anyway, thanks for the reply, Jofre.

---

### Post by markovuc on 2006-01-16
You can try with installing dict-freedict-spa-eng package, but that dictionary doesn't look very big ;) , good for start, maybe...

(and in Preferences, in Database, choose 'Spanish-English Freedict dictionary' instead of 'Search all databases', if you want only that results to be shown)

Marko

---

