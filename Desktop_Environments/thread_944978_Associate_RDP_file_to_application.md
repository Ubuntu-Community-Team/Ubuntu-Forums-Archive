---
title: "Associate RDP file to application?"
date: 2008-10-11
forum: Desktop Environments
---

### Post by suprfli on 2008-10-11
I've been using Terminal Server Client to RDP to my WinXP machine.  

1. I use it frequently enough that I saved the connection properties.  
2. I then created a link to the saved RDP file and dragged the link to my desktop.  
3. By default the RDP link opens with the text editor so I right clicked on the desktop RDP link and chose "Open with Other Application."
4. I see Remote Desktop Viewer but I don't see Terminal Services Client.
5. I assume I can "use a custom command" but I don't know where Terminal Services Client is located.  I tried a search.  This is one of the most frustrating things for me about Linux.  I wish it were easier to know exactly where particular apps are located(other than the panel). :(

Can someone help me out?  Thanks!

---

### Post by prshah on 2008-10-12
> **suprfli said:**
> I've been using Terminal Server Client to RDP to my WinXP machine.  

I wish it were easier to know exactly where particular apps are located(other than the panel). :(


Terminal Server Client command is ```
tsclient
```

In the future, to find the command used to launch a program from the menu, right-click the menu, choose "Edit Menus" and browse to the program you want; double clicking the entry will open up the properties, including the command used to start the program.

So, to associate your RDP file with tsclient, follow the steps as you have done earlier; then, in the program selection box, click on "Choose a custom command" and give the command as ```
/usr/bin/tsclient
``` The path should be the same, but you can confirm it by opening a terminal (Applications-Accessories-Terminal) and give the command ```
which tsclient
```

---

### Post by suprfli on 2008-10-12
prshah: Ah!  Thanks you!  I was CLOSE.  I right-clicked on TS Client in the menu hoping to see the properties.  I didn't think to click on the menu where I would see the edit menus option.  Following your instructions worked out perfectly.  Thanks very much.

One other quick question: Following your instructions, after double clicking on the entry I see the command but it is "tsclient."  I entered "tsclient" in as my custom command rather than the full path and it worked perfectly.  I also did a "which tsclient" and it gave me /usr/bin/tsclient.  I guess my question is I thought I may see the full path in the properties and didn't.  I think using your instructions and remembering the 'which' command will help me a lot moving forward.

---

