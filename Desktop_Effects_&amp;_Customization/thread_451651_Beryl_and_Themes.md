---
title: "Beryl and Themes"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by Yazaaab on 2007-05-22
I have Beryl installed and working fine,  I would like to be able to theme my panels and Icons.  Is Beryl stopping me from doing this.  I go to gnome-look.org and download the theme and place it into the theme section in the preferences.  There is no change in the panels but I can change the Window Decorator in Beryl.  Looking for some guidance on getting my entire desktop themed.

Thanks

---

### Post by Brackish_zygote on 2007-05-22
Try going to system > Preferences > Theme. 

I don't think that's going through beryl, but it changed some things Beryl didn't for me

---

### Post by konungursvia on 2007-05-22
Are you downloading Metacity themes (for normal gnome) or Emerald themes (for the effects in Beryl)? You can have one of each selected.

---

### Post by Yazaaab on 2007-05-22
> **konungursvia said:**
> Are you downloading Metacity themes (for normal gnome) or Emerald themes (for the effects in Beryl)? You can have one of each selected.

I have tried both but I can't get the Panel to change.  I think maybe I am missing something.

---

### Post by garv284 on 2007-05-23
I am having the same issue. Even if I switch back to gnome for my theme manager, the only thing that changes when I select a theme is the border, the content of the window remains the same along with the desktop icons and the menubar/taskbar.

---

### Post by crimesaucer on 2007-05-23
Do you have the correct theme engines installed like for the popular murrine themes, you need the murrine engine.

In Synaptic it's: gtk2-engines-murrine

And if you have been downloading the gtk-2.0 themes, then they should work. In xubuntu, I move my themes into /usr/share/themes using "sudo mv" in the terminal.

---

### Post by ironslave on 2007-05-28
i am having a similar problem, when i try to change a gtk theme with an xgl session, it does nothing and runs the default theme that includes icons and all same with the cursor, it goes back to the original. i can can only change them when i am runing a gnome session with no xgl.

---

### Post by mcduck on 2007-05-28
> **Yazaaab said:**
> I have tried both but I can't get the Panel to change.  I think maybe I am missing something.

Both Metacity and Emerald are window managers, so their themes only change your window frames. Panels are handled by GTK2-themes (or by using a custom background pic for the panel).

Those having troubles with GTK2/icon themes with Beryl, try running 'gnome-settings-daemon &', and if that helps add 'gnome-settings-daemon' to your startup in System/Preferences/Session.

---

### Post by garv284 on 2007-05-28
> **mcduck said:**
> Both Metacity and Emerald are window managers, so their themes only change your window frames. Panels are handled by GTK2-themes (or by using a custom background pic for the panel).

Those having troubles with GTK2/icon themes with Beryl, try running 'gnome-settings-daemon &', and if that helps add 'gnome-settings-daemon' to your startup in System/Preferences/Session.

This fixed my problem listed above. Thanks.

---

### Post by Yazaaab on 2007-05-29
> **mcduck said:**
> Both Metacity and Emerald are window managers, so their themes only change your window frames. Panels are handled by GTK2-themes (or by using a custom background pic for the panel).

Those having troubles with GTK2/icon themes with Beryl, try running 'gnome-settings-daemon &', and if that helps add 'gnome-settings-daemon' to your startup in System/Preferences/Session.

This fixed my problem also,

Thank you,

---

