---
title: "HOWTO: Nice menu fonts (XMMS, Xine, Mplayer)"
date: 2005-08-28
forum: Desktop Environments
---

### Post by buldir on 2005-08-28
Make a file called ".gtkrc" in your home directory and slap in the following text:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"
```

Wallah!  Decent looking menu fonts for XMMS, Xine, and Mplayer.

*NOTE: For Ubuntu change the file name to ".gtkrc.mine".  Thanks again, samwyse.

---

### Post by jrcmuniz on 2005-09-10
[QUOTE=buldir]Make a file called ".gtkrc" in your home directory and slap in the following text:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"
```

Wallah!  Decent looking menu fonts for XMMS, Xine, and Mplayer.

*NOTE: For Ubuntu change the file name to ".gtkrc.mine".  Thanks again, samwyse.[/QUOTE]

Hey Buldir!!!

Thank you very very much!!!!
I' ve been playing with this problem since I installed Kubuntu...
GREAT work! Nice tip!!!

Joao Renato.

---

### Post by buldir on 2005-09-10
No problem!  I can't take credit, though...thank [samwyse](http://ubuntuforums.org/member.php?u=33152).

---

### Post by precinto on 2006-12-13
This doesn't work for me, probably because I'm using Xgl. 
Does someone know of a way of getting the menus right with Xgl?

Thanks.

---

### Post by LordYama on 2006-12-31
> **buldir said:**
> Make a file called ".gtkrc" in your home directory and slap in the following text:

```
style "user-font"
{
fontset="-adobe-helvetica-medium-r-normal-*-12-*-*-*-p-*-iso8859-1"
}
widget_class "*" style "user-font"
```

Wallah!  Decent looking menu fonts for XMMS, Xine, and Mplayer.

*NOTE: For Ubuntu change the file name to ".gtkrc.mine".  Thanks again, samwyse.

This does not work with Xine, since Xine is not GTK based. There is a [bug report]("https://launchpad.net/distros/ubuntu/+source/xine-ui/+bug/49642") for Xine.

---

### Post by MD_Marsh on 2007-02-03
> **precinto said:**
> This doesn't work for me, probably because I'm using Xgl. 
Does someone know of a way of getting the menus right with Xgl?

Thanks.

Here's what I did with AIGLX and Beryl it may work for you:

gedit .gtkrc.mine

copy/paste the following in to it and save:


style "default-text" {
fontset = "-adobe-helvetica-medium-o-normal--10-100-75-75-p-57-iso10646-1,\
-*-r-*-iso10646-1,*"
}
class "GtkWidget" style "default-text"



Cheers.

PS - My source was: [http://doc.gwos.org/index.php/Making_Gtk1.2_not_so_ugly](http://doc.gwos.org/index.php/Making_Gtk1.2_not_so_ugly) (just left out the theme part though).

---

