---
title: "How to prevent 9.04 Netbook Remix Desktop from always maximizing windows?"
date: 2009-04-26
forum: General Help
---

### Post by AlexsAntidote on 2009-04-26
Hello,

I've been using Ubuntu since Gutsy went official and just installed the netbook remix. I like it a lot with one major exception... I want to prevent the windows from always maximizing.

I know you can switch to the standard desktop view, but I like the netbook remix menu (I don't use Gnome Do or Conky or  any of the like, so I don't really need to see my actual desktop). I also know it is possible to unmaximize a window by right clicking the title bar and selecting unmaximize and then resizing the window, but this is tedious.

So is it possible to modify the settings for the netbook remix desktop view? Or is it possible to use the netbook remix menu with the classic desktop view?

Any thoughts? 

Thanks!

---

### Post by antikristian on 2009-04-26
you can launch the netbook-launcher while in classic mode, and you can also stop maximus (which handles automatic resizing) from starting by default.

To stop maximus, uncheck maximus from System -> Prefrences -> startup Applications 

To start netbook-launcher in classic mode, switch to classic mode, open "startup applications" and either check the netbook-launcher item, or create a new item that runs the command "netbook-launcher"

I'm not sure if window picker (the bar at the top in netbook remix) works flawlessly with maximus disabled though.

---

### Post by AlexsAntidote on 2009-04-26
Excellent! Thank you very much. Now I can play around with these settings for a bit and see what I like best. I appreciate it.

---

