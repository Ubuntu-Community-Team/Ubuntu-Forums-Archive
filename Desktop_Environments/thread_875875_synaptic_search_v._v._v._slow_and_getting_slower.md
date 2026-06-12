---
title: "synaptic search v. v. v. slow and getting slower"
date: 2008-07-31
forum: Desktop Environments
---

### Post by undecidable on 2008-07-31
I am installing Ub 8.4.1 for my 78 y.o mother - it is never too late to leave the dark side.  Moved my 7y.o. daughter to it last week - it is also never too early to leave the dark side - and she is thrilled.  

When I open synaptic and search on a pkg, say "tilda" (in th name or description) it takes over 3 minutes to return the result.  It was taking 1'15" then went to 2' now over 3'.  

I don't think it is a problem with the pkg cache.
sudo apt-cache search "tilda" 
returns the result in 1 second.  

I don't think it is the machine spec - I have Ub 7.04 on a much lower spec machine and it returns the result in 23".  Also this machines time for opening OOO or FFx is reasonable.  

Is there some kind of synaptic cache or config file that might be corrupt that can be deleted?  

Lookiung forward to any ideas:  My mother has not got time on her side, and so patience is not her strong point.

---

### Post by tamoneya on 2008-07-31
you could try cleaning things out with:```
sudo apt-get clean
```

---

### Post by undecidable on 2008-08-01
Clean didn't work - as I surmised above there was no problem with the cache.

What has worked is uninstalling (apt-get --purge remove synaptic) and re-installing Synaptic.  
Hopefully it won't re-deteriorate again.  

If anyone else tries this, make sure you make a note about what other programs also get uninstalled when you uninstall Synaptic (eg update -manager, update-notifier), as when you re-install synaptic, these don't automatically get re-installed.   You must re-install them  manually.

---

### Post by rugbeeprop on 2009-03-04
I had to reinstall 8.10 because I messed the system up...
 
I found the similar problem with current Synaptic. What I also noticed was that if I used the Search function (not the Quick Search), the speed was normal. When using Quick Search, it took longer to search, and then when it took a futher few minutes to "Mark" or "Unmark" an item.
 
I will try your suggesstion when I get home.
 
Thanks.

UPDATE:
I did as undecidable suggested and it solved my issue. Thanks.

---

