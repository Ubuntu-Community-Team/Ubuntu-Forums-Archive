---
title: "Add Groups and/or Applications to Global Menu(AppMenu)"
date: 2011-05-02
forum: Desktop Environments
---

### Post by babltiga on 2011-05-02
Hi, I want to add custom application launchers to Global Menu(AppMenu) is this possible and if yes how can I do that ?

Fore example I have an application at ~/apps/myapp/bin/myapp.sh and I want to add a launcher for it !

One more question is it possible to add Groups to Global Menu(AppMenu), as by default we have All Applications, Accessories, Universal Access .... I want to add new thing there.

Thanks in advance.


P.S. It will take ages to get in touch with this new features ... ;)

---

### Post by Krytarik on 2011-05-02
Please see my earlier post regarding both of your questions:
[http://ubuntuforums.org/showthread.php?p=10742492#post10742492](http://ubuntuforums.org/showthread.php?p=10742492#post10742492)

Greetings.

---

### Post by practic on 2011-05-02
Krytarik,

I don't think that really answers the question, at least not the second question.

What I would also like to know, is how to add in custom groups in the Categories list. For example, press Super-A. In the top right corner you see "All Applications" and if you click on it, you see categories, which are taken from the root of the regular Gnome Applications menu. But if you created any user-defined categories in previous Ubuntu/Gnome, or created any sub-categories...none of these show up. That means you will not see the applications in these custom categories, or sub-categories unless you search All Applications. This is unfortunate. 

For example, with the Ubuntu 10/Gnome menu system, I created a custom category under Office for PDF-related apps and viewers. None of these show up if I filter the categories to Office in the new Dash. I have to search for them by name with All Applications selected as the Category.

So if anyone knows how to hack the Categories, or where this stuff is stored, let us know. I've done a bit of poking around, but discovered nothing significant yet...

---

### Post by mc4man on 2011-05-02
> So if anyone knows how to hack the Categories, or where this stuff is stored, let us know. I've done a bit of poking around, but discovered nothing significant yet...
There is nothing I've seen as yet to allow modifying the globalmenu, dash and applications.place menus, certainly not creating tree's, -  though, 
you could apt-get and  take a look at the various source files, as far as the unity-place-application categories they're shown in /etc/xdg/menus/unity-place-applications.menu
Whether you can do anything there have never tried.. (likely not much if anything

Overall though I'd wait and see what comes down with 11.10 as far as offering any mods, ect

---

### Post by Krytarik on 2011-05-03
> **practic said:**
> 
I don't think that really answers the question, at least not the second question.

What I would also like to know, is how to add in custom groups in the Categories list.
I didn't say that there *is* a solution right now, but both topics were in fact handled by the thread I was linking to, the OP was asking for exact the same thing.

But +1 for *mc4man's* suggestion, I have no Natty install running, so I can't check some things for myself.

---

### Post by practic on 2011-05-03
Well the problem is worse than I thought. All the apps I had placed in subfolders in the Gnome menu will not show up under the Unity Categories even if I revert the Gnome menu to it's original layout, and then move the shortcuts to one of the standard places (in the Gnome Main Menu Editor (alacarte). 

I then thought, "Okay, I'll just uninstall the program and reinstall it." This also failed to bring it up under the proper category. I have probably over one hundred apps that do not show up under any category now, except "All Applications". That is a bit annoying.

I also found that apps do not immediately disappear from their category after uninstall. I just removed UMPlayer and it's still showing in Dash.

I took a look at the file you mentioned "/etc/xdg/menus/unity-place-applications.menu". I tried adding an item to it, and restarted unity, but it didn't change, so I guess the category references are tied to other files. One humorous thing though..inside that file was a comment:

```
<!-- Note: Software Center uses an OnlyUnallocated clause to generate
    --       the System section. We can't do that because we have the All Apps
    --       section. Let's cross fingers and hope we match somewhat
    -->
```

Hunhh?? :confused: "Let's cross fingers"??! Since when is that a standard coding practice?! C'mon guys, if you don't code it in, it isn't going to work! ](*,)

---

### Post by Krytarik on 2011-05-03
> **practic said:**
> Hunhh?? :confused: "Let's cross fingers"??! Since when is that a standard coding practice?! C'mon guys, if you don't code it in, it isn't going to work! ](*,)
I have to agree, that seems indeed very harsh if it reflects the current reality!! Not very confidence-building in either case.
As much as I like the hidden comments in the code -namely themes-, somewhat easter-egg type, that seems too heavy!

---

### Post by practic on 2011-05-03
> **Krytarik said:**
> I didn't say that there *is* a solution right now, but both topics were in fact handled by the thread I was linking to, the OP was asking for exact the same thing.

Well I might be misunderstanding something, but in that post you linked to the OP had a similar problem as I do. His screenshot shows that he had a special menu in Gnome for Music applications. He wanted to know how to add that to the Category list in Dash, or on the App icon right-click category list. There was no answer to this problem. 

Yes, you can make a custom launcher with it's own right-click menu...I know how to do that. But to do that for 50 or 100 applications is a big task.

And that is the same problem I have. Once these programs are in a separate menu in the Gnome menu system, Natty just ignores them. They only show up under "All Applications", with the 200 or 300 other apps. Uninstalling the apps and reinstalling them did not seem to fix it either.

It's not really a minor problem...there are about 100 orphaned applications that belong under Multimedia, Graphics, and Office, but which will not show up there. It makes these categories almost useless for me.

---

### Post by practic on 2011-05-18
Okay, I found a solution to my problem!

Shortcuts to applications have a ".desktop" extension and are located in two places: 

1. /usr/share/applications
2. .local/share/applications

When you first install an item, it puts a .desktop file in /usr/share/applications. What category or menu the app shows up under is written in the category section of the file. For example, here's the desktop file for Dia (with some of the alternate language entries removed for brevity):

```
[Desktop Entry]
Encoding=UTF-8
Name=Dia Diagram Editor
Comment=Edit your Diagrams
Type=Application
Exec=dia %F
Icon=dia
Terminal=false
Categories=GNOME;Graphics;
StartupNotify=true
MimeType=application/x-dia-diagram;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=dia
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=@0.97.1@
```

The value after "Name=" is what appears in the menu (or in the Dash search).

The value after "Icon=" is the icon associated with this shortcut, which is handy to know in case you have a program that doesn't seem to have an icon...you can add one in here. I think it automatically searches /usr/share/app-install/icons, and expects the "png" extension, if not specified. Nevertheless, you can also provide the whole path and extension, just to be safe.

The value after "Categories=" determines what category (or menu) the shortcut appears under. In the above example, if I change "Graphics" to "AudioVideo", then Dia will show up under the Multimedia category in Dash! It happens instantly, right after you save it (no need to log in/out).

Every time you move or copy an item in "alacarte" (the Gnome Menu Editor), it makes a copy in .local/share/applications. Whatever is in .local/share takes precedence over /usr/share. So when I made custom menu categories in alacarte, they got orphaned from the standard categories that Dash now uses.

The solution is to delete the ".desktop" files in ".local/share/applications" and keep the originals in "/usr/share/applications". This will revert all the shortcuts to their original categories, and they will no longer be orphaned! Yay, no need to do a clean install!!

---

