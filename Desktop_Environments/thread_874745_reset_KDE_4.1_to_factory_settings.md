---
title: "reset KDE 4.1 to factory settings"
date: 2008-07-30
forum: Desktop Environments
---

### Post by shishira on 2008-07-30
Have had Kubuntu running KDE 4.0, made a lot of changes to the panels and things now have updated to 4.1 and need to reset the panel and other setting to the factory default how do i do this

thanks

---

### Post by coffeecat on 2008-07-30
In KDE3 you could delete the .kde folder (and contents) in your home directory and it would be regenerated when KDE next started up with the desktop reset to its default configuration. But if the distro had not set up its own default it would be the vanilla kde default, so I don't know what you would get in Kubuntu.

Also, I have no experience of KDE4 so I don't know how differently it behaves. I've just had a look in my openSUSE (KDE3) home folder, and there are both .kde and .kde4 folders. (In KDE3. Hmmm...  :-k )

May I suggest you rename rather than delete those two folders? If KDE4 resets itself to defaults, then fine. But if it crashes or won't start at all, or does something else untoward, you could at least rename them back and get back to where you were - using a virtual terminal if necessary.

---

### Post by shishira on 2008-07-31
did that the settinggs went kinda real wierd rolled back the olde .kde4

---

### Post by shishira on 2008-07-31
went through the process again but this time removed all kde related things including the .qt file and even kde3 it worked 

solved

---

### Post by spybee on 2012-01-04
Can you describe exactly what files did you delete?

---

