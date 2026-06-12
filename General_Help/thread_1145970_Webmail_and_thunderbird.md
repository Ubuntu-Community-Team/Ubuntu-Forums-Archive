---
title: "Webmail and thunderbird"
date: 2009-05-02
forum: General Help
---

### Post by cornish12 on 2009-05-02
Hi

I'm am trying to set up webmail on thunderbird and am trying to download webmail using firefox. However firefox seems to download it and try and install it and I get an error saying it is not compatible with firefox 3. All I want to do is download and then point thunderbird at the software. I'm sure the solution is simple but i can't get it. Please help.

---

### Post by delcypher on 2009-05-02
I assume you're looking at [this page]("http://webmail.mozdev.org/installation.html").

You need to right-click the link and choose "Save link as" rather than just clicking on it (firefox will just try and install it if you do that).

Alternatively you can download the extension using the program wget. In the terminal type```
wget http://downloads.mozdev.org/webmail/web-mail-1-3-2.xpi
```. This will download the extension to current working directory (usually your home directory by default)

Once you've downloaded the plug-in you need to run Thunderbird and then add it (I don't use Thunderbird so I can't remember exactly how this is done but it should be fairly simple).

Hope this helps.

---

### Post by DeMus on 2009-05-02
> **delcypher said:**
> I assume you're looking at [this page]("http://webmail.mozdev.org/installation.html").

You need to right-click the link and choose "Save link as" rather than just clicking on it (firefox will just try and install it if you do that).

Alternatively you can download the extension using the program wget. In the terminal type```
wget http://downloads.mozdev.org/webmail/web-mail-1-3-2.xpi
```. This will download the extension to current working directory (usually your home directory by default)

Once you've downloaded the plug-in you need to run Thunderbird and then add it (I don't use Thunderbird so I can't remember exactly how this is done but it should be fairly simple).

Hope this helps.


What does this webmail do different in Thunderbird than my imap G-Mail account?

---

### Post by DeMus on 2009-05-02
> **DeMus said:**
> What does this webmail do different in Thunderbird than my imap G-Mail account?

Nobody?

---

### Post by delcypher on 2009-05-02
[http://webmail.mozdev.org/]("http://webmail.mozdev.org/")

I believe the webmail plug-in acts as an SMTP & a IMAP or POP server locally on your computer. The plug-in (in conjuction with a specific plug-in) connects to your account's webmail service.

I think that then you specify Thunderbird to connect to localhost for SMTP, POP or IMAP.

For something like g-mail this is pointless as google already provides a SMTP, IMAP and POP3 server.

On the other hand some e-mail providers do not provide servers so this is a way of getting an e-mail client to work with a web based e-mail service.

I could be completely wrong though.

---

### Post by DeMus on 2009-05-02
> **delcypher said:**
> [http://webmail.mozdev.org/]("http://webmail.mozdev.org/")

I believe the webmail plug-in acts as an SMTP & a IMAP or POP server locally on your computer. The plug-in (in conjuction with a specific plug-in) connects to your account's webmail service.

I think that then you specify Thunderbird to connect to localhost for SMTP, POP or IMAP.

For something like g-mail this is pointless as google already provides a SMTP, IMAP and POP3 server.

On the other hand some e-mail providers do not provide servers so this is a way of getting an e-mail client to work with a web based e-mail service.

I could be completely wrong though.

Okay, I see. Yes, G-mail already has Imap and Pop features so it's useless to use the Webmail plug-in. I tried to setup my companies e-mail address but that doesn't work. It seems only the big guys are enabled.

Thanks for your explanation.

---

