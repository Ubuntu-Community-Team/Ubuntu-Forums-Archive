---
title: "How do I change a window's menu's text color when the window is not maximized?"
date: 2014-07-11
forum: Desktop Environments
---

### Post by shaansweb on 2014-07-11
Hello,

I am using the stock Ubuntu Unity Desktop Environment. Starting with Ubuntu 14.04, Canonical moved away from using global menus for unmaximized windows and instead places the menu on the window boarder. Because my window boarder has a dark color and the text is black, it's kind of hard to read (see screenshot below). Does anyone know how I can change this?

[IMG]http://i.imgur.com/JluevBn.png[/IMG]

Clarification Edit: I have learned that the name of the text I am trying to change is the Locally Integrated Menu

---

### Post by mooreted on 2014-07-11
What theme are you using? Mine doesn't look like that. Also, you have the choice of using the window menu or the global menu.

Open "Appearance" and see if you are using the "Ambiance" theme. If not, change to that.

---

### Post by grumblebum2 on 2014-07-11
You can use gtk-theme-config to adjust some colours.
```
sudo apt-get install gtk-theme-config
```

---

### Post by shaansweb on 2014-07-12
> **grumblebum2 said:**
> You can use gtk-theme-config to adjust some colours.
```
sudo apt-get install gtk-theme-config
```

But this doesn't have an option to change the text I want to. See the text that is circled in red

---

### Post by shaansweb on 2014-07-12
> **mooreted said:**
> What theme are you using? Mine doesn't look like that. Also, you have the choice of using the window menu or the global menu.

Open "Appearance" and see if you are using the "Ambiance" theme. If not, change to that.

I don't want to change themes though. I just want to change the text color

---

### Post by grumblebum2 on 2014-07-12
In  Ubuntu 14.04 the unity compiz plugin draws the window decorations.
Changing colours for the panel also changes the same for the title bar as in my previous attached pic.
To see the change kill nautilus via terminal...
```
nautilus -q
```

Then just open your file browser.

or
you may have to log out and back in.

---

### Post by shaansweb on 2014-07-12
> **grumblebum2 said:**
> In  Ubuntu 14.04 the unity compiz plugin draws the window decorations.
Changing colours for the panel also changes the same for the title bar as in my previous attached pic.
To see the change kill nautilus via terminal...
```
nautilus -q
```

Then just open your file browser.

or
you may have to log out and back in.

I don't think you understand what I'm trying to change. Look at the text that is circled in red. I am trying to change the color of the menu text (File, Edit, View, etc). I am NOT trying to change the window title text color. The window title is the correct color, but hides when I mouse over it to display the menu, so is not visible in my screenshot. Your screenshot is showing the title text, not the menu. This was first introduced in 14.04 so if you're using an older version, you won't know what I'm talking about

---

### Post by grumblebum2 on 2014-07-12
> **shaansweb said:**
> I don't think you understand what I'm trying to change. Look at the text that is circled in red. I am trying to change the color of the menu text (File, Edit, View, etc). I am NOT trying to change the window title text color. The window title is the correct color, but hides when I mouse over it to display the menu, so is not visible in my screenshot. Your screenshot is showing the title text, not the menu. This was first introduced in 14.04 so if you're using an older version, you won't know what I'm talking about
I understand exactly what you want to change.
Changing the panel text colour using gtk-theme-config changes both the
window title and the hover menu colour here.

If it doesn't work then the theme your using may not be compatible with the latest unity.
What theme?

Test gtk-theme-config using the default ambiance theme.

---

### Post by mooreted on 2014-07-12
Found this about theming:

[https://wiki.ubuntu.com/Unity/Theming](https://wiki.ubuntu.com/Unity/Theming)

---

### Post by shaansweb on 2014-07-12
Didn't work. :(

I'm using the Numix Vince theme [http://gnome-look.org/content/show.php/Numix+Vince?content=163740](http://gnome-look.org/content/show.php/Numix+Vince?content=163740)

---

### Post by shaansweb on 2014-07-12
> **mooreted said:**
> Found this about theming:

[https://wiki.ubuntu.com/Unity/Theming](https://wiki.ubuntu.com/Unity/Theming)

This bit seems promising but I don't know where to insert in in the dozens of css files my theme has

[COLOR=#000000]    UnityDecoration[/COLOR][COLOR=#000000].menuitem[/COLOR] {
        [COLOR=#A00000]color[/COLOR]: [COLOR=#0080C0]#dd4814[/COLOR];
[COLOR=gray]    [/COLOR]}

---

### Post by grumblebum2 on 2014-07-12
Installed the theme and it has the same fault here.
Post your error to the gnome-look page
or
Try some of the themes in the noobslab ppa.
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
```

Then just browse the ppa in synaptic.

---

