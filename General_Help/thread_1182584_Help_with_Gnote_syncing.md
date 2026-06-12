---
title: "Help with Gnote syncing"
date: 2009-06-09
forum: General Help
---

### Post by bogoliubov on 2009-06-09
Hello. I use Tomboy a lot on several machines and sync my notes through "local sync" + unison. I would like to replace Tomboy with Gnote, but I can't get the syncing to work in Gnote. 

In Gnote Preferences, I don't even have a tab for synchronization settings. However, in gconf-editor, I see settings for syncing and tried to set it up there. But it did not work. It seems nothing happens when I press sync...


I have Gnote version 0.4.0 installed on my machines, all running 9.04 (two of which x86-64 and one lpia)...

---

### Post by justleen on 2009-06-09
From [http://live.gnome.org/Gnote](http://live.gnome.org/Gnote) :
>  Synchronization support is being worked on. 

---

### Post by bogoliubov on 2009-06-09
> **justleen said:**
> From [http://live.gnome.org/Gnote](http://live.gnome.org/Gnote) :

Ok, I guess I'll have to wait a bit then..

Thanks!

---

### Post by Oropher8598 on 2009-10-28
You could always set up *de facto* syncing by moving Gnote's settings into your Ubuntu One folder.

[list]
[*]Go to your home folder and find the '.gnote' folder
[*]Drag and drop this into Ubuntu One
[*]Right-click on the .gnote folder and select 'Make link'
[*]Drag the link it makes back to your home folder and rename it '.gnote'.
[/list]

---

### Post by mantaraya36 on 2009-11-04
That is an excellent trick that will work for most anything. Thanks for the idea.

Cheers,
Andres

---

### Post by cavh on 2010-01-14
+1 for the 'make link' process. Thanks Oropher8598!:)

---

### Post by mememe on 2010-01-21
I am just curious:
what happens if I want to make a note while offline? (with the link to Ubuntu One). I was thinking of doing the same thing with Pidgin's .purple folder, but mostly because I run Pidgin only while online...

---

### Post by xoan on 2010-01-21
All data in "~/Ubuntu One" folder is synced between your computer and [http://ubuntuone.com/](http://ubuntuone.com/) service. This means that there is always a copy in your computer and a copy in ubuntuone. When you are offline, you can make any change in your "~/Ubuntu One" folder, and the next time you go online, this changes are synced to ubuntuone service.

---

### Post by Knatchwa on 2010-02-08
Yes that worked spectacularly well, thanks for the tip, now if only could get Tomboy working again, as after the update it broke as mentioned @ [http://ubuntuforums.org/showthread.php?t=1396901](http://ubuntuforums.org/showthread.php?t=1396901) that has people more then a bit frustrated with v 1.1.1 of Tomboy that after the update recently crashed and is non op for the moment. 

Fortunately I had used Conduit Synchronizer which can be found via Synaptic, that enabled me to have semi recent notes before Tomboy crashed out, synced to the Memo's in Evolution thereby enabling me to either sync those notes to a folder and do some copy and pasting or just update those that are in Evolution.

---

### Post by bogoliubov on 2010-03-04
I'd like to point out that I've switched completely to Zim ( [http://zim-wiki.org/](http://zim-wiki.org/) ) which I think is much better. It's a little more advanced than Tomboy/Gnote but has more features. It can also sync, but I do it from it's built-in version control (subversion).
I suggest you all to have a look at it, because I'm very happy with it.

---

### Post by kokoshmusun on 2011-01-13
How do you synch with Zim wiki?  Can you explain?

---

### Post by bogoliubov on 2011-02-04
I have my Zim notebooks in my Dropbox folder, so they are all synced automatically between my computers.

Also, the Zim notebooks are stored as text files, so they can be edited without the Zim application if needed.

---

### Post by hemebond on 2011-10-06
> **Oropher8598 said:**
> You could always set up *de facto* syncing by moving Gnote's settings into your Ubuntu One folder.

[list]
[*]Go to your home folder and find the '.gnote' folder
[*]Drag and drop this into Ubuntu One
[*]Right-click on the .gnote folder and select 'Make link'
[*]Drag the link it makes back to your home folder and rename it '.gnote'.
[/list]

Please note, everyone who finds this thread, that Gnote notes are no longer in ~/.gnote, even though that directory still exists. The new directory, on Ubuntu and Debian at least, is in ~/.local/share/gnote.

Be sure you are backing up/syncing the correct directory.

---

### Post by XianToa on 2011-12-08
The nice thing about Gnote is that its lightweight. I use Ubuntu on a lame-top computer with crappy specs. The point of a notes app is to be so simple that its like taking notes in a terminal.

I've found that syncing through Ubuntu One (thank you hemebond and Oropher8598) shaves a little bit off my task load.

---

