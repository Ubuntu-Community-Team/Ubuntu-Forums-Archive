---
title: "[SOLVED] Apply theme to ALL windows"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by Zodiachus on 2008-04-02
Hello,


I've noticed that when I apply a theme, it doesn't apply to all windows. I'm just wondering, why is this and how do I rectify it? I've attached a screenshot to show you what I mean. The theme in the screenshot is what gets applied to some windows if I apply ANY theme other than the default one.

Oh, and I run 8.04.


Many thanks,

Henrik

---

### Post by viciouslime on 2008-04-02
You'll notice it isn't applied to any windows that are running with escalated privileges, i.e. you've had to enter your password to run them. To fix this, you need to copy your theme to /usr/share/themes and ti will work :)

If you need any help on doing this, let me know.

---

### Post by Zodiachus on 2008-04-02
Oh I see! Is it because these are essentially run by a different user (root)? 

So for every theme I install, I need to copy the same to /usr/share/themes? Is there any good reason why this isn't done automatically?

---

### Post by Sukarn on 2008-04-02
Useless/Incorrect post. Contents removed.

---

### Post by nebu on 2008-04-02
the windows which are not themed as u want them to be are tose of the root user.....

if u want to change the root user theme....

first get root acess...

> su
u wil have to enter the root password here....

then enter...
> gnome-appearence-manager

now if u select the theme... it should also be applied to the windows in question....

---

### Post by Zodiachus on 2008-04-02
After testing, it seems that I don't have to change theme for the root user at all. All I had to do was to copy the theme to /usr/share/themes, and it was applied automatically when an escalated window was opened, like viciouslime suggested.

This suggests that an automatic theme changing indeed takes place for the root user anyway, as long as the theme in question is accessible in /usr/share/themes.

I did a little experiment: 
I created a new user and kept the original Human theme. I opened synaptic and switched over to my default user, applied a different theme (than Human) and opened another escalated program (sudo nautilus). Neither program took on the wrong theme - both kept the themes of the currently logged in user, even though the programs were theoretically run by the same user (root).

It seems to me that theming of escalated programs is handled gracefully even though more than one user is logged in (and using different themes).

---

### Post by viciouslime on 2008-04-02
Yeh there's no need to change the root theme because root effectively doesn't exist, I actually change my original post because in it I had also put that it was because the programs are running as root, but this isn't actually true. I think it goes as follows.

When you use gksudo, there is something done to prevent anything that is then "running as root" (though really it's running as you still, but you temporarily have super user privileges) from overwriting things in your home directory. If it were allowed to overwrite things in your home directory e.g. config files, or anything in the .themes folder, then when you weren't using sudo/gksudo, you would no longer have permission to read/write/execute those files.

The reason themes aren't automatically copied to /usr/themes is because you install themes as a standard user and as a standard user you don't have permission to write there, only to the .themes folder in your home directory.

I hope that makes it a little clearer...

---

### Post by Zodiachus on 2008-04-03
Right, thanks viciouslime, that makes sense.

Maybe a good solution would be to have an "Install for all users" button when you mark a theme, which brings up a PolicyKit window for authorization of the request. 
Maybe even group the themes into two sections in the team selection window: "Your themes" and "Shared themes" or some similar distinction to make clear which ones are your personal ones, and which ones are shared.

---

### Post by viciouslime on 2008-04-03
That does sound like a very good idea, perhaps you should suggest it on launchpad?

---

### Post by Zodiachus on 2008-04-03
OK, I'll post it there!

There is one thing that concerns me though: how do you make it apparent to a user that a theme needs to be shared for it to affect all windows (i.e. escalated applications)? 
The reason why is logical enough once you know it, but many potential users are not going to be very familiar with the underlying system at all. It might prove to be a usability issue; even if there is a solution handy (as proposed above) that doesn't require any command line work, how do you help the user make a logical connection between the sharing of a theme and the theming of all windows?

---

### Post by Sukarn on 2008-04-03
The first time the theme window is opened, display a message saying something like -

> 
If a custom theme is installed by a user then it can only be used by that user and not other users (including the windows opened as root by the user who installed the theme).

If you want a custom theme to be applied to windows like Synaptic and Update-manager, which ask you for your password so that they can be run with administrator privileges, then press the "Copy to root" button when you are done customizing and applying your theme. This will ensure that you get the same theme in all windows.


There should be a check box at the bottom of the window that says "Do not show this message again".

This would be like the message window you get when the first time you run synaptic. That window tells you how to use synaptic.


Maybe this can be displayed the first time a user installs a theme.

---

### Post by kpkeerthi on 2008-04-03
> **Zodiachus said:**
> Hello,
I've noticed that when I apply a theme, it doesn't apply to all windows. I'm just wondering, why is this and how do I rectify it? I've attached a screenshot to show you what I mean. The theme in the screenshot is what gets applied to some windows if I apply ANY theme other than the default one.


Simply link the .themes folder to root's
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

```

---

### Post by viciouslime on 2008-04-03
> **kpkeerthi said:**
> Simply link the .themes folder to root's
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

```

This won't work as the programs aren't running as root. They're running as you but with escalated privileges. Also, you couldn't link that directory to more than one user's .themes folder, so this would only work for one user.

---

### Post by Sukarn on 2008-04-03
> **viciouslime said:**
> This won't work as the programs aren't running as root. They're running as you but with escalated privileges.

And since the programs will be running with root privileges, any changes taking place to the stuff inside .themes as root will change the permission for you as well.

---

### Post by metrorat on 2008-04-29
Hi folks.  I'm having the exact same problem - with the Mac4Lin theme specifically.  When I open Synaptic the Emerald OSX theme window borders are correctly applied but the window contents and progress bars etc appear in nasty default colours with complimentary sketchy icons.  Also if I run Nautilus as root I get the same thing.  Copying the Mac4Lin theme I save to /usr/share/themes had no effect.  Any more ideas, please?

Cheers...

---

### Post by kylirh on 2008-07-12
Thank you very much for this information. I was having the same problem, but it turns out to be an easy fix! Thanks!

---

