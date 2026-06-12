---
title: "import contacts from outlook into evolution?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by mandt on 2006-10-06
Hi knowledgable ubuntu users!
Quick question for you, how can I import all my contacts into Evolution from Outlook 2003?
Thanks
Steve

---

### Post by jonnymccullagh on 2006-10-06
I remember reading about this some time back to import emails into Evolution and I think the advice at that time for contacts was exporting from outlook as CSV. I'm not sure if it will work but it might be worth a try.
Another solution I read involved importing into another email program before importing into Evolution. I think the email program I read about then was the Netscape/Mozilla one (i think it was called SeaMonkey or something like that).
I haven't tried any of this but just offering some ideas.
jonny

---

### Post by Yeti can't ski on 2008-04-18
Hey Guys, I tried all sorts of ".CSV" imports from Outlook and nothing really worked. The information was there, but Evolution would never pick the right format (for instance, the e-mail would be in the "name" field). 

The first breakthrough was to notice that Evolution imports properly ".VCF" files or vcards. I still had the problem of exporting vcards from Outlook 2003 - which doesn't seem to allow the export of a single file with a consolidated vcards address book (and hundreds of individual files are just a nightmare). 

In several forums I read the suggestion of first installing Mozilla in the Windows system to do a conversion of the “.CSV” file, but that seemed too troublesome. Indeed, Gmail will easily do the same trick.

- Export your contacts from Outlook to as a regular ".CSV" file;
- Import those contacts into Gmail (in webmail mode);
- Export from Gmail to a ".VCF" file; and finally
- Import ".VCF" file to Evolution. 

The "bonus" is that Gmail will automatically cancel doubled/repeated entries. Really great. I hope someday Evolution will do all that by itself.

Good luck.

---

### Post by Nilleb on 2008-05-11
Hey, I have had same problem when I installed Ubuntu 7.10 some months ago.
I found a solution in:
(I am sorry to say that I don have the intact adres but...)

Ubuntu Forums>The Ubuntu Forum Community>Absolute Beginner Talk

"How do I import email from Outlook to Evolution?"

February 28th, 2007 muguwmp67
"I also had a huge outlook mailbox with lots of directory nesting. Thunderbird chrashed each time it tried to read it. I ended up importing it into outlook express. Then I installed thunderbird in windows and imported from outlook express to thunderbird.

I have my windows partition mounted, so I could find:"

(the path to Thunderbird email folder)

On my PC:
I managed to export directly from Outlook to Thunderbird (had no "huge" email;-)
C:\Documents and Settings\Owner\Application Data\Thunderbird\Profiles\cdakprro.default\Mail\Local Folders\Outlook e-post.sbd

muguwmp67 again:
Copy the entire content of the folder containing the .sbd file to:

/home/usr/.evolution/mail/local

Select Your own "usr" folder.

I opened evolution and the folder was displayed with all of the nesting intact. All of the messages were marked unread, but this can be fixed by right clicking the folder in Evolution and selecting "mark read".

This was a great help for me and a lot of guys in the forum!

Thanks muguwmp67!!!

But don do as I did, exported several versions of my email in Outlook to Evolution. It caused me a lot of tiding up in Evolution :)
Clean the emails up and get rid of old garbage before You export from 
Outlook!

---

### Post by markyb on 2008-05-13
Another option is to use [outport]("http://outport.sourceforge.net/index.php").  This will export the contacts, calender and tasks into ics files which can then just be simply moved into the evolution file structure.  Then just start evolution and there they are.

---

