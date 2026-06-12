---
title: "gdm session option"
date: 2009-04-29
forum: Desktop Environments
---

### Post by jeezum crow on 2009-04-29
Where is the file that tells gdm what window managers to display under the "sessions" tab? I am using xubuntu. I have neither gnome nor kde installed, yet both openbox-gnome and openbox-kde are offered as session chioces by gdm. I would like to edit the file to delete these choices.

---

### Post by jeezum crow on 2009-04-30
I guess no one knows.........../usr/share/Xsessions............delete the unwanted options.

---

### Post by x1a4 on 2009-04-30
Hi,
GDM gets its session information from launchers located in /usr/share/xsessions/

To remove the openbox-kde, openbox-gnome entries move/delete (or rename extension of) the files: 
openbox-gnome.desktop
openbox-kde.desktop

---

### Post by jeezum crow on 2009-04-30
your username is x1a4

---

### Post by x1a4 on 2009-04-30
I know my username, but was my advice helpful?

---

### Post by jeezum crow on 2009-04-30
If you read my post directly above your 1st reply, you'll see that I had already found the solution to my problem.

---

