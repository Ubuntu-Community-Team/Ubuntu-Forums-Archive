---
title: "Virtual Box and Ubuntu (64-bit)"
date: 2012-02-26
forum: Desktop Environments
---

### Post by Dirge Inferno on 2012-02-26
I setup a virtual machine for Ubuntu (64-bit) on Virtual Box after failing on Virtual PC due to it thinking I don't have a 64-bit processor. After setting up I mounted the ISO and soon after it auto-closed and I got this message:

```
Failed to open a session for the virtual machine Ubuntu.

VT-x features locked or unavailable in MSR. (VERR_VMX_MSR_LOCKED_OR_DISABLED).

Result Code: E_FAIL (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
```I have no idea what this means or how to fix it. Can someone please help me? I had no problem running Ubuntu the last time I had it.

---

### Post by LinuxFan999 on 2012-02-26
Running 64 bit guests in Virtualbox requires a 64 bit processor and hardware virtualization support (VT-X/AMD-v).

---

### Post by 3Miro on 2012-02-26
You probably have to enable VT-x in the BIOS (assuming your CPU has the feature).

---

### Post by Dirge Inferno on 2012-03-31
Well thanks for rudely ignoring my thread :).

---

### Post by haqking on 2012-03-31
> **Dirge Inferno said:**
> Well thanks for rudely ignoring my thread :).

People have already responded.

Enable virtualisation support in bios or make sure it is enabled in the VM settings.

Or read the documentation [http://www.virtualbox.org/manual/ch03.html#intro-64bitguests](http://www.virtualbox.org/manual/ch03.html#intro-64bitguests)

---

### Post by markbl on 2012-03-31
> **Dirge Inferno said:**
> Well thanks for rudely ignoring my thread :).
Yeah, some people are just so rude aren't they? :o

---

