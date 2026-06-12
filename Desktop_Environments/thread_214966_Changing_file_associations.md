---
title: "Changing file associations"
date: 2006-07-13
forum: Desktop Environments
---

### Post by neutro on 2006-07-13
Hi -- I'm rather new at using Gnome. I recently installed a new app just to try it (Texmaker, for editing .tex files). This automatically caused .tex files to be associated with texmaker in Nautilus. Now, Texmaker is great, but I still prefer Kile. How can I associate .tex files back to Kile?

I tried the System -> Preferences -> Prefered Applications menu, but this only enables me to choose my default browser, mail app and terminal. There doesn't seem to be a MIME-type association tool anywhere. Even gconf returned nada on this. In KDE, I would simply right-click on a .tex file, select "open with", use Kile and click on the "always use this application in the future" checkbox. But I haven't found anything similar yet.

Also: is there a way to use the graphical interface to create a shortcut (link or launcher) on the desktop to another directory? I can create a folder or an application launcher easily, but not a link to an existing folder. Is the only way right-clicking on the folder inside Nautilus, creating the link, then dragging it on the desktop?

Thanks for any hint about these two questions.

---

### Post by Bossieman on 2006-07-13
Just find the text-file, rightclick on it, choose properties and then go to the tab open with. There you can select what application to open the file.

---

### Post by aysiu on 2006-07-13
To link to a folder, middle-click-drag the folder to the desktop and select **link here**.

---

### Post by kanem on 2006-07-13
> **Bossieman said:**
> Just find the text-file, rightclick on it, choose properties and then go to the tab open with. There you can select what application to open the file.

My 'open with' tab is full of apps that I can't get rid of. I hightlight one, click on remove and not only does it stay there, but the remove button gets greyed out. This used to happen with 'official' Gnome apps that the devs always wanted to be present as an option. But now it seems to happen with all of my programs that ever got into the 'open with' list.

Anybody else seen this? Or have a workaround?

---

### Post by aysiu on 2006-07-13
Have you tried this? ```
sudo chown -R kanem:kanem /home/kanem
```

---

### Post by Bossieman on 2006-07-13
> **kanem said:**
> My 'open with' tab is full of apps that I can't get rid of. I hightlight one, click on remove and not only does it stay there, but the remove button gets greyed out. This used to happen with 'official' Gnome apps that the devs always wanted to be present as an option. But now it seems to happen with all of my programs that ever got into the 'open with' list.

Anybody else seen this? Or have a workaround?

I think you missunderstood what i meant. You want to be able to open up a textdocument with kile. In the tab 'open with' choose kile and press ok. if you cant find kile there, klick on the lowerpart of the window corresponding to "use a special command" and put in kile there.

---

### Post by aysiu on 2006-07-13
> **Bossieman said:**
> I think you missunderstood what i meant. You want to be able to open up a textdocument with kile. In the tab 'open with' choose kile and press ok. if you cant find kile there, klick on the lowerpart of the window corresponding to "use a special command" and put in kile there.
kanem isn't the OP. It's a slightly different issue. It's borderline "hijacking" the thread...

---

### Post by neutro on 2006-07-13
I'm the OP and the two first replies enlightened me, thanks :)
You can continue hijacking the thread, I don't mind at all.:rolleyes:

---

### Post by kanem on 2006-07-13
> **aysiu said:**
> kanem isn't the OP. It's a slightly different issue. It's borderline "hijacking" the thread...

Yeah, sorry. I figured the other problem had been solved, so I tried to sneak a related question in while folks were on the subject.

Thanks aysiu, I'll try your suggestion.

---

