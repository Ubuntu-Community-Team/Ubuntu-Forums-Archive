---
title: "Windows staying on top"
date: 2012-08-16
forum: Desktop Environments
---

### Post by A Traveller on 2012-08-16
Hi all.

I have suddenly started experiencing a very strange problem, which I have never had before.

I have Ubuntu 10.04 and what has started happening is that when I open a program, for example, Firefox and then open another one, for example, Calculator, if I click anywhere in the Firefox window, the Calculator doesn't disappear into the background like it used to. It just stays on top of the Firefox window even though there is no check mark in the 'Always on Top' context menu for the Calculator. This is just one example I have given. The problem is present with any window/program.

I have tried searching the Internet for a solution, but can only find requests asking to keep windows on top!

Anyone any ideas?

Thanks.

---

### Post by Frogs Hair on 2012-08-16
I am using 12.04 and the always on top setting is found by right clicking the title bar. Is this the context menu you are referring to ? I have not used 10.04 for a long time so I don't remember if this is applicable.

---

### Post by A Traveller on 2012-08-17
Hi Frogs Hair.

Thanks for your reply. Yes that is the context menu I referred to, however, why are my window staying on top even though I have not selected 'Always on Top' and it does not have a check mark next to it by default either? I am keep having to manually minimise each window if I want to get it out of the way. Thanks.

---

### Post by Frogs Hair on 2012-08-17
I know it is possible to override standard window settings in Compiz if in use. Restarting the window manager in use may help also. ```
compiz --replace
``````
metacity --replace
```

---

### Post by A Traveller on 2012-08-17
Hi Frogs Hair.

Thanks for your suggestions. I never enable Compiz and also never install anything to do with Compiz via the Update Manager, so I assume I don't need to run the first code. Will running the second code mean that all my window management settings will restore to default and I will have to set them all again? Thanks.

---

### Post by Frogs Hair on 2012-08-17
It simply restarts the window manager and that can be helpful if there is a glitch.

---

### Post by A Traveller on 2012-08-19
Hi Frogs Hair. I tried it but it doesn't seem to have worked. Any idea what else it could be that is causing this? Thanks.

---

### Post by Frogs Hair on 2012-08-19
Exploring the configuration editor might help , but 12.04 uses a different application so I can't tell you where to look.

---

### Post by A Traveller on 2012-08-19
Thanks Frogs Hair. Your suggestion has fixed the problem! Here is what I did:-

Press 'Alt + F2'
Typed 'gconf-editor' and clicked 'Run'
Expanded 'Apps', then 'Metacity' and the clicked on 'General'
Double-clicked 'raise_on_click' and changed the 'Value' to 'True' by clicking on the button which said 'False'
Clicked 'OK' and then closed the Gconf Editor window
Voila!

I have read warnings advising against changing the Value to False, but can't remember ever changing it to False. I have played with the location of the maximise, minimise and close buttons but I don't know how the raise-on-click got changed. I did install Ubuntu Tweak recently but don't know if anything I may have changed in that caused the problem.

Anyway, thank you for your help. I have really appreciated it.

---

