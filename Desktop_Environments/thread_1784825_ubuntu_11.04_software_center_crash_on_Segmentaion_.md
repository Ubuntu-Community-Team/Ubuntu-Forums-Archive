---
title: "ubuntu 11.04 software center crash on Segmentaion Fault"
date: 2011-06-17
forum: Desktop Environments
---

### Post by stonexjr on 2011-06-17
After I uprading my ubuntu from 10.10 to 11.04, the software center cannot start up.
Everytime i type software-center in terminal, its main window first appears, and then disappear leaving the following error message:

/usr/share/software-center/softwarecenter/app.py:1188: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-06-17 10:03:04,804 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-06-17 10:03:04,804 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
Segmentation fault

Is there anybody who has meet the same problem or got any solutions?
Thanks!

---

