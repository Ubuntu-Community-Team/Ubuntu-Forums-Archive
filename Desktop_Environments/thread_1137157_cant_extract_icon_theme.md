---
title: "cant extract icon theme"
date: 2009-04-25
forum: Desktop Environments
---

### Post by sayk on 2009-04-25
i cant extract the 'nuove-xt aero icon them' i have downloaded.

_i need to install i_t, i've done ones before but can't remember how i did it.

please help.

---

### Post by VCoolio on 2009-04-25
Can't you drag and drop the archive in the themes tab from your appearance window? Is it .tar.gz? Where did you get it?

---

### Post by sayk on 2009-04-25
yes its tar.gz

can you people explain in simpler words.

im dont understand the 'computer lanuage'

thanks anyway

---

### Post by Therion on 2009-04-25
Put your icon-theme download file (the tar.gz) on your desktop.

Go to System/Preferences/Appearance.

Drag and Drop the downloaded icon file (the tar.gz) onto the Appearance Preferences window.

You should get a pop up message that the theme installed.

On the Appearance Preferences window, click on the "Customize" button and then the "Icons" tab to select the icon theme you just installed.

Save the new desktop theme and name whatever you want to make it the new default.

---

### Post by VCoolio on 2009-04-25
OK, as simple as it gets:
right click on desktop
change desktop background
click theme tab
drop .tar.gz into that

post error message here if any

---

### Post by JK3mp on 2009-04-25
Well if its tar.gz and you can't drag over themes. Just extract it. 

```
tar -xzvf file.tar.gz
```

then mv to your .icons folder.

```
mv file $home/.icons
```

---

### Post by sayk on 2009-04-25
> **JK3mp said:**
> Well if its tar.gz and you can't drag over themes. Just extract it. 

```
tar -xzvf file.tar.gz
```

then mv to your .icons folder.

```
mv file $home/.icons
```

what do you mean with the codes??

---

### Post by Therion on 2009-04-25
> **JK3mp said:**
> Well if its tar.gz and you can't drag over themes. Just extract it. 
No need to extract and such.  Drag and Drop will work just fine.  OP doesn't know how to do that...  Yet.

**@ sayk:**  See posts 4 & 5.

---

### Post by sayk on 2009-04-25
drag and drop doesnt work either......

the same messeage comes up which i mentioned earlier.

---

### Post by sayk on 2009-04-25
this is the icon package....

you can try and tell me if its working on your competer(s)........

it worked on my other computer.

---

### Post by sayk on 2009-04-25
sorry, forgot to post the link

link: [http://www.1-filehost.midnightirc.info/index.php?t=dl&hash=Mu17auig4JHE3Npe6vNhf3wl92qJdwuj](http://www.1-filehost.midnightirc.info/index.php?t=dl&hash=Mu17auig4JHE3Npe6vNhf3wl92qJdwuj)

---

### Post by VCoolio on 2009-04-25
EDIT: forget what I posted. The archive is not .tar.gz although it is named like that. I get the same error.

---

### Post by sayk on 2009-04-25
link:[http://www.1-filehost.midnightirc.info/index.php?t=dl&hash=Mu17auig4JHE3Npe6vNhf3wl92qJdwuj](http://www.1-filehost.midnightirc.info/index.php?t=dl&hash=Mu17auig4JHE3Npe6vNhf3wl92qJdwuj)

---

### Post by JK3mp on 2009-04-25
with code. I meant use those commands i just wrapped it in code tags. Open terminal. Go to the directory where its stored. (probably your desktop or home folder) then use the mv command to mv it into your $home <-- or your name folder then into the .icons folder. Sometimes doing it manually this way works when drag and drop doesn't.

---

### Post by sayk on 2009-04-25
dont understand a word of what you people are saying, but appriciate your that you are trying to help.

please explain in simpler terms

---

### Post by roachk71 on 2009-04-25
It should be mentioned here, that some users of other distributions are used to building from source code, and installing that way...This is especially troublesome for inexperienced users, who are usually accustomed to the drag-and-drop installation method, since there are often too many unresolvable dependencies. Bleh! 
There really should be a uniformly simple installation method across all distros. Unfortunately, there isn't... :-(

I've often had this kind of problem with KDE themes, which is one of the reasons I don't use that environment now.

I might be able to help, but I have to ask a few questions first, such as:

[LIST=1]
[*]Where did you get this icon theme?
[*]Is the icon theme for GNOME, XFCE, or KDE?
[*]Did you acquire it as a standalone theme, or did the post read as source?
[/LIST]

---

### Post by JK3mp on 2009-04-25
Well..also since nobody yet has asked. What "error" do you get when you try to drag and drop? Just noticed nobody asked ^-^ just seems like ev1 assumes u don't know what your doing , when the error could lead to a different issue.

---

### Post by sayk on 2009-04-25
[U]Cannot install theme

There was a problem while extracting the theme.[/U]

this is the propblem i get

---

### Post by sayk on 2009-04-25
please help!!

---

### Post by roachk71 on 2009-04-26
Hello Again,

It would appear your archive download was interrupted when the file in question was removed from the server (for whatever reason.) I'm including a link to another theme archive that's aero-type.

This theme must be copied to /usr/share/icons as superuser. To do this, first rename the end of the file to .tar.bz2 and extract the theme in one of your user directories, then use Alt-F2 and issue this command:

```
gksudo nautilus
```This will run your file manager as root, allowing you to copy the directory to the one mentioned earlier. If it looks different, that's normal; don't let it bother you.

[Please click here to go to the icon theme page.]("http://www.gnome-look.org/content/show.php/LiNsta-icons?content=62759")

Once you have the theme copied, you can use the Customize button in your Appearances manager to mix-and-match. :KS

---

