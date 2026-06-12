---
title: "Menu Editor for Gnome?"
date: 2005-06-11
forum: Desktop Environments
---

### Post by aysiu on 2005-06-11
This is weird. When I install other Gnome desktops, I can always right-click a menu item and do whatever I want to it. For some reason, in Ubuntu's Gnome, I can't do much except add the application to the panel.

I've tried installing SMEG, with no luck. I tried the tar ball. I tried the .deb. I see something called an auto-installing script, but I have no idea where to put the script.

In some of the Ubuntu forum archives, they mention SMEG being in the backports, but they appear not to be there any more.

The Ubuntu wiki says I can just type *applications:///* in the Nautilus location bar, but apparently that location doesn't exist.

Is my Ubuntu installation are freak, or are other Hoaries out there experiencing the same thing? How do I edit the menu?

---

### Post by emperor on 2005-06-11
There are a couple of user created menu editors for Hoary's Gnome 2.10. IT's a Gnome issue not Hoary's fault. Anyway search the forum and you shall find!

---

### Post by tread on 2005-06-11
Go to 3rd party projects at the top of this page.

---

### Post by NeoChaosX on 2005-06-11
He already knows about Smeg, guys. He mentioned it in his second paragraph.  ](*,) 

aysiu: You're supposed to run the autoinstall script manually. Save it to your home folder, open a terminal, go to where in your home directory you saved it, and run it with "sudo ./installsmeg". THe script will download and install all the necessary dependencies for Smeg.

---

### Post by aysiu on 2005-06-11
Thanks for the help. I'm a bit of a newbie. I just want to make sure I got this straight. So I copy the text and put it in a text file? What do I call the file when I save it?

Well, the command you gave me didn't work. It didn't recognize the command ./installsmeg.

What did work was saving [this target as](http://dev.realistanew.com/smeg/installsmeg) *installsmeg* to my home folder, then opening it with Python2.4 (which was in the usr/bin directory).

---

### Post by wylfing on 2005-06-11
Gnome's in a bit of transition now with 2.10. I believe that in 2.12 we can expect a nicer way to edit menus.

---

### Post by jerrybme on 2005-06-15
[QUOTE=aysiu]Thanks for the help. I'm a bit of a newbie. I just want to make sure I got this straight. So I copy the text and put it in a text file? What do I call the file when I save it?

Well, the command you gave me didn't work. It didn't recognize the command ./installsmeg.

What did work was saving [this target as](http://dev.realistanew.com/smeg/installsmeg) *installsmeg* to my home folder, then opening it with Python2.4 (which was in the usr/bin directory).[/QUOTE]
It's a bit late but the step you missed was making the installsmeg executable by using chmod.

Cheers,
Jerry

---

### Post by tread on 2005-06-15
And a bit too late, I'd like to apologize for not reading the thread very well  :---)   :roll:

---

