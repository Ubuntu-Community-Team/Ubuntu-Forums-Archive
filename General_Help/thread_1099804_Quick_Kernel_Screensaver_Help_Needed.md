---
title: "Quick Kernel Screensaver Help Needed"
date: 2009-03-18
forum: General Help
---

### Post by inspirations365 on 2009-03-18
I'm trying to get this working: [http://micrux.net/?p=66]("http://micrux.net/?p=66"), essentially a screensaver of the kernel. I'm fine up to the last part, where it asks me to input ```
cat `find /usr/src/linux-source/ -name ‘*.c’ | argshuf`
```

This wouldn't be a problem if I knew where to input this. I do not know how to access screensaver settings through the terminal. 

If you really want to help me, could you also tell me where/how to tweak speed, scale, and fade settings. 

Thanks!

---

### Post by inspirations365 on 2009-03-18
The obvious choice would be to input that code into the terminal, but I don't think it goes there. The context of the code is this (from the site):

"Now we&#8217;re ready to put it all together. Go into your screensaver preferences, and go into the phosphor setup. You can set up the speed, scale and fade settings however you like. The important part is the &#8220;text program&#8221; box."

Then it lists the command.

---

### Post by inspirations365 on 2009-03-18
Sorry for the multiple posts, but I input the command into the terminal for kicks and it made all the prompts turn into symbols instead of text. I closed it and reopened it and everything seems fine. But when I go to the screensaver menu, it's still listing the same few lines (it's supposed to be random).

---

### Post by inspirations365 on 2009-03-18
Okay, I think I half solved the problem: I needed xscreensaver to edit the settings. I still don't know where to enter that command, but that's the last thing I need to solve. If anyone can help me answer that, I think I'm golden.

---

### Post by mcduck on 2009-03-18
The command would go into "phosphor"-screensavers advanced options (in the xscreensaver settings). There's a text entry box called "text program" where you can use any command you want to display it's output in the phosphore screensaver.

---

### Post by inspirations365 on 2009-03-18
I found a picture of what that menu is supposed to look like here: [http://eddie.niese.net/images/phosphor-settings.png](http://eddie.niese.net/images/phosphor-settings.png)

My menu options do not have that box in there at all.

---

### Post by inspirations365 on 2009-03-18
Should I try uninstalling the screensaver and then reinstalling it? How would I do that?

---

### Post by mcduck on 2009-03-18
> **inspirations365 said:**
> I found a picture of what that menu is supposed to look like here: [http://eddie.niese.net/images/phosphor-settings.png](http://eddie.niese.net/images/phosphor-settings.png)

My menu options do not have that box in there at all.

You need to select "dump pipe" in the dropdown box, as seen on that picture. The text entry for the command should appear then.

edit: Sorry, you are probably using the Gnome's dialog for xscreensaver, not the KDE dialog shown in the picture you posted.. You need to go tho the Advanced-tab of the screensaver dialog, and under "Text Manipulation" enable "Program" and type that command into the command field.

---

### Post by tad1073 on 2009-03-18
I tried it but the command doesn't work.

---

### Post by inspirations365 on 2009-03-18
I think we're almost there. The command doesn't work as it should. Instead, it gives "no such file or directory".

There must be something I we should append to the command to make it direct to the /usr/src/linux-source directory...

---

### Post by inspirations365 on 2009-03-18
I'm so close I can taste it. Okay, so in that program box listed above, you go to browse, and navigate to the proper directory. Then paste in the command in my original post AFTER the directory in the box. 

NOW the only issue I see standing between me and awesome is that permission is denied. putting "sudo" in front of the command won't work since I can't enter my password. Can anyone think of a workaround for this?

---

### Post by inspirations365 on 2009-03-19
Is there some way I can give the program privs to run without entering my password?

---

### Post by inspirations365 on 2009-03-20
Or is there some way I can give the command access to the files? I know there's a way to do this...

---

### Post by inspirations365 on 2009-03-21
Someone?

---

