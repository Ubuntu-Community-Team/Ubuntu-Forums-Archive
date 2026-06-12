---
title: "Is there an Exchange Server Client Available - not Evolution"
date: 2007-02-28
forum: Desktop Environments
---

### Post by gnu2tux on 2007-02-28
Hi,

 I wonder if there is an exchange server client that's available for Linux. My workplace use Outlook and Exchange 2000 and Evolution is very flaky. 

Is there any other clients out there that work?

Regards,

Ali

---

### Post by setterm on 2007-03-15
I don't mind evolution, but it can be really slow when loading mail from the server. I'm not sure on any way to speed it up, but if anyone has a suggestion, it would really be appreciated. The only other option that I'm aware of is **Thunderbird** using **IMAP**, so long as it's enabled on the server.

Setts.

---

### Post by sshetye on 2007-04-06
Even I'm interested in the answer ... are there really no exchange compatible email clients on ubuntu ?? 

Evolution doesn't seem to handle the calendar, notes etc of Outlook very well. It is also PAINFULLY slow compared to Outlook ... I hate to say it, but now that I'm trying to setup Evolution in place of Outlook, Outlook beats Evolution hands down.

---

### Post by setterm on 2007-04-10
There is a library called [tinymail]("http://www.tinymail.org/"), but other than that I've not found much at all that can handle exchange. The one thing that I did find is that the default install of evolution turns on all of the plugins which often times are not necessary, covering hula, groupwise, exchange and so on. so if you don't need some of these, turn them off, run evolution --force-shutdown and then restart evolution. You should find that it will run a bit, if not noticeably faster.

**Matt**

---

### Post by sshetye on 2007-04-12
> **setterm said:**
> There is a library called [tinymail]("http://www.tinymail.org/"), but other than that I've not found much at all that can handle exchange. The one thing that I did find is that the default install of evolution turns on all of the plugins which often times are not necessary, covering hula, groupwise, exchange and so on. so if you don't need some of these, turn them off, run evolution --force-shutdown and then restart evolution. You should find that it will run a bit, if not noticeably faster.

**Matt**

Thanks Matt. Actually what I noticed is that Exchange functionality in Evolution is tied down to Outlook _Web Access_ (OWA) and NOT thru the regular exchange protocol (from what I could make out). 

My employer doesn't use OWA, so is there a way/plugin by which I can tell Evolution/any other ubuntu mail client to "talk exchange" with the corp exchange server? 

I'd like to send/receive email, contacts meetings etc just like outlook does.

---

### Post by mathenge on 2007-11-02
I've used Evolution but don't like the fact that it uses OWA as well. We have network sniffers to monitor LAN traffic and Evolution will send your username/password to the Exchange server in plain text.

If you configure Evolution to use IMAP, you loose the Global Address Book and the Calendar.

So, I'm also trying to find a way to get my email, address book and calendar from Exchange. Perhaps using a secure OWA connection (using Firefox) might be the only way to achieve that for now.

---

### Post by gnu2tux on 2007-11-02
Hey,

 Since there seems to be some activity on this thread again (one day someone will answer all my prayers and tell me Exchange is supported flawlessly!) I'll tell you what I have done thus far:

I experimented with Kontact (kubuntu/kde) and found that whilst it was anything but properly usable, it did provide an interface to Exchange, rather than OWA. Furthermore, I was generally able to receive calendar appointments and save them to my calendar. Some times they synced flawlessly, sometimes I had to save as an ical file then re-import into my calendar. Either way, Kontact would occasionally flake out and crash when using Exchange and leave connections open and processes parentless. Not ideal.

However, I've not yet had the chance to check out Kubuntu 7.10 with Exchange yet. The big difference between previous (K)Ubuntu versions is that they used the standard release of Kontact/Kmail, whereas the 7.10 version uses the Enterprise branch of Kontact. So far, I've only seen an increase in stability and usability with this new version, but I'm itching to put Exchange to it and see what happens. Has anyone else had any experience with it thus far?

Cheers,

Ali

---

