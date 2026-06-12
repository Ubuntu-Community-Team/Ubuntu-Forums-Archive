---
title: "want delete list program can't use"
date: 2009-01-17
forum: General Help
---

### Post by ngetngot on 2009-01-17
allow, im newbie in use linux ubuntu. now i use ubuntu  hardy in my computer. i just got trouble. please i need your help.

the problem is  I want delete history list program i already use.

i just open program file but my hardy really can't read the program. my ubuntu hardy not supported to open this program before i already installed program for open it. because i wanna try and make experience, i always open the program with properties the file program i want open > show me option aplication i want use to open program.

because in that option nothing list program i like, i use option command in below. browse in filesytem and choose application i want use.

after choose in command, the program always can't open. but the history program i already use always show in my list program.i want delete it. because that list disturb for me. nothing program it can open.i can't find option for delete.

the file i want delete [ like this]("http://i248.photobucket.com/albums/gg192/dingting_2008/Screenshot.png"). in this image have control panel app. new application i already add in my ubuntu. soo this program in my list i want deleted. did anyone know to fix this???:(

thank before:)

---

### Post by utnubuuser on 2009-01-17
Applications >> Accessories >> Terminal >> type: sudo apt-get remove --purge nameofprogram >> enter

---

### Post by ngetngot on 2009-01-19
wait brother my problem not solved yet:(

i mean delete list program not to uninstall the program from my ubuntu.

let u now. try to open file program. **before u open** > click properties > scrool to tab open with > click add > scrool below use a **custom command** and browse in filesystem choose file u want to open. **finish**. 

and what happen???

in my ubuntu hardy in tab **open with** have a list program I add before from custom command. this list i want delete. how too???

in your command i have this
> eddy@eddy-desktop:~$ sudo apt-get remove --Purge ControlPanel
[sudo] password for eddy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ControlPanel
eddy@eddy-desktop:~$ 


i hope u understand:P

---

### Post by ngetngot on 2009-01-30
no anybody can help me???:(

ubuntu is difficult for use???

---

### Post by jrusso2 on 2009-01-30
I am sorry and I realize english is probably not your first language but I am very confused by your post what you want to do.

---

### Post by slakkie on 2009-01-30
I do not know what your primary language is, but maybe you can fire up a irc client and ask the question in your native language in a localized ubuntu channel: [https://help.ubuntu.com/community/InternetRelayChat#Channels](https://help.ubuntu.com/community/InternetRelayChat#Channels)

I also have problems understanding your question :(

---

### Post by todak on 2009-01-30
Deleted

---

### Post by mc4man on 2009-01-30
Navigate to home folder -> .local/share/applications  (.local is hidden, when in home folder go Ctrl+h if not visible or edit -> preferences -> show hidden files...

If in the applications folder you see a blue diamond named controlpanel delete it.

---

### Post by drs305 on 2009-01-30
Another option, if I understand your situation is that you can't remove an option you created. 

Try opening your mimeapps.list with the following command:
```

cp $HOME/.local/share/applications/mimeapps.list $HOME/.local/share/applications/mimeapps.list.bak  # make a backup 
gedit $HOME/.local/share/applications/mimeapps.list

```
Once it opens, see if you can find a line listing "jar" and "ControlPanel". If you do, delete the line and save the file.

---

### Post by todak on 2009-01-30
**drs305**: my solution was incorrect. **mc4man** got it right. The menu you see in the OP image is what you will see when you select **Add** and then **Use a custom command** from the **Properties** context menu. Mine was just the **Open With** dialog. So I removed my post to avoid confusion.

---

### Post by drs305 on 2009-01-30
Ok *todak*, I modified my previous post should the app not appear in the folder as mc4man suggests.

---

### Post by mc4man on 2009-01-30
If it was created off of the r. click 'open with other application' -> 'use a custom command' then there will be a userapp.desktop in applications (blue diamond

The .desktop is what showing up in the r. click menu, the mimeapps line is where it's registered.

If you want to remove the entry and or line it would look like below (the actual userapp entry would be slightly different (different name, number

If it's the only entry then delete the line, otherwise just the entry, (no spaces, end with ;

application/x-java-archive=userapp-evince-7M1UOU.desktop;file-roller.desktop;

should look like after deleting entry

application/x-java-archive=file-roller.desktop;

---

### Post by ngetngot on 2009-02-02
thank for mc4man. im happy. my problem solved now.  i use your command like this;)
> Navigate to home folder -> .local/share/applications (.local is hidden, when in home folder go Ctrl+h if not visible or edit -> preferences -> show hidden files...

If in the applications folder you see a blue diamond named controlpanel delete it.
soo,i can remove an option app list i created use custom command file > program properties > **open with**.

@all
im soory, my english not good:( i just want say thank for all. thank for give me good answer. i will try and eror with ubuntu. i think will make new post again with different eror problem, make experience more and more;)

---

