---
title: "Nautilus shortcut only works sometimes"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-04
I put a shortcut to the command "sudo nautilus --browser /" on my desktop to serve a file browser that lets me manipulate files. (removing sudo makes it work, but defeats the purpose as I can't actually do anything without it.)

Sometimes this shortcut works, but it usually doesn't. If it is working, rebooting breaks it. How can I make this shortcut work all of the time, and why is it bugging up and not runnign when I click it? Entering the command through the terminal works every time.

---

### Post by crash369 on 2005-06-04
this is a total guess on my part, but i think it doesn't work because it requires a password, but has no way to ask you for it.

it works sometimes, because the system keeps the last sudo password (if you use sudo in a terminal, for example), or at least it does so for me.  if it has a stored sudo password, it opens nautilus.  if it doesn't, it stalls at "what's the password?" stage.

like i said, total guess on my part, but hope it leads you in the right direction.

---

### Post by Curlydave on 2005-06-04
Hey, I think you're right! If I run somethign else that provides that password GUI, eg synaptic system manager, the nautilus shortcut works until a reboot. That's a temporary fix, but any suggestions for a permanent one would rock. Maybe some command that prompts the pword gui or enters it automatically?

---

### Post by crash369 on 2005-06-04
try this

[http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus](http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus)

---

### Post by Curlydave on 2005-06-04
Hey, thanks man! It works now. Based on that link, it turns out that there were two things wrong; I needed "gksudo" instead of "sudo", and I needed quotes around it because I added the --browser and / commands.

---

