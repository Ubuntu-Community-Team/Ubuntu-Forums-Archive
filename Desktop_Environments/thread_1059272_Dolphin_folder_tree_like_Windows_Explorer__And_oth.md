---
title: "Dolphin folder tree like Windows Explorer ? And other questions."
date: 2009-02-03
forum: Desktop Environments
---

### Post by dargaud on 2009-02-03
Hello all,
My Windows system disk died yesterday and that was the opportunity I was waiting for to jump ship to Ubuntu... I already know Linux pretty well from the inside (I write device drivers and build embedded Linux distros at work), but it's the first time I actually try it on my main desktop, so I need a bit of help.
Everything works so far (except my ntfs truecrypt drive, and my DS-240WB screen, and my wireless...), but I'm annoyed by the file manager...

So with Dolphin I figured out how to get a folder tree in one panel and file+folder view in the other, similar to Windows explorer... but I can't do much on the tree (I can't select a folder and delete it, only view it), and I can't double click a folder on the right to view it. Why the difference in behavior ?

Side question, how do I import my wab (Windows Address Book) file in Kmail ? Or do I need to use a different contact manager like KaddressBook ? Anyway, in the imports there's nothing about wab format.

One more: what's the keyboard shortcut to switch desktop ? Is there a global list of KDE shortcut keys ? Are the [Win] and [Menu] keys used for anything ? In particular it would be nice to have the latter operate as a right-click alternative on selected item(s).

Thanks !

---

### Post by lykwydchykyn on 2009-02-03
> **dargaud said:**
> Hello all,
My Windows system disk died yesterday and that was the opportunity I was waiting for to jump ship to Ubuntu... I already know Linux pretty well from the inside (I write device drivers and build embedded Linux distros at work), but it's the first time I actually try it on my main desktop, so I need a bit of help.

Welcome and good luck with the transition.  
> 
Everything works so far (except my ntfs truecrypt drive, and my DS-240WB screen, and my wireless...), but I'm annoyed by the file manager...

You wouldn't be the first KDE user annoyed with Dolphin, though it's getting better.  You might want to try Konqueror, which used to be the file manager in KDE3.  It's not as good in KDE4, but it's another option to Dolphin.
> 
So with Dolphin I figured out how to get a folder tree in one panel and file+folder view in the other, similar to Windows explorer... but I can't do much on the tree (I can't select a folder and delete it, only view it), and I can't double click a folder on the right to view it. Why the difference in behavior ?

In KDE 4.2 I can do what you're describing, but not by splitting the window.  I go to "view=>panels" and select "folders". You might want to update to v 4.2 (instructions can be found on the Kubuntu website here: [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)) as most people regard it to be a major feature fix of kde 4.1.

Also, I believe by default KDE does only single-click, but you can configure it to use double-click instead.  Check the "keyboard and mouse" config in the settings tool.
> 
Side question, how do I import my wab (Windows Address Book) file in Kmail ? Or do I need to use a different contact manager like KaddressBook ? Anyway, in the imports there's nothing about wab format.

Not sure about that one; KaddressBook is integrated with Kmail, if I'm not mistaken.   You can also use Thunderbird in KDE, which is what I do.
> 
One more: what's the keyboard shortcut to switch desktop ? 

ctrl-F1 will take you to your first desktop, ctrl-f2 to your second, etc.
> 
Is there a global list of KDE shortcut keys ? 

Don't know about a list, but you can configure them in the settings tool, under "keyboard shortcuts".
> 
Are the [Win] and [Menu] keys used for anything ? In particular it would be nice to have the latter operate as a right-click alternative on selected item(s).

To my knowledge [win] does nothing by default, but that's good because it makes it useful for custom keyboard shortcuts.  On my machine [menu] brings up a context menu, but that may be because I'm on 4.2.

---

### Post by dargaud on 2009-02-04
Thanks for the answers. Here's another question: I have a wide screen, so I preffer to have the KDE bar (ribbon ? whatever its called) placed vertically on the side... but it's too narrow and I can't figure out how to enlarge it. I can't see the names of the running apps.

---

### Post by lykwydchykyn on 2009-02-04
Using the "cashew" up top, unlock widgets.  You'll notice another "cashew" appears on the panel.  Click on it.  Another thing pops out of the panel and allows you to resize.

---

### Post by dargaud on 2009-02-05
Thank you, that worked (I didn't see that I need to drag the 'thing' itself instead of the ribbon).

---

### Post by dargaud on 2009-02-07
I'm used to Truecrypt on Windows, and I see it works the same on Ubuntu. But are there alternatives ? In particular I see the 'encryption' option to the mount/fstab command. How does that work ?

I've been using Outlook Express for 15 years, so converting to Kmail is a bit traumatic. I still have no idea how the 'mailing list management' is supposed to work; is it a type of 'meta' filter rule ?
Also, how do I see images attached to messages without having to click on every single one of them, OK, Esc...?
How can I display a single message in HTML, without going through all the options to change Text/Html for all ?

Another thing, how come the Open/Save popup windows are completely different from one app to another ? [I guess the answer is some are KDE, some are gnome, etc] Is there a way to switch between type or enforce a common type ? Or to use image thumbnails when the option is not present ? Or to change the sort order of the files when not available ?

---

### Post by lykwydchykyn on 2009-02-09
> **dargaud said:**
> I'm used to Truecrypt on Windows, and I see it works the same on Ubuntu. But are there alternatives ? In particular I see the 'encryption' option to the mount/fstab command. How does that work ?

No idea, really.
> 
I've been using Outlook Express for 15 years, so converting to Kmail is a bit traumatic. I still have no idea how the 'mailing list management' is supposed to work; is it a type of 'meta' filter rule ?

For mailing lists, I just right-click on an email and go to the "filter on" menu, and select "filter on mailing list (list name)".  Then you can create a separate folder to chuck them into.
> 
Also, how do I see images attached to messages without having to click on every single one of them, OK, Esc...?
How can I display a single message in HTML, without going through all the options to change Text/Html for all ?

Kmail is weird about that.  It's why I generally use thunderbird (I use kmail at work, thunderbird at home; don't ask why).  The kmail authors don't seem to be keen on html email and don't accomodate it well.

You might want to try thunderbird if you're frustrated with kmail.
> 
Another thing, how come the Open/Save popup windows are completely different from one app to another ? [I guess the answer is some are KDE, some are gnome, etc] Is there a way to switch between type or enforce a common type ? Or to use image thumbnails when the option is not present ? Or to change the sort order of the files when not available ?
Basically, dialogs like that are built in to whatever graphics toolkit you write a program with; if you use GTK, you'll get those Gnome dialogs.  If you use QT, you'll get the KDE dialogs (yes, I'm massively glossing over the details there).  Some programs can be tweaked to change the dialogs, and some have extra "integration" packages you can install to change those dialogs, but mostly you're stuck with whatever the program has built in.  

If there are hacks to get around them, it's usually program-specific.

---

### Post by Monsieur Gonzalez on 2009-02-10
If you have not already, upgrade to 4.2. Great improvements on every area, including Kmail. 

Regarding the HTML formating for messages, you can globally turn it on in Kmail options (it's disabled for safety reasons), or just go the the message with the attachments and then, from the menu, View, Attachments, Inline. 

Also, though I've not tested it, there's is a message import wizard for many mail clients, including Outlook Express.

As for the file dialogs, I think Kde's are way better, but that's just my opinion.

---

