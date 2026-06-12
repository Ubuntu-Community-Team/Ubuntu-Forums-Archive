---
title: "Terminal not available"
date: 2006-04-28
forum: Desktop Environments
---

### Post by bonefishchris on 2006-04-28
Trying to open terminal. When I go to Applications menu - System Tools , terminal is not on the list. When I look for it in 'add applications - system tools' it's greyed out and when I double click it it tells me that it's an unavailable program. The computer I have installed 5.10 on is not connected to the internet (that's what I'm trying to do) so I have tried downloading gnome-terminal_2.12.0.orig in both tar and  deb forms (I don't know the difference). For .deb I get the message that this archive type is not supported and for .tar that I don't have permission. I've searched these treads and see that to install applications I need to open Terminal and...

I have found Root Terminal, but I guess that's not quite the same thing. In any case it doesn't seem to recognise any directories I try cd-ing.

Help please?

---

### Post by simplyw00x on 2006-04-28
What happens if you press Alt+F2 and enter 'gnome-terminal'?

---

### Post by bonefishchris on 2006-04-28
Thank you - I get a terminal window that looks like the one I want! It's headed <myusename>@ <mycomputername>:~

I still can't get it to cd to where I want, but that's another problem I guess.

Any idea how I can get Terminal to show up in the application list though? It sounds like I'm going to need it frequently.

---

### Post by Ramses de Norre on 2006-04-28
applications > system tools > applications menu editor
Add new entry: command=gnome-terminal --working-directory=%f
Your free to choose the other fields.

---

### Post by bonefishchris on 2006-04-30
OK ... a couple of points though - 

1 - Not sure where I should enter the working directory. I tried adding it on the end of 'the command exactly as you had written it (including --) Also entered 'Terminal' in the name field. When I click 'Terminal' in apps>system tools, nothing happens. When I removed the working directory portion, it now brings up the correct terminal window.

2 - Is there a reason Terminal was not in the sys tools menu in the first place? ie - why should my install be any different to everyone elses?

---

### Post by _linux_ on 2006-04-30
Did you check in Applications > Acessories > Terminal? That's where it is on my computer.

---

### Post by bonefishchris on 2006-04-30
ah-HA! I read this in the Wiki:

In Ubuntu 5.04 (Hoary Hedgehog): Applications menu - System Tools - Terminal; or right-click on any empty area of desktop and choose "Terminal".

I guess it's changed in Breezy. Should have looked around a bit more I guess. Maybe I should change my login to boneHEADchris. Anyway, thank you one and all for the help.

Now to get my wireless adapter working...

---

