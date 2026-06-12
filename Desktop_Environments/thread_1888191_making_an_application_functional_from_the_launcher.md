---
title: "making an application functional from the launcher"
date: 2011-11-28
forum: Desktop Environments
---

### Post by danh-h on 2011-11-28
Hi,

I'm using ubuntu 11.10, with what i think is called the unity desktop.

It has a launcher (like a dock) that active applications show up in.

I downloaded an application from the net, valaterm, and although it works, and shows up in the launcher, if i right click on the app icon in the launcher and chose "Keep in Launcher", it won't launch from the launcher.

That is, after i quit the application, and double click on the icon in the launcher, the app icon, it flashes a few times, but doesn't open a window or do anything.

So, a couple of questions, (1) is there a log for the launcher somewhere that i can consult to see what is going on (and where is it, if so)?  (2) any advice on how to cure the problem?  Obviously the computer knows where the software is because it is running it.

For reference, valaterm is at [https://gitorious.org/valaterm](https://gitorious.org/valaterm) and is a project to code a terminal application in vala.

Thanks in advance for any info from anybody!

---

### Post by stinkeye on 2011-11-28
After added to the launcher look in **~/.local/share/applications**
for the .desktop file.
Drag and drop into gedit to view the exec line.

---

### Post by secretrobotron on 2011-11-30
So glad I found this post; was just about to write about this myself.

Trying to place firefox-nightly in the launcher never works. I even reformatted the firefox.desktop file from /usr/share/applications to try to make it work.

The icon pulses a few times and then does nothing.

Is there some log somewhere to see what's going wrong? Is there some software to use or file I can edit that will dictate what's in the launcher?

Interestingly, if I launch nightly from the "Dash Home" menu (by just typing "nightly", since I have that soft-linked from /usr/local/bin), an icon appears in the launcher, but it's a question mark. BUT, it works. I can launch the app from there.

wut.

---

### Post by stinkeye on 2011-11-30
Try dragging whatever is working in the dash into gedit to view.

---

### Post by BC59 on 2011-11-30
You could try to drag and drop the icon from the dash to the desktop. Then right click and from Properties--Permissions check to make it executable if not.

Then you drag and drop to the launcher.

The icon stays to the desktop and to the launcher. If you delete it from the desktop, i'ts just gone from everywhere.

So if you don't like to have links to your desktop, you can create a hidden folder to the home with the links. Then you drop the desktop links to the folder and drag and drop them again to the launcher.

---

### Post by secretrobotron on 2011-11-30
That seems to have worked, although dragging an icon from the dash to the desktop to the launcher seems like it's not the most optimal approach.

Is there a bug on this perhaps?

---

### Post by BC59 on 2011-11-30
No there is no bug, it's just Canonical which doesn't like to make Ubuntu adaptable to the user needs.

Apple Mac OS works -somehow- like this.

---

