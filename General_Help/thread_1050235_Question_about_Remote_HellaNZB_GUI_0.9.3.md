---
title: "Question about Remote HellaNZB GUI 0.9.3"
date: 2009-01-25
forum: General Help
---

### Post by y0diggity on 2009-01-25
I'm trying to get this app running on my laptop. I have Hellanzb running and when I open the Gui, I get errors. in the terminal. The error is:

```
"warning: Connection error: <ProtocolError for hellanzb:@127.0.0.1:8760/RPC2: 401 Unauthorized>"
```

In the config for the GUI, I have "host" set to the loopback of 127.0.0.1. I assumed that was what it should be, since Hellanzb is running locally.

Can you look at the error above and tell me what the problem is? If there's a protocol error, then what protocal should it use?? I looked around and it seems that the port is a standard port for Hellanzb. 

I don't have a password entered since I don't have a password set in the application. I haven't messed with the SSH tab in the GUI config, because again, I don't think I have any need for it. 

Let me know if you need any additional information.

---

### Post by y0diggity on 2009-01-25
Anyone else use this app that can maybe help?

---

### Post by cmize on 2009-02-17
Try using changeme as the password.

---

