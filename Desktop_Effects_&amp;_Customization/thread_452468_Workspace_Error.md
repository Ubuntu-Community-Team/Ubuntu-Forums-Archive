---
title: "Workspace Error"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by Kemical on 2007-05-23
As soon as I activate desktop effects, I cannot change workspaces. Only one box appears down the bottom right corner.

---

### Post by codesplice on 2007-05-23
I encountered the same problem when I tried using the fglrx driver for my ati card to run Compiz under XGL.... never could get it to play nice.  You might try right-clicking on your workspace switcher applet (it is there, right? :) ), select preferences, and change the number of workspaces to 4 (or however many you want).  You might not be able to get the pretty cube functionality working, but that will at least let you switch workspaces as you need to.

Hopefully someone else can help you with a more permanent solution :-D

---

### Post by Karsa on 2007-05-23
You might want to try this.
press alt-f2, type gconf-editor.
Go to apps->compiz->general->screen0->options
Change the value of Hzise from 1 to 4.
That should give you 4 workspaces :)

---

### Post by Kemical on 2007-05-23
I did that, however, now my Taskbar has disappeared on the other work spaces.

---

### Post by Karsa on 2007-05-23
Oh crap. I'm afraid I can't help you with that one. Never encountered anything like that before. Hopefully someone else have and they'll help you get it sorted.

---

### Post by Kemical on 2007-05-23
Alright then thanks mate. I'll just sit and wait :)

---

### Post by codesplice on 2007-05-24
Haha, mucking about with compiz has gotten me in the same state that you are... I'll let you know if I fix it :)

---

### Post by Kemical on 2007-05-24
I already got it fixed. It doesn't make the taskbar remove if you set the value to 4. But it does any less.

---

### Post by codesplice on 2007-05-24
Do you have spinny cube action?  Cause since this has been going on, the cube doesn't spin...

---

### Post by codesplice on 2007-05-24
Nevermind, got my issues worked out.  Figured out that I need to have gdm set for 1 virtual desktop, and use gnome-compiz-settings to set compiz for 4.  Now spinning occurs.  Hooray.

---

### Post by eddyr on 2007-05-24
> **codesplice said:**
> Nevermind, got my issues worked out.  Figured out that I need to have gdm set for 1 virtual desktop, and use gnome-compiz-settings to set compiz for 4.  Now spinning occurs.  Hooray.

Can you explain that in more detail thanks?

---

### Post by leopard6661 on 2007-05-24
Thanks I had the same error but Karsa said and voila it worked
thanks again

---

### Post by codesplice on 2007-05-24
> **eddyr said:**
> Can you explain that in more detail thanks?

First, set GNOME for only one virtual desktop by right-clicking on the Workspace Switcher applet.  Select preferences, and change the number from 4 to 1.

Next, install gnome-compiz-manager and gnome-compiz-manager-extras:

```
csplice@Lappy486:~$ sudo aptitude install gnome-compiz-manager gnome-compiz-manager-extras
```

You might need to add the gandalfn repository to your /etc/apt/sources.list:
```
## Compiz
deb http://gandalfn.club.fr/ubuntu feisty motu

```

Run the manager: System-->Preferences-->GL Desktop
On the Workspaces tab, change the number of Viewports to 4.

Make sure that cube rotation is also enabled, and you should be good to go.

Hope this heps :)

---

