---
title: "starting '/bin/bash' instead"
date: 2009-06-06
forum: General Help
---

### Post by notsomeone on 2009-06-06
I downloaded and installed the Pulse plugin for Eclipse just because it was the most popular plugin and I wanted to see what it did.
So now it has an entry on my Start menu, but it doesn't work. I think it does not like the space in the path:"/home/notsomeone/Genuitec/Pulse Explorer/pulse-explorer".
Instead a bash shell is opened that says:
"Warning: Could not find '/home/notsomeone/Genuitec/Pulse Explorer/pulse-explorer', starting '/bin/bash' instead.  Please check your profile settings."

It does work if I cd to the working directory and type ./pulse-explorer, or if I double-click on it from Dolphin.

I would uninstall it if I knew where all of the files were installed.
There is also an entry on the Start menu that says 'Uninstall Pulse' but that does not work either.

Of course it does still work, like I said, if I navigate to the directory, but that is not as easy.

Can I get the menu to find the location of this program?
I am so used to using apt-get to install all of my programs. I don't know how to fix this if I can't just `apt-get remove`.

---

### Post by sdennie on 2009-06-06
You could try putting a \ before the space.  So instead of "/home/notsomeone/Genuitec/Pulse Explorer/pulse-explorer" try: "/home/notsomeone/Genuitec/Pulse\ Explorer/pulse-explorer".

---

### Post by colau on 2009-06-06
Yes, a "\" backslash before a space.

---

### Post by notsomeone on 2009-06-06
Worth a try.
But I still get the same error message.

edit:
You mean change the name of the actual folder inside my home folder, right?

---

### Post by colau on 2009-06-06
> **notsomeone said:**
> Worth a try.
But I still get the same error message.

edit:
You mean change the name of the actual folder inside my home folder, right?
Yes,you also could rename your folder.:)

---

### Post by BCurtisWX on 2009-06-06
well since it works from using 'cd' then go to the file-explorer and type PWD and make sure that matches the directory structure in the start menu iteam

---

### Post by notsomeone on 2009-06-06
> **BCurtisWX said:**
> well since it works from using 'cd' then go to the file-explorer and type PWD and make sure that matches the directory structure in the start menu iteam

I don't know how to check the directory structure of the start menu item. I guess if I could check and/or change that then my problem would be solved.

---

### Post by colau on 2009-06-06
> **notsomeone said:**
> I don't know how to check the directory structure of the start menu item. I guess if I could check and/or change that then my problem would be solved.
From terminal type
```

pwd

```

:)

---

### Post by notsomeone on 2009-06-06
> **colau said:**
> From terminal type
```

pwd

```


I know how to check the current working directory from the shell. And when I type `pwd` from the pulse-explorer directory, it does match the what the Start Menu says.
I was just hoping that I could change where the Start menu points.

---

### Post by michy99 on 2009-06-06
Try putting quote marks around the path in the start menu.

---

### Post by notsomeone on 2009-06-06
> **michy99 said:**
> Try putting quote marks around the path in the start menu.

So it is possible to edit the path in the start menu?
If someone could tell me how to do this, I would be pretty happy.

---

### Post by michy99 on 2009-06-06
> **notsomeone said:**
> So it is possible to edit the path in the start menu?
If someone could tell me how to do this, I would be pretty happy.

Just to be clear, when you say 'start menu' do you mean the Applications menu on the top panel?

---

### Post by colau on 2009-06-06
> **notsomeone said:**
> So it is possible to edit the path in the start menu?
If someone could tell me how to do this, I would be pretty happy.
What do you mean by start menu?

---

### Post by notsomeone on 2009-06-06
> **colau said:**
> What do you mean by start menu?

Well, I guess I don't know the correct term, but it is basically the same thing as in Windows. A button on the left side of the taskbar which brings up a list of all the applications on my system.
Anyway, I think I have it figured out. I can edit that menu with kmenuedit since I use Kubuntu.
And I guess alacarte does the same thing in Ubuntu.
Thanks for all your help though.

---

