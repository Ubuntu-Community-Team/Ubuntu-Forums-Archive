---
title: "How do I resume a download with gnome-btownload?"
date: 2005-03-16
forum: Desktop Environments
---

### Post by frijolito-ts on 2005-03-16
Hi all,

(First off, I am running Hoary and have just updated/upgraded a few minutes ago.)

I had gnome-btdownload running for a few days now (three separate instances actually since it doesn't allow multiple downloads) and occasionally when I returned to my PC in the morning I would see some (10, 20 maybe) "warning" windows that read something like "Error connecting to tracker". BTW, these windows cannot be closed by clicking the "OK" button.. you have to close them some other way.

Anyway, when I sat down today in the morning at the PC that had been downloading all night, I find that there are 250+ of those warning windows! I tried to close them, but my system was really slow and unresponsive (I imagine, due to all of the memory consumed by the different gnome-btdownload programs running), so there was no practical way to close them other than running from a terminal "killall gnome-btownload". Even after I did that, and all the windows had closed (including my download windows!), the system was so slow that I decided the best course of action was to reboot.

So, I rebooted now, and everything is working fine... but how can I resume those downloads? Please don't tell me I have to click again on the same URL in firefox because for the life of me I cannot remember where those links are.

I know there must be some way to resume the download, right? Right?

---

### Post by iomicifikko on 2005-03-16
[QUOTE=frijolito-ts]Hi all,

(First off, I am running Hoary and have just updated/upgraded a few minutes ago.)

I had gnome-btdownload running for a few days now (three separate instances actually since it doesn't allow multiple downloads) and occasionally when I returned to my PC in the morning I would see some (10, 20 maybe) "warning" windows that read something like "Error connecting to tracker". BTW, these windows cannot be closed by clicking the "OK" button.. you have to close them some other way.

Anyway, when I sat down today in the morning at the PC that had been downloading all night, I find that there are 250+ of those warning windows! I tried to close them, but my system was really slow and unresponsive (I imagine, due to all of the memory consumed by the different gnome-btdownload programs running), so there was no practical way to close them other than running from a terminal "killall gnome-btownload". Even after I did that, and all the windows had closed (including my download windows!), the system was so slow that I decided the best course of action was to reboot.

So, I rebooted now, and everything is working fine... but how can I resume those downloads? Please don't tell me I have to click again on the same URL in firefox because for the life of me I cannot remember where those links are.

I know there must be some way to resume the download, right? Right?[/QUOTE]
 --> im a newbie <--

ok, first of all when start a torrent remember to save the ".torrent" file too so u won't have these kind of problems;). then i have not hoary but warty and there is not btdownload so i dont use it but if i was u id try these things:

a torrent is not just a text file with the url of the tracker and the file name so i think that u must find the actual torrent.

maybe it could be somewhere in your home directory: i'd try to search in your home if there is a .btdownload directory or something like that  or u can try in firefox cache directory at /home/teo/.mozilla/firefox/default.k13  (i'm teo, use your home dir name) but in that directory pay attenction at the file type (.torrent) couse its full of strange names.

if u cant find the file in your disk u have to find out that file in the net one more time, maybe the name of the torrent could hep u. -> try searching for a log file of btdownload, that could give u some info (try in that .btdownload directory in your home if it exist or use synaptic and select the pack of btdownload, then right click on it and choose "file installed", scroll down the list and look at any files that sounds like a log file).

if u can find the name try google then put the name with extension between "" and in advanced search set "search in url pages" and start hoping.


well anyway as i told u at the beginning im a newbie, maybe there is a 2click passage to find all u need;)

byezzz

---

### Post by frijolito-ts on 2005-03-16
hehe thanks a bunch for the reply!

sadly, what I'm looking for is a way to *avoid* searching on the web for the files again!

let me tell you about an experience I had using bittorrent in (gasp!) windows: I had left bittorrent running for a couple of days, and some moron unplugged the power supply from my pc! the next morning, I fired it up again and lo and behold, bittorrent just resumed downloading as if nothing had happened.

I *know* gnome-btdownload must save somewhere the urls to resume the download! if anyone can point me to the way to do this I will be most grateful!

---

### Post by bored2k on 2005-03-16
[QUOTE=frijolito-ts]hehe thanks a bunch for the reply!

sadly, what I'm looking for is a way to *avoid* searching on the web for the files again!

let me tell you about an experience I had using bittorrent in (gasp!) windows: I had left bittorrent running for a couple of days, and some moron unplugged the power supply from my pc! the next morning, I fired it up again and lo and behold, bittorrent just resumed downloading as if nothing had happened.

I *know* gnome-btdownload must save somewhere the urls to resume the download! if anyone can point me to the way to do this I will be most grateful![/QUOTE]
 bittorrent.com , this one saves your files and is MUCH better than crappy gnome-bt.
gnome-bt is based on old bt released ages ago.

---

