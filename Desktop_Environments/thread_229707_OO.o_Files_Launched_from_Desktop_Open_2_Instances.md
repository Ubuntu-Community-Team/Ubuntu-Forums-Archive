---
title: "OO.o Files Launched from Desktop Open 2 Instances"
date: 2006-08-04
forum: Desktop Environments
---

### Post by BadServo on 2006-08-04
After a fair bit of searching, I've been unab;e to determine a solution or even find another report of the issue.

My wife's PC is running a fully updated Dapper installtion.  It was upgraded from Breezy.  She often places frequently used spreadshees and documents on her Desktop.  Whenever she launches an OpenOffice associated file from the Desktop, it appears as though 2 instances of OO.o attempt to start.  The second is presented as an open document, but you get a "busy" icon and are unable to modify the document.  On the taskbar you can see another instance traying to open, tho it never does.  Eventually it simply times out and vanishes.

I know it's a minor issue, but it's really frustrating her, and I'm at a loss as to what the problem might be.  Any advice is appreciated.

---

### Post by thingy on 2006-08-04
Need more info:

1. Did the problem first develop after upgrade from breezy to dapper?

2. Did OO.o work properly in dapper at all for you?

3. To rule out things, can you:

- Rule out the documents she normally opens, by creating some new test ones and see if the issue replicates

- Create a new user(e.g. test1), login as this user, try and replicate the issue by double clicking a document on your desktop

4. Does the issue only happen when double clicking on a document on the desktop?

5. Attach the ~/.xsession-errors file after the issue has happened once during your current X session.

6. Can you check the documents for macros/viruses which could be causing the behaviour...

7. Can you grab a screenie to show what you meant by this: "The second is presented as an open document, but you get a "busy" icon and are unable to modify the document."

jin

---

### Post by BadServo on 2006-08-04
I have finally tracked down a lead.  When I enabled the OO.o Quickstart feature on the new user account, I began to have the same issue there as well.  This feature has been on for some time in the previous account.

She really enjoys the quickstart feature, since she uses OO.o frequently.  Any advice on getting around the issue, while still allowing her to use this option?

Can someone see if they can replicate this effect by enabling the quickstarter?

---

### Post by thingy on 2006-08-04
Can you investigate what the parameters for quickstart being used are...i.e. are they as follows:

ooffice -quickstart -nologo -nodefault

See the nodefault bit...i think that stops the blank doc from popping up if thats what the issue was...

---

### Post by thingy on 2006-08-04
Oh wait! Here's a nicer way of quickstart

[http://www.ubuntuforums.org/showthread.php?t=52380&highlight=openoffice+quickstart]("http://www.ubuntuforums.org/showthread.php?t=52380&highlight=openoffice+quickstart")

---

### Post by BadServo on 2006-08-04
Still no joy.  I checked the parameters of the quickstarter and they are jsut as you listed.

I attempted the speed-up tip in the link you last post contained, but it didnt' work too well.  It get starting OO over and over, if I closed it, it restarted, and it stayed on top of other windows.  Not good.  ^_^

Managed to get that fixed, but m still open to suggestion.

---

