---
title: "Convert Outlook .pst to KMail??"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Robert Leithe on 2006-08-11
Hi,

I've eksported my calendar, contacts and e-mail from Outlook to .pst-files. And using the tool "readpst" I've been successful in importing my contacts to Kontact. However, my calendar and e-mail remain.

Upon running the tool on a selected .pst (either my calendar or e-mail) the output throughout the process tells me everything completes without any errors. There are so and so many e-mails converted, 0 failed etc etc.

But when the process ends, I am stuck with an empty output file.

Any suggestions on this?

Sincerely
Robert Leithe

---

### Post by dtfinch on 2006-08-12
If you still access to the Windows computer with Outlook, you should be able to install thunderbird (but leave Outlook as the default email client for now) and import your email from Outlook to Thunderbird, which effectively converts all your email to mbox format (stored in documents&settings/.../application data/thunderbird/profiles/.../Mail I think, or maybe local settings). You should then be able to import the mbox-formatted email into KMail. I've never really imported from Outlook to TB or used KMail much, but I think that should work.

---

### Post by Robert Leithe on 2006-08-13
Well, I installed Thunderbird and imported everything from Outlook.
I found the directory structure under C:\..\Application Data which contain all my e-mails. I copied the structure to my Linux computer. But can't find a way to import it into KMail. The Import command under the File menu is disabled.
I'm using Kontact to combine several KDE components as an Outlook replacement. When I'm working with Contacts or the Calendar, the Import command is enabled. But not when I'm working with e-mails.

---

### Post by editrix on 2006-08-13
> **Robert Leithe said:**
> ...The Import command under the File menu is disabled.
I'm using Kontact to combine several KDE components as an Outlook replacement. When I'm working with Contacts or the Calendar, the Import command is enabled. But not when I'm working with e-mails.

Try running Kmail as a standalone. Close Kontact, and in the terminal type kmail--you'll get a lot of messages, one of which *might* explain the problem. Then Kmail will open. See if the File/Import messages menu item is there.

---

### Post by Robert Leithe on 2006-08-13
I received this output when I ran the "kmail" command:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81eaac8 ): KAccel object already contains an action name "delete"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81eaac8 ): KAccel object already contains an action name "edit"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81eaac8 ): KAccel object already contains an action name "display_message"
robert@C-3PO:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.

Being new to Linux this doesn't tell me much :(
KMail started, but the Import command is still disabled. I've tried switching between folders (Local Folders, inbox and then another folder I created myself) to see if this enabled the command, but no such luck.

EDIT: When I closed KMail, the terminal window received these lines:
Weaver dtor: destroying inventory.
WeaverThreadLogger: thread (ID: 1) destroyed.
WeaverThreadLogger: thread (ID: 2) destroyed.
WeaverThreadLogger: thread (ID: 3) destroyed.
WeaverThreadLogger: thread (ID: 4) destroyed.
Weaver dtor: done

---

### Post by editrix on 2006-08-14
> Being new to Linux this doesn't tell me much 

Same here, I'm sorry to say. I know a lot of those messages don't mean much even if you do understand them.

Try typing ```
which kmailcvt
``` in the terminal. If you get nothing in response, then for some reason you haven't got the Kmail convert program installed. In which case, you'll have to install it.

---

### Post by Robert Leithe on 2006-08-14
When I type which kmail I get this response:

/usr/bin/kmail

---

### Post by editrix on 2006-08-15
> **Robert Leithe said:**
> When I type which kmail I get this response:

/usr/bin/kmail

Yes, but I said kmailcvt

the "cvt" = convert.

As an aside, whenever anyone says to "type this" the easiest way to do it is to highlight it with the mouse, which automatically copies it into the clipboard, then paste it into the terminal by hitting the middle mouse button.

---

### Post by Robert Leithe on 2006-08-15
The first thing you loose when you go blind, is your eyesight...
I'll try that copy and paste tips the next time :)

Anyway, problem solved thanks to you!

Sincerely
Robert Leithe

---

