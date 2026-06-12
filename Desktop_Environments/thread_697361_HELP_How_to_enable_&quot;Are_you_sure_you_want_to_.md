---
title: "HELP: How to enable &quot;Are you sure you want to delete this file?&quot; prompt in Nautilus?"
date: 2008-02-15
forum: Desktop Environments
---

### Post by MoToR on 2008-02-15
Hello.

I've been looking for an answer and only saw similar unanswered questions. How to make Nautilus ask after I press Del key if I really want to delete the file? Is there something like "Are you sure you want to delete this file?" prompt in Nautilus? How came that this prompt isn't enabled by default or doesn't exist?

Thank you in advance.

---

### Post by zaynhamdan on 2008-02-15
Hi,

I think this is the default action for deleting files. I try to find some setting on gconf-editor and found no keys to change to make this default behavior.

---

### Post by MoToR on 2008-02-16
I could call it default if I had options, but it seems like I don't, so it's not a default but a fault. That's what it seems to be.

---

### Post by rainwalker on 2008-02-16
Do you mean you want to literally delete the file or just move it to the trash?
If you want to move it to trash, that's all that pressing Delete does
If you want to actually delete it, right-click the file and select "Delete". It will ask you if you are sure you want to delete it

---

### Post by MoToR on 2008-02-17
I'm looking for a setting or a tweak that will eliminate the possibility that I press Del by mistake and make maybe minor but unwanted and unnoticed changes to my filesytem.

---

### Post by Keith Hedger on 2008-02-17
The delete key just moves a file to the trash if under the nautilus preferences you have the "ask before deleteing" box checked the trash wont be emptied until you confirm also you wont be able to accidentally delete or "move to trash" a system file as you need root permissions to do that, so unless your using nautilus as root you are fairly safe, the only way to get the exact behavior you want is to download and change the source code.

---

### Post by MoToR on 2008-02-17
So right now there's no tweak or option I can change to enable the prompt. Only source code modification. Thanks. I hope I'll be able to successfully edit the code one day.

---

