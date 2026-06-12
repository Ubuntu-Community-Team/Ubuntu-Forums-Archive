---
title: "Installed Beryl -- Themes window edges but not windows and top/bottom bar"
date: 2007-03-08
forum: Desktop Environments
---

### Post by se1zure on 2007-03-08
SO, I installed Beryl, and so far everything seems to work okay.

I can go under the emerald theme manager, install new themes, and change themes.

HOWEVER, when I change themes, it only changes the borders of hte windows. THe actual windows themselves, and the top bar are stuck on a super ugly grey. Here is a screenshot:

[IMG]http://free.hostultra.com/~scetchbook/Screenshot.png[/IMG]

I even switched back to metacity themes, and the windows still do this!

Can you help?

---

### Post by se1zure on 2007-03-08
bump. :confused:

---

### Post by ComplexNumber on 2007-03-08
there's no screenshot.

---

### Post by guillepb on 2007-03-17
No screenshot indeed, but I believe I'm having the same problem you're having.

My Beryl looks pretty ugly and I don't know how to get rid of those boxy grey buttons and huge font sizes all over the place: emerald will only change the window borders, titlebars and the close/minimize/maximize buttons.

I'm just trying Beryl for the first time, so I'm pretty sure it's my fault, but I'm clueless anyway...

Thanks!

---

### Post by mcduck on 2007-03-17
Beryl is just a window manager, so it is not supposed to change your application theme or your panels in any way. They are still controlled by GTK themes, just like in normal Gnome.

If GTK themes are not working correctly with beryl, try running 'gnome-settings-manager &', and if that helps add 'gnome-settings-manager' to your session startup in System/Preferences/Sessions.

---

### Post by guillepb on 2007-03-18
Thanks, I think you meant gnome-settings-daemon but anyway your message pointed me to the right direction.

Anyway, the alternative start-up script mentioned on [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL) did the trick for me.

Thanks for your help!

---

