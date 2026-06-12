---
title: "USB storage and exec permission - how?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by cellstije on 2006-08-31
Heya there!

I' having some problems with the exec permission on USB sticks and hardrives.

I searched the forums but not much luck....

What I gathered so far is that ubuntu (kubuntu in my case) mounts storage media trough HAL and pmount. pmount by default mounts external media with  noexec option. However should be possible to change this behaviour by editing some fdi files.

in the file:
/etc/hal/fdi/policy/preferences.fdi

I added:
```
<device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/computer">
      <merge key="storage.policy.default.mount_option.exec" type="bool">true</merge>
    </match>
  </device>

  <device>
    <!-- Whitelist bus types of storage devices we care about  -->
    <match key="info.capabilities" contains="storage">
      <match key="storage.bus" string="mmc">
        <merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="usb">
        <merge key="storage.policy.should_mount" type="bool">true</merge>
        <merge key="storage.policy.default.mount_option.exec" type="bool">true</merge>
      </match>
...
```

which i took from:

/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

My understanding is that the option:

```
<merge key="storage.policy.default.mount_option.exec" type="bool">true</merge>
```

should do the trick, but it actually does not work. I can't get exec permissions on my external devices.

I would avoid editing the fstab because it defeats the purpose of having multiple external discs/sticks which i plug in different time and order ...

Can somebody tell me where I'm wrong?

Cheers
c.

---

### Post by cellstije on 2006-09-01
can anybody help me plz?

---

