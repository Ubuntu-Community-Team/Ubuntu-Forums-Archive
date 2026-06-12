---
title: "Shortcut to a .sh file?"
date: 2005-09-02
forum: Desktop Environments
---

### Post by sandmanfvr on 2005-09-02
I created wow.sh to execute World of Warcraft.  I can terminal to /home/mmelton and then run it with **sh wow.sh**, but can I make a shortcut?  Thanks.

---

### Post by frodon on 2005-09-02
Could you show me your script ?
Why didn't you add cd home/mmelton line in your script and then put it in /usr/bin in order to be allowed to execute this script everywhere ?
I use icons in the gnome panel to run my scripts, to do that : right click on gnome panel and add a shortcut, choose custom shortcut in the menu and add /usr/bin/wow.sh in the command field and select "run in a terminal" option if your script use a sudo command and ask you for your password.

---

### Post by sandmanfvr on 2005-09-02
Well still new to Linux.  I have played with it before, but my script is:

cd /media/cdrive/Program\ Files/World\ of\ Warcraft
*execute command I got from Transgaming*
cedega wow.exe -opengl

So what do I need to do to make it executable from anywhere?  Thank you.

---

### Post by dahli.llama on 2005-09-02
You should be able to just put that sh file in your /home directory and then make a launcher that executes sh wow.sh

That's what I did for City of Heroes and a few other games and it works just fine.

---

### Post by frodon on 2005-09-02
Your script looks good.
If you want to be allowed to run your script from everywhere put it in /usr/bin : ```
sudo mv /home/mmelton/wow.sh /usr/bin
``` and restart your terminal. 
But you just want to make an icon which run your script, so you will not need to use the terminal to launch the game but the icon, you can put it in /usr/bin or not ... up to you.
So all you have to do to create your icon is : 
right click on gnome panel and add a shortcut, choose custom shortcut in the menu and add /home/mmelton/wow.sh (or /usr/bin/wow.sh if you put your script in /usr/bin) in the command field .

good game  ;-)

---

### Post by sandmanfvr on 2005-09-02
[QUOTE=frodon]Your script looks good.
If you want to be allowed to run your script from everywhere put it in /usr/bin : ```
sudo mv /home/mmelton/wow.sh /usr/bin
``` and restart your terminal. 
But you just want to make an icon which run your script, so you will not need to use the terminal to launch the game but the icon, you can put it in /usr/bin or not ... up to you.
So all you have to do to create your icon is : 
right click on gnome panel and add a shortcut, choose custom shortcut in the menu and add /home/mmelton/wow.sh (or /usr/bin/wow.sh if you put your script in /usr/bin) in the command field .

good game  ;-)[/QUOTE]
 Thanks.  I will move that over tonight and make an icon. :)

---

### Post by plb on 2005-09-02
be sure to mark the script executable......... chmod +x /usr/bin/wow.sh

---

