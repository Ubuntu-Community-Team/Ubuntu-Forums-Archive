---
title: "Adding additional workspace keyboard shortcuts"
date: 2008-07-31
forum: Desktop Environments
---

### Post by andrewdied on 2008-07-31
I like to use Alt-1 through Alt-N for keyboard shortcuts, but the keyboard shortcut app in gnome only has spots for workspace 1 and 2.  Is there a way to add more?

---

### Post by falcon61102 on 2008-07-31
Depending on what you are trying to do and if you are using Compiz you can set up keyboard shortcuts through there.  What type of shortcuts are your trying to creat?

---

### Post by andrewdied on 2008-08-02
> **falcon61102 said:**
> Depending on what you are trying to do and if you are using Compiz you can set up keyboard shortcuts through there.  What type of shortcuts are your trying to creat?

if compiz is the default, that's what I'm using.  I want to create shortcuts so I can go right from workspace 1-6, but there are only defaults I can change for 1 and 2.  I normally use more workspaces than this.

I used ion3 a while back, and I really liked going rapidly from, say, 1 to 2 with ALT-1 and ALT-2.

---

### Post by sayakb on 2008-08-03
Press Ctrl+Alt+Left (or right) to switch between workspaces.

---

### Post by andrewdied on 2008-08-03
> **LinuxIsInnovation said:**
> Press Ctrl+Alt+Left (or right) to switch between workspaces.

Do you know how I can go directly to, say, workspace 7 from any workspace?  I want to set preset keyboard shortcuts per workspace.

---

### Post by pmasereeuw on 2008-08-05
I would like this feature back too. I used to have it on a previous computer with Fedora (6, I believe) and Gnome. It is very handy to have a desktop per activity (mail, programming, browsing, etc) and to go there by just pressing ALT-1, ALT-2, ALT-3 etc.

I don't know why this is currently limited to desktop 1 and 2, so if anybody has an idea: here is another person that would be grateful.

---

### Post by pmasereeuw on 2008-08-05
The solution is described here:

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg02089.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg02089.html)

It amounts to:

- start gconf-editor from the command line
- browse to Apps > Metacity > general > num_workspaces
- change the value of the key to the number of your workspaces
- close gconf-editor

You should now be able to assign keyboard shortcuts via System > Preferences Keyboard Shortcuts

It worked fine for me.

---

