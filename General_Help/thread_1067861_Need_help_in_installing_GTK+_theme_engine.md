---
title: "Need help in installing GTK+ theme engine"
date: 2009-02-12
forum: General Help
---

### Post by walker077 on 2009-02-12
I recently installed a desktop theme called overglossed forgot the version though. Anyway, after I installed the theme, it says in the background setting that the theme will not display properly until I install a white and black something. I forgot its real name T_T, anyways I downloaded it and then installed it but then my background settings displayed another message saying I don't have a GTK+ theme engine installed. So I searched for it in the package manager but then there appeared too many results. I didn't know which GTK+ theme engine to download so I just chose 2 out of the many results which I think is right then installed it but the message still did not change. I'm an absolute newbie when it comes to linux and I hope you guys could help me out here. What version or what is the exact name of the GTK that I need to download. I'm currently using a linux mint distro if anyone needs to know and the theme I need to install is overglossed. Hope someone could help.

---

### Post by IceReaver75 on 2009-02-12
Does it just say the gtk engine "" isn't installed cause if that's the case there is 2 things you can do to fix it:

1) Just ignore the message : it isn't hurting the theme any just has to do with the way ubuntu intrepid ibex reads the themes now but like I have stated all aspects of the theme will still work

2) You can navigate to either your /home/.themes(which is a hidden file) or to /usr/share/themes and find the over glossed theme folder.  In that folder you will find the gtk 2.0 folder.  Inside that folder you will find a gtkrc file.  Open that file up with a text editor and usually towards the bottom you will find something that looks like this:

style "unstyle"
{
  engine ""
  {
  }
}

change it to this:

style "unstyle"
{
  engine "pixmap"
  {
  }
}

and it will stop complaining about the theme engine not being installed.

---

### Post by walker077 on 2009-02-12
How do you edit it? It keeps saying that I don't have the authority to change it. How can I save it?

---

### Post by dox_drum on 2009-02-12
> **walker077 said:**
> How do you edit it? It keeps saying that I don't have the authority to change it. How can I save it?

You should open the file using sudo command

```
sudo gedit .theme/(etc)
```
and it'll ask you for the root's passwork (if you have installed Ubuntu by your own, it's most likely to be your password)

[CENTER]Enjoy![/CENTER]

---

