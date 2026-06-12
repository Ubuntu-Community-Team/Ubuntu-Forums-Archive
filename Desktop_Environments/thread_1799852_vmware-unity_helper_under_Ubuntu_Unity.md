---
title: "vmware-unity helper under Ubuntu Unity"
date: 2011-07-08
forum: Desktop Environments
---

### Post by RikoW on 2011-07-08
Dear all,
 
I run a windows guest under VMware Workstation / Player. The VMware Unity mode (not to confuse with Ubuntu unity) allows to seamlessly integrate the guest applications into the host environment.

I created short start-up scripts for CLI and launchers for the desktop/dock, which would start for example MS Office applications on the guest OS like for the host. In the terminal that looks like that:
 

```
> /usr/bin/vmware-unity-helper --run "/mnt/data2/wichmann/VM/mpyxlriko/mpyxlriko.vmx" "c:\Program Files\Microsoft Office\Office14\WINWORD.EXE"
(vmware-unity-helper:6501): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
(vmware-unity-helper:6501): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
>
(vmware-unity-helper:6512): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
(vmware-unity-helper:6512): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
```


This would work great in 10.10 and still works in Gnome Classic under 11.04. 

However when using the Ubuntu Unity desktop (this is getting very confusing with the naming), the launchers don't work anymore and the above example code just spits out the warning, but no Word window appears.

Because it works under Gnome Classic, I suspect a Compiz setting which screws it up, but I have no idea which one it could be.
Anybody encountered that, too and knows of a fix?

Thanks and cheers,
                     Riko

---

