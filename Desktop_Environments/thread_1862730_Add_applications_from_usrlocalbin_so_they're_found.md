---
title: "Add applications from /usr/local/bin so they're found by gnome shell"
date: 2011-10-17
forum: Desktop Environments
---

### Post by jozeph78 on 2011-10-17
How do I get applications I've installed from source or other than apt to be found by the gnome shell launcher? Is there a setting to have it look at /usr/local/bin or do I need to move the link/executable somewhere?

Thanks.

---

### Post by jozeph78 on 2011-10-17
I just learned that creating a desktop file in /usr/share/desktop is what i was after. Wish make install would have created that =/

---

### Post by suspa555 on 2011-10-17
Even am looking for the same.I too don't have any idea on it,if you people can guide us.

---

### Post by suspa555 on 2011-10-17
The best thing is to read all the manuals before uploading any thing,it could be possible u have missed something while downloading the first disc,Jst do it once again .

---

### Post by jozeph78 on 2011-10-17
I'm not sure what you're talking about. If you'd like, I can detail the process of creating a .desktop for an application. 

Basically, there are a bunch of .desktop files in /usr/share/applications. I needed to create one for Emacs (I use emacs 24 and compile it from HEAD, if you don 't know that that means don't worry). 

I basically copied a similar .desktop file (Gedit):


```

sudo cp /usr/share/applications/gedit.desktop /usr/share/applications/emacs.desktop

```

Then edited the values so they made sense for emacs instead of Gedit. The values are pretty straightforward but I did stumble across a reference for every known value which I can find if you'd like.

---

### Post by areeda on 2011-10-17
Thanks Joseph,  I have a few new apps to add also.

I found a couple of links that describe in detail the .desktop files:

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

[https://wiki.ubuntu.com/PackagingGuide/Howtos/DesktopFiles](https://wiki.ubuntu.com/PackagingGuide/Howtos/DesktopFiles)

I wonder if /usr/share/applications is the correct place for applications that are loaded by a regular user into their account.  I realize the OP is talking about things in /usr/local which are system wide.

Is there a "standard" place in my account for these types of files?

Joe

---

### Post by crdlb on 2011-10-18
> **areeda said:**
> Is there a "standard" place in my account for these types of files?

~/.local/share/applications/ is the user equivalent of /usr/share/applications/.

---

### Post by areeda on 2011-10-18
> **crdlb said:**
> ~/.local/share/applications/ is the user equivalent of /usr/share/applications/.
Thank you

---

