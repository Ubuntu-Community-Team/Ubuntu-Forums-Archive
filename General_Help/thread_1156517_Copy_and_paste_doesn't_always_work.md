---
title: "Copy and paste doesn't always work"
date: 2009-05-11
forum: General Help
---

### Post by feedmecereal on 2009-05-11
I upgraded from Intrepid to Jaunty beta 1 and then to the current stable release. Ever since beta 1, copy and paste has sometimes failed to work. What happens is that I will try to double click on some text and it will change color and then I right-click and select copy. But when I go to paste it, the "copy" option in the context menu is grayed out as if it was never copied.

I thought it would be fixed by the time I upgraded to the stable version but I still have this problem every once in a while.

So, any ideas?

---

### Post by geraldvillorente on 2009-05-11
try **cp** or **mv** command...
cp = copy
mv = move or cut

example:
sudo cp [source file] [target directory]
sudo mv [source file] [target directory]
**sudo cp -R foo /home** for directory or **sudo cp foo.txt /home** for file
**sudo cp -R /home/foo /home/root/Desktop** or **sudo cp /home/foo.txt /home/root/Desktop**

Also, check the man page for cp and mv commands.
In terminal type these:
[B]man cp
man mv[/B]

---

### Post by Tipped OuT on 2009-05-11
It's true, if you copy text from a .txt file, for example, and you close it, you can't paste what you copied any more, only if you keep the .txt file open.

---

### Post by feedmecereal on 2009-05-11
I think you two might believe that I'm referring to the terminal, but I'm not. This mainly happens when I want to copy and past from Firefox to another program. I have Firefox open when I try to copy and past.

---

### Post by Iowan on 2009-05-11
Although I haven't had problems from inside Firefox, The terminal hs caused issues - but seems to work if I use the toolbar _E_dit copy/paste options.

---

### Post by geraldvillorente on 2009-05-11
try to use shortcut keys
CTRL+C for copy and CTRL+V for paste (think this is more precise than the traditional copy/paste method...

---

### Post by Zoowey on 2009-05-11
If you copy something then close that program you can't paste. Go into Synaptic and install "glipper" then go to your panel, right click and select "add to panel..." and select glipper. With this tool you'll be able to paste something from a closed program. It may take some time to show up in the "add to panel.." list.

Hope this helps.

---

