---
title: "Metacity Mistake"
date: 2009-02-25
forum: General Help
---

### Post by gunksta on 2009-02-25
I hope there are some Metacity geniuses out there. How do I delete all of Metacity's settings? I seem to have created a terrible setting for Writer.

I'm using Intrepid and whenever I open up Writer, Metacity fails to draw a window border around Writer. When I open Calc, Base, etc. Metacity does draw a window border. My problem appears to be ONLY with Writer. This results in a permanently "maximized" application. When I am viewing a Writer window, I can not access my panels at the top or bottom. However, I can Alt-Tab to another window if I so desire, at which point I am once again given access to my window borders and panels. This is . . . weird.

I looked at the manual and Alt-F5 should "un maximize" a window, but when I do this, I get no response. Writer remains "maximized". But, when I hit Alt-Space, I DO get the Metacity Window menu, just like I should. In this menu, there is an option titled "Move Titlebar On Screen". I have tried to select this option, since it sounds really nice, but nothing changes. 

I looked in .local, .gnome, and .gnome2 but I didn't see anything that looked like Metacity settings, but I could have missed something.

I should mention that I am using Writer from the OOo PPA. But, I don't think that is the problem.

Any suggestions to get Metacity to put a window border around Writer again?

Thanks!

Edit 2/26/2009 - Changed the name of the thread to better reflect what I am trying to learn.

Edit 3/2/2009 - SOLVED - By deleting .openoffice.org, I got Metacity to work correctly with Writer. I don't know why this was only happening in Gnome and not XFCE. Now I have to download all of my plug-ins and start over.

---

### Post by smani on 2009-02-25
You aren't using compiz by any chance are you? In case in the CompizConfig settings manager, under window decorations you can choose which applications have a border and which not, maybe you'll find something there. Otherwise as a workaround you could try Devil's pie ([http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)) which allows you to tweak some window settings even under metacity - maybe you are able to restore the border that way - but would only be a workaround...

---

### Post by gunksta on 2009-02-25
I am using Metacity, with-out compositing.

I had not thought od devil's pie. I may give that a go.

Alternatively, I could just use XFCE, which is installed on this machine as well. But, I would rather wipe out my Metacity settings and see if I can restore everything to proper working order.

---

### Post by gunksta on 2009-02-26
bump

---

### Post by smani on 2009-02-26
Well in this case you would have to locate the source of the error. One way is by creating a new account and logging into that one to see if the issue exists there too. In that case it would mean that a configuration file in your home directory is broken.

---

### Post by gunksta on 2009-02-26
Yep. I created a temporary user last night and tried everything out, and OOo worked as expected. It also works correctly under XFCE, regardless of who I log in as, so the problem is definitely a problem local to my current gnome installation.

Which, leads me back to me the heart of my original question - Does anyone know where metacity stores it's settings? I want to delete them. I would prefer to NOT do a "rm -rf .*" in my ~ directory. I would prefer to do something a little more precise. But, I can't find metacity's settings (or I am unable to recognize them as such).

---

### Post by smani on 2009-02-26
I'd suggest somewhere like .gconf or .gnome*, but just try to rename a few of the suspect-folders and log back in so that default entries are created, once you have found the folder, you can proceed that way.

---

### Post by gunksta on 2009-03-02
After playing around with moving .gnome, .gnome2, .local, etc around, I was still faced with Writer using the entire screen, while Calc, Base, etc had a window wrapper around it.

For some reason, deleting .openoffice.org fixed the problem.

This really surprised me, because Writer works correctly in XFCE.

Oh well. Writer is now behaving like a good program again and I no longer want to strangle Metacity.

---

