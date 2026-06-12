---
title: "Emerald themes + Compiz Fusion"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by alecwh on 2007-06-25
I'm having problems with my Emerald theme manager. I recently switched to Compiz-fusion, and whenever I type: "emerald --replace &" I get this error multiple times in the Terminal: (emerald:7380): Wnck-WARNING **: Unhandled action type (nil)"
Is there a fix?
Emerald still runs, but when I close the terminal, it reverts back to Metacity.

---

### Post by walkerk on 2007-06-25
press alt + f2

run this command:
```
compiz --replace -c emerald
```

to run c.fusion & emerald at boot insert that command under System > Preferences > Sessions

---

### Post by neo.patrix on 2007-06-25
why are you using terminal to start emrald? I think you can just start beryl manager and beryl will place a ruby icon on your top desktop panel. When you right click on it a menu appears. You can use this menu to switch between windows manager or windows decorators. 

Once you start beryl-manager there no need to do anything regarding beryl from terminal.

---

### Post by alecwh on 2007-06-25
alt + f2 does nothing. :(

---

### Post by alecwh on 2007-06-25
NEVERMIND! It worked!

Thanks a lot!

---

### Post by walkerk on 2007-06-25
no problem :)

---

### Post by walkerk on 2007-06-25
> **neo.patrix said:**
> why are you using terminal to start emrald? I think you can just start beryl manager and beryl will place a ruby icon on your top desktop panel. When you right click on it a menu appears. You can use this menu to switch between windows manager or windows decorators. 

Once you start beryl-manager there no need to do anything regarding beryl from terminal.

he is using compiz fusion and emerald.. not beryl and emerald.. c.fusion doesn't have beryl-manager equivalent..

---

### Post by nasov on 2007-08-09
had the same problem but running compiz --replace -c emerald helped
however i can not change themes on the fly... like in metacity but have to restart ubuntu,
Is this how it should be? or is there a way to bypass this rather annoying ... ... thing?

---

### Post by mcduck on 2007-08-09
> **walkerk said:**
> he is using compiz fusion and emerald.. not beryl and emerald.. c.fusion doesn't have beryl-manager equivalent..

No, but the same Beryl Manager manages Compiz just as well as it manages Beryl.

---

### Post by Paul133 on 2007-08-14
Actually, fusion-icon is pretty close to what I had with Beryl. It gives me an icon in the tray I can right-click and then choose my wm (compiz or Metacity) and my window decorator (Emerald or GTK). Of course, when I choose emerald, I lose the window decorations, so I'm stuck with GTK, but that's getting off-topic.

---

### Post by misfitpierce on 2007-08-14
emerald --replace is another option to replace just emerald window deco manager

---

### Post by eje_s on 2007-08-29
The problem as I see it is that emerald will be killed when the terminal is closed using the close button in the title bar. What actually happening when one closes the terminal in such a way is that the process is killed, and so is all child processes in this case emerald.

The solution is simple, don't use the close button. Instead close the terminal nicelly using the command "exit". This will maintain child processes.

---

### Post by dennis.groome on 2007-10-24
> **Paul133 said:**
> Actually, fusion-icon is pretty close to what I had with Beryl. It gives me an icon in the tray I can right-click and then choose my wm (compiz or Metacity) and my window decorator (Emerald or GTK). Of course, when I choose emerald, I lose the window decorations, so I'm stuck with GTK, but that's getting off-topic.

Where do I get fusion-icon?

---

