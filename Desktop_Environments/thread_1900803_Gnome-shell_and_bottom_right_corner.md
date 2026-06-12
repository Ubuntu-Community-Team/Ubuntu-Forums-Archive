---
title: "Gnome-shell and bottom right corner?"
date: 2011-12-27
forum: Desktop Environments
---

### Post by idef1x on 2011-12-27
Does anyone know what the idea is behind the textbox that shows up at the bottom right corner as you click on an empty space on the desktop and start typing?

It doesn't seem to do anything?

---

### Post by Frogs Hair on 2011-12-27
I Haven't noticed a text box but the Pastie clipboard manager , weather indicator , and Opera icon appear there . There may be information at the link . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by Hylas de Niall on 2011-12-27
I get it too when i have an app running (ie, not in 'Activities' mode).

[IMG]http://i190.photobucket.com/albums/z59/Hylas_de_Niall/Screenshotat2011-12-27.jpg[/IMG]

---

### Post by idef1x on 2011-12-28
> **Frogs Hair said:**
> I Haven't noticed a text box but the Pastie clipboard manager , weather indicator , and Opera icon appear there . There may be information at the link . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

just left clicking on the desktop,so no application has the focus and then typing doesn't give you a extbox in the notification area? the cheatsheet wasn't helpfull for this item. it just speaks about notification area. thanks for the link though.

---

### Post by idef1x on 2011-12-28
> **Hylas de Niall said:**
> I get it too when i have an app running (ie, not in 'Activities' mode).

[IMG]http://i190.photobucket.com/albums/z59/Hylas_de_Niall/Screenshotat2011-12-27.jpg[/IMG]

that's exactly what i mean, so i am not alone ;) 
but no clue what it is meant for?

---

### Post by Hylas de Niall on 2011-12-28
No idea! :P

Possibly some Gnome Shell function that's not completely implemented yet?
(or at least in the version in Ubu Repos)

I wonder if it happens in Fedora 16 too?

---

### Post by sanderd17 on 2011-12-28
I don't have this. Can you give the version of gnome you're using, and maybe what extensions?

I'm using Gnome 3.2.1, and my working extensions are 

[LIST]
[*]Music integration
[*]Jump lists
[*]smart launcher
[*]journal extension
[*]system monitor
[*]workspace navigator
[/LIST]

Using Arch btw.

Edit: Do you still have it when you disable "let file manager handle desktop" in the advanced settings (gnome-tweak-tool)?

---

### Post by jissouille on 2011-12-28
Looks like a search box. If you have icons on your desktop, maybe it will help you find one specifically ? Unfortunately, gnome-shell does not run on my machine but this search box on my desktop does just this.

---

### Post by Hylas de Niall on 2011-12-28
gnome-shell 3.2.1-0ubuntu1 - from Ubuntu software centre
Applications menu extension 'on' (no others added)
and yep it still works without file manager handling the desktop.

---

### Post by Frogs Hair on 2011-12-28
> **idef1x said:**
> that's exactly what i mean, so i am not alone ;) 
but no clue what it is meant for?

I have never seen the text box regardless of what application is in use . :confused:

---

### Post by sanderd17 on 2011-12-28
> **Frogs Hair said:**
> I have never seen the text box regardless of what application is in use . :confused:

I see it when I enable nautilus to handle the desktop. But when I disable that, I can never get focus to the desktop. The focus is always on the last-selected window. So any key is sent to that window instead of the desktop.

---

### Post by cbowman57 on 2011-12-28
The OP must have the file manager handling the desktop, clicking is not necessary, just starting to type is all that should be required to use the search in nautilus.

(That's how I replicated it here)

---

### Post by idef1x on 2011-12-29
It's indeed only when the filemanager is handling the desktop. But no matter what I type in, it doesn't give any result and the box just disappears when hitting enter. Also nothing when there's a nautilus screen open (which has its own search box by the way in the right upper corner). So how does the desktop box work then? Looks more like a "test your keyboard settings". Maybe it's something not completely implemented yet, since if you right click on the box, you get some options for "input methods" and "Unicode control character"...

---

### Post by cbowman57 on 2011-12-29
When I type in the box it selects the file on the desktop beginning with the text I enter, it's not so much a search function as it is a file finder.  Not real useful for most desktops but it's a nautilus function.

---

### Post by idef1x on 2011-12-29
Indeed it does do highlight the file/folder what you type in...i see the light! ;)
Thanks [cbowman57]("http://ubuntuforums.org/member.php?u=1089002")
It is only useful then when you have a lot of files/folders on your desktop, which I normally don't so not really useful for me.

---

### Post by cbowman57 on 2011-12-29
> **idef1x said:**
> Indeed it does do highlight the file/folder what you type in...i see the light! ;)
Thanks [cbowman57]("http://ubuntuforums.org/member.php?u=1089002")
It is only useful then when you have a lot of files/folders on your desktop, which I normally don't so not really useful for me.


I had to explore it myself when you asked the question. :)

Handy function when you're in a directory with many files, on the desktop not so much.

---

