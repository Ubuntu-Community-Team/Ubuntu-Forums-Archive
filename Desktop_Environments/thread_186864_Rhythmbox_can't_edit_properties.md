---
title: "Rhythmbox can't edit properties"
date: 2006-06-02
forum: Desktop Environments
---

### Post by jdbartlett on 2006-06-02
In Rhythmbox, when I right-click on a track and click 'properties' to edit its ID3 tags, I cannot write anything in the edit boxes. They are filled with data, but it is not correct. I want to be able to change the artist name, song title, etc.

After searching the Ubuntu forums for solutions, I've installed EasyTAG from the repo and that works well to edit ID3 tags, but it doesn't actually solve the problem with Rhythmbox. Has anyone been able to solve this in Dapper? Thanks!

---

### Post by Rackerz on 2006-06-02
I'm not too certain how it works in Rhythmbox but by anychance would the file your trying to edit thr tags for is on an NTFS drive? I'm just brainstorming :).

---

### Post by jdbartlett on 2006-06-02
No, it's default Linux filesystem. It's pretty much a fresh install of Dapper (installed yesterday!) There's no other OS or filesystem on the box.

---

### Post by simms on 2006-06-02
[QUOTE=jdbartlett]In Rhythmbox, when I right-click on a track and click 'properties' to edit its ID3 tags, I cannot write anything in the edit boxes. They are filled with data, but it is not correct. I want to be able to change the artist name, song title, etc.[/QUOTE]

afaik, rhythmbox does not support tag editing at all (at least not the version that ships with Breezy).  but EasyTag is indeed a great solution -- the best I've found so far.

---

### Post by PriceChild on 2006-06-02
Don't like easytag.... i use Amarok inside Dapper.

Even though its a KDE app, it works perfectly in GNOME and does everything! (including id3 editing and ipod synching.)

---

### Post by cbudden on 2006-06-02
If you fancy building your own rhythmbox, you can and pass the option --enable-tag-writing

---

### Post by jdbartlett on 2006-06-02
[QUOTE=cbudden]If you fancy building your own rhythmbox, you can and pass the option --enable-tag-writing[/QUOTE]Thanks, everyone, for bringing me up to speed on this! Any idea why tag writing is disabled in the default dapper build? Seems odd to me.

---

### Post by apejcic on 2006-06-02
download the latest rhythmbox 0.9.4.1... u'll find debs here on the forum, or google

---

### Post by btlee on 2006-06-02
[QUOTE=cbudden]If you fancy building your own rhythmbox, you can and pass the option --enable-tag-writing[/QUOTE]

Rhythmbox 0.9.3.1 with gst-plugins 0.10.x does not support tag writing.
For that, we should upgrade rhythmbox to 0.9.4.1 or cvs version.

---

