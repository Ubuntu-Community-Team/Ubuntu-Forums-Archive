---
title: "Volume Control Screenlet Not Working"
date: 2009-01-25
forum: General Help
---

### Post by KevDo on 2009-01-25
Hi,

I've had a search and went through a lot of the basic stuff when faced with this error. The volume control screenlet doesn't appear when activated.

I do have a "Master" channel so it shouldn't be that. I've tried restarting, autoloading, restart etc.. nothing.

Here's an output when i try to run it. (I've also tried copying the files to /home/kev/.screenlets and ran it from there with the same error)

kev@ubunk:~/Desktop$ '/usr/share/screenlets/VolumeControl/VolumeControlScreenlet.py' 
CachingBackend: Loading instances from cache
Found a running session of VolumeControl, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.VolumeControl was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.kev.running
Loading instances in: /home/kev/.config/Screenlets/VolumeControl/default/
No instance(s) found in session-path, creating new one.
/home/kev/.config/Screenlets/VolumeControl/default/VolumeControl1
LOAD NEW THEME: cone
FOUND: /usr/share/screenlets/VolumeControl/themes/cone
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Max vol: 65536; Master
Traceback (most recent call last):
  File "/usr/share/screenlets/VolumeControl/VolumeControlScreenlet.py", line 186, in <module>
    screenlets.session.create_session(VolumeControlScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 254, in start
    sl.finish_loading()
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1243, in finish_loading
    self.on_init()
  File "/usr/share/screenlets/VolumeControl/VolumeControlScreenlet.py", line 111, in on_init
    self.on_control_update(self.control, self.control)
  File "/usr/share/screenlets/VolumeControl/VolumeControlScreenlet.py", line 106, in on_control_update
    self.updateBar()
  File "/usr/share/screenlets/VolumeControl/VolumeControlScreenlet.py", line 151, in updateBar
    assert(len(mixer_info) > 0)
AssertionError

I can't really make too much sense from this output (I'm pretty new to linux, see) I've fixed all of my other problems but just can't get this one working :(

Thanks.

---

### Post by KevDo on 2009-01-26
OK I give up trying to fix it myself, it's beyond me. I tried various things including editing the py file. Changed it the end to something else I read on the internet which didn't work either, just returned to me a prompt without any errors/output/debug. I tried making a new user and start from as fresh as i know how, still the same.

---

