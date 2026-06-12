---
title: "Kopete starts Kmail???"
date: 2006-05-13
forum: Desktop Environments
---

### Post by miobio on 2006-05-13
Ave Forum!!!

I'm experiencing a rather strange problem with kopete. Whenever i launch it, Kmail starts as well :???:   ](*,) 

Does anybody have an idea why this happens???

I'm running Kubuntu  Dapper but i also had the same problem on Breezy, I read somewhere that this could be somehow related to the fact that I'm keeping my address book on IMAP with kmail but why should kopete access my address book???

Thanks in advance  :-k

---

### Post by msak007 on 2006-06-18
I hope someone has an answer as this problem is driving me nuts. I just installed Dapper on my sister's laptop and set up kopete for her with no problems. I'm not sure what she did, but now everytime kopete starts it starts kmail with it. I've found no setting in either program that tells one to start with the other or vice versa, and I've cleared all stored session files. It's not a session thing as kopete launches kmail regardless of whether it's started with the session or manually. I've even deleted all the kopete settings in the .kde folder, no luck. She doesn't use kmail so I'm about to just uninstall that completely to get rid of this problem unless somebody has a better solution.

---

### Post by Jason_25 on 2006-06-18
Instead of uninstalling it, which might remove needed packages, you could find the kmail executable and make it non-executable.

---

### Post by msak007 on 2006-06-18
Well I figured out the problem. Even after uninstalling kmail, kopete kept trying to start it. And btw, it only uninstalls 2 packages but does break the "kubuntu-desktop" metapackage. Anyway, when I tried to run kopete from the console, I got the following output:

```
kio (KMimeType): WARNING: KServiceType::offers : servicetype DCOP/ResourceBackend/IMAP not found
kopete: WARNING: KDCOPServiceStarter: No service implementing DCOP/ResourceBackend/IMAP
kresources: ERROR: Couldn't connect to the IMAP resource backend
kopete: ERROR: Unable to open resource 'Kolab Server'!
```

Well I checked kmail, and went to the settings (Settings --> Configure Kmail --> Accounts) and there was an entry for "Kolab Server" (from the error above), with one of the account names used in kopete. Apparently it tries to set up your email automatically?  Either that or my sis did something to try and have it set up email. So anyway I deleted that and still, it launched kmail. I tried deleting all the accounts from kopete so it didn't connect on startup, same result. Finally, I checked kcontrol / System Settings, and went to the KDE Components module. There were no services under "Service Manager" that fit the description of the error above. I checked "KDE Resources", and sure enough there was an entry for "Kolab Server". At first I couldn't delete it because it was set as "Standard --> Yes". There was another entry for "resource", so I made that the standard and then I was able to delete the Kolab Server entry. I'm pretty sure I didn't mess anything up, and now kopete starts without starting kmail. I'll read up more on Kolab Server and see what exactly it is and why it was set as a KDE Resource / account type in kmail.

---

### Post by tristangrimaux on 2007-12-13
You are a genius!! I had the same problem and now its gone!!!! In fact I would love to use kmail but it doesn't work with imap, it stops checking email, and it has no server notification protocol.

---

