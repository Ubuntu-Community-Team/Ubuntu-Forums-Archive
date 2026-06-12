---
title: "Evolution and Self-Signed SSL Certificates"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Freddie on 2006-07-08
In my house I run my own mail server, which I access using IMAP over SSL with a self-signed certificate. Today I decided to try and access my mail from my local Ubuntu PC and so set up evolution and it all seemed to work except for the fact that when ever I start Evolution, or try to send a message I get a load of junk about how my self-signed SSL certificate is 'BAD' and have to click Ok *every* time.

I have looked through all of the settings but can not find anything and can not see a 'remember this' button.

Does anyone know how I can get it to always accept my certificate, rather than asking me each and every time, as it is verging on retarded. If it is not possible to fix this, then can anyone recommend a decent mail client that I should be using?

Thanks for all of your help.

---

### Post by cybergypsy on 2006-07-23
Hi Freddie

This bugged me for a while but its quite easy to fix.

Go to Evolution , Preferences , Certificates , Authourities and import the servers imapd.ped file.

I ticked all three boxes to use the certificate for everything.

Then either restart Ubuntu or use System Monitor to End ALL the Evolution Processes.

Next time you start Evolution its doesn`t mention the certificate.

Good Hunting.
cybergypsy

---

### Post by TerryHowe on 2006-11-30
That would be the pem file, not the ped file I think.

---

### Post by Rescue9 on 2007-05-13
I have tried this with my certificates, and unfortunately this isn't working for me.

Any other clues?

---

### Post by Rescue9 on 2007-05-13
NM, I finally fixed this after numerous hours of problems.

---

### Post by fimblo on 2007-09-15
Could you jot down how you fixed the problem rescue9? I seem to have the same problem as you did.

---

### Post by Jazmo on 2007-11-09
I want to use SSL with servers I don't have other accesses (only email) to (like our Department's server) but because certificates aren't official, the question about accepting them is raised every time.

Neither I have access to any .pem -file that i could import somehow. Is there a workaround? I mean other than asking developers to add "Remember my choice" tag in the program.

---

