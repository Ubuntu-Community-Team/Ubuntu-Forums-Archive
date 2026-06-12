---
title: "EVOLUTION MAIL: Mail showing up as black when highlighting msgs and headers at top"
date: 2012-05-01
forum: Desktop Environments
---

### Post by CWM800 on 2012-05-01
Hello Everyone

Think I finally found the buntu I like !! Away from Unity * shivers*

Anyways... I just installed Evolution mail and when highlighting an email it highlights it in a DARK grey... I am using Redmond theme for Xubuntu 12.04

Everytime I highlight an email its in that grey black and you cant read what the subject is.. I am having to rely on webmail until I can figure this out!

How do I change it?

Thanks,
Christopher

---

### Post by felixbecker2 on 2012-05-04
Same problem here.


Using Arch Linux, xfce window manager (standalone) and xfce panel. Upgraded to evolution 3.4.1-1 and that problem appeared:
* Selected text is black on black,
* Headers in the message preview are black on black.


What can I do? Opening gnome-control-center seems not the help since I do not find any theme- or colouring-options (I do _not_ have a full gnome installation).


Bye,
Felix.

---

### Post by cackerso on 2012-05-10
Just a note, I'm having the same problem with Evolution and I'm running it in Kubuntu 12.04.  I hope someone here has a solution.

---

### Post by lefty73 on 2012-05-11
fwiw, me too seeing this ... 12.04 with xfce ... could not figure anything to resolve this. Is this evolution issue or more likely desktop settings?

---

### Post by lefty73 on 2012-05-11
> **lefty73 said:**
> fwiw, me too seeing this ... 12.04 with xfce ... could not figure anything to resolve this. Is this evolution issue or more likely desktop settings?
looks that to do  with xfce4 styles?
I can change Settings->Appearance->style to eg. 'Adwaita' this looks better for the evolution stuff ... more of a workaround I guess

---

### Post by BananaJoe on 2012-05-13
Hello,

i think i have the same problem... :mad:

Also other programs are affected. For example the bottom line of the software center.

Changing styles does not help. I also use XFCE 12.04.

kind regards

---

### Post by rai4shu2 on 2012-05-13
I suspect a lot of this is caused by the GTK2/3 problem. If you have a theme that only supports gtk2 and not gtk3, all kinds of problems appear. For now, you need to stick with graybird/bluebird or some other theme that supports gtk3 (see [http://www.gnome-look.org/](http://www.gnome-look.org/) for more themes).

---

### Post by BananaJoe on 2012-05-13
Thank you! Now it works!

Best regards

---

### Post by JonNicholson on 2012-05-22
Thanks -- Good advice, it worked.

---

### Post by ZeroFossilFuel on 2012-05-30
> **rai4shu2 said:**
> I suspect a lot of this is caused by the GTK2/3 problem. If you have a theme that only supports gtk2 and not gtk3, all kinds of problems appear. For now, you need to stick with graybird/bluebird or some other theme that supports gtk3 (see [http://www.gnome-look.org/](http://www.gnome-look.org/) for more themes).

Great. I have this same problem too. It took me a long time to settle on a theme that I liked, MurrinaGilouche. Now, because Evolution has chosen to drop support of GTK2 themes, I have to go shopping again for a GTK3  compatible theme? That stinks.

---

### Post by ZeroFossilFuel on 2012-08-10
Bump.

Several kernel and GTK upgrades later and Evolution in Xubuntu still it looks like S__T unless I use Greybird or Bluebird. Do any of the developers ever read these posts?

Color me annoyed.

---

