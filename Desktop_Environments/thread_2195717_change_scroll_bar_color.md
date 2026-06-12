---
title: "change scroll bar color"
date: 2013-12-26
forum: Desktop Environments
---

### Post by cybernetic12 on 2013-12-26
I have a dark theme and the scroll bar is near invisible.

But it's not easy to change the scroll bar color globally, due to various Linux desktop idiosyncrasies.

Specifically, I want to change the scroll bar color of the **PDF viewer**:[INDENT]Document Viewer 3.4.0[/INDENT]
[INDENT]Using poppler/cairo (0.18.4)  (libraries for PDF rendering)[/INDENT]

I am using the Desktop:  LXDE.

There are too many places where I can set my color settings and I'm very confused:


[LIST=1]
[*]Preference -> Customize look and feel:   LXAppearance 0.5.1  for LXDE
[*]Preference -> Gnome color chooser
[*]Preference -> KDE system settings
[*]Preference -> Openbox configuration manager
[/LIST]

Plus there are many other "tricks" that directly edit some config files or theme files.

I don't want to be like a mad man randomly trying all the above tricks -- I am already a mad man.

Is there a systematic way where I can pinpoint which settings are responsible for this specific scroll bar (ie, for the PDF viewer)?

Thanks in advance :)

---

### Post by vasa1 on 2013-12-26
Why do you have "KDE System settings"?
The scrollbar appearance depends on the theme you're using.

---

### Post by cybernetic12 on 2013-12-26
vasa1:

I might have installed KDE previously.  "System profiler" says that I'm using LXDE desktop, I assume that's correct.

Do you think I should uninstall KDE?  but I have not done so for fear that some software would cease to work after that.

I have tried changing my desktop theme ("Nodoka-Midnight" from LXAppearance 0.5.1 for LXDE), I had to manually edit the theme file, and it does work -- my scroll bar is visible normally.  But it fails for some apps, such as the PDF viewer.

Apparently the PDF viewer is using some GUI platform that is unaffected by the LXDE theme, but I don't know where / how to configure that.

---

### Post by vasa1 on 2013-12-26
> **cybernetic12 said:**
> ...

Do you think I should uninstall KDE?  but I have not done so for fear that some software would cease to work after that.
It's not necessary but I read posts about conflicts. Unless there's a real need to remove it, you may just let it be.
> **cybernetic12 said:**
> I have tried changing my desktop theme ("Nodoka-Midnight" from LXAppearance 0.5.1 for LXDE), I had to manually edit the theme file, and it does work -- my scroll bar is visible normally.  But it fails for some apps, such as the PDF viewer.

Apparently the PDF viewer is using some GUI platform that is unaffected by the LXDE theme, but I don't know where / how to configure that.
The PDF viewer, if it is Evince, is a GTK 3 app. It's not clear what you edited but I'd guess that what you want to edit to make changes to Evince's scrollbar will be within a subfolder called gtk-3.0 in your theme folder.

---

### Post by cybernetic12 on 2013-12-26
vasa1:

Thanks, I went to /usr/shared/themes and found the dir "Nodoka-Midnight" and in it is only a directory named "gtk-2.0".

I have previously edited the file gtkrc inside it:
```
style "fedora-scrollbar" = "fedora-button"
{
    text[NORMAL]      = shade (0.2, @bg_color)
    bg[NORMAL]        = shade (0.2, "#33dd33")
    bg[PRELIGHT]      = shade (0.2, "#33dd33")
    bg[ACTIVE]        = shade (0.2, "#33dd33")
    fg[NORMAL]        = shade (0.2, "#33dd33")
}
```

And it worked for some other apps, such as Terminal, but it doesn't seem to affect PDF Viewer (yes, it is Evince).

---

### Post by vasa1 on 2013-12-26
> **cybernetic12 said:**
> vasa1:

Thanks, I went to /usr/shared/themes and found the dir "Nodoka-Midnight" and in it is only a directory named "gtk-2.0".
...
Okay, so that's the beginning of the solution. Most distros are a mix of gtk-2 and gtk-3 apps. (Then there are "qt" apps as well.) As I said, Evince is a gtk3 app. 

I'd say that you need a theme that supports **both** gtk2 and gtk3. Also, gtk3 is "evolving" pretty fast and so please use a relatively modern theme.

All the best.

Edit: 
[LIST]
[*]While changes to gtk2 themes are reflected quite easily by switching to another theme and back, getting changes to a gtk3 theme may need a log out and log in (or even a reboot).
[*]Try to pick a theme that doesn't rely heavily on images to make up the scrollbar. If you do use such a theme, you'll have to edit image files to make changes. I like themes that use CSS as far as possible.
[/LIST]

---

### Post by cybernetic12 on 2013-12-26
Thanks, I installed a gtk-3 theme and the problem is kind of alleviated.

LXappearance is not working for me -- the preview is not working (it stays in my current theme, and I don't even remember how I got the current theme to work in the first place).

But since my pain has gotten some relief I'm willing to leave it like this.  Maybe later I'll tackle the LXappearance issue.

Thanks again ;)

---

