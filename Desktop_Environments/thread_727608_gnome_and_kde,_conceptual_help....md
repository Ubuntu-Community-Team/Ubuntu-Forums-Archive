---
title: "gnome and kde, conceptual help..."
date: 2008-03-17
forum: Desktop Environments
---

### Post by kforum on 2008-03-17
quick question... does gnome have registries? and if so how does it work...

registries and dlls are some of the main reasons as to why does windows, ultimately, lags your pc and crashes your to death x.X

so please give me the whole speech; also i hear kubuntu is more of a stand alone architecture(if i can call it that), as in it DOESN'T have registries...

so please, please share any info on anything regarding all related subjects, ive searched inside the forums... found nothing on this, unfortunately.

thanks in advance.

---

### Post by fifth on 2008-03-18
If you mean 'Registries' as in the ms windows method were the os and its apps are supposed to store all there settings in one file, then no. Neither Gnome nor KDE use this method. Have a look in your home folder for hidden files, thats where all your app settings are, in seperate files. Most of the os settings are stored in the /etc folder. Again, different parts of the system use different files.

Linux does have an equivalent of dll files. Many programs make use of library files which share common functions between programs. The library files typically have a '.so' extension.

---

### Post by tubasoldier on 2008-03-18
fifth is right on. Linux does not have a rediculous registry. No putting all the eggs in one basket.
Your system config files are all in /etc 
However, you may notice that there are hidden files in your home directory. /.firefox /.mozilla /.gnome ...  These folders are where your user configurations are saved. You can view the hidden files in nautilus by pressing ctl+h, if i remember correctly.

---

### Post by kforum on 2008-03-18
i can deal with the existence of library files i think, but im not so sre about these 'config files'.

does both gnome and kde have them? and are they, in teh long run, efficient? unriliable? dangerous(security-wise)? or, anything i havent mentioned?

so more explanation on that would be great if u guys can give it.
be mindful that im asking questions here, i really wanna be sure of this...

thanks again for the replies :)

---

### Post by p_quarles on 2008-03-18
Configuration files in Linux bear little resemblance to the Windows registry. For one thing, nearly all of them are plaintext files, and the few that aren't tend to be in widely used text formats such as XML (this is true, for instance, of Gnome's configuration files). 

More importantly, they are all separate. Thus, a bad setting in the config file for, say, SSH, will not affect the functioning of the X server. 

Finally, both Gnome and KDE are very high-level parts of the system. Neither one is necessary for the system to run, and they are consequently not usually important parts of the system's security.

---

### Post by kforum on 2008-03-18
also, does xfce have something like gconf on it?
(this may sound off topic, but its right in with the 'conceptual' questions, since to me, so far, gconf is a registry-but-improved interface.)

---

### Post by p_quarles on 2008-03-18
> **kforum said:**
> also, does xfce have something like gconf on it?
No. Xfce inherits gconf settings, but isn't dependent upon them.
> (this may sound off topic, but its right in with the 'conceptual' questions, since to me, so far, gconf is a registry-but-improved interface.)
Yes, these are conceptual questions. Please don't hesitate to search/ask furthere.

---

### Post by kforum on 2008-03-18
so let me refrase that, does xfce use a gconf style setup? or what?
how does it config its files?

im asking mostly because i really dont like centralised config ideas, and im having trouble chosing a linux distro/DE because of that... everything just lacks the info i need to understand.

you do a lot of reading, but its really hard to find these 'simple' answers anywhere, mostly all ppl talk about is -my de is better then yours becaue~~~~ or something of a sort.

any grand or small info here is truly appreciated.

---

### Post by samwyse on 2008-03-18
xfce configs are in ~/.config/xfce4 as xml files.

---

