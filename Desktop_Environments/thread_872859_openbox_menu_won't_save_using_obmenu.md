---
title: "openbox menu won't save using obmenu"
date: 2008-07-28
forum: Desktop Environments
---

### Post by rolypolycat on 2008-07-28
Hello!

I've had this problem for some time now, and it's very annoying. I did a cli (using gutsy)  install of openbox. obmenu, obconf, and pcman fm. Everything works fine for a while, then for some strange reason, obmenu won't save any new additions I make. I've tried editing the menu in a text editor; it saves in the editor, but the changes don't come up in the menu. And obmenu won't save them. It says I made the changes, but acts like I never saved them.  Adding new categories, entries--zilch.
Anyone have any idea why obmenu stops saving anything new?:confused:
Thanks in advance!

---

### Post by eriqjaffe on 2008-07-28
I've never had that problem, but you may try running "openbox --reconfigure" in a terminal and see if the menu changes show up.

---

### Post by rolypolycat on 2008-07-29
I tried running openbox--reconfigure, but the terminal just says:bash: openbox--reconfigure: command not found.
Is there some special way to run that command in the terminal? I also ran the same command from the menu while obmenu was open, but no change. 

When I hit save in the obmenu program, I don't get any error message; only when I exit the obmenu program does the unsaved changes message show up.

---

### Post by Korrode on 2008-07-29
> **rolypolycat said:**
> I tried running openbox--reconfigure
You forgot the space.

openbox --reconfigure

;)

---

### Post by rolypolycat on 2008-07-29
Tried again; the command went through, but still won't save or change the menu. I re-installed obmenu, ran the command again,still no save. I'm really stumped with this one.

---

### Post by eriqjaffe on 2008-07-30
Something I just thought of - you **are** editing the menu.xml in your ~/.config/openbox directory, right?

---

### Post by rolypolycat on 2008-07-31
As far as I know, that's the one that I thought I was editing. Is there another menu somewhere else? Also, obconf doesn't save my changes anymore without an error message. Something must have gotten screwed up here. 
I was wondering, if I delete my menu.xml file and my rc.xml file, will openbox build new ones? Then I could just try with those. Or is it necesssary to re-install everything for a clean set of files?:confused:

---

### Post by urukrama on 2008-07-31
Are you sure you have read/write permissions for these files? (Right click on the file > Properties) If you don't, you obviously won't be able to edit them.

If you delete the rc.xml and menu.xml file in ~/.config/openbox Openbox will use the default configuration files, which are in /etc/xdg/openbox/ . You can copy those to your home directory with the following command:

```
cp -ri /etc/xdg/openbox/ /home/USERNAME/.config/
```

You don't need to reinstall Openbox.

Make sure you perform this action as your username (in other words, don't use sudo for this!), as you won't have read/write permissions for the files then. 

What error message does obconf give you?

---

### Post by rolypolycat on 2008-07-31
It says
"an error occured while saving the config file '/home/shell/.config/openbox/rc.xml
The file exists, so I don't know why it can't save.
I checked the permissions for menu.xml; they were somehow changed to root. I changed them to mine, and now obmenu is working again. I haven't the foggiest notion how it changed from one usr to the other, though. One other question: I put permissions as read, write, execute. Is that right for this type of file, or should I uncheck execute?

---

### Post by urukrama on 2008-07-31
You don't need execute for the rc.xml and menu.xml, but you do need it for autostart.sh.

---

