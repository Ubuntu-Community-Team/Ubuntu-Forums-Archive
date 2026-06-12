---
title: "someone with python knowledge"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by PurposeOfReason on 2008-03-19
I'm trying to get this pipe menu to work with openbox, and it does, but it only works once. It creates a /tmp/gmail.cache and won't run again until it is deleted. I'd rather the script still have that part but I'll take any fix.
```
#!/usr/bin/python
# Authors: cduquette@gmail.com follower@myrealbox.com
# License: GPL 2.0

# Usage:
# Put an entry in your ~/.config/openbox/menu.xml like this:
# <menu id="gmail" label="gmail" execute="~/.config/openbox/scripts/gmail-openbox.py" />
# And inside <menu id="root-menu" label="openbox">, add this somewhere (wherever you want it on your menu)
# <menu id="gmail" />

import os
import sys
import logging

name = "111111"
pw = "000000"
browser = "firefox3"
filename = "/tmp/.gmail.cache"

login = "\'https://mail.google.com/mail\'"

# Allow us to run using installed `libgmail` or the one in parent directory.
try:
    import libgmail
except ImportError:
    # Urghhh...
    sys.path.insert(1,
                    os.path.realpath(os.path.join(os.path.dirname(__file__),
                                                  os.path.pardir)))

    import libgmail

    
if __name__ == "__main__":
    import sys
    from getpass import getpass

    if not os.path.isfile(filename):
        ga = libgmail.GmailAccount(name, pw)

        try:
            ga.login()
        except libgmail.GmailLoginFailure:
	    print "<?xml version=\"1.0\" encoding=\"UTF-8\"?>"
            print "<openbox_pipe_menu>"
	    print "  <item label=\"login failed.\">"
            print "    <action name=\"Execute\"><execute>" + browser + " " + login + "</execute></action>"
            print "  </item>"
	    print "</openbox_pipe_menu>"
	    raise SystemExit

    else:
        ga = libgmail.GmailAccount(
            state = libgmail.GmailSessionState(filename = filename))
    
    msgtotals = ga.getUnreadMsgCount()
    
    print "<?xml version=\"1.0\" encoding=\"UTF-8\"?>"
    print "<openbox_pipe_menu>"
    print "<separator label=\"Gmail\"/>"

    if msgtotals == 0:
	print "  <item label=\"no new messages.\">"
    elif msgtotals == 1:
        print "  <item label=\"1 new message.\">"
    else:
        print "  <item label=\"" + str(msgtotals) + " new messages.\">"
    print "    <action name=\"Execute\"><execute>" + browser + " " + login + "</execute></action>"
    print "  </item>"
    print "</openbox_pipe_menu>"

    state = libgmail.GmailSessionState(account = ga).save(filename)


```

---

### Post by Blacklife08 on 2008-03-26
I only have a very basic knowledge of Python, but what if you make a way to delete the file at the end of the code?
Is the file needed after it is done running??  If not then u should be able to delete it with a command, (sorry don't know what it would be)

---

