---
title: "Nautilus - Thumbnails without caching?"
date: 2009-04-18
forum: Desktop Environments
---

### Post by Coltin on 2009-04-18
Is it possible to have thumbnails in Nautilus without caching, or have caching directly in RAM? I'm exploring all avenues to avoid any writes to main storage. I'm working strictly with a 4gb SSD for everything, so space is a premium I want to constrain as much as possible.

I'm using the latest stable release of Easy Peasy, with an up to date Nautilus.

---

### Post by davec64 on 2009-04-18
Haven't got a clue on the actual answer but thought it an intersting question so I started delving!

I found this on "reducung Disk Writes" in the Easy PEasy Documentation:

[http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive]("http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive")

So what about adding to fstab something like:

```
tmpfs </PAth To Cache/> tmpfs defaults,noatime 0 0
```

You might need to play around with the permissions.

---

### Post by davec64 on 2009-04-18
I was just thinking a bit more and you might run into trouble if you view a lot of images as the cahe wouldn't get cleared until you rebooted.
So therefore you might want to write a script that empties the cache. You could then set it up using cron to execute every so many minutes .

---

### Post by StuartN on 2009-04-19
> **Coltin said:**
> Is it possible to have thumbnails in Nautilus without caching, or have caching directly in RAM?

You can disable the thumbnail cache under Preferences->Preview within Nautilus if you want to save space. Thumbnails won't involve rewrites to your SSD though, unless the source images change, so once written they are only read.

---

### Post by Rigrig on 2009-05-28
You can also have the folder where Nautilus saves it's thumbnails point to /dev/null:
Open a terminal, then type
```
cd ~
rm -r .thumbnails
ln -s /dev/null .thumbnails
```
Now if you enable thumbnails they are generated every time you view a folder, but won't be saved to disk.

---

### Post by faixan on 2010-11-02
> **Rigrig said:**
> You can also have the folder where Nautilus saves it's thumbnails point to /dev/null:
Open a terminal, then type
```
cd ~
rm -r .thumbnails
ln -s /dev/null .thumbnails
```
Now if you enable thumbnails they are generated every time you view a folder, but won't be saved to disk.

Great tip, thanks... took me 3 hrs to figure out what's been eating up all the space...
but i still feel risky using this method since i don't know the reversal...
please tell if i make this symbolic link, how can i remove it later on (this one specifically)

---

### Post by MestreLion on 2011-06-15
To restore previous behaviour is as easy as deleting the symlink and re-creating the folder:

```

cd ~
rm .thumbnails
mkdir .thumbnails

```

---

