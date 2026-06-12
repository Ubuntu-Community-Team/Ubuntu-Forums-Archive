---
title: "Desktop configuration file"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Da_MerV on 2010-05-04
Hello,

After several days of google searching, frustrated attempts at lsof, and exhaustive searches through my filesystem, I cannot seem to find this file.

I would like to know which file(s) are responsible for storing the positions and sizes of the icons on the desktop. I am hoping to be able to save and restore icon layouts, such as possible with a certain OS from Redmond.

Thanks for any help or hints,
~Merv

---

### Post by Dayofswords on 2010-05-04
it should be in your home somewhere...

---

### Post by Da_MerV on 2010-05-04
I would think so too. I'm afraid that really doesn't cut down my search. At all. I wouldn't expect one's personal desktop to be anywhere but.

Any ideas?

---

### Post by Da_MerV on 2010-05-04
I've found a file of potential interest.```
~/.local/share/gvfs-metadata/home-*.log
```where * seems to be some sort of hash updating every few minutes.

This file appears to change when I move a desktop icon. However, in a hex editor, the file seems to be mostly null bytes.

Any clues?

UPDATE:
On closer inspection, this file seems to be a "todo list" for updating icon data, some sort of queue before actually writing the changes to the main file. So it's this "main file" I'm looking for.

---

### Post by Da_MerV on 2010-05-04
Ok, so I think I've got a pretty good theory of how this works.

Whenever you change icons, position, or scale data, it is first added to```
~/.local/share/gvfs-metadata/home########.log
```This acts as a queue for icon changes. ######## is a hex value, and is found within the first few bytes of the file. It is 32768 bytes with a list of changes, and the rest is null bytes. When changes are pending, they are written to```
~/.local/share/gvfs-metadata/home
```the next minute. The queue file is then deleted and a blank one is created with a new ########.

With this information, I can replace```
~/.local/share/gvfs-metadata/home
```with a similar one, logout and back in, and the icons with change accordingly. So far, so good.

Unfortunately, this only works if the home directory has the same files. So now my question is, is there any reliable method of backing up the layout data of the desktop?

Thanks in advance,
Merv

---

### Post by Da_MerV on 2010-05-05
For anyone that was wondering, and to anyone that stumbles across this thread in the future, I've finally figured out how to manage this desktop icon data.

You can get the scale and position data from gvfs-info, and set the data with gvfs-set-attribute.

For instance, if I wanted icon "example.txt" at position 220,50 and 2.5x scale, I can use:```
gvfs-set-attribute example.txt metadata::icon-scale 2.5
gvfs-set-attribute example.txt metadata::nautilus-icon-position 220,50
```

I still haven't seen any utilities promising to save and restore your layout, so I decided to write one myself. I wrote a shell script "backup-desktop-layout.sh" that generates another shell script. To restore, just run the restore file it generated and logout and back in to see the changes.

It's my first big shell script, so its very messy, but it works. If you have any tips to improve it, I'd love to hear them.

Thanks,
~Merv

---

### Post by zarap on 2010-05-12
Thank's a lot for that! 
I was looking for this directory for quite a while, because I was not able to arrange my desktop-icons any more - they were auto-restored after each login or F5. Now I just had to delete the ~/.local/share/gvfs-metadata directory, log out and back in and everything is working like a charm .
I haven't tested your shell script yet, but it looks very usefully and I'll try it out later.

---

### Post by zarap on 2010-05-12
Just tested your script!
It's great - this adds a really nice new feature to my desktop which i will definitely use.
The only tiny bug I noticed was the overlapping of newly added icons after restoring, but this is no problem for me.
Thanks again for that!

---

### Post by cfth on 2010-06-04
Dude you are a champ! I haven't tested it yet, but if this works it will be *so* helpful.  This is totally one of those essential-tools to have in a toolkit. Thanks for keeping the script short too.  Great job!

---

### Post by fuzz500 on 2010-06-05
Thanks for the info Merv.
I was banging my head on this since the gvfs was introduced (gutsy?) and I couldn't do things like stack scaled icons ontop of one another and push them into the corners of the screen. 

This was also useful [http://blogs.gnome.org/alexl/category/gvfs/](http://blogs.gnome.org/alexl/category/gvfs/) for more indepth info, I found the examples about halfway down informative.

Also, If anyone cares, in Lucid, to remove the white border around desktop images, delete or rename this file 
"/usr/share/pixmaps/nautilus/thumbnail_frame.png"

Also, I am somewhat puzzled about your script. I found that the new locations that I set for files on the desktop were persistent from boot to boot. Perhaps I misunderstood the purpose of the script?

Fuzz

---

