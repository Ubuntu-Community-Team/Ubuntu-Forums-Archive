---
title: "Making new MIME types with Overrides.xml in Edgy"
date: 2007-02-09
forum: Desktop Environments
---

### Post by Mank on 2007-02-09
So, I wanted to create some new MIME types, or rather, alter the MIME type-sniffing techniques Nautilus or Gnome or Linux or whatever's the culprit here uses. I've just made the transition from Mac OS 9 to Ubuntu, you see, and I want the system to automatically recognize my old Word documents, among other things.

I read the section on MIME types in the GNOME Desktop System Administration Guide, and then I tried the "application/x-newtype" example it gives. It worked, in the sense that gnomevfs-info says that testing.xyz is of the new type, but Nautilus hasn't been so well-behaved. When I open the window of the folder containing testing.xyz, the "Type" and "MIME Type" columns (I'm using list view) read "new mime type" and "application/x-newtype", as they should. But when I select the file, after a moment, the type becomes "plain text document" and the MIME type becomes "text/plain". They stay that way until I  close the window and reopen it; then, the cycle restarts. Meanwhile, Nautilus doesn't recognize the new MIME type at all in testing.xyz's Properties window, and when I use the terminal, the "file" command says it's ASCII text. (Which it is, but shouldn't "file" be affected by Overrides.xml?)

Would anyone be so kind as to tell me what's going on and how to fix it?

---

