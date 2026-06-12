---
title: "[SOLVED] Force an application to Launch on a specific Workspace"
date: 2007-06-24
forum: Desktop Environments
---

### Post by kspn on 2007-06-24
I have just finished installing Xubuntu and I an **very** happy with it.

I have beryl running and I like the cool effects.

I was wondering though, how do I get an application (eg GAIM) to launch on a specific Workspace no matter when I am,
EG I am on Workspace 1, Launch GAIM and it opens on Workspace 4.

I know that I can switch workspaces but I would also like to be able to set this up so that if I am automatically starting some applications then they go the the workspaces that I want them to.

---

### Post by Anon Customer on 2007-06-26
The only thing I can find so far is this:

Devil's Pie

(in the repositories as "devilspie")

Website:
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

Guides and help:
[http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

My script (in ~/.devilspie) looks like this (erg, but with proper spacing):

[FONT="Courier New"]
; application settings for devil's pie
;
; see s-expressions in /usr/share/doc/devilspie/

(begin

   ;(debug)

   ; SET BROWSERS TO WORKSPACE 2
   (if  
      (contains (window_name) "fox")
         (begin
            (set_workspace 2)
            (maximize)
         )
   )

   ; SET EMAIL AND CHAT TO WORKSPACE 3
   (if
      (contains (window_name) "Thunderbird")
      (begin
         (set_workspace 3)
         (geometry "+217+0")
         (maximize_vertically)
      )
   )
   (if
      (is (application_name) "Gaim")
      (begin
         (set_workspace 3)
         (skip_tasklist)
      )
   )
)

[/FONT]

---

### Post by kspn on 2007-06-27
I reposted the Question in another thread and got an answer the works quite well.

[http://ubuntuforums.org/showthread.php?t=483701](http://ubuntuforums.org/showthread.php?t=483701)

---

