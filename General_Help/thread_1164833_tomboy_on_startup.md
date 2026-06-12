---
title: "tomboy on startup"
date: 2009-05-20
forum: General Help
---

### Post by leemajors on 2009-05-20
hi there,

when i first start up tomboy notes is set to start up quiet (tomboy --tray-icon) but regardless it starts by opening the "search all notes" window. if i close it, tomboy closes completely and i need to run it again.

any thoughts? would just like tomboy to start up in the tray and stay running until i need it.

---

### Post by leemajors on 2009-05-23
hmm, no answers? have i put this in the wrong forum perhaps?

---

### Post by DeMus on 2009-05-23
> **leemajors said:**
> hi there,

when i first start up tomboy notes is set to start up quiet (tomboy --tray-icon) but regardless it starts by opening the "search all notes" window. if i close it, tomboy closes completely and i need to run it again.

any thoughts? would just like tomboy to start up in the tray and stay running until i need it.

Did you try this from the help files:

2.1.&#8195;Adding Tomboy to the Panel

To add Tomboy to a panel, right-click on the panel, then choose
      Add to Panel. Select Tomboy Notes in the Add to the panel dialog,
      then click Add. You should see a yellow note icon appear in the panel,
      representing Tomboy. The panel icon is illustrated in Figure 1.

It seems to me you can boot your computer without having to start Tomboy yourself, or via a link in the start-up list. Just put it on the panel and you can go from there.

---

### Post by ASchweitzer on 2009-05-23
> **DeMus said:**
> 
It seems to me you can boot your computer without having to start Tomboy yourself, or via a link in the start-up list. Just put it on the panel and you can go from there.

I second that. It works quite nicely, and gives you the same functionality of the tray icon, only where ever you place it on the panel. I've had problems with it crashing a few times, but it's been stable the last few weeks.

---

### Post by leemajors on 2009-05-23
Thanks for responding:)

I do already have Tomboy added to the panel, however that still requires me to run it when I then want to use the notes program.

I would like Tomboy to start up automatically, so it just sits there in the tray and when I click its icon it displays a list of notes.

I should add it was working perfectly in Hardy and Intrepid...

---

### Post by ASchweitzer on 2009-05-23
> **leemajors said:**
> Thanks for responding:)

I do already have Tomboy added to the panel, however that still requires me to run it when I then want to use the notes program.

Correct me if I'm wrong, but I think you have a shortcut added to the panel. If you right-click on the panel, and select "Add to Panel..." you can add the Tomboy applet, rather than a shortcut, which will give you the functionality you're used to. I'm running 9.04 now, I'll restart X and play with that for a bit, maybe you're right.

EDIT:

Nope, works fine here. You can restart the X server by using right-hand Alt key, followed by SysRq and K. (this replaced the old ctrl-alt-backspace). If you want to test the applet and such without full restarts

---

### Post by leemajors on 2009-05-23
oh!! that's great! i never knew you could add anything other than shortcuts and launcher type stuff to a panel.

thanks so much :)

---

### Post by ASchweitzer on 2009-05-23
glad to be of assistance

---

### Post by mocha on 2009-05-24
Thanks for the tip.  I didn't realize Tomboy was available as an applet.  This must have changed a few upgrades ago, because I always used to have it startup in my sessions and go to the notification panel.  I also had the same problem as the OP, upon reboot or log-in, the search all notes would come up, then when closing it the entire app would crash.

---

