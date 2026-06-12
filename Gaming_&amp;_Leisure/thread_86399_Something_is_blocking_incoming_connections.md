---
title: "Something is blocking incoming connections"
date: 2005-11-05
forum: Gaming &amp; Leisure
---

### Post by silentQ on 2005-11-05
hey guys
i've been hostin dedicated for Unreal engine in windows for a long time
now ran the game on gnome with cedega  it runs fine...
but when i host dedicated and any 1 tries to join the console log gives me the following

ScriptWarning: WebServer DM-Hildir.WebServer0 (Function UWeb.WebServer.BeginPlay:01ED) BindPort: bind failed
Init: Game engine initialized
Log: Startup time: 2.688453 seconds
Log: Resolved master.gamespy.com (207.38.11.34)
ScriptLog: UdpServerUplink: Master Server is master.gamespy.com:27900
ScriptLog: UdpServerUplink: Port 7778 successfully bound.
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: info
ScriptLog: UdpServerQuery: Unknown query: info
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: status
ScriptLog: UdpServerQuery: Unknown query: status

and so on.... seems like something is blocking the application... 
i'm behind the router but all the needed ports are forwarded..

maybe i'm doing smth wrong?
thanx:rolleyes:

---

### Post by Remmelas on 2005-11-05
any chance you've set up a firewall on your linux box as well?

---

### Post by silentQ on 2005-11-06
no man, gnome has no firewall....

---

### Post by jeffreyvergara.NET on 2005-11-06
[QUOTE=silentQ]no man, gnome has no firewall....[/QUOTE]

umm... so Firestarter Firewall is not built for gnome?

---

### Post by cdhotfire on 2005-11-07
[quote=jeffreyvergara.NET]umm... so Firestarter Firewall is not built for gnome?[/quote]

Im sure he ment, built in.

Also, no to your question, Firestarter is built for linux.

---

### Post by silentQ on 2005-11-07
firestarter is built for gnome but not built-in.... and i didnt install firestarter with automatix... so i dont have no firewal but my router

---

