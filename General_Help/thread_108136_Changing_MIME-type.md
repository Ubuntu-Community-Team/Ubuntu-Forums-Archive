---
title: "Changing MIME-type"
date: 2005-12-25
forum: General Help
---

### Post by Deneb Algedi on 2005-12-25
How do you do it?
I have a couple of files that won't open if i double-click them, although they have the right extension.
Instead I get a warning that says:"file extension says it is this, while mime-type says it is that... only open it if you trust the source...". 
I can still open it with the Right Mouse Button.
Other files have the same extension but with a different MIME-type and just open when I doubleClick them.
How can I change the MIME-type for those files that won't open when I double click them?

---

### Post by kaamos on 2005-12-25
You are probably talking about wmv files?

I actually have not tried this, but I think something like this should work
```
gedit ~/.local/share/mime/packages/Override.xml
```
And insert
> <?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="video/x-extension-wmv">
	<comment>WMV video file</comment>
	<glob pattern="*.wmv"/>
</mime-type>

</mime-info>
Then do
```
update-mime-database ~/.local/share/mime
```
And tell me that did it work. The idea is taken from here: [http://ubuntuforums.org/showthread.php?t=83499](http://ubuntuforums.org/showthread.php?t=83499)

---

### Post by Deneb Algedi on 2005-12-25
Looks like it worked.
Many thanks.:D

---

### Post by mcduck on 2006-01-18
That's a nice way to solve it, thanks. Until this I've just renamed all .wmv's to .asf to solve that problem :D

You should make a HowTo about that, I bet many people are having the same problem. (Thanks, Microsoft, for renaming old file formats to make them look like your own)

---

