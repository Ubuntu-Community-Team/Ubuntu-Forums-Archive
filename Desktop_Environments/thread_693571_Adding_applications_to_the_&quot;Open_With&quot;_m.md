---
title: "Adding applications to the &quot;Open With&quot; menu"
date: 2008-02-11
forum: Desktop Environments
---

### Post by ThomasNovin on 2008-02-11
I would like to add my custom application to the "Open With" menu. However, I don't want to do it by just specifying for example /usr/bin/myprogram. I would like to add a nice looking shortcut with a describing name which points to /usr/bin/myprogram.

How can I accomplish this?

---

### Post by hyperair on 2008-02-11
Right click on the file, click properties. Under the "Open With" tab, you should be able to add applications there.

---

### Post by ThomasNovin on 2008-02-11
AFAIK you can only do "Use a custom command" and that will not give you a nice looking entry in this list for future use. You will only have the command you entered without an icon.

I'm looking for a way to create a icon there similar to the existing ones.

---

### Post by hyperair on 2008-02-11
Aah. I see. From what I know, you'll have to create a launcher somewhere inside your menu. Use Alacarte Menu Editor (Right click on the menu bar and click edit menus) for that. Stick an appropriate icon for the launcher, and the command should be the command you said earlier.. 

After doing all that, follow what I said in the previous post. You should be able to find the appropriate application there. Select it, Add, and you're done. =)

---

### Post by ThomasNovin on 2008-02-11
After adding a custom command that had an unique name it was easy to find it using grep in my home directory.

The magical directory is /home/<username>/.local/share/applications/

To add an entry for Adobe Acrobat Reader I added a custom command pointing to /usr/bin/acroread. Then a file called userapp-acroread-NKDL6T.desktop was created. After editing this file to have a better suiting name and icon it looked like this:

$ cat userapp-acroread-NKDL6T.desktop

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/usr/bin/acroread %f
Icon=/usr/share/pixmaps/AdobeReader.png
Name=Adobe Acrobat Reader
Comment=Custom definition for acroread
NoDisplay=true

Voilá.. :KS

---

### Post by ThomasNovin on 2008-02-11
> **hyperair said:**
> Aah. I see. From what I know, you'll have to create a launcher somewhere inside your menu. Use Alacarte Menu Editor (Right click on the menu bar and click edit menus) for that. Stick an appropriate icon for the launcher, and the command should be the command you said earlier.. 

After doing all that, follow what I said in the previous post. You should be able to find the appropriate application there. Select it, Add, and you're done. =)

That is not correct for my install. For example, after installing Adobe Reader it was present in Application>Office but it was not available to open files with until I did as I described above.

---

### Post by caljohnsmith on 2008-03-23
Ok, I followed ThomasNovin's advice and got it to work on my system, but is there possibly an easier way to do this than modifying .destop files?

---

