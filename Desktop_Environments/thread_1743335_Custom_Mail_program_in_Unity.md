---
title: "Custom Mail program in Unity?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by castironpants on 2011-04-29
I just upgraded from Maverick to Unity (which proved to be a chore in itself) but I came across a shockingly un-Linux change Unity. What happened to the 'Custom' option for Preferred Applications (in this case, Mail)?

Letme explain the sweet setup I had in 10.10. I had a Prism (1.0b4 from source) webapp for Gmail complete with icon, extensions and Greasemonkey userscripts. I set it as my Preferred Application. Then I installed GM-Notify and set it open the preferred application so that whenever I had new mail I could click on it and it would open the Prism window.

Well after installing Unity I tried to configure my setup again. The Prism app runs fine, but in Preferred Applications there is ONLY a dropdown menu that ONLY has Evolution. In the meantime I've had to set GM-Notify to open the web client but this is sort of a slap in the face. Isn't the whole idea of Linux to be free to choose your own programs instead of having a default suite forced upon you?

So now the question is how to fix this. I've already tried opening the Evolution desktop file, copying all the MimeType info to the Prism Gmail app desktop file then commenting it out on the original. It still didn't change anything. What else can I do?

---

### Post by fbartels on 2011-05-24
This would interest me, too.

Doesnt seem to be an answer out there.

Regards Felix

---

### Post by mcduck on 2011-05-24
That actually has nothing to do with Unity, but the underlying desktop environment, Gnome.

This should help: [http://live.gnome.org/ControlCenter/AddingDefaultApplications]("http://live.gnome.org/ControlCenter/AddingDefaultApplications")

---

### Post by fbartels on 2011-06-07
Thanks I will try this.

---

