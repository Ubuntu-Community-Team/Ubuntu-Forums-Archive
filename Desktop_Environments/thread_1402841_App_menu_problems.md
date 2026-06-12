---
title: "App menu problems"
date: 2010-02-09
forum: Desktop Environments
---

### Post by Hellenion on 2010-02-09
hey,
I've got a problem with my applications menu,
when I click the applications menu, it does not show the actual menu, just some empty ~5*15 pixel box...

also the menu editor does not work anymore (it did before). my system activity measuring thingy shows some activity at first, but then it stops and the menu editor never pops up :(

it first occurred when I ran the menu editor, and ticked the box to put the menu editor itself in the applications menu, no problems so far, but after I had used the menu editor located in the applications menu itself, the applications menu stopped working (as described earlier)

after some search on the web, this site offered the solution, I fixed it =)

but something like a month later (now) i did the same thing: putting the menu editor in the applications menu and running it. just ticking tick-boxes, like, editing the menu.

now i'm stuck with the same problem and I'm unable to find the solution I used earlier to fix it (or I did find it but didn't work)
this makes me think it's a bug or a flaw or I don't really know the proper name for it.
i acknowledge it could just be my system that's ****** up but it might just be an unfixed bug :P

it might also be cause there are non-existent wine applications in the menu, or just wine applications, can't remember if I had uninstalled them, too lazy to check ;)

(reinstalling alacarte does not work, neither does re-booting, or killing the gnome-panel)

does anyone know what might have caused it or (even better) how to solve or prevent it?

Thanks in advance,
Hellenion

---

### Post by Hellenion on 2010-02-14
i really was in need of the applications menu lately, so i really started to dig in the unbuntu forums and tried every possible solution.
eventually i stubeled across this:

[QUOTE=Brandel Valico]
October 1st, 2007, 07:26 AM

Just had this happen to me. My Applications menu stopped working. To fix it I Copied the information from the Applications menu found at /etc/xdg/applications.menu

To the one found in the Home Folder/.config/Menus/applications.menu

It completely restored my application menu to working order and so it shows all my installed applications as well.

Hope this helps those still having issues with this

[/QUOTE]

/etc/xdg/applications.menu
in my case this was: /etc/xdg/menus/applications.menu

Home Folder/.config/Menus/applications.menu
was: Home Folder/.config/menus/applications.menu

but it worked :)

any idea how the files get messed up like this?

---

