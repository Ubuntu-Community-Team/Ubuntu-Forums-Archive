---
title: "KDE 4 and CUPS Client"
date: 2011-11-24
forum: Desktop Environments
---

### Post by Arrouan on 2011-11-24
Hello,

I want to setup a remote cups server on my Kubuntu 11.10.
So I edit client.conf to add my server IP.
But it does not work.
Okular does not show the printer.

Anyone have an idea how to setup a cups remote server within KDE 4.

Thanks

---

### Post by teh603 on 2011-11-24
You went onto "server settings" on the workstation and checked the option to show printers connected to other systems? Its unchecked by default for some stupid reason, and gave me several hours' worth of headaches before I figured it out.

---

### Post by Arrouan on 2011-11-25
I add to the client.conf:

Encryption Always

Show printer connected to other systems only allow to browse printer on the same network.

I still have an issue. Indeed, the cups server asks for authentication. Gnome creates a popup to ask the login/password but KDE does not. Thus, I still can not print. 

If anyone knows how to make KDE launch the popup or where to hardcore the login/password...

Thanks

---

