---
title: "Gnome Shell, close button on LEFT; HOW?"
date: 2012-05-24
forum: Desktop Environments
---

### Post by darolu on 2012-05-24
I'm using Ubuntu 12.04 x86_64 with Gnome Shell.

I want to set my windows close button to the left side of the window.

I've tried using gconf-editor to modify the buttons lay-out at "desktop/gnome/shell/windows" (close: ) and at "apps/metacity/general" (where it shows the old layout 'close,minimize,maximize:menu'); but doesn't seem to work.

Is it a bug? Do I need to modify another file or settigns? where?

Thanks in advance for your help.

---

### Post by nothingspecial on 2012-05-25
*Thread moved to **Desktop Environments**.*

---

### Post by maverickaddicted on 2012-05-25
Have you tried Ubuntu tweak? You can download it from here - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/).  There is windows manager settings section, you can try changing it from there.

---

### Post by darolu on 2012-05-26
> **maverickaddicted said:**
> Have you tried Ubuntu tweak? You can download it from here - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/).  There is windows manager settings section, you can try changing it from there.

Thank you very much kind sir, Ubuntu Tweak did the trick. My close button is finally on the left corner.

It's a very nice application, I loved the cleaner also. It should come with the default Ubuntu install.

---

### Post by tshannon on 2012-05-29
Any idea what Ubuntu Tweak actually does?  It seems kind of like overkill to install a whole app to tweak one setting.

---

### Post by tshannon on 2012-05-29
Nevermind, found it: [ http://www.jairusmartin.com/2012/04/how-to-move-window-close-minimize.html]("http://www.jairusmartin.com/2012/04/how-to-move-window-close-minimize.html").

The change from the last version of ubuntu is that you use the dconf editor rather than the gconf editor.

---

