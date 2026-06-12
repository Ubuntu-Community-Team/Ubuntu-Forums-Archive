---
title: "HOWTO : Pidgin text to speech via Mbrola"
date: 2009-01-03
forum: General Help
---

### Post by ulli.winter on 2009-01-03
Hi,

just a small script to let the TTS-system Mbrola speak Pidgin messages.

I installed german Mbrola according to [http://tintuc.no-ip.com/linux/tipps/MbrolaInstallation.html]("http://tintuc.no-ip.com/linux/tipps/MbrolaInstallation.html") - other lanugages should work similar.

And with the Python script below Pidgin instant messages will be written to a textfile and spoken via the "say" script from the link above.

If someone is interested at all / has comments, leave a message ;)) 

```

	

#!/usr/bin/env python

def speak(account, sender, message, conversation, flags):###### TTS ###############################
	bus = dbus.SessionBus()
	obj = bus.get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
	purple = dbus.Interface(obj, "im.pidgin.purple.PurpleInterface")
	
	UINnick = {}	 	########### Dictionary for conversion UIN->Nickname ###############
	
	UINnick["1234567"] = "Dieter"	#
	UINnick["34243243"] = "Thomas"	#
	UINnick["34234324234"] = "Kuhn"	#

	try:			#if entry exists use nickname from dictionary UINnick
	 nick = UINnick[sender]
	except KeyError:	#else use UIN
	 nick = sender


	tmp = open('/tmp/pidginsay.tmp','w')	#tmp file for TTS
	text = '%s sagt: %s' % (nick,message)

	import sys		############ Encode text -> system encoding #######################
	# Encoding der Standardausgabe herausfinden
	stdout_encoding = sys.stdout.encoding or sys.getfilesystemencoding()
	# Nachricht umwandeln (unicode -> Ausgabe-Encoding)
	text_out = text.encode(stdout_encoding)	

	tmp.write(text_out)	############ write file ###########################################
	tmp.close()

	import os		############ execute TTS script ###################################
	import subprocess
	cmd = 'say /tmp/pidginsay.tmp'
	subprocess.call(cmd,shell=True)

	tmp = open('/tmp/pidginsay.tmp','w')#### clear file - why not... ####################
	tmp.close()

import dbus, gobject		############ get DBUS signal ######################################
from dbus.mainloop.glib import DBusGMainLoop
dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
bus = dbus.SessionBus()

bus.add_signal_receiver(speak,
                        dbus_interface="im.pidgin.purple.PurpleInterface",
                        signal_name="ReceivedImMsg")

loop = gobject.MainLoop()
loop.run()



```

---

