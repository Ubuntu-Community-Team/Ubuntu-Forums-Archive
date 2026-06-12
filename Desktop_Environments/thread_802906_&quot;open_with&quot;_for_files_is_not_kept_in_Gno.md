---
title: "&quot;open with&quot; for files is not kept in Gnome Panel"
date: 2008-05-21
forum: Desktop Environments
---

### Post by CromagDK on 2008-05-21
Hello,

If the prefix is wrong, let me now :)

I have searched for at bit for a solution, or at least an aswer for why the following happens:

I have placed a .pls file on my desktop. (pls is a playlist file for i.e internet radio station, maybe more).

In 'properties' for the file i select Audacious as the 'Open with' application. This works fine. Audacious opens and opens the .pls.
BUT, when i copy this or make a shortcut in the gnome panel, when i press it, it will be opened with Totem.
The shortcut/copy has the correct info to just open the .pls file, nothing else.
I have ctrl+alt+backspaced to see if it helped.

Do you have an idea to what i can do here ?
Is it just in generel those settings are overruled ?

I appreciate your help :)

\br
CromagDK

---

### Post by CromagDK on 2008-05-22
Bump ?

---

### Post by dje on 2008-05-22
Right click on the launcher on the panel and select properties, in the command box put the following:
```
audacious /home/you/my_playlist.pls
```
where /home/you/my_playlist.pls is the full path to the .pls file

hope that helps,
dje

---

### Post by CromagDK on 2008-05-22
Thanks, that would be an easy way.
But i am kinda looking for why it is this way.
It seems that settings are removed when launched from the panel.

---

