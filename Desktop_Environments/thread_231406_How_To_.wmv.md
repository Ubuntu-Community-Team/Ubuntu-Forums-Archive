---
title: "How To: *.wmv"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Branta on 2006-08-07
Ubuntu 6.06 LTS - the Dapper DrakeDapper - x86
[B][SIZE="4"]
How do I view *.wmv files?[/SIZE][/B]



--- Bob --:rolleyes:

---

### Post by Tomosaur on 2006-08-07
Download mplayer and the 'essential codecs' pack from [their website](http://www.mplayerhq.hu/design7/news.html).

---

### Post by Branta on 2006-08-07
I am the only user GID 1000

I will install mplayer following [Debian directions here]("http://www.tldp.org/HOWTO/DVD-Playback-HOWTO/install.html")...but how do I edit> /etc/apt/sources.list 
Because I get a message the > /etc.apt/sources.list is running but I click on **edit to add this anyway** ```
deb http://hpisi.nerim.net/ stable main
deb http://www.interq.or.jp/libra/oohara/debian-unofficial/ ./
deb http://download.videolan.org/pub/videolan/debian woody main
```
 but [COLOR="RoyalBlue"]cannot save [/COLOR](I can 'Save As')

--- Bob ---

---

### Post by etank on 2006-08-07
You have to edit this file with root priviledges. First make sure that the file isn't already open then try:```
sudo gedit /etc/apt/sources.list
```

---

### Post by christhemonkey on 2006-08-07
Try following the intructions of the oficial ubuntu wiki:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

