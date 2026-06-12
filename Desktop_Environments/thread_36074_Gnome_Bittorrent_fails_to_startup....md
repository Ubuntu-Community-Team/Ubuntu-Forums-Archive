---
title: "Gnome Bittorrent fails to startup..."
date: 2005-05-21
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-05-21
I double-clicked on the desired file and nothing happened. It simply had the little circle spinning for some time and that stopped. I didn't see a bittorrent window or anything... what gives?

---

### Post by bored2k on 2005-05-21
[QUOTE=YourSurrogateGod]I double-clicked on the desired file and nothing happened. It simply had the little circle spinning for some time and that stopped. I didn't see a bittorrent window or anything... what gives?[/QUOTE]
 I don't know, but I sincerely wouldn't suggest you use it. Get the official bittorrent source package from bittorrent.com or install azureus. [http://ubuntuguide.org/#azureus](http://ubuntuguide.org/#azureus)

---

### Post by YourSurrogateGod on 2005-06-08
Once I install it, how do I start up the client that I get from the bittorrent website? Is there some sort of a specific command? I went to the original site, but didn't find anything...

---

### Post by bored2k on 2005-06-08
[QUOTE=YourSurrogateGod]Once I install it, how do I start up the client that I get from the bittorrent website? Is there some sort of a specific command? I went to the original site, but didn't find anything...[/QUOTE]
 What file did you download ? If you downloaded the source package, after extracting it, make the file btdownloadgui.py executable (right click - properties - permissions) then double clic on it.

---

### Post by YourSurrogateGod on 2005-06-08
[QUOTE=bored2k]What file did you download ? If you downloaded the source package, after extracting it, make the file btdownloadgui.py executable (right click - properties - permissions) then double clic on it.[/QUOTE]
rpm file...

---

### Post by YourSurrogateGod on 2005-06-08
Crap, I broke one of the packages and supposed to use the "Broken" filter in order to locate it, what's that?

---

### Post by bored2k on 2005-06-08
[QUOTE=YourSurrogateGod]Crap, I broke one of the packages and supposed to use the "Broken" filter in order to locate it, what's that?[/QUOTE]
 Open synaptic - custom - broken
There you will see the package and you will be able to fix it.

Back on topic, do not download the rpm, get the source package for BT, make btdownloadgui.py executable (properties - permissions) and double clic on it.

---

### Post by YourSurrogateGod on 2005-06-23
[QUOTE=bored2k]Open synaptic - custom - broken
There you will see the package and you will be able to fix it.

Back on topic, do not download the rpm, get the source package for BT, make btdownloadgui.py executable (properties - permissions) and double clic on it.[/QUOTE]
Thanks, but one of the things that I've noticed is the fact that bittorrent doesn't work only for one file that I download, Yesy. It's weird, all of the other bittorrent files that I download work fine...

Here is the link to their site...
[http://yesy.fansub-torrents.com/](http://yesy.fansub-torrents.com/)

---

### Post by Dave_is_sexy on 2005-06-23
> Thanks, but one of the things that I've noticed is the fact that bittorrent doesn't work only for one file that I download, Yesy. It's weird, all of the other bittorrent files that I download work fine...

That'll probably be something outside of your control. like no peers, seeds or tracker. If you're new to bittorrent, it's worth finding out what they are  :smile:

---

### Post by YourSurrogateGod on 2005-06-23
[QUOTE=bored2k]get the source package for BT, make btdownloadgui.py executable (properties - permissions) and double clic on it.[/QUOTE]
[Here](http://sourceforge.net/project/showfiles.php?group_id=33044&package_id=25125) is the entire list of sources and executables that I've found. I take it that I should download a .tar.gz file? Sorry, I don't understand 100%...

I'm just curious... that and apparently the tracker rejected my version of the client *sigh* .

---

