---
title: "Temperature2 Screenlets"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by santiagoward2000 on 2007-10-22
Hi everyone!
I'm having a problem with this particular screenlet (Temperature2). I tried to run it from a terminal to see if it sent me any erros, and I got this:
> Launching Screenlet from: /home/santi/.screenlets/Temperature2/Temperature2Screenlet.py
Logging output goes to: $HOME/.config/Screenlets/Temperature2Screenlet.log
Traceback (most recent call last):
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 251, in <module>
    screenlets.session.create_session(Temperature2Screenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 392, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 186, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 68, in __init__
    self.__hddtemp = self.get_hddtemp_data()
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 126, in get_hddtemp_data
    s.connect(('localhost', 7634))
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')


I tried to search this error, but I found nothing. Can someone please tell me what's wrong?
Thank you!!

---

### Post by santiagoward2000 on 2007-10-23
I hate to bump, but I can't find it anywhere. Any help?

---

### Post by santiagoward2000 on 2007-10-24
Hi,
OK, as I got no reply, I tried to install the old Temperature Screenlet. It works with no problem.
Still, can somebody explain to me what the problem with Temperature2 is?
Thanks

---

### Post by apedraza on 2008-05-06
It is due to one of two possible things:

1. Temperature2 screenlet is dependent on the hddtemp package.
2. hddtemp must be started and listening in on port 7634.

If you have hddtemp installed, verify that it is running by typing on the terminal: sudo netstat -lntp

This should give you a list of ports with active listeners on.  hddtemp should be listed. If not listed, verify that it is installed in your system.

---

