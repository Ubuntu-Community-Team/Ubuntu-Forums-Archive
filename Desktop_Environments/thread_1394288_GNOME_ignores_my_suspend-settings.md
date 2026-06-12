---
title: "GNOME ignores my suspend-settings"
date: 2010-01-30
forum: Desktop Environments
---

### Post by produnis on 2010-01-30
Hi folks,

usually my PC gets into suspend-mode after 10 miuntes of idle..

As there is no way to change 10 minutes to 1 minute graphically, I
tried the following command in  a terminal today:

```
gconftool --set --type int /apps/gnome-power-manager/timeout/sleep_computer_ac 60
```


Unfortunately, now the PC won't suspend automatically at all!

If I type in

```
gconftool --get /apps/gnome-power-manager/timeout/sleep_computer_ac
```
it answers   "60" , so settings seem to be ok...


I even rebooted my PC, but no chance - it won't suspend...

If I do it graphically, then my PC suspends, but if it runs idle, there is no suspend at all.--


Anyone any hint?
If I graphically reset it to 10 Minutes, and then click "make it default" (mine is german language), then everythings ok again--

Is there something I need to do additionally to the gconfeditor-command to get it right?

---

### Post by warfacegod on 2010-01-30
Did you try using sudo?

---

### Post by produnis on 2010-01-30
Just to get it, you mean I should type in

```
sudo gconftool --set --type int /apps/gnome-power-manager/timeout/sleep_computer_ac 60
```  
??

I don't understand what difference that would make, as without sudo it does saves the new time...

---

### Post by warfacegod on 2010-01-30
It may not make any difference at all but it's worth a try.

---

### Post by produnis on 2010-01-31
It makes no difference whether I type in the command with or without sudo...

The only time settings are really not ignored is if I click graphically on "make it default" 

(see screenshot)


[IMG]http://www.produnis.de/blog/wp-content/uploads/2010/01/screenshot_003-Energie.png[/IMG]



Does anyone know how to call this function via terminal?

---

### Post by warfacegod on 2010-01-31
> Is there something I need to do additionally to the gconfeditor-command to get it right?

Try going to: Configuration Editor> apps> gnome-power-managment> timeout

---

### Post by produnis on 2010-01-31
Yes, I know,
and my "new" settings are shown there...
but they are ignored by GNOME!..

Do you know which script is started if someone klicks at "make it default" in the graphical energy-menu? (see screenshot of my previous post)

Currently, only if I klick that button, new settings are stored...

---

### Post by warfacegod on 2010-01-31
> **produnis said:**
> Yes, I know,
and my "new" settings are shown there...
but they are ignored by GNOME!..

Do you know which script is started if someone klicks at "make it default" in the graphical energy-menu? (see screenshot of my previous post)

Currently, only if I klick that button, new settings are stored...

No, I don't. Try setting the key as Mandatory.

---

### Post by produnis on 2010-01-31
I'd like to do these settings from a script!!

So the problem is that I actually have to click a key via graphical surface...
:(

Anyone else any ideas?

---

### Post by warfacegod on 2010-01-31
No need for shouting. I'm trying to help you with the knowledge that I have and, unless I missed something, I'm the *only* one so far.

---

### Post by produnis on 2010-01-31
shouting?

I thought shouting IS SOMETHING LIKE THIIIIIIISSSS!!!!

I just asked if anyone else has any idea....?!?!

---

### Post by warfacegod on 2010-01-31
> I'd like to do these settings from a script!!

Seems like shouting to me.

---

### Post by produnis on 2010-01-31
I'm sorry, it wasn't ment like that..


back to topic:  anyone any ideas?

---

### Post by produnis on 2010-02-02
my dirty workaround:

1. Install gnome-devel (sudo apt-get install gnome-devel)

2. create a file "gpm-trigger.c" with the following content:

```
#include <glib.h>
#include <dbus/dbus-glib.h>

#include <string.h>
#include <gconf/gconf-client.h>

int main()
{
    GConfClient *client;
    DBusGProxy *proxy;
    DBusGConnection *connection;
    GError *error = NULL;
    const gchar *keys[5] = {
        "/apps/gnome-power-manager/actions",
        "/apps/gnome-power-manager/ui",
        "/apps/gnome-power-manager/buttons",
        "/apps/gnome-power-manager/backlight",
        "/apps/gnome-power-manager/timeout"
    };


    g_type_init ();

    dbus_error_init (&error);
    if (error != NULL) {
        g_warning ("failed to init dbus: %s", error->message);
        g_error_free (error);
        return;
    }


    connection = dbus_g_bus_get (DBUS_BUS_SYSTEM, &error);
    if (error != NULL) {
        g_warning ("failed to get system bus connection: %s", error->message);
        g_error_free (error);
        return;
    }

    proxy = dbus_g_proxy_new_for_name (connection,
                       "org.gnome.GConf.Defaults",
                       "/",
                       "org.gnome.GConf.Defaults");
    if (proxy == NULL) {
        g_warning ("Cannot connect to defaults mechanism");
        return;
    }

    //client = gconf_client_get_default ();
    //gconf_client_suggest_sync (client, NULL);
    //g_object_unref (client);
    dbus_g_proxy_call (proxy, "SetSystem", &error,
               G_TYPE_STRV, keys,
               G_TYPE_STRV, NULL,
               G_TYPE_INVALID, G_TYPE_INVALID);

    g_object_unref (proxy);
}
```

Compile it using the command:
```
gcc `pkg-config --libs --cflags dbus-glib-1 dbus-1 gconf-2.0` gpm-trigger.c  -o gpm-trigger
```

Now after editing sleep_computer_ac, e.g.:
```
gconftool --set --type int /apps/gnome-power-manager/timeout/sleep_computer_ac 60
```

you need to run "gpm-trigger" (which we compiled)
```
gpm-trigger
```

the graphical GNOME-Session asks for a root-pwd now. After you entered the password, you need to reboot the machine (at least my machines need to be rebooted).
After the new start, the settings are active..

dirty hack, and no chance to use it for scripts (as the GNOME-GUI will ask for the passwd), but it works (at least for me).

---

