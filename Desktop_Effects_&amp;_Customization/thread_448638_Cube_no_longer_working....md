---
title: "Cube no longer working..."
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by coinstarpatrick on 2007-05-19
Hi, 

 Compiz has been working fine on my Fiesty install, however now everything but cube works. The only thing I have done that I can think of was flashing my bios (upgrade). Is there some simple trick to get my cube back? Also, by default on each login I only have 1 workspace now. Thanks for any help.

---

### Post by Psicolonia on 2007-05-19
open terminal and type:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1


tell me if it worked

---

### Post by coinstarpatrick on 2007-05-19
That first command worked, the second one said that the directory didn't exist (or similiar). However now my cube works again, thank you! Any explanation of how that worked would be really appreciated.

---

### Post by Psicolonia on 2007-05-19
basically the cube forgets it's horizontal size. Like this, you only have one desktop but compiz cube makes 4! If you disable it you'll have one again! And it keeps that number.

You could do that manually, run gconf-editor and navigate through apps, compiz, plugin, cube.

you'll see many options there. If you want a pentagon or whatever, just change the number 4. I've made a desktop with 22 screens once!

What's happening is that compiz forgets it's horizontal screen size.

I made a script to fix it with these lines because it's frequent when you disable compiz.

---

