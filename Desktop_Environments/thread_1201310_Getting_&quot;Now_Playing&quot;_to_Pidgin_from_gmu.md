---
title: "Getting &quot;Now Playing&quot; to Pidgin from gmusic"
date: 2009-07-01
forum: Desktop Environments
---

### Post by jadez03 on 2009-07-01
Now, this may be pretty basic to you gurus out there, but I figured out how to get this script working from an archive post with no solution, so I figured I'd write a quick tut for anyone else that has a large (220gb here) music collection and wanted a music player that could handle it (and found gmusicplayer), and who uses pidgin and wants to have their now playing as their status.

I know, my target audience is probably narrow, but what the hey. :P

1) Open Gmusicplayer, and navigate to the plugins window in settings
2) Select "Now Playing" and enable it
3) In that window, you're going to have to give it something to execute to get your status message to your IM client, that's where I come in.

Or more accurately, this python script, written by reda_ea, thanks go to him!

```

#! /usr/bin/python

################################################################################
# pidgin-setmessage by Reda El Khattabi <reda.ea@gmail.com>
#     Ugly python and dbus hack to tell people what you're listening to.
#    LICENSE: This product is provided under the "I don't care" license.
#             Do whatever you like with it :p
################################################################################


# bug: when pidgin auto switches to away on idle, setting the message will also really set the status to away, logging in invisible users and such. And won't get back to previous status on user's return. solution: disable auto away on idle


import sys
import dbus

# prefix to musical status messages : ** THIS IS WHAT YOU WANTED TO CHANGE **
# http://www.fileformat.info/info/unicode/char/266c/
STAT_DELIM = u'\u266C '
# nickname and song name separator for MSN' zzuglyyy haxx
MSN_DELIM = u' ' + STAT_DELIM

bus = dbus.SessionBus()
obj = bus.get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
purple = dbus.Interface(obj, "im.pidgin.purple.PurpleInterface")

def pidgin_set_message(message):
    current = purple.PurpleSavedstatusGetCurrent()
    curtype = purple.PurpleSavedstatusGetType(current)
    status = purple.PurpleSavedstatusNew("", curtype)
# DON'T    purple.PurpleSavedstatusSetTitle(status, "Listening to music")
    purple.PurpleSavedstatusSetMessage(status, STAT_DELIM + message)
    if purple.PurpleSavedstatusHasSubstatuses(current):
        for account in purple.PurpleAccountsGetAllActive():
            substat = purple.PurpleSavedstatusGetSubstatus(current, account)
            if substat:
                purple.PurpleSavedstatusSetSubstatus(status, account, purple.PurpleSavedstatusSubstatusGetType(substat), STAT_DELIM + message)
            else:
                purple.PurpleSavedstatusSetSubstatus(current, account, purple.PurpleStatusTypeNewFull(curtype, purple.PurplePrimitiveGetIdFromType(curtype) , purple.PurplePrimitiveGetNameFromType(curtype), True, False, False), STAT_DELIM + message)
    purple.PurpleSavedstatusActivate(status)


def get_base_name(fullname):
    return fullname.partition(MSN_DELIM)[0]

def pidgin_set_msn_message(message):
    for account in purple.PurpleAccountsGetAllActive():
        proto = purple.PurpleAccountGetProtocolName(account)
        if(proto == 'MSN'):
            connection = purple.PurpleAccountGetConnection(account)
            oldname = purple.PurpleConnectionGetDisplayName(connection)
            newname = get_base_name(oldname)
            if len(message) > 0:
                newname = newname + MSN_DELIM + message
            purple.PurpleConnectionSetDisplayName(connection, newname)

pidgin_set_message(' '.join(sys.argv[1:]))
pidgin_set_msn_message(' '.join(sys.argv[1:]))

```

4) Take the text of that, and save it as pidginnowplaying.py, to make a python script.
5) Navigate back to the plugins window of gmusicplayer, and direct the command line in "Now Playing" to your script. (Make sure you enter /home/someuser/desktop/directory/etc if you saved it somewhere other than root)
6) Change a song, and your status should be updated in pidgin!

Hope that helps someone! :P

---

### Post by jpeddicord on 2009-07-07
Moved to Desktop Environments from Tutorials & Tips, since this is really just a plugin/script and not really a tutorial as required by the criteria.

Jacob

---

