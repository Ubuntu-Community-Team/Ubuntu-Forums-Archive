---
title: "how can i prevent 1 user from connecting to the internet whle allowing all others"
date: 2005-10-27
forum: Desktop Environments
---

### Post by kakashi on 2005-10-27
how can i prevent 1 user from connecting to the internet whle allowing all others.
i bascially want 1 user that can do nothing except use openoffice or gimp or anyother offline program just not be able go online ever. 
i also want to able to simultaneously run another user who's downlaoding stuff using 
azureus.

how can i do this 
i have tried to uncheck the modems box in the gnome-user box but does not help.

---

### Post by gillion on 2005-10-27
[QUOTE=kakashi]how can i prevent 1 user from connecting to the internet whle allowing all others.
i bascially want 1 user that can do nothing except use openoffice or gimp or anyother offline program just not be able go online ever. 
i also want to able to simultaneously run another user who's downlaoding stuff using 
azureus.

how can i do this 
i have tried to uncheck the modems box in the gnome-user box but does not help.[/QUOTE]
Depending on the skill lelvel of the person try ...

1. Editing the menu of the person in question and remove their access to internet applications, and the terminal. Then remove the menu editor.

2. Edit the panel of the person using gconf-editor and disable their add to panel feature.

3. Edit the panel of the person using gconf-editor and remove their command line run feature (Alt+F2). Then remove the gconf-editor menu item.

4. If the person writes a URL inside open office or tomboy, then clicks it, they might inadvertently startup Firefox so you will have to edit their file associations and default applications settings as well.

Unchecking the modems box only prevents a user from being able to dial out.

Maybe you want to uncheck the user groups to which the person is assigned.

Good question.

---

### Post by HermanAB on 2005-10-27
The only way to do that is with something like Squid-Cache and user authentication.  Effectively, Squid should pop-up a box asking a user to log in, before allowing online communications from that machine.

See this for some ideas:
[http://www.aerospacesoftware.com/squidguard-howto.html](http://www.aerospacesoftware.com/squidguard-howto.html)

Cheers,

Herman

---

### Post by kakashi on 2005-10-27
[QUOTE=gillion]Depending on the skill lelvel of the person try ...

1. Editing the menu of the person in question and remove their access to internet applications, and the terminal. Then remove the menu editor.

2. Edit the panel of the person using gconf-editor and disable their add to panel feature.

3. Edit the panel of the person using gconf-editor and remove their command line run feature (Alt+F2). Then remove the gconf-editor menu item.

4. If the person writes a URL inside open office or tomboy, then clicks it, they might inadvertently startup Firefox so you will have to edit their file associations and default applications settings as well.

Unchecking the modems box only prevents a user from being able to dial out.

Maybe you want to uncheck the user groups to which the person is assigned.

Good question.[/QUOTE]

actually the skill level is high. very high as that person is me and almost all of the things you have said i can bypass one way or anoter.

basically i have a nasty habit of starting to surf the internet when i should be studying on the comp. so i need to block my own internet access so that i can work. 
don't tell me go for will power cuz i have little to none in this matter.

---

### Post by gillion on 2005-10-27
[QUOTE=kakashi]actually the skill level is high. very high as that person is me and almost all of the things you have said i can bypass one way or anoter.

basically i have a nasty habit of starting to surf the internet when i should be studying on the comp. so i need to block my own internet access so that i can work. 
don't tell me go for will power cuz i have little to none in this matter.[/QUOTE]

Then you might as well forget it then.

---

### Post by Diziet Asahi on 2005-10-27
One effective way to restrict internet usage is to set the permissions on /etc/resolv.conf so that only a certain group, lets say 'net' has read access.
Every account part of the 'net' group could "use" the internet (since I wish you good luck to surf the web without DNS).
Create an account which is not part of the net group under which you log on during your studying.

I doubt such a solution would save you, but it's the answer to your question

---

### Post by kakashi on 2005-10-27
[QUOTE=gillion]Then you might as well forget it then.[/QUOTE]

not really 
i have plenty of control. 
its just that when azureus is working right on your taskbar you can't help but check out the progress or start a new dl. 
same way you can't just help but check if your favourite manga is translated or add just 1 new post at the forum.:rolleyes:

---

### Post by kazuya on 2005-11-01
off topic. Hello Kakashi-sensei.. Cool login name dude. I am guessing from the awesome anime, Naruto.

---

### Post by suRoot on 2005-11-01
[QUOTE=kakashi]not really 
i have plenty of control. 
its just that when azureus is working right on your taskbar you can't help but check out the progress or start a new dl. 
same way you can't just help but check if your favourite manga is translated or add just 1 new post at the forum.:rolleyes:[/QUOTE]


Come on, dude.  If you set it up, you'll know how to defeat it.  It's a lost cause.

---

### Post by queenorych on 2005-11-01
iptables has --uid-owner field.  Just make a rule. (you also may need to install the proper module(s)).  See iptables man page.

---

### Post by raghav_p on 2005-11-01
ha.. I get into the same problem (like now)..

When I need to really study, I shut off my wireless router. You might want to try disconnecting yourself from your internet connection?

---

