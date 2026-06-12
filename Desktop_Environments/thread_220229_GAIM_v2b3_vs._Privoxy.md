---
title: "GAIM v2b3 vs. Privoxy"
date: 2006-07-21
forum: Desktop Environments
---

### Post by AlphaMack on 2006-07-21
The default version of GAIM with Dapper worked flawlessly with Privoxy (and pointed to Privoxy in System->Preferences->Network Proxy).  For reference, I have only HTTP and HTTPS set to port 8118 @ localhost.

Unfortunately with the 2.0 beta 3, I now get an error message:

"Access Denied:  Proxy server forbids port 5190 tunneling."

I don't know if this is an issue because GAIM 2 is in beta or if something has changed.  1.5 wasn't a problem before with Privoxy's settings.

The only obvious solution is to manually edit each account and change the proxy type setting from "Use global proxy settings" to "No proxy."  But I can easily see this as a somewhat not-so-intuitive task.

In order to use the default global proxy settings option again, what will I need to add or modify either via Privoxy (requires sudo) or the Network Proxy preference?

---

