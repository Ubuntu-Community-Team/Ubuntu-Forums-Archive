---
title: "Evolution and Exchange 2007"
date: 2008-11-28
forum: Desktop Environments
---

### Post by jlward4th on 2008-11-28
One of the most painful things about my use of Linux has been the poor support for Exchange servers.  Recently my company upgraded to Exchange 2007 and this broke the Exchange support in Evolution.  I could use IMAP but I really need my calendar and contacts as well.  MAPI support in Evolution seems like the right long term solution but that is still a ways away so I'm searching for solutions that will work today.  Openexchange seems like it might be an option especially now that it is available in Ubuntu.  But I can't seem to get it working and I haven't found any useful documentation on getting it setup.  Another option is using Outlook 2007 via the CrossOver software but I haven't been able to get that working either.  Anyone have any ideas on this stuff?  Thanks.

---

### Post by albandy on 2008-11-28
Well, this is not a Linux problem, M$ don't provide a connection API or the specifications of a Exchange client, so compatibility is not guaranteed.

Use the exchange owa (webmail) to use your calendar and mail until the new exchange connector will be ready.

Novell "promised" that will work on 2.12 version.

Maybe your company needs a solution like zimbra (open source, free and better than exchange)

---

### Post by jlward4th on 2008-11-28
> **albandy said:**
> Well, this is not a Linux problem, M$ don't provide a connection API or the specifications of a Exchange client, so compatibility is not guaranteed.

Use the exchange owa (webmail) to use your calendar and mail until the new exchange connector will be ready.

Novell "promised" that will work on 2.12 version.

Maybe your company needs a solution like zimbra (open source, free and better than exchange)

Thanks but none of these options are very good.  The OWA is terrible on Firefox.  And I can't get a company of 8000 to switch their email solution.  MAPI certainly is the best solution.  Hopefully Novell provides a solution soon.

---

### Post by albandy on 2008-11-28
If you have time you can use this, but this solution is not opensource:

[http://www.javaexchangeconnector.com/](http://www.javaexchangeconnector.com/)

it's well documented, and there are a lot of examples in their web page, the server license is about $600, and you can get a trial version to test it.

You can make your own calendar client with java and this api.

---

### Post by knight187 on 2009-08-11
Try this: [http://ubuntuforums.org/showthread.php?t=1237875](http://ubuntuforums.org/showthread.php?t=1237875)

Cheers.

---

