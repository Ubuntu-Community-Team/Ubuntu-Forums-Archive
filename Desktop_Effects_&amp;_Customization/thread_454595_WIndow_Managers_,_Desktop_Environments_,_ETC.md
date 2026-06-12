---
title: "WIndow Managers , Desktop Environments , ETC"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by Cows on 2007-05-25
I have been using ubuntu for about 2-3 months now and its currently my only os ( I switched completely from windows ). Now everyone knows that there is ALWAYS something to learn. My questions ATM are:

For GNOME:
Gnome = Desktop Environment ( Meaning all the gnome applications )
Metacity = Window Manager
Nautilus = File Manager

Now I want to change my window manager and file manager. So far I tried Rox as file manager and it's not bad. Also Thunar is a good file manager. I use Window Maker as my window manager and used icewm , fvwm , fluxbox , etc. I want to also know what are some other managers like rox that make icons on my desktop and a few more customization tips/tricks that you can give me. Thank you.

**EDIT**: Learned how to make Thunar my default file manager.
Also im using gnome idk as wat im using it atm .. I have the panel open on the bottom and nautilus is not started so thats good. Thunar took over nautilus. as my window manager atm im using beryl. Now for a low end machine I don't have the luxury of using beryl as my window manager. So can someone teach me how to remove the workspace and stuff from icewm panel?

**aysiu's desktop**
[http://ubuntuforums.org/attachment.php?attachmentid=16238&d=1159087147](http://ubuntuforums.org/attachment.php?attachmentid=16238&d=1159087147)

I already have the theme 'IceBuntu'.

---

### Post by Cows on 2007-05-25
Bump

---

### Post by juxtaposed on 2007-05-25
>  I use Window Maker as my window manager and used icewm , fvwm , fluxbox , etc. I want to also know what are some other managers like rox that make icons on my desktop and a few more customization tips/tricks that you can give me. Thank you.

A good way to customize gnome is to take away it's window manager (metacity) and replace it with one that uses much less resources.

sudo apt-get install openbox
openbox --replace

And some other file managers to try are PCManFM and Nao.

---

### Post by Cows on 2007-05-25
Alright thank you. Im testing them out atm and I need as much help as possible so anything else tips/tricks you want to teach me you can :). If you can also add me on msn or msg me ur msn.

---

### Post by merlinus on 2007-05-25
> 
I already have the theme 'IceBuntu'.


OK, so where can I get this?  I have searched the forums, and looked in Add/Remove and Synaptic.

Thanks!

-merlin

---

### Post by Cows on 2007-05-25
You get it from freshmeat's theme website .. let me get you the link ..

ok just open terminal and copy/paste this:

```
wget http://themes.freshmeat.net/redir/icebuntu/64282/url_tgz/icebuntu-default-feisty.tar.gz
```

---

### Post by merlinus on 2007-05-25
OK.  I downloaded the file and followed these instructions for installing:
To Install a New Theme

You can add a theme to the list of available themes. The new theme must
be an archive file that is tarred and zipped. That is, the new theme must
be a .tar.gz file.

To install a new theme, perform the following steps:

   1.                Start the Theme preference tool.
              
   2.                Click on the Install Theme button.
      A Theme Installation dialog is displayed.
              
   3.                Enter the location of the theme archive file in the drop-down
      combination box. Alternatively, to browse for the file, click on the Browse button. When you have selected the file, click OK.
              
   4.                Click on the Install button to install  the new theme.

But then I got an error message that the file format is invalid.  Now what???

Thanks for your help!

-merlin

---

### Post by Cows on 2007-05-26
I can't tell you how to do it since I don't use IceWM but there should be a themes folder in your .icewm dir.

---

