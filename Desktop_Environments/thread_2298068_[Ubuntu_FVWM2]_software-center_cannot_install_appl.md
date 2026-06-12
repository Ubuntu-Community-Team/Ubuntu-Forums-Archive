---
title: "[Ubuntu FVWM2] software-center cannot install applications because of policykit error"
date: 2015-10-08
forum: Desktop Environments
---

### Post by psychotux2 on 2015-10-08
Fresh installation of  Ubuntu 14.04.3 LTS.
 Attempting to install software fails with an error messagebox:
 
 ```
Software can't be installed or removed because the authentication service is not available.  
  (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.135'}): org.debian.apt.install-or-remove-packages
``` 

 This looks similiar to a bug that apparently got fixed and now seems to have reappeared again after years.
 See [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/785117](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/785117)

 The problem seems to be that I use FVWM instead of Unity.
 However, policykit seems to be running according to ps axuww:

 ```
root      1364  0.0  0.0 296300 11152 ?        Sl   Okt07   0:00 /usr/lib/policykit-1/polkitd --no-debug
``` 

 Here is what appears on the xterm when launching software-center:
 
```
$ software-center&

 [1] 15507
 name@host:/dir$ 2015-10-08 00:54:21,915 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
 2015-10-08 00:54:22,300 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
 2015-10-08 00:54:22,302 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
 2015-10-08 00:54:22,345 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
 2015-10-08 00:54:22,854 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
 2015-10-08 00:54:22,854 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
 Traceback (most recent call last):
   File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
     self._dump_bsddbm_for_unity(outfile, outdir)
   File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
     0600)
 DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
 /usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 68 was not found when attempting to remove it
   return super(MainContext, self).iteration(may_block)
 2015-10-08 00:54:23,935 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'leadwerks\r\nleadwerks-indie'' not available
 /usr/bin/software-center:184: Warning: Source ID 128 was not found when attempting to remove it
   Gtk.main()
 /usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
   return super(MainContext, self).iteration(may_block)
 2015-10-08 00:54:28,726 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
 /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 169 was not found when attempting to remove it
   GLib.source_remove(self._timeout)
 /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 1223 was not found when attempting to remove it
   GLib.source_remove(self._timeout)
 /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 1256 was not found when attempting to remove it
   GLib.source_remove(self._timeout)
 2015-10-08 00:55:03,853 - softwarecenter.backend - WARNING - _on_trans_error: 'AuthorizationFailed(u"('system-bus-name', {'name':  ':1.141'}): org.debian.apt.install-or-remove-packages",)' '<AptTransaction object at 0x7f1ca2e770f0 (aptdaemon+client+AptTransaction at 0x408bee0)>' 'gparted'
 2015-10-08 00:55:03,999 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py', 1090, '_call_apport_recoverable_error')'
 2015-10-08 00:55:03,999 - root - WARNING - /usr/share/apport/recoverable_problem returned '1' ('', 'Traceback (most recent call last):
   File "/usr/share/apport/recoverable_problem", line 64, in <module>
     main()
   File "/usr/share/apport/recoverable_problem", line 60, in main
     with open(apport.fileutils.make_report_path(report), 'wb') as fp:
 AttributeError: 'module' object has no attribute 'make_report_path'
 ')
 /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 1406 was not found when attempting to remove it
   GLib.source_remove(self._timeout)
 2015-10-08 00:55:06,422 - softwarecenter.backend - ERROR - error in _on_trans_finished 'Error: You are not allowed to perform this action
 You don't have the required privileges to perform this action.
 

 org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name': ':1.141'}): org.debian.apt.install-or-remove-packages'
```

Any idea what I could do as workaround?
(I could of course start a session in Unity, where software-center works correctly. But I'd love to avoid Unity... :frown:)

---

### Post by TheFu on 2015-10-09
Use apt-get or aptitude or synaptic?

---

### Post by psychotux2 on 2015-10-09
@ TheFu

I am actually doing this.
However I think this is a bug, as the Ubuntu software center should be available to all users, even those who prefer to use less common WM/DEs.
So I am actually looking for a workaround/fix that enables me to use software-center...

---

### Post by TheFu on 2015-10-09
And if SW center requires  services that are only running/installed when Unity is used?

I suspect it was a design decision and they are making use of new Unity 1-GUI development for desktops, laptops, phones, tablets.  

But I don't know - haven't looked at the code myself.

---

### Post by MattBro on 2015-11-21
> **TheFu said:**
> And if SW center requires  services that are only running/installed when Unity is used?

I suspect it was a design decision and they are making use of new Unity 1-GUI development for desktops, laptops, phones, tablets.  

But I don't know - haven't looked at the code myself.

I'm seeing this error on both Unity and Xfce.  Though I do not get the message that the authentication service is not available.  It is available and running.  Rather authentication simply fails and I get the same policy kit error message.  Sudo however works fine and I can use apt-get install and so forth.

---

