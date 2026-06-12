---
title: "I Need Help! - Kubuntu Hoary Broken"
date: 2005-04-01
forum: Desktop Environments
---

### Post by emrys on 2005-04-01
I installed Kubuntu from Ubuntu in a AMD64 but it's unusable:

1.No Control Panel icon. I can call it with kpanel from a terminal but then, it is almost empty. Nothing there except a couple unusable icons...

2.No file manager!!! Initially when I click in a folder, it opens Filelight!. I uninstalled Filelight and then when I click on a folder, It says that "KDEInit could not launch filelight". I can oppen it from a terminal, but it is empty. If I put whatever in the Location bar, same error... "...filelight".
The only way to go through folders in a windows enviroment is calling nautilus from a terminal...

Everything else seems just fine. But in it's actual state it is unusable for me.

Edit: I can't use either the Configure Panel..., Configure Window Behavior...

Edit2: I renamed the .kde folder and restart. Some things changed, I have a System Icon in the taskbar... but if I click... Empty... :(

Someone can help me? Any Idea??

What It is happening?????

Thanks a lot.

---

### Post by soul_rebel on 2005-04-03
you are missing some packages or have been unluky and got some corrupted one. Kde is evolving fast in repos. Try an upgrade and install kubuntu-default-settings (and maybe kubuntu-desktop if you want kdm) packages to get dependences resolved. Or just check to have konqueror and kcontrol.
bye

---

### Post by emrys on 2005-04-03
[QUOTE=soul_rebel]you are missing some packages or have been unluky and got some corrupted one. Kde is evolving fast in repos. Try an upgrade and install kubuntu-default-settings (and maybe kubuntu-desktop if you want kdm) packages to get dependences resolved. Or just check to have konqueror and kcontrol.
bye[/QUOTE]

Thanks soul_rebel. Finally, I had to reinstall Kubuntu. After trying to defrost and reinstall the packages (thks apokryphos), is seemed the only remaining option.

Now, everything is ok, well, not everything because of the lack of flash and other "normal" problems with x86_64... :)

---

