---
title: "Uninstall Enemy Territory"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by Dinerty on 2006-07-14
Hi all

 On the new Ubuntu and wish to remove Enemy Territory, I'm using the KUbuntu (KDE)

```
sudo rm -rf /usr/local/games/enemy-territory/
sudo rm -rf /usr/share/gnome/apps/Games/et.desktop
```


```
rm -rf ~/.etwolf
```

**Taken from endy post**

I don't want to enter this incase I muck my system up, I installed ET in the default directory and have a launch icon in "Lost & Found"

---

### Post by Dinerty on 2006-07-14
It's ok I deleted them now ! :D

---

### Post by Mr_HeNtAi on 2006-07-14
I wish there was a better cleaner way to unistall software. I guess I'm still used to the way some other OS's handle uninstallation.

---

### Post by The Noble on 2006-07-14
I concur, Linux needs an easier way to uninstall programs. Sure, you can remove programs with the install deb, but who wants to keep all of the install files? Maybe debian will rework the .deb file type to have this functionality.

##Please ignore this comment, as I was new and had no clue what I was talking about##

---

### Post by nicoladimaria on 2007-03-12
> **Dinerty said:**
> 
 On the new Ubuntu and wish to remove Enemy Territory
[...]

thanks

---

### Post by dmn_clown on 2007-03-12
> **The Noble said:**
> I concur, Linux needs an easier way to uninstall programs. Sure, you can remove programs with the install deb, but who wants to keep all of the install files? Maybe debian will rework the .deb file type to have this functionality.

Why would they change something that works perfectly fine?  Or are you saying that you've never uninstalled something by accident and had to re-install and then reconfigure?

If you want apt to remove everything from a package that is what the -purge flag is for.

Considering that et uses the loki installer there IS a way to uninstall it without using rm -rf ```
./uninstall
Usage: ./uninstall product to uninstall the product
       ./uninstall -l      to list all products
       ./uninstall product -l        to list all components
       ./uninstall product component to uninstall a single component

```

---

### Post by The Noble on 2007-03-12
I revoke my previous statement, as that was a month* after I started using Linux. Now, I know better and I still don't know what I was getting at. Ah, the beauty of naivety...


*Now that I think about it, it may have been a few months, but you get the idea.

---

### Post by _Void on 2008-10-21
Thank you very much everyone, I am new to Ubuntu (ex-Window$ user).
I have learned allot from this thread.

Cheers!

---

### Post by powerqun on 2008-10-22
An old lady's husband had just died and she felt their was no reason to live anymore. She called the doctor and asked exactly where her heart was. He told her it should be under her left breast. That night she went to the emergency room with a shot in the knee.     ....................................................................................................................................................buy [world of warcraft gold](http://www.mmoinn.com/)| cheap [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)| site: [http://www.mmoinn.com](http://www.mmoinn.com)|cheapest [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)|buy [wow gold](http://www.mmoinn.com)

---

### Post by Legendário on 2010-01-06
> **dmn_clown said:**
> Why would they change something that works perfectly fine?  Or are you saying that you've never uninstalled something by accident and had to re-install and then reconfigure?

If you want apt to remove everything from a package that is what the -purge flag is for.

Considering that et uses the loki installer there IS a way to uninstall it without using rm -rf ```
./uninstall
Usage: ./uninstall product to uninstall the product
       ./uninstall -l      to list all products
       ./uninstall product -l        to list all components
       ./uninstall product component to uninstall a single component

```

I know this thread is old, but i just couldn't find the uninstall script...

```
$ ./uninstall -l
bash: ./uninstall: Arquivo ou diretório não encontrado
```
File not found. Is there a specific path for that?

---

