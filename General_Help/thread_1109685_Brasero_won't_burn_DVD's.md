---
title: "Brasero won't burn DVD's"
date: 2009-03-29
forum: General Help
---

### Post by ramjet_1953 on 2009-03-29
Hi, Guys!

Just recently, I have been having problems with Brasero.

It works flawlessly with CD's, but when I try to copy a DVD, it says that the inserted DVD isn't big enough!.

This is not the case, as I am only trying to copy a standard DVD5 that is not overburnt.

I have tried it on several DVD's with exactly the same result.

I have no problems when using K3b or the Ubuntu built-in copy program.

I have attached a screenshot.

Regards,
Roger :)

---

### Post by DeMus on 2009-03-29
> **ramjet_1953 said:**
> Hi, Guys!

Just recently, I have been having problems with Brasero.

It works flawlessly with CD's, but when I try to copy a DVD, it says that the inserted DVD isn't big enough!.

This is not the case, as I am only trying to copy a standard DVD5 that is not overburnt.

I have tried it on several DVD's with exactly the same result.

I have no problems when using K3b or the Ubuntu built-in copy program.

I have attached a screenshot.

Regards,
Roger :)

The screenshot states you have a blank DVD, but still there are just 0 bytes available. It looks to me Brasero does not read the DVD correctly.
It does this with all kinds of actions, not only the copy action I mean?
An option would be to completely un-install it using Synaptic and then re-install it, but since this kind of answer is not welcome in the forum I will not suggest it.
Do you have one burner in the computer or two? When two, reverse the order and try to burn with the other burner, see how that goes.

I know, this is not a real help, but maybe some things to think about.

---

### Post by ramjet_1953 on 2009-03-29
Thanks for the reply.

Yes, I know that for some reason it Brasero isn't reading the disc capacity correctly.

I only have one internal CD-RW/DVD Reader and an external LG Super Multi Drive.

I have exactly the same problem using either USB or FireWire interfaces to the LG external drive.

The problem is definitely with Brasero, as burning is not a problem with other packages.

As I said in my original post, Brasero works perfectly with CD's.

Regards,
Roger

---

### Post by DeMus on 2009-03-29
> **ramjet_1953 said:**
> Thanks for the reply.

Yes, I know that for some reason it Brasero isn't reading the disc capacity correctly.

I only have one internal CD-RW/DVD Reader and an external LG Super Multi Drive.

I have exactly the same problem using either USB or FireWire interfaces to the LG external drive.

The problem is definitely with Brasero, as burning is not a problem with other packages.

As I said in my original post, Brasero works perfectly with CD's.

Regards,
Roger

Then maybe the idea of re-installing Brasero does not sound so bad, does it? Just make sure you delete everything related to Brasero after uninstalling it and before reinstalling it. In Synaptic choose Mark for Complete Removal. Then in Nautilus search for Brasero and delete all files and folders still present.
I hope this helps.

---

### Post by ramjet_1953 on 2009-03-29
Been there -done that.

I even downloaded the latest version, compiled it and created a .deb package.

Still no joy.

Regards,
Roger :)

---

### Post by DeMus on 2009-03-29
> **ramjet_1953 said:**
> Been there -done that.

I even downloaded the latest version, compiled it and created a .deb package.

Still no joy.

Regards,
Roger :)

I hope somebody else will pick up this thread and will give you an answer which helps. I can't, I'm sorry.
Good luck.

ps: I was just looking in Brasero to find some settings which could be wrong (didn't find any settings at all) but I did find something strange:
Yesterday I burnt a few .ISO files to DVD with Linux-Nero and now these files are mentioned in Brasero as recent projects. Is Brasero used when I use Nero to burn a DVD? Is Nero just a shell around the burning part of Brasero? Does that mean when I uninstall Brasero, Nero won't work anymore? Very strange.

---

### Post by zanoza on 2010-03-18
Shalom to All.
I'm new here, and in Ubuntu too, but my mind in yours Brasero problem it's a right permissions for burning and temp folder using. try to use your own temp folder let's say /home/username/tmp or open Brasero as root : $ sudo brasero

I think it's help you.

---

