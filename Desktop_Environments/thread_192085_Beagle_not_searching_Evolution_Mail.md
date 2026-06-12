---
title: "Beagle not searching Evolution Mail"
date: 2006-06-08
forum: Desktop Environments
---

### Post by kaplanmyrth on 2006-06-08
I see that Beagle is supposed to index Evolution's mail and calendar by default, but mine isn't. It's indexing documents under my home directory, but it doesn't give me results from mail or calendars.

I ran beagle-index-info and it gave me:
```

ï»¿Index information:
Name: KMail
Count: 0
Indexing: False

Name: Files
Count: 5883
Indexing: False

Name: GaimLog
Count: 4
Indexing: False

Name: IndexingService
Count: 0
Indexing: False

Name: Tomboy
Count: 0
Indexing: False

Name: Blam
Count: 0
Indexing: False

Name: Liferea
Count: 0
Indexing: False

Name: Akregator
Count: 0
Indexing: False

Name: KonquerorHistory
Count: 0
Indexing: False

Name: Kopete
Count: 0
Indexing: False

Name: applications
Count: 137
Indexing: False

Name: documentation
Count: 2942
Indexing: False

```

Should it list Evolution there? I don't even know what half of those things are... (although Tomboy looks cool now that I googled it :-)

Is there anything I can do to see why beagle isn't searching mail, or force it to do so?

---

### Post by asimon on 2006-06-08
Do you have 'beagle-backend-evolution' installed? You probably need it if you want your evolution stuff indexed.

---

### Post by kaplanmyrth on 2006-06-08
[QUOTE=asimon]Do you have 'beagle-backend-evolution' installed? You probably need it if you want your evolution stuff indexed.[/QUOTE]

I'll try it, but I didn't think I needed it for beagle to search mail. I thought beagle-backend-evolution was needed so beagle could search contacts, but I thought it would do mail without plugins.

---

