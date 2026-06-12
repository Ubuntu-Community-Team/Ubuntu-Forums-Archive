---
title: "importing .dbx mail files from outlook express"
date: 2005-06-23
forum: Desktop Environments
---

### Post by dworzec.net on 2005-06-23
Outlook express keeps mail in large dbx files. My Windows is permanently broken and I can't export outlook mail to eml files - I have only huge dbx files and no access to outlook. Does anybody know how to import those files to any linux mail client? Is it possible?
thanks in advance

---

### Post by Dave_is_sexy on 2005-06-23
Ah there are many ways. Most suck. 

**OPTION 1**

But there is one good way which requires a windows thunderbird instalation.

If you can get that, just use it to import your outlook express mail (it's fully automatic) and then copy your windows thunderbird profile folder over the top of your linux one.

**OPTION 2**

Kmail can import from outlook express. So apt-git install kmail and then export them from their to the client of your choice. Although i think kmail's alright actually, but not the best thing to run in gnome. Maybe Evolution or Thunderbird

Dave

---

### Post by dworzec.net on 2005-06-23
well, option 1 makes little sense - if I had windows thunderbird, I could have outlook as well
but option 2 looks perfect as I have both Gnome and Kubuntu so I'll try it in a minute
thnx.

---

### Post by bdamon on 2005-06-23
I used a utility called dbxconv. This will take a Outlook Express dbx file and convert it to standard mbox format. Worked like a charm for me.

[http://people.freenet.de/ukrebs/dbxconv.html](http://people.freenet.de/ukrebs/dbxconv.html)


Ben

---

### Post by agger on 2005-09-05
[QUOTE=bdamon]I used a utility called dbxconv. This will take a Outlook Express dbx file and convert it to standard mbox format. Worked like a charm for me.

[http://people.freenet.de/ukrebs/dbxconv.html](http://people.freenet.de/ukrebs/dbxconv.html)


Ben[/QUOTE]

Only it doesn't run under Linux and I can't get it spinning with wine - I think I'll go for KMail ...

---

### Post by agger on 2005-09-06
[QUOTE=agger]Only it doesn't run under Linux and I can't get it spinning with wine - I think I'll go for KMail ...[/QUOTE]
 KMail didn't do the job, which may be because I'm not using Kubuntu nor do I have KDE installed. 

Anyway, kmail launched OK, but the "Import" command was dimmed.
So right now it seems the only way to go if you want to import .dbx files is
to to use a tool like dbxconv on windows and then move the files to Ubuntu
afterwards.

---

### Post by airjunman on 2006-07-08
this works under Linux ...its KMail itself along with a plugin called KMail CVT to import dbx files... try to work it this way:
[http://www.ubuntuforums.org/showthread.php?t=210638](http://www.ubuntuforums.org/showthread.php?t=210638)

---

### Post by agger on 2007-06-19
> **agger said:**
> KMail didn't do the job, which may be because I'm not using Kubuntu nor do I have KDE installed. 

Anyway, kmail launched OK, but the "Import" command was dimmed.
So right now it seems the only way to go if you want to import .dbx files is
to to use a tool like dbxconv on windows and then move the files to Ubuntu
afterwards.

Actually, I ended up using dbxconv and copying the files from NTFS to the Linux file system afterwards. It also makes sense, in a way, to use a few free Windows programs as part of the migration that allows you to finally kiss Bill Gates goodbye :-)

---

