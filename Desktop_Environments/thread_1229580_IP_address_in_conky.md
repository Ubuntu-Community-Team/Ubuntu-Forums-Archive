---
title: "IP address in conky?"
date: 2009-08-02
forum: Desktop Environments
---

### Post by josephellengar on 2009-08-02
Is there a way to post your real IP address in conky?  When I use the addr eth0 command it gives me the local IP and I'd like to have the real one, that my router uses.  Would I have to use some sort of a command through a text-based browser with execi or something to do that?  I was thinking maybe 
```

execi 1000 'elinks http://www.whatismyip.com/ >> sometextfile.txt'
execi 1000 cut -l sometextfile.txt 3 | cut -c 20-30 

```

There has to be an easier and less unwieldy way.  Suggestions?

---

### Post by ivan0921 on 2009-08-03
I use the following

Public IP: (${execi 3600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail})

---

