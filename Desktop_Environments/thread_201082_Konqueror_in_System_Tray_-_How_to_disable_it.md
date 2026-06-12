---
title: "Konqueror in System Tray - How to disable it?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by alexsb on 2006-06-21
Hi,

whenever I start an instance of konqueror I get an icon of a folder in my system tray. This is also true for some other applications, that do not belong there (in my opinion). Is there any possibility to configure this?

Greetings,

Alex

---

### Post by Jucato on 2006-06-21
Hmm... this is very strange. Is this a fresh install of Kubuntu? AFAIK, this isn't the default behavior.

I can only think of one possible cause: click on the K Menu and go to the entry for Konqueror. Don't click on Konqueror, right-click it and choose Edit Item. KMenuEdit (KDE Menu Editor) should launch. Make sure that the "Place in system tray" box is unchecked. Check the other apps that behave this way. 

Other than that, I really don't know.

Hope that helps.

---

### Post by alexsb on 2006-06-21
Great, that was exactly the problem!
Strange that it had been set.

Thanks,

Alex

---

