---
title: "broke lubuntu again. Lxde and Lubuntu netbook still work fine"
date: 2014-12-05
forum: Desktop Environments
---

### Post by RabbitWho on 2014-12-05
I the session before I broke it I didn't run any commands from the terminal (except to write "launchy" and "which launchy") 

What I did do was 

install recommended updates

uninstall slypheed using lubuntu software center (i put it back again and it hasn't helped) 

in **"default applications for lxsession"** I changed the file manager from **pcmanfm** to something that just said "files", but I've changed that back and it  hasn't helped... but **I've changed it back through LXDE / lubuntu desktop**, not lubuntu itself since I Can't get in, maybe that's the problem.

changed default communication 1 to empathy (back to pidgin and it hasn't helped)

added **launchy** and **empathy** to **autostart** (they're not there now, but probably because I'm in lubuntu desktop) 

I have run 
```
sudo apt-get update && sudo apt-get -f install 
```
and
```
sudo apt-get install lubuntu-desktop 
```

and it hasn't worked


I can still see lubuntu on the login screen but when I go to log in it won't, it goes black for a split second, then takes me back to the login screen.

Thanks in advance for your help



(if this was related to the things I uninstalled.. is there a list somewhere of default programs it's actually safe to uninstall?)

---

### Post by RabbitWho on 2014-12-05
Ok, that was a dramatic adventure. 

Most important things: if you are going to change anything.. ANYTHING on lxsession, make sure that your computer does not log into that desktop manager session without asking for a password, as mine does (I have a bios password instead) because if you completely break lubuntu it won't matter that ubuntu and lxde are working fine if your computer starts right into a broken desktop when you restart. 

Next thing:

If you're going to change something on lxsession.. maybe don't, but if you are going to, save the contents of both files in ~/.config/lxsession/lubuntu so that you can revert it back to that if you have a problem.

If i had to do this over what I would do would be to edit the startup file in that folder directly, and I would write this: 
```

@xscreensaver -no-splash
@lxpanel --profile Lubuntu
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
launchy

```
(empathy opens directly and doesn't run in the background, so i took it out) 
If you don't want to use pcmanfm.. don't touch it! just put a link to nautlius on your panel instead of pcmanfm.. because if you try to do anything to that program at all lubuntu won't start properly.  There might be a way to do it without breaking lubuntu, but don't try uninstalling it or using lxsession, because i broke lubuntu both those ways



I made a video about how to add launchy to your startup programs in lubuntu without breaking it like I did. [http://youtu.be/L0QN2fedKfQ](http://youtu.be/L0QN2fedKfQ)

---

