---
title: "problem with vimrc"
date: 2005-11-29
forum: Desktop Environments
---

### Post by clapton on 2005-11-29
Hi all.
I've got problem with vimrc, I don't know why, it was fine that somebody can help me :)


```
me@pcname:~$ vim
Cannot source a directory: "$HOME/.vimrc"
Hit ENTER or type command to continue

```

that's what appears when I type 'vim'.:(

This is the sample of vimrc that I been use, and on hoary I haven't any kind of problems
[http://www.stripey.com/vim/vimrc.html]("http://www.stripey.com/vim/vimrc.html")

---

### Post by amohanty on 2005-11-30
you probably have a folder called .vimrc in your home folder.
Goto Places->Home Folder
Select View->Show Hidden Files

find .vimrc and make sure that it is not a folder with a folder icon.

If that does not work please post the results of this command:
ls -F

HTH
AM

---

### Post by clapton on 2005-12-10
No, there's isn't a folder.
Sorry, I've been far away from linux, work with NI labview leaves me on *wintendo*
(If anyone knows a way to put labwiew work on ubuntu ... )


```
ls -f
.                 .gtkrc-1.2-gnome2     pics            .amsn
..                .update-notifier      .fonts.cache-1  .gimp-2.2
.bashrc           .nautilus             .xchat2         .icons
.bash_profile     Desktop               .xine           amsn_received
.Xauthority       .Trash                .face           TPI
.xsession-errors  .gksu.lock            .gdesklets      .adobe
.dmrc             .mozilla              cabulas         .local
.gconf            .gaim                 .macromedia     .openoffice.org2
.gconfd           .bash_history         .xscreensaver   Exercicios LabView
.gnome2           .gnome                docs            .evolution
.gnome2_private   .thumbnails           Biblia.zip      .xmms
.esd_auth         .recently-used        aula            analise_ju
.gstreamer-0.8    .vimrc                .dia            .aMule
.ICEauthority     .viminfo              .qt             drivers
.metacity         themes                .themes         labs
.rnd              .mozilla-thunderbird  .kde

```

[img]http://www.alojarfotos.com/images/clapton/capturaecra_4.jpg[/img]

---

### Post by elijah_snow on 2005-12-11
Is $HOME set? What do you see if you do
echo $HOME
or
env | grep HOME
?

---

### Post by clapton on 2005-12-11
$echo HOME

---

### Post by oxEz on 2005-12-11
I don't think that having $HOME/.vimrc/vimrc is right.
The .vimrc has to be directly in $HOME, if I remember correctly.
That's what I would suggest:
```

mv $HOME/.vimrc $HOME/.vimrc2; mv $HOME/.vimrc2/.vimrc $HOME
```

---

