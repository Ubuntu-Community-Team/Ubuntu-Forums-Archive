---
title: "logining into root"
date: 2005-12-13
forum: Desktop Environments
---

### Post by bidza on 2005-12-13
hey guys i'm kinda new to using ubuntu linux, previously i was using fedora core 3, but got fed up with it. however i' having a few problems with my ubuntu, when i try using my login password to log into my root, i'm denied the access to my root. do u guys know how i can set my password so that i'll be able to got to my root. secondly i was wondering wat kind of installation packages i can use to install applications on my ubuntu, coz i tried using the .rpm packages from my fedora but they don't work.

---

### Post by 23meg on 2005-12-13
```
sudo passwd root
``` will allow you to use root. System / Administration / Login Screen Setup / Security / Allow root to login with GDM will allow you to log in as root in GDM.

Disclaimer: Don't do it. Use sudo.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

To convert rpm files to deb, use alien. ```
sudo apt-get install alien 
```will install it.

---

### Post by aysiu on 2005-12-13
[QUOTE=bidza]hey guys i'm kinda new to using ubuntu linux, previously i was using fedora core 3, but got fed up with it. however i' having a few problems with my ubuntu, when i try using my login password to log into my root, i'm denied the access to my root. do u guys know how i can set my password so that i'll be able to got to my root.[/quote] You shouldn't need to. In order to make root changes graphically, just run the command ```
gksudo nautilus
``` If you find yourself doing that a lot, consider making a launcher on the panel for that command or even a keyboard shortcut. When prompted for a password, it's the password of the first user you created.

If you prefer to make root changes in the terminal, just preface each command with the word *sudo*. Instead of this ```
su
password:
apt-get update
apt-get install program
exit
exit
``` you would type this ```
sudo apt-get update
password:
sudo apt-get install program
exit
``` > secondly i was wondering wat kind of installation packages i can use to install applications on my ubuntu, coz i tried using the .rpm packages from my fedora but they don't work. Are you lacking an internet connection? If so, use alien (as described above). Otherwise, you should use .deb files and it's best to use apt-get to install (or Synaptic, if you prefer a graphical installation).

---

### Post by Zonkle on 2005-12-13
What is root ::? ?
Isn't it the same when I login to ubuntu normally???
And what is grahpical sudo !?

I'm kind of confused guys ...

In Windows there were like guest,Mod,Admin ...... so does it go in Linux ??

I installed some theme the other day ... and I noticed that some programs has their GUI in different theme (they look old ... not usual) ... and I heard it has something to do with root. ... can some body explain please?

Thanks.

---

### Post by 23meg on 2005-12-13
[QUOTE=Zonkle]What is root ::? ?
Isn't it the same when I login to ubuntu normally???[/quote]
[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)
[QUOTE=Zonkle]
And what is grahpical sudo !?
[/quote]
It's the way of launching GUI apps as root, essentially the same as [sudo]("http://wiki.ubuntu.com/RootSudo").[QUOTE=Zonkle]
I'm kind of confused guys ...

In Windows there were like guest,Mod,Admin ...... so does it go in Linux ??
[/quote]
In Linux there's root (the superuser), and normal users with certain levels of privileges. When you have to make system-wide changes, you have to become root. An easy way to become root for the duration of one single command is "sudo" which is short for "superuser do", like in "do as superuser".

[QUOTE=Zonkle]
I installed some theme the other day ... and I noticed that some programs has their GUI in different theme (they look old ... not usual) ... and I heard it has something to do with root. ... can some body explain please?

Thanks.[/QUOTE]
Start the theme manager as root with ```
sudo gnome-theme-manager
``` and choose a theme for root. Now every app you launch as root with sudo or gksudo will be decorated with this theme.

---

### Post by Zonkle on 2005-12-13
Thank you very much 23meg that was very helpfull :)

About the theme thingy ..... I didn't run any program as root before .. I think I did run gedit before ...... but can you please explain why is this happening?

As I understand ... I think that the theme manager ran as (from) normal user ... so then it couldn't effects the root programs' theme? ..... but I thought that all the windows that shows inherits the theme of the system ::?... or it works in a different way?

Thanks ;)

---

### Post by 23meg on 2005-12-13
[QUOTE=Zonkle]Thank you very much 23meg that was very helpfull :)

About the theme thingy ..... I didn't run any program as root before .. I think I did run gedit before ...... but can you please why this is happening?

As I understand ... I think that the theme manager ran as (from) normal user ... so then it couldn't effects the root programs' theme?

Thanks ;)[/QUOTE]That's correct; programs you run as a normal user use the theme you select with gnome-theme-manager from the themes in your ~/.themes folder, whereas those you run as root use root's selected theme under /root/.themes .

---

### Post by Zonkle on 2005-12-13
Thanks :)

So all programs looks for the theme folder .... I get it :)
But it is kind of weird .... isn't it ? ... all progs should have the same look I think ... any way .. thanks :D

Cya ;)

---

### Post by 23meg on 2005-12-13
They don't look for the theme folders, they just happen to be the default folders where themes are stored. You select the themes to be used with gnome-theme-manager from those folders. When you run gnome-theme-manager as root you'll only see the themes under /root/.themes as choices.

> But it is kind of weird .... isn't it ? ... all progs should have the same look I think ... any way .. thanks All programs do look the same, it's just that they look different ways to different users. This is the *nix way, to which you'll have to get used :cool:

---

### Post by Zonkle on 2005-12-13
[QUOTE=23meg]When you run gnome-theme-manager as root you'll only see the themes under /root/.themes as choices.[/QUOTE]

So I have to re-install the theme again I guess in the root.... waste space!?

[QUOTE=23meg]This is the *nix way, to which you'll have to get used :cool:[/QUOTE]

Are you threatening me :D ? heh ... just kidding, I'll try getting used to it. BTW, I've just saw you are from Istanbul ... we're nieghbors :) I'm In Syria.

Cya ;)

---

### Post by 23meg on 2005-12-13
You don't have to reinstall, you can make symbolic links from the ~/.themes folder to /root/.themes with the "ln" command (-s parameter) or by drag and drop (middle button).

---

### Post by kaamos on 2005-12-13
[QUOTE=Zonkle]So I have to re-install the theme again I guess in the root.... waste space!?[/QUOTE]

Not if you create a link from your root account to your user account. meaning:
```

sudo ln -s /home/**username**/.themes /root/.themes
sudo ln -s /home/**username**/.icons /root/.icons

```

---

### Post by Zonkle on 2005-12-13
Thanks kaamos :) that cleared it out.

But what about that middle button dragging ??

---

### Post by 23meg on 2005-12-13
When you drag and drop something with the middle button, there appears a "Link here" option that allows you to do the same thing with the GUI.

---

