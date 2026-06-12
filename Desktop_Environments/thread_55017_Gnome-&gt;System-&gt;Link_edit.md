---
title: "Gnome-&gt;System-&gt;Link edit"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Sianis on 2005-08-07
Hi!

I have a little question. 

How can i edit the links under the Gnome System menu? I wanna change the Synaptic command "gksudo synaptic" to "gksu synaptic". Can I do this? Thanks any reply.

---

### Post by SFN on 2005-08-07
I don't know that you can edit the System menu. However, you can add this entry to your Applications menu using the Menu Editor.

Install [this](http://ubuntuguide.org/#menu-editor). Then click Applications\System Tools\Smeg Menu Editor. Click on the section under which you want entry added, then click the button marked New Entry. There you can put "gksu synaptic" in for the command.

One question though. Have you changed the root password so that you know what it is? If you haven't that entry won't allow you to start Synaptic at all.

---

### Post by Sam on 2005-08-07
Create a new .desktop entry in /usr/share/applications and change the Categories lines with:
```
Categories=GNOME;Application;Settings;System
```

---

### Post by Sianis on 2005-08-08
Hi all! Thanks the post, but I wanna edit THE System->Administration->Synaptic link, and not create a new. It's a security question on the GNOME panel cause', someone know my password (not ott password), can add/remove programs, casue the System->Administration->Synaptic link and it's ask my password and not root password. Where can I find the links on my machince, what I see in the system menu?

---

### Post by Sam on 2005-08-08
It's also in /usr/share/applications, the file for Synaptic is called synaptic-kde.desktop. But removing that file won't disallow someone using it. It's still possible to use the command line to launch Synaptic as root.

---

### Post by Spudgun on 2005-08-08
Or, by using SMEG, right click on the Synaptic entry and click 'Properties'.

---

### Post by Sianis on 2005-08-08
[QUOTE=Sam]It's also in /usr/share/applications, the file for Synaptic is called synaptic-kde.desktop. But removing that file won't disallow someone using it. It's still possible to use the command line to launch Synaptic as root.[/QUOTE]
 No, no. I want reach, just open synaptic with root password, and not a link to open with root password. So I need edit the System -> Administration -> Synaptic link, cause the link create is okey, but will stay a link what can open without root password. 

The SMEG just edit with aplication menu, not the System...

---

### Post by Sianis on 2005-08-10
[QUOTE=Sianis]No, no. I want reach, just open synaptic with root password, and not a link to open with root password. So I need edit the System -> Administration -> Synaptic link, cause the link create is okey, but will stay a link what can open without root password. 

The SMEG just edit with aplication menu, not the System...[/QUOTE]
 There isn't ask for this question?

---

### Post by krusbjorn on 2005-08-10
[QUOTE=Sianis]Hi all! Thanks the post, but I wanna edit THE System->Administration->Synaptic link, and not create a new. It's a security question on the GNOME panel cause', someone know my password (not ott password), can add/remove programs, casue the System->Administration->Synaptic link and it's ask my password and not root password. Where can I find the links on my machince, what I see in the system menu?[/QUOTE]

If someone would know your password and know what synaptic is, they probably would know how to open a terminal, and from there "sudo synaptic" ;)

---

### Post by varunus on 2005-08-10
I think you want to edit the following file:
/usr/share/control-center-2.0/capplets/synaptic.desktop

Use sudo gedit, and you can change the "exec" line.

---

### Post by Sianis on 2005-08-11
[QUOTE=varunus]I think you want to edit the following file:
/usr/share/control-center-2.0/capplets/synaptic.desktop

Use sudo gedit, and you can change the "exec" line.[/QUOTE]
 Yes, yes, yes this is it. Thank you very much!

---

