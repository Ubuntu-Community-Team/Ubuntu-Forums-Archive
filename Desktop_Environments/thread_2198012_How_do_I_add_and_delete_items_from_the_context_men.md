---
title: "How do I add and delete items from the context menu choices?"
date: 2014-01-06
forum: Desktop Environments
---

### Post by mactecdev on 2014-01-06
Recently my friends (a good thing if you ask me as that is how you learn by exploring but he didn't) overly curious kids broke the install of Ubuntu 10.04 LTS while playing around in the administration section and terminal. So I am setting up a system for them that allow their kids to have access to items in the context menu. Mainly they don't want them to have access to system administration and control centre. But once they have been removed all you have to do is right click edit menus and you can have them back again and even from the restricted user account. So I want to remove terminal from applications (and maybe other programs later on) and completely remove administration and control center from System in the launcher panel. How can I achieve this. I am not a total newb but please rty to keep it fairly simple so I don't have to bug you with added questions as to who now with the wtf
Thanks

I don't want to disable access to the context (right click menu, if it's called that in Linux too. I'm more of a Windows person sadly I like gaming) menu completely as this will make it a pain to copy and paste and create new folders just to mention a few areas where right clicking is indespensible

---

### Post by Bucky Ball on 2014-01-06
Might be easier to add the kids as new 'standard' users and restrict their access that way. Standard users can't sudo or do other things. They then log in with their own username and password. For dad (the administrator user) just log out a kid and log dad in.

[http://myubuntublog.com/adding-users-and-setting-permissions-to-users-within-ubuntu/](http://myubuntublog.com/adding-users-and-setting-permissions-to-users-within-ubuntu/)

Unsure if there's a way you can switch users or permission 'on the fly' in a running install by a simple switch.

---

### Post by Frogs Hair on 2014-01-06
10.04 is not supported anymore and the software repositories are not accessible unless the old repositories are added manually . You may want to consider installing 12.04 which will have support until 2017 before putting effort into an unsupported release. Newer versions of nautilus have different features in the context menu than they did with Gnome 2. There is also a guest account on newer versions that doesn't allow much tinkering and saves no personal settings after log-out. Edit menus is no longer an option unless alacarte is installed and even then doesn't appear in the context menu.

---

### Post by mactecdev on 2014-01-06
i am using 10.04 because on my laptop an Acer 3830tg the only problem is that I have to fix the sound on 12.04 I don't get video either and have never succesfully made it work. So to not run into those types of problems I thought I would just go the easier route

---

### Post by mactecdev on 2014-01-06
re: Might be easier to add the kids as new 'standard' users and restrict  their access that way. Standard users can't sudo or do other things.  They then log in with their own username and password. For dad (the  administrator user) just log out a kid and log dad in.'

I am going to hsve an admin and standard user account setup. But i want to block access to editing the menus at the top of the screen Applications Places and System it defeats the purpose if I remove the items like administration if all you have to do is right click and edit them again to show the choices again

---

