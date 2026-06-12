---
title: "root problem"
date: 2009-03-12
forum: General Help
---

### Post by TwistedNail on 2009-03-12
Hi!
I have kinda' serious problem, that I can't get done with...
After I changed permissions for my profile, so I can play one game, who needs to download files in folders, where normal user can't do anything, after a while I got an error when I log in as root.. Because of that error I can't go in to many programs and all folders... 
Error log:
[http://i207.photobucket.com/albums/bb46/Twisted_Nail_photo/Screenshot.png](http://i207.photobucket.com/albums/bb46/Twisted_Nail_photo/Screenshot.png)

I hope, that someone of You knows the reason and solution for this problem, because I realy need to go in some folders through root...

---

### Post by Neo_The_User on 2009-03-12
Terminal:

```

gksudo nautilus

```

---

### Post by TwistedNail on 2009-03-12
> **Neo_The_User said:**
> Terminal:

```

gksudo nautilus

```

In root's terminal?

---

### Post by bodhi.zazen on 2009-03-12
I do not know the solution other then changing the permissions back.

Depending on what you changed, mind you, that may mean re-installation.

As you can see , changing permissions or ownership on system files as a short cut to learning about Linux permissions is not a good idea and as in your case most often results in breakage and re-installation.

See :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

and

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

This thread is a prime example of why we ask community members to teach these things rather the spewing information like "set a root password" and "gksu nautilus". We have a lot of new users who do not know how to use these tools yet and omissions of information result  in breakage.

/end rant

I hope you are able to fix it easily without re-installing.

---

### Post by TwistedNail on 2009-03-12
I don't think I could fix it without re-instaling...

Ok, here's a new question - can I re-install my system without loosing my files?

---

### Post by heindsight on 2009-03-12
The error message in that screenshot has nothing to do with permissions. Those are errors in your gconf database.

Open the gconf configuration editor, either by going to Applications>System Tools>Configuration Editor, or by running:
```
gconf-editor
```
in a terminal.

Then, in the left-hand pane of the Configuration Editor window, navigate to apps/nautilus/desktop. In the right-hand pane, you should then see an entry for computer_icon_name, right click that, click "Edit Key..." In the dialog that appears change the Type to String, click OK and close the Configuration Editor window.

---

### Post by TwistedNail on 2009-03-12
Problem solved, thanks to heindsight :)

---

