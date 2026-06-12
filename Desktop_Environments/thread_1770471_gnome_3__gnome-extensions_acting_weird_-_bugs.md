---
title: "gnome 3 : gnome-extensions acting weird - bugs"
date: 2011-05-29
forum: Desktop Environments
---

### Post by maizuddin35 on 2011-05-29
Hello everyone. 

I have a little bit problem with my gnome-extensions , I'm using gnome 3. 

please see the image  below, the first image is when after I **Alt+F2 and r**
and after that, when I click/or put my mouse cursor at the activities to show up the menu and return back to the desktop/normal view , it changes like the second image below(sorry for my english) 
[IMG]http://i.imgur.com/X43Bb.jpg[/IMG]

and here is the bug/error I encounter.

[IMG]http://i.imgur.com/X69mw.png[/IMG]

the extension version before was 3.0.1 and I already change the version to 3.0.2.

and I already **sudo apt-get update && sudo apt-get upgrade , **everything..

anyone please?thanks in advance.

by the way, I used ubuntu 11.04

---

### Post by maverick280857 on 2011-05-29
Can you highlight the difference between the two images..I mean the part that seems troubling. I see that the menu on the right hand side loses its black background.

What are the permissions of the extension files and folders in /usr/share/gnome-shell/extensions? Try copying the extensions to $HOME/.local/share/gnome-shell/extensions. If you move them, then you won't get 'already loaded' errors from lg, which you can safely ignore.

Alt+F2 and r is one way to restart the gnome-shell, and it seems to work for most people, but it also causes the shell to crash sometimes when I install a new extension.

According to looking glass, the extensions you've installed are incompatible with the shell. Which version of the shell do you have? Try modifying metadata.json to reflect the version '3.0'.

This could be due to some random update which could've messed up things, as they're all in a state of flux.

Did you install gnome-shell using the instructions posted here: [http://ubuntuforums.org/showpost.php?p=10734567&postcount=1?](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1?) If not, do so. I could only get it to work after using this PPA, not some of the other sources I found on the net (which seemed to work for other people).

---

### Post by maizuddin35 on 2011-05-29
yes I did install gnome-shell based on that given link . 
this is the things that changes : dock , system-monitor,  workspace-indicator, and I think some other stuffs also, that I even I  can't see it.

about the version, Im not really sure, I will try to change the metadata.json.

---

### Post by maverick280857 on 2011-05-29
> **maizuddin35 said:**
> yes I did install gnome-shell based on that given link . 
this is the things that changes : dock , system-monitor,  workspace-indicator, and I think some other stuffs also, that I even I  can't see it.

Ah ok.

Get rid of all the extensions. Install them one by one, in $HOME/.local/share/gnome-shell/extensions. Every time you put in one extension in that directory, restart gnome-shell (or log out and log back in). Some extensions are not compatible with others.

> **maizuddin35 said:**
> about the version, Im not really sure, I will try to change the metadata.json.

Yeah do that anyway. But my guess is that this isn't a problem in your case because the extensions are loading. If it were, you would get an error message and would be asked to log out.

---

### Post by maizuddin35 on 2011-05-31
thank you for your reply, I will update this when I done my job;;)

---

### Post by nilarimogard on 2011-06-02
Are you using the user-theme extension? That's known to remove CSS for the other extensions - bug [here]("https://bugzilla.gnome.org/show_bug.cgi?id=650971").

---

### Post by maizuddin35 on 2011-06-02
yes, the same thing happen to me like that. thanks for the link. I really needed that :)

---

### Post by maizuddin35 on 2011-06-05
> **nilarimogard said:**
> Are you using the user-theme extension? That's known to remove CSS for the other extensions - bug [here]("https://bugzilla.gnome.org/show_bug.cgi?id=650971").

sorry, i was a little bit confuse based on that link you give me, can you teach me how to fix this thing?

---

