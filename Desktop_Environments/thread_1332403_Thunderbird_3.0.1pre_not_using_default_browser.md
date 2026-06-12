---
title: "Thunderbird 3.0.1pre not using default browser"
date: 2009-11-20
forum: Desktop Environments
---

### Post by bjtuna on 2009-11-20
I am running the Thunderbird 3.0.1pre release candidate from the Ubuntu repos ("Shredder").  When I first installed it, my default browser (set via System -> Preferences -> Preferred Applications) was "firefox-3.6".  I've since changed my default browser to "firefox-3.5" but Thunderbird is still sending links to firefox-3.6.

It's as if upon initial setup/import, TB3 imported my system settings and then froze them in time. I've crawled through the "Config editor" in TB3 (Edit -> Preferences -> Advanced -> Config Editor) but the network.protocol-handler entries are all just set to 'default'. 

Any ideas?

---

### Post by bjtuna on 2009-11-20
In typical fashion, as soon as I wrote out my question, I discovered the answer for myself:  basically, close TB3, do a search/replace on 'firefox-3.6' to 'firefox-3.5' in ~/.thunderbird-3.0/<profile>/mimeTypes.rdf, and re-open TB3. That fixes it.

I'll probably troll the TB3 bugzilla later and see if anybody knows that TB3 doesn't seem to react dynamically to these system-wide changes.

---

