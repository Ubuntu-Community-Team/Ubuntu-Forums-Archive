---
title: "Xubuntu 17.10 - Make Xorg default"
date: 2018-03-21
forum: Desktop Environments
---

### Post by MotoTom on 2018-03-21
I am running standard Xubuntu 17.10 on a Samsung NC-110 notebook that I manage remotely using Teamviewer. 

Today I updated the system and now Teamviewer advises that it will not work with Wayland. How do I revert to Xorg? I've not been able to find a solution on the web so any help will be greatly appreciated.

Also, non-related, I'd appreciate knowing why I am forbidden to search on this forum. Need to check the FAQ on that.

Best,
Tom

---

### Post by #&amp;thj^% on 2018-03-21
[B]EDIT: Your title says Xubuntu??? Wayland is not used on XFCE?
First show us this from the terminal[/B]
```
echo $XDG_SESSION_TYPE
```

Well when you are first met at the login screen>>>look for the "cog" to the side of your user name and you should see options to effect of Ubuntu or Ubuntu on wayland.

If you wish to disable it at login on future starts, edit this file:
Via:
```
sudo nano /etc/gdm3/custom.conf
```

and uncomment the line

```
#WaylandEnable=false
```
by removing the # in front.

#WaylandEnable=false by removing the # in front.
So it will look like this
```
WaylandEnable=false
```

Save the file and then on reboot you will never see the cog asking for which session to use.

---

### Post by MotoTom on 2018-03-21
Many thanks, 1fallen.

"echo $XDG_SESSION_TYPE" says I'm running X11 which is what I expected. Now to figure out why Teamviewer thinks it's running Wayland. BTW, none of the Wayland folders are in /etc. Also there is no cog on the login screen.

Attached is a screen capture of Teamviewer that prompted this post.

Again, many thanks for your help.

Tom

---

### Post by #&amp;thj^% on 2018-03-21
> **MotoTom said:**
>  BTW, none of the Wayland folders are in /etc. Also there is no cog on the login screen.

Tom

Yes I rushed my reply and overshot "Xubuntu" >>>hence the edit.:)
And that location would not have been created "GDM" is a Gnome Thing and so is Wayland.
My friend I have no idea why that would show the "Wayland" issue?
You may have to open a ticket with Team Viewer, unless someone wiser here jumps in.
Good Luck

---

### Post by MotoTom on 2018-03-21
Already have headed to Teamviewer support for help.

Thanks for pointing me in the right direction.

---

### Post by #&amp;thj^% on 2018-03-21
Great! :) and if you would be kind enough to post back anything relevant I'm sure it would be useful to others here>
Kind Regards

---

