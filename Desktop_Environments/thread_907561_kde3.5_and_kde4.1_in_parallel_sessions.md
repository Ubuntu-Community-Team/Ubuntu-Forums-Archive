---
title: "kde3.5 and kde4.1 in parallel sessions"
date: 2008-09-01
forum: Desktop Environments
---

### Post by benvantende on 2008-09-01
Hi,

I have KDE 4.1 running 'parallel' to KDE 3.5 as different sessions. I get all oxygen goodies except the window decorations. The window decorations default back to the kde3.5 ones. Obviously the KDE 4.1 session still has some links to KDE 3.5. How can I get this straight? I have tried some things like symlinking the theme, but that does not help.

tHNx

ben

---

### Post by Kamotiq on 2008-09-01
Hey,

   I did the exact same thing. I didn't like seeing all the KDE 3 apps left behind. I found out that you can download Kubuntu with KDE 4 iso file from [www.kubuntu.org](www.kubuntu.org).

   I now have a clean system working perfect (knock on wood) and it looks great.

   It's a little bit of work rebuilding your desktop again, but that's why we like Linux, right?

Cheers,

...Kamotiq (Linux newbee)

---

### Post by benvantende on 2008-09-02
Heyla,

I guess I will do that.

tHNx

ben

---

### Post by Tiny Grasshopper on 2008-09-22
I too would like to have this fixed.

[A bug has been filed]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/228758/") about this behavior. It looks like it has been fixed in KDE 4.1. I assume that version of kde 4 will ship with intrepid which shouldn't be long. There is a workaround described in the bug comments. It didn't work for me though

---

### Post by benvantende on 2008-10-06
heyla,

just did a clean install of kde 4.1 and i got the same effect (oxygen with plastik window decoration) at one point. My cursor set is also half oxygen. I think that happened when installing the gtk-qt transitional package. There seems no way to revert it though.

gRTz

ben

---

### Post by moomooranch on 2008-10-13
Hi, I had the same problem and was able to get around it with this method:

Press Alt+F2. This will bring up a run dialog. Keep it for later.

Press Ctrl+Esc, and search for kwin. Select it and kill it.

Now in the run dialog that you saved, type kwin and press Enter. Oxygen should be your decorator now, and your shortcuts and stuff will change from the ones you set in kde3 to the kde4 ones. Your system tray will also start displaying kde3 programs that put an icon up there.

Hope this works for you.

---

### Post by moomooranch on 2008-10-14
Another thing you can do is to remove kdm for kde3, kwin, and kdesktop.

---

