---
title: "How to make a portable Minecraft"
date: 2014-06-24
forum: Gaming &amp; Leisure
---

### Post by Vombocorn on 2014-06-24
*Sorry if this is in the wrong topic section*

I was wondering if I could make a portable Minecraft (Minecraft on USB) for Ubuntu?

Thank you so much!

---

### Post by bapoumba on 2014-06-25
*Thread moved to **Gaming & Leisure**.* :)

---

### Post by R33D3M33R on 2014-06-25
Try this
1. Run the game once
2. A [hidden folder]("http://askubuntu.com/questions/293526/hide-and-unhide-folders") .minecraft will appear in your home directory
3. **Cut** and paste this folder to the USB key
4. On each computer/user account you want to play the game, just [create a symlink]("http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link") of this folder to the home directory again

Alternatively, you can **cut** and paste the folder to your cloud software folder (Dropbox, Google Drive) and create symbolic link from there.

---

### Post by Vombocorn on 2014-06-25
I can't really seem to understand how to make a symlink.

---

### Post by R33D3M33R on 2014-06-25
Try dragging the .minecraft folder from the USB into the home folder while holding Ctrl+Shift.

---

### Post by Vombocorn on 2014-06-26
Then do I launch the Minecraft.jar that is saves on the USB?

---

### Post by R33D3M33R on 2014-06-27
Yes. If you did everything correctly, files should be saved on USB key.

---

