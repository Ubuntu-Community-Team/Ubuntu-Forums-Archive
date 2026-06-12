---
title: "How do I make a custom right-click option in Dolphin?"
date: 2007-10-19
forum: Desktop Environments
---

### Post by Shadow ZERO on 2007-10-19
In Konqueror, I used to make custom service menus so i could enqueue files in XMMS without clearing the current playlist.  How would i go about doing the same thing in Dolphin?

---

### Post by Shadow ZERO on 2007-10-20
I used to do this by creating custom service menus in konqueror, but now that Kubuntu uses Dolphin as the main file browser, i need to know how to do it with that.

For example, the first thing that I do when i install Kubuntu is remove that bad excuse for a media player Amarok.  Unfortunately, the "Append to Playlist" "Queue Track" and "Append Play" are still under the Actions submenu when i right click on a media file in Dolphin.

So I need to know how to remove those, and add one for appending/enqueing to playlist for a real audio player such as XMMS or Audacious.

---

### Post by davidjmayo on 2007-10-20
hope this gets you on track but it's not something I did before

In Dolphin hit F1 for help then see chapter 5  FAQ
5.1 has the path wher you need to save your custom service menus

---

### Post by Shadow ZERO on 2007-10-20
I Found a Bug in Kubuntu Gusty!

The directory that the Dolphin help says to put the service menu in is:
```
/home/house/.kde/share/apps/dolphin/servicemenus/
```

But the actual directory you have to put the service menu file in to get it to work is this:
```
/home/kage/.kde/share/apps/d3lphin/servicemenus/
```

Looks like a 1337 speak typo LOL!

Hope this helps someone else, I was stumped for hours on this.

---

### Post by Caffeine_Junky on 2007-10-20
I just removed Dolphin from my system, I was not impressed with it at all!

I like Konqueror much better

---

### Post by aparigraha on 2008-02-14
> **Shadow ZERO said:**
> I Found a Bug in Kubuntu Gusty!

The directory that the Dolphin help says to put the service menu in is:
```
/home/house/.kde/share/apps/dolphin/servicemenus/
```

But the actual directory you have to put the service menu file in to get it to work is this:
```
/home/kage/.kde/share/apps/d3lphin/servicemenus/
```

Looks like a 1337 speak typo LOL!

Hope this helps someone else, I was stumped for hours on this.

that's not where i find it. more like:
```
/usr/share/apps/d3lphin/servicemenus/
```

I use Audacious and made a .desktop file to enqueue a folder in Audacious:

```
cd /usr/share/apps/d3lphin/servicemenus/
sudo nano enqueue_audacious.desktop
```

paste the following:

```
[Desktop Entry]
ServiceTypes=inode/directory
Actions=EnqueueAudacious;

[Desktop Action EnqueueAudacious]
ServiceTypes=inode/directory
Name=Enqueue in Audacious
Icon=audacious
Exec=audacious -e
```

if u use XMMS just replace every Audacious entry with XMMS. and if u want to just start the player from that folder remove the enqueue option "-e"
hope it helps

---

