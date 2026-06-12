---
title: "Evolution: (1) drag-and-drop? (2) opening other mail formats?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Howzit on 2005-11-09
Hi there. 

I'm new to both Linux & Ubuntu. I'm looking into the possibility of moving our company over to Ubuntu in future (from MS Windows). For that reason I've loaded Ubuntu on one of our machines and am test-driving it in my spare time. I've been trying out Evolution, it seems OK but I'm experiencing problems with two matters.

**_(1) OPENING OTHER E-MAIL FORMAT DOCS_**
[LIST]In our small family business we save correspondence with clients in their respective folders as we negotiate, etc. All of this correspondence has been done via Outlook Express (on our side) and has thus been saved in that format  (.eml) in regular (non-Outlook Express) folders on our server.[/LIST]
[LIST]I expected that double-clicking on such a .eml document (or right-click "open") would open it up as an e-mail via Evolution. However, Ubuntu opens it with gedit. That obviously means that you get to see headers and other formatting code, which I don't want to see, and that you don't have the option to reply, forward, etc.[/LIST]
Can Evolution open such an "externally" saved Outlook e-mail document (not received as e-mail by Evolution), if so how do I create an association to speed this up in future?

**_(2) DRAG-AND-DROP E-MAILS INTO EXTERNAL NON-EVOLUTION FOLDERS_**
As explained above we save correspondence with clients in their respective non-mail-client folders (I believe "Nautilus" folders in Linux/Ubuntu?). If we switch to Ubuntu in future we need to be able to do this. The above-mentioned non-mail-client folders obviously also contains non-e-mail documents (currently MS Word docs, Excel, etc.).

I've tried dragging e-mails from Evolution's inbox and dropping them in external folders. The action was either refused (no error message) or it was dropped as a text file, with no indication that it should be assocciated / opened by Evolution. The - file > save as - action seems to have the same effect. I'm sure Evolution must be able to do this, if so pls tell me how?

Thanks - Mike

---

### Post by VR6Pete on 2005-11-10
You will need to import your emails into Mozilla Thunderbird (this will change the formatting to mbox, you will then be able to import these into Evolution.

This tool will help you along with the process:

[http://www.neotek.hu/en/o2e_en.html](http://www.neotek.hu/en/o2e_en.html)

Thanks,

Pete

---

### Post by Howzit on 2005-11-12
Thanks Pete

If I understand correctly "mbox" is the extention for a mail folder (mailbox), rather than an individual file / e-mail message document? 

In Windows an individual file / e-mail message has the extension "*.eml*". Is there a common extension for individual e-mail files in Linux (Gnome/Ubuntu)? Is there a way to change the format of individual files (i.e. single messages) rather than folders? I ask this because we have thousands of individualy saved e-mail messages in ".eml" (Windows mail format) that are scattered across hundreds of different client folders. I'm talking about regular file system folders here (Nautilus in Ubuntu?), not mail-boxes within an e-mail clients such as Outlook, Evolution, etc. 

My preference would be if some app or plug-in would allow Evolution (or Thunderbird) to open an "*.eml*" file on the fly, without the user having to convert that file in some other way first... I'll be quite happy if the file remains "*.eml*", as long as it can be opened and read as an e-mail (not a text document).

Probably not possible, but I'm hoping anyway.

I still have the question about drag-and-drop as well. If we change over to Ubuntu in future I want to be able to drag an e-mail received from a client into his/her Nautilus client folder and have it end up there as an e-mail message file - not a text file. Any help...?

Thanks

Mike

---

### Post by dcstar on 2005-11-12
[QUOTE=Howzit]Hi there.

I'm new to both Linux & Ubuntu. I'm looking into the possibility of moving our company over to Ubuntu in future (from MS Windows). For that reason I've loaded Ubuntu on one of our machines and am test-driving it in my spare time. I've been trying out Evolution, it seems OK but I'm experiencing problems with two matters.
...........
I've tried dragging e-mails from Evolution's inbox and dropping them in external folders. The action was either refused (no error message) or it was dropped as a text file, with no indication that it should be associated / opened by Evolution. The - file > save as - action seems to have the same effect. I'm sure Evolution must be able to do this, if so pls tell me how?

Thanks - Mike[/QUOTE]
You can "drag and drop" Evolution e-mails into file folders, but the resulting file is the full e-mail with headers etc.

If you want to read them as e-mails, you then have to drag them back into Evolution.

---

### Post by mattotoole on 2005-11-13
[QUOTE=VR6Pete]You will need to import your emails into Mozilla Thunderbird (this will change the formatting to mbox, you will then be able to import these into Evolution.

This tool will help you along with the process:

[http://www.neotek.hu/en/o2e_en.html](http://www.neotek.hu/en/o2e_en.html)

Thanks,

Pete[/QUOTE]

That will work.  

Another approach is to upload your messages into an IMAP account (with Outlook or whatever you were using).  Then just open that account with Evolution, and download/sync as necessary.  For cheap IMAP accounts, try [www.fastmail.com](www.fastmail.com), or [sdf.lonestar.org](sdf.lonestar.org).

--

---

### Post by Howzit on 2005-11-14
*[COLOR="RoyalBlue"]> "Another approach is to upload your messages into an IMAP account (with Outlook or whatever you were using). Then just open that account with Evolution, and download/sync as necessary. For cheap IMAP accounts, try [www.fastmail.com](www.fastmail.com), or sdf.lonestar.org."[/COLOR]*

Thanks Matt... The IMAP server thing is new to me. Used to simply download straight from a pop3 server. It may have interesting applications for our small business. I've tried to follow the links you've provided but can't get through to them at this time. Are you sure about the URL's you've given? I have found an interesting short article on the Ubuntu Wiki (searchind for more info on "IMAP" after you mentioned it). Apparently there is an IMAP server (?) called Dovecot in the Ubuntu repository. If you or anyone else is interested have a look at [https://wiki.ubuntu.com/WhyIMAP?highlight=%28IMAP%29](https://wiki.ubuntu.com/WhyIMAP?highlight=%28IMAP%29). I'm curious wether it is powerful enough to support Evolution's calender functions between various users (or I suppose whether Evolution will allow it to...)?

All of the above has helped my quite a bit, but I suspect it doesn't yet address all of my needs. Any more advice or ideas anyone?

---

### Post by mattotoole on 2005-11-14
[QUOTE=Howzit]*[COLOR="RoyalBlue"][/COLOR]*

Thanks Matt... The IMAP server thing is new to me. Used to simply download straight from a pop3 server. It may have interesting applications for our small business. I've tried to follow the links you've provided but can't get through to them at this time. Are you sure about the URL's you've given? I have found an interesting short article on the Ubuntu Wiki (searchind for more info on "IMAP" after you mentioned it). Apparently there is an IMAP server (?) called Dovecot in the Ubuntu repository. If you or anyone else is interested have a look at [https://wiki.ubuntu.com/WhyIMAP?highlight=%28IMAP%29](https://wiki.ubuntu.com/WhyIMAP?highlight=%28IMAP%29). I'm curious wether it is powerful enough to support Evolution's calender functions between various users (or I suppose whether Evolution will allow it to...)?

All of the above has helped my quite a bit, but I suspect it doesn't yet address all of my needs. Any more advice or ideas anyone?[/QUOTE]

Sorry, the Fastmail address I gave you was incorrect.  Try [www.fastmail.fm](www.fastmail.fm)  They're my main provider, and I've had excellent luck with them.  Note that they offer many other domains besides "fastmail" -- [http://www.fastmail.us/docs/faqparts/General.htm#OtherDomains](http://www.fastmail.us/docs/faqparts/General.htm#OtherDomains)

sdf.lonestar.org definately works, but you may have to hunt around on their site to see how.  It's a public access Unix system, almost free, where you get a shell account, email account, and some web space.  I say "almost free" because there's a one-time fee of $2 or so, which you send in via snailmail.  IME their email system is often slow, and the webmail interface a bit raw.  But it works, and the price is right.  SDF is a great public service -- read the mission statement on their homepage.

I don't see why anyone would use POP if IMAP is available.  Your mail is stored on the server, and can be sync'ed with whatever client machine you wish.  Plus you usually get a webmail interface.  You also have an automatic backup.  You should never have to deal with this transferring of email again, until you switch servers.

--

---

