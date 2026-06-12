---
title: "Bastion freezing/crashing (HIB V via Software Centre)"
date: 2012-06-05
forum: Gaming &amp; Leisure
---

### Post by sffvba[e0rt on 2012-06-05
Hi,

Purchased the Humble Indie Bundle 5 and installed Basion via the Ubuntu Software Centre.

When I launch the game it will imidiatly stop responding as soon as I move my mouse. I typically have to switch to another console (Ctrl+Alt+F1) and back to get out and then close it.

If I don't move my mouse the game loads up to the menu where I can see the mouse cursor but when moving the mouse nothing happens... I eventually have to do the same as above to get out.

Any thoughts?


404

---

### Post by Sofox on 2012-06-06
Check the Software Updater and ensure you're using the most recent version of Bastion.

---

### Post by sffvba[e0rt on 2012-06-06
> **Sofox said:**
> Check the Software Updater and ensure you're using the most recent version of Bastion.

Hi,

Yes I am very very up-to-date (When I have nothing better to do I usually; Ctrl+Alt+t - *sudo apt-get update && sudo apt-get upgrade*)


404

---

### Post by CFWhitman on 2012-06-09
Try editing the file OpenTK.dll.config in the directory where Bastion is installed (for me it's /usr/local/games/Bastion, but I didn't use the Software Center, so your location could be different).  Add this line:
<dllmap os="linux" dll="libXi" target="libXi.so.6"/>

right after the other lines that start with dllmap os="linux" (actually it doesn't matter where as long as you add it within the configuration tags that the file begins and ends with).  Oh, I meant to add that you will need to do this as root (use sudo).

---

### Post by sffvba[e0rt on 2012-06-10
> **CFWhitman said:**
> Try editing the file OpenTK.dll.config in the directory where Bastion is installed (for me it's /usr/local/games/Bastion, but I didn't use the Software Center, so your location could be different).  Add this line:
<dllmap os="linux" dll="libXi" target="libXi.so.6"/>

right after the other lines that start with dllmap os="linux" (actually it doesn't matter where as long as you add it within the configuration tags that the file begins and ends with).  Oh, I meant to add that you will need to do this as root (use sudo).

Thanks for the info... bit late for me as I am running Windows on my gaming rig again and it works flawlessly... &#9829; the game!!!


404

---

### Post by Shwetank on 2012-06-11
> **CFWhitman said:**
> Try editing the file OpenTK.dll.config in the directory where Bastion is installed (for me it's /usr/local/games/Bastion, but I didn't use the Software Center, so your location could be different).  Add this line:
<dllmap os="linux" dll="libXi" target="libXi.so.6"/>

right after the other lines that start with dllmap os="linux" (actually it doesn't matter where as long as you add it within the configuration tags that the file begins and ends with).  Oh, I meant to add that you will need to do this as root (use sudo).

Hello.. noob here.... I have the same problem .. how am I supposed to edit the dll file... baby steps plzz :(

---

### Post by encompass on 2012-06-25
To edit a file as root try using this:
Open the program called terminal.
type:
sudo gedit
then click file and open and locate the file, where ever it is...
Make the editings that were listed above.
Save the changes and close the program.

---

