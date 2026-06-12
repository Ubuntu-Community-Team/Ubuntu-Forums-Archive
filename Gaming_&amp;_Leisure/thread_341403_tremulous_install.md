---
title: "tremulous install?"
date: 2007-01-18
forum: Gaming &amp; Leisure
---

### Post by haxer on 2007-01-18
Hello i wounder how to install tremulous i found it here [http://www.tremulous.net](http://www.tremulous.net) anyone who knows how to install the stand alone version? :-k  Or which one should i install?

---

### Post by dimeotane on 2007-01-18
yea. it was super easy for me:
all I did was open the terminal and enter:

```
$sudo apt-get install tremulous
```


Tremulous is one of the linux crown jewels in my opinion.

Nothing like a little spider stomping after a hard day at work.... :twisted:

---

### Post by haxer on 2007-01-18
when i do it it says couldnt find package:(?

---

### Post by Perfect Storm on 2007-01-19
Download tremulous-1.1.0-installer.x86.run to your Desktop.

```
cd ~/Desktop
sudo sh tremulous-1.1.0-installer.x86.run
```

Exit the installer (don't push the run*/start tremulous button).
```
tremulous
```

---

### Post by haxer on 2007-01-19
Already tried that one to but when im typing in tremulous nothing happends it says that "that its only an folder" :-k

---

### Post by Perfect Storm on 2007-01-19
Hmm.... I just test it on my computer, no problem there.

Lets try:
```
cd ~/Desktop
ls -a
```

---

### Post by haxer on 2007-01-19
now it works but laggy as hell :S

---

### Post by tjb891 on 2007-01-20
very laggy for me also, i just ran the .run file from the games website and it ran fast but then there are some issues with configuring its permissions to allow you to save settings.

---

### Post by burek on 2007-01-20
> **haxer said:**
> Hello i wounder how to install tremulous i found it here [http://www.tremulous.net](http://www.tremulous.net) anyone who knows how to install the stand alone version? :-k  Or which one should i install?

I did : 
sudo apt-get install tremulous
sudo apt-get install nexuiz

no drops

---

### Post by haxer on 2007-01-20
nexuiz belongs to tremulous? Or does they have anything common togheter?

---

### Post by burek on 2007-01-20
> **haxer said:**
> nexuiz belongs to tremulous? Or does they have anything common togheter?

oups's I though you would understand :
nexuiz is another game in the same style... [http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/)

---

### Post by haxer on 2007-01-20
Yes i know both are made on quake III ? ive played both :)

---

### Post by Snoochi on 2007-01-24
ive installed and it works but whenever i try to connect to a server it says i dont have the map where can i get them?:confused:

---

### Post by JunySan on 2007-03-15
Thanks Artificial Intelligence!  It worked for me. :)

---

### Post by mixium on 2007-03-15
> **Snoochi said:**
> ive installed and it works but whenever i try to connect to a server it says i dont have the map where can i get them?:confused:

**Option 1**
You can either get the maps in one large (138 MB) package from here on my server: [http://tuxgames.net/zenwalk/games/tremulous_maps_addons-1.0-noarch-1z42.tgz](http://tuxgames.net/zenwalk/games/tremulous_maps_addons-1.0-noarch-1z42.tgz)

You will need to uncompress the package, then 

sudo nautilus

...so that you can copy and paste the contents to the directory /usr/share/games/tremulous/data

**Option 2**
You can either get the individual maps here on my server: [http://tuxgames.net/zenwalk/source/tremulous_maps_addons/](http://tuxgames.net/zenwalk/source/tremulous_maps_addons/) I built packages for other Linux distros and I keep the sources to remain GPL compliant.

You will need to uncompress them, then 

sudo nautilus

...so that you can copy and paste them to the directory /usr/share/games/tremulous/data

There is also an option that you can set (with tremulous open press ESC Options) that when you are on a server for which you have no map it will download it for you. But this option is extremely slow and not recommended.

**Option 3**
If you do not trust me or the map packages I offer you then you can get theme from here: [http://tremulous.megavoid.de/index.php?module=download&action=category&type=map](http://tremulous.megavoid.de/index.php?module=download&action=category&type=map)

I'm just offering to save you the trouble of having to chase all of those links by downloading from my machine.

:)

Michael

---

### Post by Oddgeir on 2008-05-26
I had to do:
[PHP]SUDO bash[/PHP]
then i did the:
[PHP]sudo apt-get install tremulous[/PHP]

now its downloading :)

---

### Post by awlogue on 2010-02-12
Thanks! the code worked perfectly!

---

