---
title: "Create launcher for an application with no terminal window"
date: 2012-06-03
forum: Desktop Environments
---

### Post by asus-user on 2012-06-03
Hello all, 
recently i faced that when creating a launcher for an application which needs a terminal command to run it, a terminal window always opens up with the application and if it was closed , the application would close of course, and here i tell how not to have  that external terminal window opened:

create a document with the extension .desktop and write in it the following code:

```

[FONT=Courier New][FONT=courier new][Desktop Entry][/FONT][/FONT] [FONT=Courier New]
[FONT=courier new]Type=Application[/FONT][/FONT] [FONT=Courier New]
[FONT=courier new]Terminal=false                  // true will show terminal window[/FONT][/FONT] [FONT=Courier New]
[FONT=courier new]Icon="icon file complete path"[/FONT][/FONT] [FONT=Courier New]
[FONT=courier new]Name="application name"[/FONT][/FONT] [FONT=Courier New]
[FONT=courier new]Exec="command line for executing the application, can hold parameters"[/FONT][/FONT] 

```this was tested on ubuntu 12.04 and worked just fine.
please comment with your experience
hope you get benefit from that  :smile:

---

### Post by Paddy Landau on 2012-06-03
Thank you for sharing.

You can also install [alacarte]("apt:alacarte") (Main Menu), and add menu entries there, which will become available on the Dash. It provides an option to open a terminal or not.

---

