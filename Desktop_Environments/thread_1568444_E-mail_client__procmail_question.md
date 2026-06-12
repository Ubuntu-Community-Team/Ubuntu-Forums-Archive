---
title: "E-mail client / procmail question"
date: 2010-09-05
forum: Desktop Environments
---

### Post by glondor on 2010-09-05
I am looking for an e-mail client that will allow me to download only the message text, then insert a link to download attachments.

I have tried Evolution, Thunderbird, and Balsa, and none of them seem to have this feature. The closest is Thunderbird (and Balsa, I think), which allow you to specify a maximum message size that is downloaded. But no matter what number you choose, you run the risk of either failing to download all of a long text message or accidentally downloading a small attachment.

This should be possible to do, by scanning incoming messages and terminating the transmission as soon as the client encounters a MIME boundary. Does anyone know if there are any clients that can do this?

If not, it should be possible to set up a local mail proxy that would listen for connections from the client, connect to the server, terminate the connection as soon as it reached a boundary, insert a link to download the rest, etc. Could this be done with procmail?

glondor

---

