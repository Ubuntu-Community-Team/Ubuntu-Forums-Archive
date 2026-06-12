---
title: "Share desktop icons with all users"
date: 2010-01-10
forum: Desktop Environments
---

### Post by Jasonx86 on 2010-01-10
Hi,

Another simple GNOME related question...

Is there a common desktop folder shared between all users of a system? i.e. If i place an icon in this common folder then all user desktops will have this icon.

If not how can this be achieved?


Thanks.

---

### Post by stinkeye on 2010-01-10
> **Jasonx86 said:**
> Hi,

Another simple GNOME related question...

Is there a common desktop folder shared between all users of a system? i.e. If i place an icon in this common folder then all user desktops will have this icon.

If not how can this be achieved?


Thanks.
/usr/share/icons

same deal for
/usr/share/fonts
/usr/share/themes

---

### Post by Boondoklife on 2010-01-10
I think you are asking a way to have the same desktop links on each desktop, no?

If so then really the best I could think of would be to change the default home directory skeleton and have it include the wanted desktop icons, but this would only work for new users and it would not update.

You could always write a startup script to be run by each user copying the links from a common folder to the desktop each login. This would be more what you want and easier to manage.

Hope that helps

---

### Post by Jasonx86 on 2010-01-11
> **Boondoklife said:**
> I think you are asking a way to have the same desktop links on each desktop, no?

Yes.

Shame there is no efficient way of doing this. In the end I created a script which copied the icons/lauchers to the Desktop folder for every user from the location of a folder which contains common launchers:

```

LAUNCHER_SRC=/usr/share/launchers
USERS_DIR=/home
cd "$USERS_DIR"
find -maxdepth 1 -type d | while read N
do
     (
       LAUNCHER_DEST="$N"/Desktop
           cd "$LAUNCHER_DEST" > /dev/null
           if test "$?" = "0"
           then
        user_name=${N//[-.\/_]/}
        echo "Recreating desktop icons for $user_name"
        rm -R *.desktop > /dev/null
        cp -R "$LAUNCHER_SRC"/*.* "./" > /dev/null
        cd "$USERS_DIR"
           fi
     )
done
```

---

### Post by Moddemeijer on 2011-03-17
Make a directory anywhere on the system.
Set the acces properties so that everyone has access
Make a symbolic link towards this directory

It would be something like

mkdir /anwhere/icons
cd /anywhere
chmod gua+rwx icons
ln -s /anywhere/icons ~user1/icons
ln -s /anywhere/icons ~user2/icons
and soon .....

---

### Post by stpgod on 2011-07-29
Jason, I need to do exactly the same thing. How did you get the script to run for each user?

---

