---
title: "'check syslog for diagnostics' says it has failed on every boot"
date: 2009-01-17
forum: General Help
---

### Post by piemonkey on 2009-01-17
I'm not sure what it's called, but on the list of things that kubuntu does as it starts up (what you see if you press ctrl-alt-F8), there's an entry which is "check syslog for diagnostics" and for some reason it always says fail.

I'm not sure this is a serious issue, it probably isn't, seeing as I appear to be getting no ill effects, but I just thought I'd see if it might cause problems later or something.

Does anyone know what causes it, how to solve it or whether it's actually a problem?

I'm using intrepid-amd64

---

### Post by dcstar on 2009-01-17
> **piemonkey said:**
> I'm not sure what it's called, but on the list of things that kubuntu does as it starts up (what you see if you press ctrl-alt-F8), there's an entry which is "check syslog for diagnostics" and for some reason it always says fail.

I'm not sure this is a serious issue, it probably isn't, seeing as I appear to be getting no ill effects, but I just thought I'd see if it might cause problems later or something.

Does anyone know what causes it, how to solve it or whether it's actually a problem?

I'm using intrepid-amd64

Why don't you look in your syslog and see what the problem is?

---

### Post by piemonkey on 2009-01-19
I did, but it I had no idea what the huge list of entries was. I just looked again, and figured out how it works (ie. with a seperate file per boot) so, I just looked at the start, rather than trying to work from the end like before. The only entry that I could both make sense of, but seemed to be indicating an error was this:
anacron[6431]: Job `cron.daily' terminated

---

