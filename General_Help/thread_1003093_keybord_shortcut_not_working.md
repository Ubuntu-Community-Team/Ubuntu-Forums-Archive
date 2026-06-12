---
title: "keybord shortcut not working"
date: 2008-12-05
forum: General Help
---

### Post by Red-Shield on 2008-12-05
my key board short cut for launch a web browser only is not working when i hit the key it is supposed to be assined to it says : 

Couldn't execute command: /home/terminal-junky/Desktop/firefox/firefox ""
Verify that this is a valid command.

dose any one know how to verify if it is a valid command of how to change this i have tried changing the key used i get the same results.

---

### Post by Red-Shield on 2008-12-07
is there no one out there that can help with such a thing

---

### Post by Denestria on 2008-12-07
You can find out where a program is with whereis
```
whereis firefox
```
Unless you have done something very strange I doubt you have firefox installed in a directory on your desktop.  The likely path to the executable is  /usr/bin/firefox.

---

### Post by Red-Shield on 2008-12-07
well ilooked at this file and what i found is here but i found nothing i can make heads or tails of but here it is is any way:

APPNAME=firefox
MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.0.4
DROPPED=abandoned

FOUND=""
if [ -d $MOZDIR/firefox ] ; then
  FOUND=firefox
fi

FOUND_BETA=""
BETA_LIST=""
for betaname in granparadiso firefox-trunk firefox-3.0; do
  if [ -d $MOZDIR/$betaname ]; then
    BETA_LIST="$BETA_LIST $betaname"
    FOUND_BETA=$betaname
  fi
done

if [ "$FOUND" != "" -a "$FOUND_BETA" != "" ] ; then
  echo -n "Found Beta Participation ..."
  $LIBDIR/ffox-3-beta-profile-migration-dialog
  result=$?
  if [ $result = 1 ]; then
     mv $MOZDIR/$FOUND $MOZDIR/$FOUND.2-replaced
     mv $MOZDIR/$FOUND_BETA $MOZDIR/$FOUND
     for beta in $BETA_LIST ; do
       if [ $beta != $FOUND_BETA ] ; then
         mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
       fi
     done
     echo " keep beta profile."
  elif [ $result = 2 ]; then
     for beta in $BETA_LIST ; do
       mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
     done
     echo " use firefox 2 profile."
  else
     echo " use firefox 2 profile, but will ask again next time."
  fi
  echo " ... will check again next time."
elif [ "$FOUND_BETA" != "" -a "$FOUND" = "" ]; then
  # in case we only have a beta profile the user most likely wants to use
  # that. just doing, no questions asked.
  mv $MOZDIR/$FOUND_BETA $MOZDIR/firefox
  for beta in $BETA_LIST ; do
    # Move out the older beta profiles
    if [ $beta != $FOUND_BETA ] ; then
      mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
    fi
  done
  echo "*NOTICE* Profile $FOUND_BETA found and moved as main profile"
fi

exec $LIBDIR/$APPNAME "$@"
terminal-junky@terminal-junky:/usr/bin$   

so if there is some thing i missed here some one please help me i love this short cut it is one of the greatest things about linux well not the greates thing but a dam great thing

---

### Post by Denestria on 2008-12-07
The file isn't anything for you to make sense of.  Your supposed to point the keyboard shortcut you are trying to create to run /usr/bin/firefox.  Right now you have it pointing to /home/terminal-junky/Desktop/firefox/firefox and that doesn't work.

---

### Post by Red-Shield on 2008-12-14
ok i do understand this but how is that done there must be a place to change this mabey a file to edit how do i point it to this file.

---

### Post by dovalize on 2008-12-14
Have you tried to remove and reinstall firefox?

---

### Post by Denestria on 2008-12-14
> **Red-Shield said:**
> my key board short cut for launch a web browser only is not working when i hit the key

How did you set the shortcut to begin with?  Was this done in compiz?  Gnome?  Some other way?

---

### Post by Red-Shield on 2008-12-16
gnome and i set it through the keyboard shortcut app and all the other ones work i cant even seem to remove the app and reinstall it

---

