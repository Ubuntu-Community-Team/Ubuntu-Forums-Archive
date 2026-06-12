---
title: "kdewallet doesn't work"
date: 2007-04-30
forum: Desktop Environments
---

### Post by eantoranz on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: kde [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Applications that use kdewallet to store passwords (like kopete or akregator) fail to retrieve them from kdewallet. The only "weird" thing I notice is that there's a "kded" processes eating up 100% of CPU time when I start kde. I can kill it and applications don't crash, but kopete nor akregator can get the passwords. What can I do to diagnose it?

---

### Post by miobio on 2007-04-30
HA!

I had that problem a couple of hours ago :-D

I solved it by deleting all the kwalletmanager config files in 

~/.kde/share/config/kwalletmanagerrc
~/.kde/share/config/kwalletrc

Try this then log off kde...

---

