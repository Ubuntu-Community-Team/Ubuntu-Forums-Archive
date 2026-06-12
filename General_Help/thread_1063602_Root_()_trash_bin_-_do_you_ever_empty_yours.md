---
title: "Root (/) trash bin - do you ever empty yours?"
date: 2009-02-08
forum: General Help
---

### Post by sofasurfer on 2009-02-08
Is everyone aware of the trash can at /root/.local/share/Trash? I never heard it mentioned. Do you empty it? Delete it? Ignore it? Or is it a surprise to learn that its there?

---

### Post by jrusso2 on 2009-02-08
I don't empty it usually but I did finally the other day when I figured it was pretty full.

---

### Post by mc4man on 2009-02-08
What I do when deleting graphically as root is use shift+delete, then nothing ever goes in there.
If I have concerns about restoring the item, then I'll just copy it to my desktop or a dir. in home first.

---

### Post by mb_webguy on 2009-02-08
I very rarely use nautilus as root.  Since if I'm doing something as root I'm typically running commands in the terminal anyway, it's more convenient just to deal with files from the terminal rather than switching gears and windows to do something I can probably do with one command anyway.

If you don't use nautilus as root, then nothing ever gets put in root's Trash.

---

### Post by DeMus on 2009-02-08
> **sofasurfer said:**
> Is everyone aware of the trash can at /root/.local/share/Trash? I never heard it mentioned. Do you empty it? Delete it? Ignore it? Or is it a surprise to learn that its there?

I don't even have a /root/.local folder.

---

### Post by adamlau on 2009-02-08
.bash_logout under root does a quick rm -rf sweep of Trash.

---

### Post by drs305 on 2009-02-08
> **DeMus said:**
> I don't even have a /root/.local folder.

The folder(s) won't exist until/unless you have deleted something as root. If you delete the folder (SHIFT-DEL), it won't reappear until the next time root deletes something.

For a detailed look at how Trash works, check out the link on Trash in my signature line.

In response to the OP, normally I don't think new users are even aware of root trash until they either stumble across a file that won't delete from the Trash bin or their partition runs out of space. It doesn't really have to be emptied until those issues arise - unless you are a tidy person who likes to keep a clean house.  ;-)

---

### Post by mc4man on 2009-02-08
While I don't recommend editing there to any great extent, you can if you wish add a delete command to the root file browser (gksudo nautilus)

```
sudo nautilus-file-management-properties

```

---

