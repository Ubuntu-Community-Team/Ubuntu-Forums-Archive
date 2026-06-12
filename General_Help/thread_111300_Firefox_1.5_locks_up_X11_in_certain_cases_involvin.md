---
title: "Firefox 1.5 locks up X11 in certain cases involving XML + SVG compound documents"
date: 2006-01-02
forum: General Help
---

### Post by Kethinov on 2006-01-02
Hi all. I installed Firefox 1.5 from the binary provided at mozilla.com. I'm currently developing a webapp that uses SVG in a compound XML document. Whenever I resize the SVG, it locks up my X11 session.

Anyone brave enough to confirm that this bug is not limited to me?

Go here: [http://halo43.com/beta/map_view_moz.php?gid=2](http://halo43.com/beta/map_view_moz.php?gid=2) then right click on the black and change the zoom level.

---

### Post by Tuf on 2006-01-02
Probably doesnt help you much but its works well for me in Firefox 1.5, but I'm on Win XP at the moment.

BTW - Nice Page!

I'll check it again later when I am on Linux :)

---

### Post by jarechu on 2006-01-02
It works for me without problems. It could be a bug in your graphics card driver. I am using nvidia 7174 for Geforce chipsets, but I am a newbie.

---

### Post by steve.horsley on 2006-01-02
No problems for me. Using Firefox 1.5 from the Mozilla site, on Breezy. My only plugin is Sun java 1.5.  
Extensions installed are:
  Talkback 1.5 (installed by default)
  DOM Inspector 1.8 (optional part of the firefox install)
  NoScript 1.1.3.4
  Adblock 0.5.1.055
  Web Developer 0.9.4
Graphics: nVidia MX400, using the 3d driver packaged in Breezy repos.

---

### Post by Kethinov on 2006-01-02
[QUOTE=steve.horsley]No problems for me. Using Firefox 1.5 from the Mozilla site, on Breezy. My only plugin is Sun java 1.5.  
Extensions installed are:
  Talkback 1.5 (installed by default)
  DOM Inspector 1.8 (optional part of the firefox install)
  NoScript 1.1.3.4
  Adblock 0.5.1.055
  Web Developer 0.9.4
Graphics: nVidia MX400, using the 3d driver packaged in Breezy repos.[/QUOTE]

Strange. My setup is almost identical to yours. The only difference is I installed my NVIDIA driver by using NVIDIA's installer. I wonder if that's the cause of my troubles.

I get other bugs with FF too. For example, if I save any file on any web page as, my browser lags for a while then a new line on the menu bar appears. After which, the browser still works, but the bookmarks menu glitches somewhat.

---

### Post by kperkins on 2006-01-03
Works fine for me.  Taht's pretty cool. (are all the stars supposed to bunch up like that at Zoom 1?)
(Using FF1.5 installed according to the Wiki--on a Laptop--I have a bunch of extensions, and plugins, no nvidia graphics though)

---

### Post by Kethinov on 2006-01-03
Yes, they are. But I'll probably remove the level 1 zoom and a few other low levels when this is done. That does look pretty silly.

---

