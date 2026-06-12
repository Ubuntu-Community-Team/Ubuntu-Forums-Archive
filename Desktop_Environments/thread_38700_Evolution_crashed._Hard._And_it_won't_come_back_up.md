---
title: "Evolution crashed. Hard. And it won't come back up"
date: 2005-06-01
forum: Desktop Environments
---

### Post by pdpi on 2005-06-01
Like the subject line says. When I highlighted an email I received (a forward of a plain-text business email), evolution crashed. Any attempts to bring it back up have failed thus far. Help? Ideas?

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=pdpi]Like the subject line says. When I highlighted an email I received (a forward of a plain-text business email), evolution crashed. Any attempts to bring it back up have failed thus far. Help? Ideas?[/QUOTE]
 Open system monitor (from system tools menu, IIRC) and kill all remaining "evolution-..." processes. 
Now start evolution again. Does it work?

If not, try logging out and logging back in.

---

### Post by pdpi on 2005-06-01
[QUOTE=Alexander Kirillov]Open system monitor (from system tools menu, IIRC) and kill all remaining "evolution-..." processes. 
Now start evolution again. Does it work?

If not, try logging out and logging back in.[/QUOTE]
 Thanks for the quick reply (as good as it did me, as I wasn't here to see it, lol). Tried a full reboot, to no avail. Any ideas?

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=pdpi]Thanks for the quick reply (as good as it did me, as I wasn't here to see it, lol). Tried a full reboot, to no avail. Any ideas?[/QUOTE]
 If you start it form the command line, does it produce any error messages?

---

### Post by pdpi on 2005-06-01
```

(evolution:11901): camel-WARNING **: Invalid root: '/home/pdpi/.evolution/mail/local/Drafts.ibex.index'

(evolution:11901): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:11901): camel-WARNING **: block size: 1024 (1024) OK

(evolution:11901): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:11901): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution:11901): camel-WARNING **: flags: unSYNC
update flow align

```

So no errors, only warnings.

EDIT:
I wasn't quite as explicit as I should've been. Evolution opens, I can clearly see the whole window, email lists, the works. It just comes crashing down imediately after. The feeling I get is that it crashes when attempting to render the last selected email

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=pdpi]```

(evolution:11901): camel-WARNING **: Invalid root: '/home/pdpi/.evolution/mail/local/Drafts.ibex.index'

(evolution:11901): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:11901): camel-WARNING **: block size: 1024 (1024) OK

(evolution:11901): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:11901): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution:11901): camel-WARNING **: flags: unSYNC
update flow align

```

So no errors, only warnings.

EDIT:
I wasn't quite as explicit as I should've been. Evolution opens, I can clearly see the whole window, email lists, the works. It just comes crashing down imediately after. The feeling I get is that it crashes when attempting to render the last selected email[/QUOTE]
 What I would try  (after backing up the whole .evolution directory)  is removing 
.evolution/mail/local/Drafts.*
- as there was a warning related to it

This way, you lose your drafts - but I do not think it is a big loss.

---

### Post by pdpi on 2005-06-01
I did it, thanks. Your solution didn't directly work, but it inspired me to delete the files relative to the affected mail box from $HOME/.evolution/mail/local/Inbox.sbd -- since I only had 2 or 3 mails there, and unimportant at that, it didn't bother me much

---

### Post by Gnobian_Ken00bie on 2005-06-03
I had the exact same problem yesterday on a machine I help to maintain. Was there no more to the error message? Something about a windows charset masquerading as ISO-8859-1? And do you receive mail from a large American vendor of office supplies? An e-mail from them caused the problem in my case.

I didn't need to delete the local folder. I only deleted the file ~/.evolution/mail/local/Inbox.cmeta

What this does is prevents Evolution from opening the same mail it had open when it crashed. 

Is there another way to do this? It's one of the few things that that mail reader used in that so-called operating system does right: not opening mail if the program had previously crashed.

Anyway, now that you can start evolution, do NOT open any e-mails UNTIL you do to Edit>Preferences>Mail Preferences>HTML Mail and then select Only Ever Show Plain under HTML Mode.

This will prevent the improperly rendered HTML from crashing Evolution when it's opened and allow you do delete it.

Two questions:

As previously asked, is there another way to prevent Evo from opening the last opened e-mail?

And

Is there a way to delete an e-mail without it being accessed by the rendering engine, short of switching HTML off? Right-clicking still caused a crash, forcing me to delete Inbox.cmeta again.

I'm still very much a newbie, so take this with a grain of salt. I hope someone more knowledgeable will chime in.

---

### Post by Gnobian_Ken00bie on 2005-06-03
My apologies for not having read your initial post more closely. If this was a plain text e-mail, my suggestion may not have helped. (Although often people still use HTML for mails with nothing but text in them.) 

But the point about Inbox.cmeta may still be useful for future reference.

And i'd definitely appreciate any feedback anyone might have to offer concerning my follow-up questions.

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=Gnobian_Ken00bie]I had the exact same problem yesterday on a machine I help to maintain. Was there no more to the error message? Something about a windows charset masquerading as ISO-8859-1? And do you receive mail from a large American vendor of office supplies? An e-mail from them caused the problem in my case.

I didn't need to delete the local folder. I only deleted the file ~/.evolution/mail/local/Inbox.cmeta

What this does is prevents Evolution from opening the same mail it had open when it crashed. 

Is there another way to do this? It's one of the few things that that mail reader used in that so-called operating system does right: not opening mail if the program had previously crashed.

Anyway, now that you can start evolution, do NOT open any e-mails UNTIL you do to Edit>Preferences>Mail Preferences>HTML Mail and then select Only Ever Show Plain under HTML Mode.

This will prevent the improperly rendered HTML from crashing Evolution when it's opened and allow you do delete it.

Two questions:

As previously asked, is there another way to prevent Evo from opening the last opened e-mail?

And

Is there a way to delete an e-mail without it being accessed by the rendering engine, short of switching HTML off? Right-clicking still caused a crash, forcing me to delete Inbox.cmeta again.

I'm still very much a newbie, so take this with a grain of salt. I hope someone more knowledgeable will chime in.[/QUOTE]
 Sorry that I can not help here - but have you tried searching evolution bug database at 
[http://bugzilla.ximian.com/](http://bugzilla.ximian.com/) ?
If this bug is not there, it needs to be filed. Please do it - this is the only way developers (and not just users like us) become aware of the problem...

---

### Post by Gnobian_Ken00bie on 2005-06-03
Thank you for the encouragement. I had intended to file a bug. (Though until getting your link, I'd only checked Ubuntu's bug database. It's not at Ximian either.) But I wanted first to get some feedback from more knowledgeable posters to see if there's anything I may be misunderstanding. tentatively, I'm considering three bugs to report:

1. HTML mail that has been tagged as  ISO-8859-1 but uses the Windows charset causes Evo to crash with a segmentation fault. 

(This is the one I'm least sure about. I only know that it didn't crash when the mail was viewed as plaintext and that the console has something about Windows charset masquerading as ISO-8859-1. I'll see what logs I can find.)

2. When Evolution crashes after opening an e-mail, it again tries to reopen the mail each time it is started. 

(Deleting a .cmeta file is a workaround, but certainly not ideal. But maybe there's a commandline option or a setting i don't know about.)

3. Right-clicking on an e-mail to delete it without opening it still seems to be trying to access it, causing a crash before it can be deleted.



Do these sound like the appropriate bugs to file?

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=Gnobian_Ken00bie]Thank you for the encouragement. I had intended to file a bug. (Though until getting your link, I'd only checked Ubuntu's bug database. It's not at Ximian either.) But I wanted first to get some feedback from more knowledgeable posters to see if there's anything I may be misunderstanding. tentatively, I'm considering three bugs to report:

1. HTML mail that has been tagged as  ISO-8859-1 but uses the Windows charset causes Evo to crash with a segmentation fault. 

(This is the one I'm least sure about. I only know that it didn't crash when the mail was viewed as plaintext and that the console has something about Windows charset masquerading as ISO-8859-1. I'll see what logs I can find.)

2. When Evolution crashes after opening an e-mail, it again tries to reopen the mail each time it is started. 

(Deleting a .cmeta file is a workaround, but certainly not ideal. But maybe there's a commandline option or a setting i don't know about.)

3. Right-clicking on an e-mail to delete it without opening it still seems to be trying to access it, causing a crash before it can be deleted.



Do these sound like the appropriate bugs to file?[/QUOTE]
 I'd group bugs 1 and 3. Other than that, seems reasonable (I am not a devleoper - they will tell you if they need more). Just do not forget to attach the  problematic email (try opening it in mutt or some other email program and saving to file), and maybe give a link to this thread. They also need to knwo whether you used IMAP, POP, local mailbox,...

BTW: evolution bugs have been moved to bugzilla.gnome.org - just found this out.

---

### Post by Gnobian_Ken00bie on 2005-06-03
I'd noticed that about Evo bugs, yes. Thank you. 

A question though. it was my understanding - though it was some time ago in passing on a Debian list - that it was recommended that bugs be filed with the distribution and they decide whether to forward it upstream, in case it's a problem unique to the distro's build. Is Ubuntu's policy different? Perhaps because so many GNOME developers work on the project? I just want to be sure about the ettiquette here, if you or anyone else can help.

Meanwhile, i believe I still have the backed up ~/.evolution folder, so I can try to extract that e-mail but also reconstruct the problem and perhaps get some debugging output. I don't think I'll need to use mutt if i just switch HTML off. or, if you save a message that you opened as plaintext, does it save as the original HTML?

Thank you again for your help.

---

### Post by Gnobian_Ken00bie on 2005-06-03
Oh, follow-up. the reason i made 3 separate is that it seems to me this is a more general problem where any number of problems with an e-mail could be exacerbated by the inability to delete an e-mail without it being accessed somehow. but i don't know exactly what's accessing what, so it's just a guess.

---

### Post by Alexander Kirillov on 2005-06-04
[QUOTE=Gnobian_Ken00bie]I'd noticed that about Evo bugs, yes. Thank you. 

A question though. it was my understanding - though it was some time ago in passing on a Debian list - that it was recommended that bugs be filed with the distribution and they decide whether to forward it upstream, in case it's a problem unique to the distro's build. Is Ubuntu's policy different? Perhaps because so many GNOME developers work on the project? I just want to be sure about the ettiquette here, if you or anyone else can help.
[/QUOTE]
Honestly, I do not know. I was filing GNOME bugs long before Ubuntu came to existence. My general rule is: I file in Ubuntu bugzilla bugs that are Ubuntu-specific (e.g., the way startup services are configured) and everything else I try to file upstream - this way, it will be immediately seen by the right people. On the other ahnd, it keeps Ubuntu developers out of the loop. These are just my rules, I do not think I have seen recommendations on this  - if you find one, let me know. 

> 
Meanwhile, i believe I still have the backed up ~/.evolution folder, so I can try to extract that e-mail but also reconstruct the problem and perhaps get some debugging output. I don't think I'll need to use mutt if i just switch HTML off. or, if you save a message that you opened as plaintext, does it save as the original HTML?

Thank you again for your help.
AFAIK, "Save As" option in Evolution saves the "email source" - i.e., the message as it came, with all the headers, multipart boundaries, etc - including HTML part if there is one.

---

### Post by kosmic on 2005-06-24
I had the same problem with one computer with evolution im my office, thanks for the help, about removing Inbox.cmeta

---

