---
title: "why unlock icon?"
date: 2017-09-23
forum: Desktop Environments
---

### Post by Nick Levinson on 2017-09-23
In Ubuntu 16.04.2 desktop, what is the right-click option to unlock an icon? Without unlocking, I dragged an icon to another position and back, so locking doesn't prevent moving. Some sources hint it's for making icons disappear but that seems strange since we might want to access the programs and might want the icons back.

---

### Post by vanadium on 2017-09-24
The dock serves as a launcher for programs that have not been started, and as a task switcher for programs that are running. Locking an icon means that the icon has to stay there even when the program is not running, so you can always start it by clicking the icon. Programs not on the dock are started quickly by the keyboard: press the Super key to open the dash, and type a few letters of the name of the program. Also the mouse can be used in the dash to find applications that are not on the dock.

Locking is only to make icons stay all the time or only when a program is running. Locking does *not* intend to lock the configuration of your dock: you can keep dragging items to another place or remove them by dragging to the trash can. The idea is that moving the place of icons already allows a very deliberate action from you: it won't happen by accident, so there is no need for a feature to block the possibility of changing the taskbar.  

Typically, you should only lock your four or five most used programs on the taskbar. Start programs you use less often using the super key, or by double clicking a data file made in a program in the file manager. If you clutter your taskbar with many icons, it becomes unwieldy. You have to scroll and scan intensively to find your icon. Managing the running programs in between all the icons becomes unwieldy.

That is just my view on how it works., and on why one would lock/unlock icons.

---

### Post by Bucky Ball on 2017-09-24
(Just a note, and slightly off-topic: unless you have a good reason for being on 16.04.2, you should be on 16.04.3. Have you updated/upgraded your release lately?

```
sudo apt update
sudo apt full-upgrade
```

... will get you to where you should be; 16.04.3. Carry on. :))

---

### Post by Nick Levinson on 2017-09-25
Thanks; good info.

I browse for apps. For example, I like having a wide variety of browsers for testing my files, but I don't remember what the little-used browsers are named, so typing doesn't help. Searching depends on the keywords assigned by developers and that should be okay for browsers, but when I need a system utility I may have no idea what keywords to use, never mind the program names.

Double-clicking a document works, and I often do it, except when I want to open it with a different app, in which case finding apps is important, and, for some functionalities, harder.

I'm on 16.04.2 because that was available when I downloaded Ubuntu and I check periodically for updates via the Ubuntu Software app > Updates. If that didn't bring me to 16.04.3 (and it didn't explicitly say it did), then I didn't know it didn't. Top panel > System Settings > System > Software & Updates > Updates tab > Notify Me of a New Ubuntu Version menu > For Long-Term Support Versions is already selected. System Settings > System > Details > Overview only says 16.04. I proposed to Fedora's people that their last update before end-of-life (EOL) should announce the EOL so users know to upgrade at that time and perhaps the same should be arranged for Ubuntu, because most of us don't monitor distro-specific news, which tend to have much more content than we want to spend time on every week. I'm not a full-time admin (I'm my own admin) and I use my laptops mostly for productivity.

---

### Post by Bucky Ball on 2017-09-25
> **Nick Levinson said:**
> Double-clicking a document works, and I often do it, except when I want to open it with a different app, in which case finding apps is important, and, for some functionalities, harder.

Have you tried right-clicking the document and 'Open with ...'? If the app doesn't come up as a default, you can find it from there, if, of course, you know what you're looking for.

---

### Post by Nick Levinson on 2017-09-27
I've given up on Open With, because the app I know I want often has some name I don't know (likely CLI-based when I use the GUI) and a location I don't know (it's installation-specific) and I'd likely have to Google for those items each time. That's a usability issue that likely affects many users many times, but that's beyond this forum's scope.

---

### Post by Nick Levinson on 2017-09-27
By the way, could someone please change the thread's prefix from UbuntuGnome to Ubuntu? I apparently can't and it was my error (it turns out I'm using Unity). Thank you very much.

---

### Post by howefield on 2017-09-27
> **Nick Levinson said:**
> ...could someone please change the thread's prefix...

Done.

---

