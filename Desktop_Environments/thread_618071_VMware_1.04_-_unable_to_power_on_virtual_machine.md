---
title: "VMware 1.04 - unable to power on virtual machine"
date: 2007-11-20
forum: Desktop Environments
---

### Post by gleesos on 2007-11-20
I have just installed VMware Server on Ubuntu 7.1

After completing install I open VMware console and create a new Virtual machine, when however I try to power on the virtual machine it will not.
below is error log:



ov 20 16:38:14: vmui| Log for VMware Server pid=14255 version=1.0.4 build=build-56528 option=Release
Nov 20 16:38:14: vmui| Using log file /tmp/vmware-gleesos/ui-14255.log
Nov 20 16:38:14: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
Nov 20 16:38:14: vmui| HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
Nov 20 16:38:15: vmui| HostDeviceInfoFindHostIDECDROMs: /proc/ide could not be explored. Unable to enumerate host IDE cdroms.
Nov 20 16:38:15: vmui| SMBIOS: can't open /dev/mem
Nov 20 16:38:15: vmui| VmhsHostInfoPopulateSystem:  Could not get information from smbios to populate VMDB.
Nov 20 16:38:15: vmui| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 1 numThreadsPerCore 1.
Nov 20 16:38:15: vmui| HOSTINFO: This machine has 2 physical CPUS, 2 total cores, and 2 logical CPUs.
Nov 20 16:38:15: vmui| Gtk: Refusing to add non-unique action 'ListNewTeamAction' to action group 'App Actions'
Nov 20 16:38:15: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Stop and Stop
Nov 20 16:38:15: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Forward and _Forward
Nov 20 16:38:15: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Information and Information
Nov 20 16:38:19: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:19: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:19: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:19: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:22: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:22: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:22: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:22: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:24: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:24: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:28: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:28: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:28: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:28: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:29: vmui| VMNetCtlConstruct: no Network Names to list
Nov 20 16:38:29: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr
Nov 20 16:38:35: vmui| vmdbLayout::rpc::Mgr::~Mgr: 2 cmds pending.
Nov 20 16:38:35: vmui| vmdbLayout::rpc::Mgr::~Mgr: 1 reqs pending.

---

### Post by vavoem on 2007-12-05
Have you punched in your freely available registration key?
You won't be able to startup a machine without it

---

