---
title: "Advanced Folder shortcut ??"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by CMNetworx on 2007-08-27
I am wondering, I already have created a few shortcuts to various things with the command
nautilus --no-desktop /media/Elements/Folder/

However I cannot drag and drop files into this as it is a shortcut..
Is there anyway I can have a folder on the desktop, that its contents are actually somewhere else? So when I can use that folder as if it was local to my desktop, but actually have it be somewhere entirely different?

Im sure there has to be a way of doing this, I just don't know how..

---

### Post by LukeCarrier on 2007-08-28
Hello there,

Do you mean folder redirections, something like that? I believe this feature is only available in Windoze...

Searching the web only produces links for redirecting from a folder in Windoze to one on a linux server.

I'll post back if I find anything.

Best Regards,
Luke Carrier.

---

### Post by CMNetworx on 2007-08-28
One of the guys I talked to mentioned something about Soft Linking?
As far as I know its on a linux machine, but It may just be the same as a link, Im not sure. I know that I have seen it when I log in with certain ftp programs they sometimes have a link that emulates /www and really goes to /html_public or something along those lines..

I never knew you could do that on a windows machine. I just started using Ubuntu linux, have been for about 3 months now and I really like it. I hope others will do the same with the emergence of vista.

---

### Post by raijinsetsu on 2007-08-28
Soft-linking(more often called Symbolic Linking) must be done from the terminal.
example:
```
cp -s /src ./dst
```
where src is the directory you want to link, and dst is the place you want to link it to. In your case, you probably want to link it to your desktop, so you'd probably want
```
cp -s /src ./Desktop/dst
```

Newer versions of Windows support hardlinking(not quite the same), so, to make up for this deficit, Explorer(not the OS) uses .lnk files for file and directory redirection.

Hope that helps.

---

### Post by CMNetworx on 2007-09-17
Here is what I eventually found that worked...

of course this has to be done in the console also, but I've got my console as my sleep hotkey.

ln -s /media/Elements/Pages /home/cmnetworx/Desktop/Pages

This provides me with a link that if I open it in the save dialogue box in firefox or something, the link will follow through to the folder instead of giving me an "this is a link you idiot" message. Versus a launcher would just give me an error msg.

---

