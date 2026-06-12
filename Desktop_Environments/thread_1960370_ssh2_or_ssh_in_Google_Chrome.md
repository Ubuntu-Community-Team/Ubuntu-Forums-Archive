---
title: "ssh2:// or ssh:// in Google Chrome"
date: 2012-04-17
forum: Desktop Environments
---

### Post by Scoubidou on 2012-04-17
Hi,

I've did my homework and search for this in google and in here but did not find anything.

I'm using Ubuntu 11.04 64bits and I'm trying to make Google Chrome open SSH links in SecureCRT. In Windows I could go in SecureCRT in Global Option -> Web and click on the button to make SecureCRT the default handler for telnet:// ssh:// and ssh2://

I can now successfully follow ssh2:// link in my MediaWiki.
It also work on Firefox on my Ubuntu by adding in about:config the following line : network.protocol-handler.expose.ssh2 FALSE

Now the only thing missing is for Chrome to be able to follow the links as well in Linux. If they open in terminal with the default command line it would also be an acceptable solution for me.

Any help, pointer would be appreciated!

I try this but it didn't work.
```

gconftool-2 -s /desktop/gnome/url-handlers/ssh/command '/usr/local/bin/SecureCRT %s' --type Strin
gconftool-2 -s /desktop/gnome/url-handlers/ssh/enabled --type Boolean true

```

Oh, and if one can also throw in a solution for rdp:// I'd be very very happy! ;)

Scoubi.

---

### Post by Scoubidou on 2012-04-23
Bump

---

