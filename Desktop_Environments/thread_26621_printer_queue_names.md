---
title: "printer queue names?"
date: 2005-04-13
forum: Desktop Environments
---

### Post by stefankluth on 2005-04-13
Hi,

I have successfully set up a remote unix network printer using the gnome printer config tool.  I only half an hour or so to find out that in /etc/cups/cupsd.conf the following change is needed:

# RunAsUser Yes
RunAsUser No

However, I can't seem to find a way to give the cups printer queues corresponding to the remote printer the names I like.  I always get the name of the printer driver I chose, e.g. "LaserJet-4200".  I would prefer to give it another name which e.g. tells me it is the printer on the 2nd floor in room 101 (I am in a large institute).

What happens when I have the same printer model in two different places on the nertwork and I want use them both?

Can somebody help me?

Cheers, Stefan

---

### Post by shakin on 2005-04-13
Is this the LPD queue name? I setup my network printer using kcontrol and it had a text box where I typed the queue name. You could give it a try.

I don't know anything about setting up printers so I may be looking in the wrong place, but in my /etc/cups/printers.conf file I have a line for the printer like this:

lpd://0.0.0.0/[queue name]

Try editing your printers.conf file similarly.

---

### Post by stefankluth on 2005-04-15
[QUOTE=shakin]Is this the LPD queue name? I setup my network printer using kcontrol and it had a text box where I typed the queue name. You could give it a try.

I don't know anything about setting up printers so I may be looking in the wrong place, but in my /etc/cups/printers.conf file I have a line for the printer like this:

lpd://0.0.0.0/[queue name]

Try editing your printers.conf file similarly.[/QUOTE]

aha, hadn't thought of kcontrol ... that has a "k" in its name though and is not in the standard menues ... I know I could also turn on the cups web interface and do what I like there.  I think I am complaining about a limitation in the gnome printer configuration tool.  Thanks anyway for your hint.

Cheers, Stefab

---

### Post by Alexander Kirillov on 2005-04-15
> I think I am complaining about a limitation in the gnome printer configuration tool
In fact, I was about to complain about the same thing. Especially since some older/stupider programs (like Acrobat Reader) require you to manually enter print command of the form lp -Pprintername - and entering something like LaserJet-4050 makes it easy to make a typo...

We should probably file a bug (request for enhancement) in bugzilla....

---

