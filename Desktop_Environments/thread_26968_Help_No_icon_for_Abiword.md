---
title: "Help: No icon for Abiword"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Psquared on 2005-04-14
I had some problems printing a document in OpenOffice so I installed Abiword. However, there is no icon in Application > Office > Abiword. There is only text. I tried to add an icon but the text disappears when I do.

Maybe I should update to a more recent version of OpenOffice. I am running Warty so I have 1.1.2.

---

### Post by Bob D. on 2005-04-14
I'll assume you've done the normal and either logged out, logged back in or issued a 'killall gnome-panel' from a terminal. While it really isn't supposed to happen, sometimes this is necessary for an icon to show up.

My next thought would be to edit the Abiword .desktop file. I've had several instances where the 'ICON=' line points to an icon but it just will not load. I've solved them all be giving an absolute reference to the icon instead. You'll normally find the icon in '/user/share/pixmaps' or a sub-directory of here.

To open the .desktop file, do a 'Find' for "abiword" or "abiword.desktop". Once you find the .desktop file, you can open it to take a look by just double clicking the file from the file browser. The file will open read-only.

If you deceide you need to edit the .desktop file, 'sudo gedit /the/location/of the/abiword.desktop' file from a terminal will open it in editing mode. If the ICON= line is "abiword,png' and the abiword.png icon is in /usr/share/pixmaps, chnage the icon line to 'ICON=/usr/share/pixmaps/abiword.png'. Save the file and see if the icon is updated.

Post back if you need more help or I wasn't clear on a point.

Bob

---

### Post by Psquared on 2005-04-14
Thanks for the help. I got the icon to appear, but when I tried to use Abiword it bugged out on me. I opened a document and tried to move a section to the end of another paragraph. It highlights fine, but when I drop it in a new location it shuts the program down. I tried several times and rather than drag and drop I just tried to cut and paste from the Edit menu. I got the same result.

There are two versions of Abiword in Synaptic. (I do have third party sources) I tried both and got the same result. They are both warty+backports. Maybe I have another conflicting package?? (I am using Warty)

---

### Post by Bob D. on 2005-04-15
> There are two versions of Abiword in Synaptic. (I do have third party sources) I tried both and got the same result. They are both warty+backports. Maybe I have another conflicting package?? (I am using Warty)
A conflict could well be the problem. Is there an Abiword version in the Ubuntu universe or multiverse? It might not be the most recent but it might work.

Bob

---

### Post by Nu-Buntu on 2005-05-05
I installed AbiWord via apt-get, and it doesn't appear on my menus either. No icon. No entry. However, if I go to terminal and type abiword, it starts.

---

