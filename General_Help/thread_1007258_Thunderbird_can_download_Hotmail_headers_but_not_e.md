---
title: "Thunderbird can download Hotmail headers but not e-mail"
date: 2008-12-10
forum: General Help
---

### Post by nLinked on 2008-12-10
I followed some steps to get Hotmail into Thunderbird on Ubuntu Ibex. I installed Thunderbird and two addons: WebMail and WebMail - Hotmail.

My e-mail address is the new @live.com address. After setting it all up with the POP port as 1100 and SMTP as 2500 (and adjusting these settings accordingly into Thunderbird for my account), it connects through to Hotmail and the status bar says its downloading message 1 of 5 (I only have 5 messages in my Inbox right now) but after a minute a message comes up saying the connection timed out.

If I go to T/bird's options and say download headers only, it successfully downloads all headers (unread and read), but clicking one to download the message just makes it keep waiting and then it times out.

I then went to Hotmail online and marked one message as unread. In T/bird, it actually managed to download the message for that e-mail but never again.

It's so close to working but downloading messages causes a timeout after a minute (and increasing the timeout doesn't help).

How can I get it downloading all messages with the body successfully? It's so close!

---

### Post by KE4AVB on 2008-12-10
If Linux TB operates the same the Win version, look under "Tools/Options/Advance/Network and Disk Space". Try increasing the connection timeout. I had to increase mine to around 300 secs under Windows. Some ISP are a little slow on responding. Netzero really gave a fit on this.

Thanks in advance about where you how to add hotmail Tbird as I am needing to add it here too. I may have the same problem but hopefully we get this worked out.

KE4AVB

---

### Post by nLinked on 2008-12-10
> **KE4AVB said:**
> If Linux TB operates the same the Win version, look under "Tools/Options/Advance/Network and Disk Space". Try increasing the connection timeout. I had to increase mine to around 300 secs under Windows. Some ISP are a little slow on responding. Netzero really gave a fit on this.

Thanks in advance about where you how to add hotmail Tbird as I am needing to add it here too. I may have the same problem but hopefully we get this worked out.

KE4AVB

Thanks, it works! I increased the delay to 9999 seconds and it is downloading messages one-by-one but VERY slowly - almost 1 minute per message.

Can this be sped-up?

I think you asked how I got it into T/bird? I'm using the Webmail plugin and Webmail-Hotmail plugin from the Thunderbird addon's page.

---

### Post by KE4AVB on 2008-12-10
Try the WebDav access funition. Hotmail is being extra picky as Microsoft don't want us to access our account otherthan  using thier website unless we pay extra. This may relieve download time problem. I have been Pop Peeper is working fine with Hotmail so you try that program too.

Microsoft is constantly making changes and it is not affecting every user the same way. Here I haven't got Linux version up yet but I was able to either the old or new versions of hotmail but the WedDAV has been working fine so far...Tommorrow may different.

KE4AVB

PS. I thought I let you know that I finally install hotmail here on Linux using the WebDAV setting and everything is working fine. It downloaded 60 emails ranging from 1k to 4.8m and it did it as fast Windows did. 12-9-08

---

