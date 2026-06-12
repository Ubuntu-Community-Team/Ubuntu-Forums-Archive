---
title: "gtkfilechooser from applications not showing network shares"
date: 2008-03-19
forum: Desktop Environments
---

### Post by bazzer on 2008-03-19
Something I've just noticed in Zimbra (and hence Firefox) has caused a small headache and I wonder if someone knows how to get around it.....

When you add an attachment in Zimbra, you are presented with the gtkfilechooser dialogue box. It's almost helpful but critically, it doesn't include network shares - whether mounted or not. I've read that there is a boolean condition used to set whether or not it looks at 'local' resources or not, but I've found no way of checking if this would crack it because I can't find a way to 'call' this dialogue box.

So, is there a way to hack Firefox about to call gtkfilechooser to see?

If you fire up Nautilus, it shows everything, in the left pane. AND you can change to tree view which is very sweet. Why doesn't the gtkfilechooser pick it's settings from Nautilus? Or at least share them?

---

### Post by rax_m on 2008-03-20
This is definitely one of my pet annoyances at the moment. 

As a workaround I've created a link in my home directory to the network share mount (on the local file system). In this way I can access my network shares. 

I would be nice if Gnome did it autmatically though. 

Rax

---

### Post by bazzer on 2008-03-27
Ah, I understand... Except I can't figure out what I'm creating a link to! I've got the icon on the desktop as a result of doing the places>connect to server from the main menu..... Care to nudge me in the right direction?

EDIT: Just tried a few things and it would seem your solution only works if you only have one share. I have many! I think there are about 15, and I don't really want to have to create a separate folder to link to for each of the shares. I'd like to browse, baby!

---

### Post by rax_m on 2008-04-01
Hi. 

Sorry I haven't looked at this for a while. 
You could try adding an fstab entry for for each of your shares.. Then they should be all listed in the /mnt folder. I then created a link in my home directory to the /mnt/share directory. 

It's a bit of a pain to setup, but it only has to be done once. 

HTH
Rax

---

