---
title: "[SOLVED] Update Manager"
date: 2008-02-28
forum: Desktop Environments
---

### Post by DanCran on 2008-02-28
I just tried upgrading to the 8.04 Alpha version, and somehow it messed up my update manager. It says that the dependency tree is broken and when I go to fix it, I get this:

```
E: /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb: subprocess pre-installation script returned error exit status 1
```

Anybody?

---

### Post by DanCran on 2008-02-28
I get this when I try to do it in the terminal:

```
Preparing to replace update-manager 1:0.81 (using .../update-manager_1%3a0.87.9_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1674, in <module>
    main()
  File "/usr/bin/pycentral", line 1668, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1169, in run
    pkg.prepare(used_runtimes, old_used_runtimes, old_pkg)
  File "/usr/bin/pycentral", line 803, in prepare
    rt.remove_byte_code(removed_fs)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.87.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Boyo on 2008-02-28
Hi Dan.

You are not alone!  If you find an solution to this will you please post it?

Many thanks

Martin

---

### Post by xl_cheese on 2008-02-28
go to synaptic and uninstall the Update Manager.  then reinstall.

that fixed it for me.

---

### Post by DanCran on 2008-02-28
The uninstalling and re-installing fixed it. Thanks guys.

---

### Post by chrisjsmith on 2008-02-28
Yeah same here.  Nice one :)

---

### Post by luke16 on 2008-02-28
It looks like synaptic also wants to uninstall "ubuntu-desktop" and update-notifier when I tell it to remove the update-manager. Is this wise?

---

### Post by lmcfadden on 2008-03-01
> **luke16 said:**
> It looks like synaptic also wants to uninstall "ubuntu-desktop" and update-notifier when I tell it to remove the update-manager. Is this wise?

Worked fine for me by letting synaptic do the uninstall.  I believe it is only the ***desktop notifier*** that will be uninstalled, if your concern was that the Desktop would be uninstalled?

---

