---
title: "whitelist to block out most websites?"
date: 2008-08-10
forum: Desktop Environments
---

### Post by 03212139 on 2008-08-10
i was hoping there was something i could do to whitelist a small number of websites for my users to visit and block out all others. i'd like to give the users free access to do anything on the computer accept change the whitelist. that would be password protected.

any ideas?

---

### Post by scorp123 on 2008-08-10
You could Linux's built-in firewall on each Linux installation. But configuring it via the command line is not so easy, so I'd suggest you use one of the many "user-friendly" GUI frontends that can help you with that. Google around for user-friendly programs such as "firestarter", "guarddog", "fireflier" ... What I mean is: You should Google those programs and check if you find tutorials and "how to's" and then decide which one suits you best. But don't use Google to download any of programs. You don't need to. All these programs should be available in the repositories, e.g. you can install them via the "Synaptic" packet manager without having to hunt around for single files and their dependencies.

As for the firewall rules: You should think of something like this:

- any outgoing traffic is blocked
- outgoing traffic on port 80 (= http) and 443 (= https) to your whitelisted hosts is allowed

You should then install the ruleset as "init" Script into /etc/init.d so the rules are auto-loaded upon system boot. Google knows how to do this, there are plenty of "how to's" out there that explain such things.

"Root" is the only user who can manipulate firewall rules, so for as long as your ordinary users have no access to the "root" account and/or cannot use the "sudo" command to change the system's configuration, there won't be much they could do about the restrictions you imposed.

On the other hand ... wouldn't it be wiser and more pleasant if you simply talked to the people and asked them not to visit certain web sites? There will always be "rebels" amongst your users who will fight your "censorship"  and they will spend incredible amounts of energy and effort to get around your restrictions. And there is no "absolute security" in IT and never will be, so chances are that someone will find a loophole and use it behind your back. 

Another approach could be to configure a web proxy (e.g. squid?) and have all your web traffic pass through the proxy. The proxy would then have to do the filtering. But this is complex and I'd only recommend it for companies ... for anyone else this would be "overkill" IMHO.

Also: Did you check your router's software? Many DSL/Cable routers these days have web-filtering capabilities built-in ... you just have to activate the filter and configure it the way you want. It's worth to take a look.

---

