---
title: "Emerald themes not working?"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Hybrid86 on 2007-07-14
I just installed beryl and then emerald, but when I tried to implement an emerald theme, it didn't work. When I clicked on one, nothing happened; when I right clicked, no menu or options came up. After searching around and reading a few posts, I went to make sure that emerald was set as my Window Decorator, but emerald wasn't on the list. The only thing there was "gtk window decorator" :confused:

Does anyone know a solution?

---

### Post by hyperair on 2007-07-14
From what you've said it's probably true that Emerald isn't installed. Could you try this command:```
sudo apt-get install emerald
```

---

### Post by Hybrid86 on 2007-07-14
That's what I typed to install emerald the first time though; I don't want to double-install it and mess up my computer. The thing is that all the stuff for emerald is there and visable, but none of it's themes can be used...

---

### Post by kiepmad on 2007-07-14
Try to use Synaptic Package Manager
>System > Administration > Synaptic Package Manager

Search for emerald and check emerald.
If it's checked, mark it for reinstallation (rightclick -> reinstallation)

---

### Post by Hybrid86 on 2007-07-14
That did it! I <3 you guys :)

---

### Post by quisnar on 2007-07-23
Hmm...I tried to follow those instructions...I reinstalled emerald but to my dismay, it still did not get the job done. Any other suggestions??  For some reason when I installed Beryl, I lost my minimize, maximize, and close buttons in the top right corners of the windows.  I figured it was because I was using an Ubuntu themes...

Please help!!!

Jon

---

### Post by hyperair on 2007-07-24
Try "emerald --replace" in a terminal or a run dialog.

---

### Post by big_danmahony on 2008-02-07
> **Hybrid86 said:**
> I just installed beryl and then emerald, but when I tried to implement an emerald theme, it didn't work. When I clicked on one, nothing happened; when I right clicked, no menu or options came up. After searching around and reading a few posts, I went to make sure that emerald was set as my Window Decorator, but emerald wasn't on the list. The only thing there was "gtk window decorator" :confused:

Does anyone know a solution?

I had the same problem,none of the emerald themes were activating for me.
All I did was go to system/preferences/appearance then go to the "visual effects tab and change it to normal,extra or custom.
Works perfectly now :)

---

### Post by ddzierzek on 2008-02-11
> **hyperair said:**
> Try "emerald --replace" in a terminal or a run dialog.

Thank you, I was having the same problem and now mine started too.  Thanks!

---

### Post by hyperair on 2008-02-11
No problem.

---

### Post by Blario on 2008-03-23
> **ddzierzek said:**
> Thank you, I was having the same problem and now mine started too.  Thanks!

Same here.  Thanks!!!

---

### Post by smooth3006 on 2008-03-26
i have emerald installed along with compiz. i cant change my themes with emerald for some reason ?  

i need help, ive followed the instructions in this thread and none helps.

---

### Post by cmirko on 2008-03-27
> **Blario said:**
> Same here.  Thanks!!!

worked for me too - thank you! \\:D/

---

### Post by hern101210 on 2008-05-03
In the system>preferences>advanced desktop effects settings menu you need to click on the "window decoration" plugin and change the line that says:

/usr/bin/compiz-decorator
to
/usr/bin/emerald

then typr in the terminal:

emerald --replace

Now open Emerald Theme Manager and click on themes.

---

### Post by Bunnywinkles on 2008-05-08
i did everything said here.

when i goto terminal and do "emerald --replace" it changes it, but as soon as i close terminal the theme changes and the windows no longer have headers. Any idea to what is wrong?

---

### Post by sujoy on 2008-05-08
when you close the terminal it terminates emerald because that was just run from the terminal and not in the background.

type this instead,

emerald --replace &

but you will need to do this everytime you login, so better go to preferences->session and in startup programs, click on add and in the command box enter, 

emerald --replace

ok and close. make sure your newly created entry is checked.

---

### Post by hyperair on 2008-05-09
> **sujoy said:**
> when you close the terminal it terminates emerald because that was just run from the terminal and not in the background.

type this instead,

emerald --replace &



This method requires you to close the terminal using the "exit" command instead of the "x" button. If you still want to use the "x" button on the terminal, use this command:
```

emerald --replace & disown

```

---

### Post by BLTicklemonster on 2008-07-05
So, am I going to have to do this every time I want to use trueglass in emerald? Seems crazy to have to open a terminal and run something every time I want to use it. Almost like ... I'm running linux or something!

:)

No really, do I have to enter that in the terminal just to use emerald every time I start my computer? Trueglass looks really cool, and I really would like to keep it for the most part.

---

### Post by hyperair on 2008-07-06
Emerald should be started up by desktop effects when you log in, if present. If not, then just add it to the start up programs (System->Preferences->Sessions). "emerald --replace" as the command.

---

### Post by BLTicklemonster on 2008-07-06
No, I mean the replace command, will I have to run it every time I start emerald or every time I start my computer?

---

### Post by hyperair on 2008-07-06
Like I said, probably not, because it should be automatically started up by Desktop Effects. The replace command is used to kill gtk-window-decorator and replace it with emerald. However, if it doesn't automatically start up, you'll have to add it to your start up programs in sessions, so that you don't have to manually run the command.

---

### Post by BLTicklemonster on 2008-07-06
Thank you

---

### Post by hyperair on 2008-07-06
No problem. Next time just click the yellow star ;)

---

