---
title: "GTK Styles and Fonts - does not start"
date: 2006-01-04
forum: General Help
---

### Post by noeluylee on 2006-01-04
Im trying to run/start my GTK Styles and Fonts on Kubuntu, but it seems like its just loading but it didnt open a windows. It does not open the program.

--Any clue on this? :)

---

### Post by noeluylee on 2006-01-04
I tried to research but no luck. any help from here? :)

---

### Post by Tuf on 2006-01-05
Yes, theres a thread about that in the Kubuntu Forums. The solution seemed to be uninstalling/reinstalling all KDE applications.  Didn't work for me though.  I am still searching for a solution and happened across this thread.

---

### Post by noeluylee on 2006-01-06
Yes, seemed other people's GTK work, others not, there's something went wrong or whatever.  I just hoped that there's a fix for this issue.  I tried uninstalling and install it back but no avail for me, I even upgraded my KDE to 3.5, and still does not solve the issue.

Any people there encounter this and solve the issue? Thanks.

---

### Post by Neo Ex on 2006-01-06
Now I have Kubuntu and it works, but before I have had Ubuntu with GNOME and KDE, and installing gtk2-engines-gtk-qt it didn't work. It seems that I had to exit and log in again, and it worked.
Have you tried to open it from settings:/LookNFeel/ instead of KControl?

---

### Post by Tuf on 2006-01-06
I got it to work by installing the GTK2 engine. Unfortunately somehow it hosed my printer address and I didnt have it backed up or written down :/

Not being that familiar with Linux I tried every possible address I could think of but none worked.  I wasnt that far along so I just reinstalled and everything is good now and yes I wrote it down this time! :D

---

### Post by noeluylee on 2006-01-07
I have gtk2-engines-gtk-qt installed. I tried uninstalling it and install again but still does work. any suggestions? how about removing gnome? :)

Have you tried to open it from settings:/LookNFeel/ instead of KControl?
- where is this?

---

### Post by Tuf on 2006-01-07
System/System/Settings/Appearance is how I get to LookNFeel

---

### Post by noeluylee on 2006-01-07
I was able to fine the FeelNLook. i just use the konqueror and path it to settings:/FeelNLook, and I saw the GTK icon, I double clicked it and still not working :(

---

### Post by yoshic on 2006-01-07
hi!! well, you can try using this to launch it:

in a console type this:
```
kcmshell  kcmgtk-xdg 
```

kcmshell is used to open specific kde modules from the command line..
i hope this will be useful :wink:

---

### Post by noeluylee on 2006-01-07
Hey! GTK was opened using kcmshell  kcmgtk-xdg. how can I make the GTK icon working? 

after applying these message appears:
Qt: Locales not supported on X server
qstring_to_xtp result code -2
qstring_to_xtp result code -2
kcmshell: WARNING: KLocale: trying to look up "" in catalog. Fix the program


Any clue on this?

---

