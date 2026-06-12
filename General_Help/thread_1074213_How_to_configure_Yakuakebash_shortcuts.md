---
title: "How to configure Yakuake/bash shortcuts ????"
date: 2009-02-19
forum: General Help
---

### Post by user-max on 2009-02-19
Hello all, I am very used to general Ctrl+c/v shortcuts that are used all over text editors, browsers and all. I was able to modify gnome-terminal's shortcuts to cut/paste with Ctrl-c/v (via gconf-editor), but for the life of me I cannot figure out how to modify those for Yakuake or bash, which Yakuake uses. I hope you all feel my pain :,)

 Any help is appreciated.

---

### Post by snova on 2009-02-19
> **user-max said:**
> I was able to modify gnome-terminal's shortcuts to cut/paste with Ctrl-c/v (via gconf-editor), but for the life of me I cannot figure out how to modify those for Yakuake or bash, which Yakuake uses.

What's wrong with adding an extra shift? ;)

Yakuake is based on Konsole, as are all terminals in KDE. The simplest way to change them would be to open a Konsole, Settings -> Configure Shortcuts, and change them there.

I would not recommend this though- especially for Ctrl-C. This is a particularly important key combination that probably won't work if you change it- or worse, *will* continue to work. It kills the current process.

---

### Post by user-max on 2009-02-19
Thank you for your input. The thing is, I am using yakuake in gnome :,) So extra shift doesnt work for some or another reason. If I could get to where to change those shortcuts, Id also change Ctrl-C to Ctrl-Z, so it wouldnt be an issue//

---

### Post by user-max on 2009-02-19
> **snova said:**
> What's wrong with adding an extra shift? ;)

Yakuake is based on Konsole, as are all terminals in KDE. The simplest way to change them would be to open a Konsole, Settings -> Configure Shortcuts, and change them there.

I would not recommend this though- especially for Ctrl-C. This is a particularly important key combination that probably won't work if you change it- or worse, *will* continue to work. It kills the current process.

PS>> when I go to settings -> configure shortcuts, the list of configurable shortcuts does not include copy and paste. However, if I try to edit current profile, then in input tab I see a possibility of changing them, just it looks foreign to me. Any suggestions?

---

### Post by snova on 2009-02-19
> **user-max said:**
> PS>> when I go to settings -> configure shortcuts, the list of configurable shortcuts does not include copy and paste. However, if I try to edit current profile, then in input tab I see a possibility of changing them, just it looks foreign to me. Any suggestions?

Odd, I can see it. Simply by searching on 'copy'.

Perhaps you're using a different version? I'm on KDE 4.2, though I imagine it would be pretty much the same...

---

### Post by user-max on 2009-02-19
It is strange, version of KDE in yakuake is 4.1.4... it must be because im using gnome.. But is there any way to configure it in some .conf file?

---

