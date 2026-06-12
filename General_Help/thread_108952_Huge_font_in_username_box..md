---
title: "Huge font in username box."
date: 2005-12-27
forum: General Help
---

### Post by ophion on 2005-12-27
I have recently installed Ubuntu on a spare PC.  The only problem that I have noticed (there may be more, as I have barely poked around the system) is that a huge font is used in the username box on the login screen.  It does not impair the login process, but it is a bit embarrassing to see little bits of letters that are far too large for their container.  How do I fix this?

---

### Post by ophion on 2005-12-28
Any ideas?

---

### Post by Danielle on 2005-12-28
if you use Opera, which you probably don't! it's tools>Preferences>Advanced>Fonts>Webpage<pre> which probably needs to been changed.

---

### Post by ophion on 2005-12-28
How would the font setting in a web browser affect Ubuntu's login screen?

---

### Post by Danielle on 2005-12-28
[QUOTE=ophion]How would the font setting in a web browser affect Ubuntu's login screen?[/QUOTE]
can't see how it could :p  sorry, i've just Opera fonts on the brain.

---

### Post by anil_robo on 2005-12-28
Are you using the default Ubuntu login theme, or did you install some other theme from somewhere? The default theme should not give you problems I guess. Please check the login screen setup in System--> Administration--> LOgin Screen Setup and tweak it as per your needs. It should work.

Still, if it doesn't work, try ```
sudo dpkg-reconfigure gdm
``` followed by a reboot.

---

### Post by horace on 2005-12-28
I had the opposite effect - tiny font in the user name entry box when using the default human logon. Solution was to edit the /usr/share/gdm/themes/human/human.xml file, adding a font tag to the item labelled id="user-pw-entry". It doesn't seem to have a font set for this item by default.
hth

---

