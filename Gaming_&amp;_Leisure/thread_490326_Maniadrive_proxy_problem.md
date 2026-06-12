---
title: "Maniadrive proxy problem"
date: 2007-07-02
forum: Gaming &amp; Leisure
---

### Post by trothigar on 2007-07-02
When I click on internet tracks in maniadrive it comes up with the message:

WARNING: Internet connection failed!
Now in offline mode. (set your proxy?)

I am on lan where there is no proxy so I just don't understand what proxy variable I need to set?

I am using the latest .deb files from getdeb.com

Thanks

---

### Post by diaa on 2008-02-14
This happens to me when the connection is busy with something else(i.e. the ping is >= 4000ms), try closing any other downloads or file sharing programs and try again.
You can check your ping manually by pinging maniadrive's website, run

```
ping maniadrive.raydium.org
```and check the output, press Ctrl-C to stop pinging.

---

### Post by diaa on 2008-02-14
I was playing around and after checking the source-code, I found a way to make it work with high-latency connections(with ping up to 6 secs), this can be accomplished by applying [this patch]("http://ubuntuforums.org/attachment.php?attachmentid=59668&stc=1&d=1203017898") to the **compiled** game, there's no need to apply this patch to the source.
if you're not familiar with patches you can just open the file *game/rayphp/libfile.php* inside the game directory then change the line

[php]curl_setopt ($ch, CURLOPT_TIMEOUT, 3);[/php]to

[php]curl_setopt ($ch, CURLOPT_TIMEOUT, 6);[/php]

---

