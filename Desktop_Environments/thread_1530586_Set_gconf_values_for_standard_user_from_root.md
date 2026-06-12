---
title: "Set gconf values for standard user from root?"
date: 2010-07-13
forum: Desktop Environments
---

### Post by Dart00 on 2010-07-13
I have a script that runs lots and lots of root commands, copying files in /usr/...stuff like that, then i want to switch users back to the original user and run some gconf tweaks, But now im stuck. I need to update a series of gconf values for a user after copying all the root files, but I noticed once your in root, any gconf values you change, change roots information, not the user who started the script useing sudo. :(

So i was wondering how you would run a script as root, then after your done with all the root commands, "un-root" to the current user who started the script and run the gconf edits:

I put together this so far. It a script that you run, it detects if it was started as root and if not it asks for root password and re-spawns its self exiting out the first instance, then the script runs, switches to the original user after all files are copyed over and starts to run the Military Time custom format update.

```
OUSER="`whoami`"

if [ "$(id -u)" != "0" ]; then
sudo -K
sudo bash $0
exit
fi

cp config.ini /usr/share/Blah

su $OUSER

gconftool-2 --set "/apps/panel/applets/applet_4/prefs/custom_format" --type string "<span font_desc=\"Trebuchet MS 8.0\" weight=\"bold\">%l:%M %p%n%m/%d/%Y</span>"

echo "Done"

read junk

exit 0
```The results!.....All it does is copy the files and then gives me a root prompt: "root@shane-desktop:/home/shane/Desktop#" :( Anyone have any ideas?

---

### Post by elliottmatthew on 2010-07-14
I agree with you The GNOME configuration tool, Gconf, aggregates thousands of user settings in one location. and interesting quire.And as far as I know Gconf works as the front end, creating an XML-based preferences "database." We're not talking about MySQL or Apache settings .

---

### Post by nilarimogard on 2010-07-14
You can find an example on how to do this in the [Ubuntu Start script]("https://launchpad.net/ubuntustart").

---

### Post by Dart00 on 2010-07-14
Well based what i found on the script, I think this code it said would do the trick to still apply gconf values to the current user, but still run the script as root.

```
ON_USER=$(echo ~ | awk -F'/' '{ print $1 $2 $3 }' | sed 's/home//g')
export $(grep -v "^#" ~/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)
if sudo -u $ON_USER test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
   eval `sudo -u $ON_USER dbus-launch --sh-syntax --exit-with-session`
fi

echo $ON_USER
echo $DBUS_SESSION
echo $DBUS_SESSION_BUS_ADDRESS
echo $DBUS_SESSION_BUS_WINDOWID
echo $DBUS_SESSION_BUS_PID
```It generated these values for my user:

```
shane

unix:abstract=/tmp/dbus-kPCNMrRJZA,guid=cf1d4d30dc64f9cbc2e74ad14c3e4f8f
8388609
1204
```It then seems im supposed to implement the gconf values like this:

```
sudo -u $ON_USER "DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS gconftool -s --type bool /apps/nautilus/desktop/volumes_visible
```Is my understanding correct so far?

Not sure why DBUS_SESSION is empty? And im having a hard time making since of "how" the code works. (iv never even see dbus in my life) Looks like I have a lot of reading to do. Anyone understand this and can give me a head start?

---

### Post by nilarimogard on 2010-07-16
Yes that's basically it. But it doesn't work in Ubuntu 9.10. Only 10.04 and probably 10.10 too (because of dbus).

Also, make sure you have this:

```
ON_USER=$(echo ~ | awk -F'/' '{ print $1 $2 $3 }' | sed 's/home//g')
export $(grep -v "^#" ~/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)
if sudo -u $ON_USER test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
       eval `sudo -u $ON_USER dbus-launch --sh-syntax --exit-with-session`
fi
```

right at the beginning of your script. I don't know why but for me it only works like that (probably there's something interfering).

Just try it like that and i should work...

---

### Post by Dart00 on 2010-07-17
uh oh...Is there a way to do it on 9.10? :(

---

### Post by nilarimogard on 2010-07-18
> **Dart00 said:**
> uh oh...Is there a way to do it on 9.10? :(

Unfortunately I have no idea.

---

### Post by stringkarma on 2010-10-12
I am trying to write a Perl script that installs packages and sets settings (for a first time on new install script) this issue is affecting me too and I was wondering if someone had made any progress on why this method worked so perhaps I could use it in my script. Thanks!

---

### Post by stringkarma on 2010-10-12
Nevermind, I got it, for some explaination see my [SO question]("http://stackoverflow.com/questions/3875715/how-can-i-run-a-perl-script-as-root-yet-still-affect-user-gconf-settings").

---

