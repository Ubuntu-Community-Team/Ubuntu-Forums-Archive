---
title: "Change KDE File Associations?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Dillius on 2005-10-15
I'm trying to figure out if there is a way to change file associations for KDE only, as I have both Gnome and KDE installed as desktops. Gnome was installed first, therefore KDE is attempting to use Totem as the default video player, which it can not do due to Arts.

Anyone able to tell me how I can change the file associations? Preferably just for KDE?

---

### Post by jeremy on 2005-10-15
If you right-click a file, then click 'open with...' then chose the programme you want to associate the filetype with, and click the box near the bottom that says 'Remember application association for this type of file'.

---

### Post by mlomker on 2005-10-15
You can also go into the Control Center.  Start, Run Command and type **kdesu kcontrol**.  Under KDE Components you'll find File Associations.

---

### Post by kalahari875 on 2006-04-15
I installed [FreeMind]("http://sourceforge.net/projects/freemind") on my Kubuntu 5.10 machine and am trying to associate its mindmap files with the application. The thing is, its mindmaps (*.mm) have the MIME type text/plain, and for the life of me I can't figure out how to get KDE 3.5.1 to not open these with Kate. Kate and KWrite are registered for text/plain, *.txt/*.TXT. How can I specify that text/plain with *.mm opens with freemind %u? ](*,) 

I've tried various things, including adding a new plain entry under text in kcontrol's File Associations, only listing *.mm, and telling it to use freemind %u, but it still opens in Kate (even though it took the existing text/plain entry and removed Kate and KWrite from its list).

---

### Post by fdoving on 2006-04-17
Go to kmenu -> run command -> Input "keditfiletype application/x-freemind" Press enter.

Now add *.mm to the extensions. Choose icon, and add the desired programs.

Save, and test.


- Frode

---

### Post by kalahari875 on 2006-04-17
[QUOTE=fdoving]Go to kmenu -> run command -> Input "keditfiletype application/x-freemind" Press enter.

Now add *.mm to the extensions. Choose icon, and add the desired programs.

Save, and test.


- Frode[/QUOTE]

I tried this but Konqueror is still opening .mm files with Kate (it also still shows these as "Plain Text Document"). Is there something else I need to set? Start a new KDE session or something?

Thanks for your help!

---

### Post by jetpeach on 2006-04-20
Are you using kde 3.5.2?  I use this version and believe I have encountered a bug where when I change file type associations it doesn't remember the changes, well it remembers them but doesn't change them.  Not sure if this is really the case for you, but it could be.
Restarting kde did not make a difference for me.

---

### Post by kalahari875 on 2006-04-21
[QUOTE=jetpeach]Are you using kde 3.5.2?  I use this version and believe I have encountered a bug where when I change file type associations it doesn't remember the changes, well it remembers them but doesn't change them.[/QUOTE]

I am now, but when I originally encountered the problem I was using 3.5.1.

---

