---
title: "minor issue with printer sharing"
date: 2009-01-26
forum: General Help
---

### Post by fm1234 on 2009-01-26
I'm sharing a Canon MP780 in a ubuntu 8.10 PC and I used CUPS for that. On the client (also 8.10) I have two printers, one called MP780 without driver and pointing to /dev/null. The other is fine, but is named MP780@server_ip.

To keep it neat, I would like the null printer MP780 to be the one connected to the server. However, I'm not able to modify configurations neither even delete printers. Cups doesn't react to buttons on this printer and System/Administration/Printing has the options dimmed. Running printer-settings with sudo, doesn't give me either access to modify/delete printer.

How can I fix my printer configuration?

TIA,
Fernando

---

### Post by cariboo on 2009-01-26
Have you tried the cups administration interface located at [http://localhost:631?](http://localhost:631?)

When you enter the above address in firefox you should see something like the attached screenshot.

Jim

---

### Post by fm1234 on 2009-01-26
Indeed, I was referring to that UI when I mentioned cups not reacting to buttons. I think it is a zombie printer from a previous setup, before I start using static IPs.

I'm trying to figure out where does CUPS, as a client, keeps info from the remote printers.

---

