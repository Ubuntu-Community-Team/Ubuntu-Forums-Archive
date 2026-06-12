---
title: "Font size problem"
date: 2006-03-16
forum: Desktop Environments
---

### Post by MichaelZ on 2006-03-16
Hello,

I have some problems with the font size in kde. I have originally Ubuntu and I have downloaded and installed kde. As I could not set correctly all the font with kcontrol (GTK+/GTK2+ applications (e.g., terminal, Code::Blocks) have a very small font size), I have installed *gtk-theme-switch* and done *sudo gnome-theme-manager*. Things are going better now, anyway, I still have a problems. Font size in kmenu are smaller than font in kedit menu. If I increase the font size with kcontrol, the font size of the kmenu items become acceptable, but the font size for the kedit menu items too big :-?.

Moreover, I begin to get this message:

> 
kwebdesktop-Kdialog

Will not save configuration.

Configuration file "/home/michael/.kde/share/config/kwebdestoprc" not writable.

Please contact your system administrator
 
And I have run kcontrol as root (sudo). 

How can I set the same font size for kmenu and kedit?

And what I can do to solve the error?

Thank you very much.

Best wishes,
Michael

---

### Post by khyron on 2006-04-15
this is happening to me too..... very annoying....
i still haven't been able to find a solution, someone has?

---

### Post by khyron on 2006-04-15
ok, i found something..... apparently the kmenu icon size is set too small by default and forces fonts to be rendered smaller too...

edit ~/.kde/share/config/kickerrc

find the section named [menus] and change (or add) the following entry:
MenuEntryHeight=desired size

mine is set to 24 and works ok ( 1024x768 )

hope it helps.

---

### Post by MichaelZ on 2006-04-15
Hello,

Thank you very much for your help:).

I will give it a try.

Best wishes,
Michael

---

### Post by khyron on 2006-04-15
there's still something that i don't quite understand...

if I do:  

dcop kicker Panel restart

then KDE reads the MenuEntryHeight entry and applies the icon size to the menu, but it doesn't seem to do it automatically at startup.... 

PS: (i forgot to mention the dcop stuff in my previous post)

---

### Post by khyron on 2006-04-16
here we go again.... i think i found the root of all evil now ;) 

i deleted the .kde directory from my home directory, restarted KDE, answered all the wizard's questions and allowed KDE to create a new brand .kde directory.... after that the font issue was solved...  i didn't like the default kmenu entry spacing so I changed it with the method described in my previous posts. This time everything was working as expected..... UNTIL i had the brilliant idea of adding gnome-settings-daemon to .kde/Autostart.....

Michael, are you running gnome-settings-daemon at startup too?  it seems that it doesn't play nicely with KDE fonts...

[http://ubuntuforums.org/showthread.php?t=53427&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=53427&highlight=gnome+settings+daemon)

---

### Post by MichaelZ on 2006-04-17
[quote=khyron]
Michael, are you running gnome-settings-daemon at startup too?  it seems that it doesn't play nicely with KDE fonts...

[http://ubuntuforums.org/showthread.php?t=53427&highlight=gnome+settings+daemon]("http://ubuntuforums.org/showthread.php?t=53427&highlight=gnome+settings+daemon")
[/quote] 
Sorry, but I do not know exactly (I am still a newbie). If this daemon is installed and used by default then I suppose yes, if not no.

Anway, thank you very much for your help:D.

Best wishes,
Michael

---

