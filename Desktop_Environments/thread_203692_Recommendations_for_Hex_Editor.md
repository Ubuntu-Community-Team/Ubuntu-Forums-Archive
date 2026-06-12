---
title: "Recommendations for Hex Editor??"
date: 2006-06-25
forum: Desktop Environments
---

### Post by tirofiban on 2006-06-25
Hello,

I'm looking for recommendations for a hex editor for Dapper. I need something that will write to specific sectors on a floppy disc. 

My mother-in-law somehow got locked out of the bios on her Toshiba laptop. Supposedly, writing some hex numbers to sector 2 and booting this disk will do the trick. I haven't used a hex editor since my old Atari computing days. So something that's easy to use is a plus. Something that's easy to install is also a plus. I searched Synaptic, but nothing came up.

Thanks,
Marc

---

### Post by nanotube on 2006-06-25
there's ghex...

---

### Post by LKRaider on 2006-06-25
Ghex is easy to use and has a GTK interface, but you cannot directly open disks with it (you would have to dump the disk to an image file, edit the file, and write the image file back to the disk).

You can try using the **ncurses-hexedit** available on Synaptic. It must be run on a terminal, but is quite simple to use, and with it you can directly edit disks ( for example, run: '*sudo hexeditor -d /dev/fd0*' to open a floppydisk).

Look at the man page to see how it works, or check the website [http://www.chez.com/prigaux/hexedit.html](http://www.chez.com/prigaux/hexedit.html)

---

### Post by VirtuAlex on 2006-08-15
I do not know who wrote ghex, but guys are nuts. Sane editor would display data by 16 byte offsets. ghex displays it as a stream. With default Monospace 12 ghex shows 17 bytes! Moreover, the cursor field is couple pixels off, so when I'm trying to edit bytes at the end of the line, it displays the value far away from the byte I'm editing. See the screenshot. And finally it totally ignores NumLock and treats the numeric panel as cursor keys. And this bug-bag they include in repos! ghex is garbage as of version 2.8.1.

---

