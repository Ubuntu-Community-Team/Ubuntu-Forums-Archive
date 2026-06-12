---
title: "Printing is a real disaster  - can anyone help please?"
date: 2009-05-27
forum: General Help
---

### Post by Edk on 2009-05-27
I am having real problems with printing.  I am giving as much information as I can, in the hope that some will be able to help me please!

I have just done a clean install of Ubuntu 9.04

My printer is a Deskjet 940C running on a QNAP Print server.  All worked well under Ubuntu 8.04

**The printing set up is as follows:**

[LIST]
[*]Driver is HP Deskjet 940c hpijs, 3.9.2
[*]HP Deskjet 940c hpijs [en](recommended)
[*]Have set "Allow printing for everyone" under "Access control"
[*]Print Test page works OK from Dialogue and from CUPS web pages
[*]Under Authentication I have set "Prompt user if Authentication is required"
[*]The "Verify" button confirms that all is OK
[/LIST]

**The problems**

[LIST]
[*]Open Office will print without error
[*]Thunderbird will print without error
[*]Firefox does nothing at all.  The printer is in its dialogue boxes, it looks like it will print but nothing.
[*]Scribus prints but it is a mess.  It looks as if the print has been shunted down and to the right, and there are a series of major glitches where it does print - in other words a mess!
[*]PDF veiwer - ?Evince? - gave me an authentication error, and then an error "Failed to print document Too many failed attempts"
[/LIST]

**My CUPS error logs are filled with entries like this:**

E [27/May/2009:17:48:36 +0100] Print-Job: Unauthorized

E [26/May/2009:20:37:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [26/May/2009:20:14:38 +0100] [Job 11] Session setup failed: NT_STATUS_LOGON_FAILURE
E [26/May/2009:20:15:17 +0100] Print-Job: Unauthorized
E [26/May/2009:20:15:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [26/May/2009:20:19:23 +0100] CUPS-Delete-Printer: Unauthorized
E [26/May/2009:20:20:41 +0100] Print-Job: Unauthorized
E [26/May/2009:20:21:55 +0100] Print-Job: Unauthorized
E [26/May/2009:20:29:58 +0100] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [26/May/2009:20:32:26 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [26/May/2009:20:33:44 +0100] Print-Job: Unauthorized

I have trawled the Forums and not found anything that helps.  I would really value some help here please!

Thanks in advance

Ed

---

### Post by timcredible on 2009-05-27
can you change the authentication to something else, like 'no authentication'?

---

### Post by Edk on 2009-05-27
No.  The options are 

[LIST]
[*]Prompt if authentication is required
[*]Set authentication details now
[/LIST]

I did not require authentication under 8.04.  What would I put here?

---

