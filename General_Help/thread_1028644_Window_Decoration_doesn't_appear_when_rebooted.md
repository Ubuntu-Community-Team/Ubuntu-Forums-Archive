---
title: "Window Decoration doesn't appear when rebooted"
date: 2009-01-02
forum: General Help
---

### Post by pedro3005 on 2009-01-02
The title practically speaks itself, when i reboot, the bar on top of the windows with the x, -, etc, go missing.. I gotta go on compiz icon and reload the window manager.. Can i avoid having to do that?

---

### Post by Forlong on 2009-01-02
What window decorator are you using?

What's the output of
```
gconftool-2 -g /apps/compiz/plugins/decoration/allscreens/options/command
```

---

### Post by pedro3005 on 2009-01-02
gtk-window-decorator --replace

---

### Post by Forlong on 2009-01-03
What happens when you run this command in a terminal?
Does it spit out any errors?

---

### Post by pedro3005 on 2009-01-03
thanks for the interest, but i fixed it, simply by telling linux to run "gtk-window-decorator --replace" on startup.

---

