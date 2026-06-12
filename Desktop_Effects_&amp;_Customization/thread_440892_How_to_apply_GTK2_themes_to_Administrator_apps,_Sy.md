---
title: "How to apply GTK2 themes to Administrator apps, Synaptic?"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by itsjustarumour on 2007-05-12
Can anyone tell me how I get GTK2 themes to apply to the Synaptic window, or applications being run as Administrator?

For example, I use the LinSta3 GTK2 theme downloaded from [www.gnome-look.org](www.gnome-look.org). The Synaptic window isn't "themed" the same as the others...  

If I run Nautilus in a terminal the GTK theme is applied OK to the Nautilus window, but if I run "sudo Nautilus" I get a Nautilus window with the basic Gnome theme, and the depressing Windows 2000-grey background.

I've tried

> sudo gnome-theme-manager

and then dragging-and-dropping the themes from there, but it doesn't work.  Is there a way to do this?  Or is this just one of those niggly little things thats impossible to fix? Its really bugging me!

Any wisdom gratefully received!  :-)

---

### Post by kpolice on 2007-05-12
Install the themes to /usr/share/themes or symlink your .themes folder to /root/.themes

---

### Post by itsjustarumour on 2007-05-12
> **kpolice said:**
> Install the themes to /usr/share/themes or symlink your .themes folder to /root/.themes

Hi kpolice,

Wow, thanks for your quick response!  :-D  I'm at work at the mo, but I'll give that a try when I get home.

Cheers!  :-D

---

### Post by screaminj3sus on 2007-05-12
I have the same problem, but when I try to copy my themes to that folder it says I do not have permission to copy to this folder, how can I get it to work?

---

### Post by itsjustarumour on 2007-05-12
Yay, success!!!  I just copied the theme folder to /usr/share/themes and it worked.  My old LinSta2 theme was in there, but not LinSta3 - no idea why one appeared and not the other, but hey, I'm not complaining!  :-)

kpolice - thanks again for your top tip  :KS 

screaminj3sus - are you sure you're trying this with Admin rights?  Unzip the .tar.bz file to your desktop, then open Gnome Terminal and do 

> sudo nautilus

and just cut and paste the folder to the right location.  Log out and in again and it should work...

---

### Post by screaminj3sus on 2007-05-12
Thank you, pasted all my themes in there and everything works as it should.

---

### Post by itsjustarumour on 2007-05-12
> **screaminj3sus said:**
> Thank you, pasted all my themes in there and everything works as it should.

Cool, glad you got it sorted :-)

---

### Post by Sirron on 2007-05-14
awesome, sorted it for me too ^^

I find it's not actually necessary to ask the forum anymore, just google.

Isn't this something that should be set by default? Seems like an important thing really.

---

