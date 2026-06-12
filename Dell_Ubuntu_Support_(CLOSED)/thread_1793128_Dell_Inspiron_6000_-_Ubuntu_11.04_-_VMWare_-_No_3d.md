---
title: "Dell Inspiron 6000 - Ubuntu 11.04 - VMWare - No 3d :( Support"
date: 2011-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arkelsa on 2011-06-29
Just trying to get 3d enabled on my old Dell machine that was had an evil virus and destroyed my whole system...

After a few tries I finally figured out how to properly install VMWare tools onto my system, but I am still unable to get 3d enabled, this is the error I managed to find

Guest: vmx_fb: Display driver is out of sync with virtual hardware.  Disabling 3d.

Any ideas how I can fix this?
Host is a Dell Inspiron 6000 with Ubuntu 11.04 running Windows XP Pro SP3, any help is greatly appreciated.

I'll also post the entire log file for if its needed, well at least the log file that I have now anyways

```
Jun 28 23:40:56.313: vmx| Log for VMware Workstation pid=17204 version=7.1.4 build=build-385536 option=BETA
Jun 28 23:40:56.313: vmx| The process is 32-bit.
Jun 28 23:40:56.313: vmx| Host codepage=UTF-8 encoding=UTF-8
Jun 28 23:40:56.313: vmx| Hostname=hacker
Jun 28 23:40:56.313: vmx| IP=127.0.0.1 (lo)
Jun 28 23:40:56.313: vmx| IP=192.168.0.54 (eth1)
Jun 28 23:40:56.313: vmx| IP=192.168.210.1 (vmnet1)
Jun 28 23:40:56.313: vmx| IP=172.16.101.1 (vmnet8)
Jun 28 23:40:56.314: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx-debug" "-s" "vmx.stdio.keep=TRUE" "-#" "product=1;name=VMware Workstation;version=7.1.4;buildnumber=385536;licensename=VMware Workstation;licenseversion=7.0;" "-@" "pipe=/tmp/vmware-arkelsa/vmxb8d351f5c83c0f66;readyEvent=96" "/home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx"
Jun 28 23:40:56.314: vmx| Msg_SetLocale: HostLocale=UTF-8 UserLocale=NULL
Jun 28 23:40:56.355: vmx| Ready event: 96
Jun 28 23:40:56.557: vmx| UI Connecting to pipe '/tmp/vmware-arkelsa/vmxb8d351f5c83c0f66' with user '(null)'
Jun 28 23:40:56.575: vmx| VMXVmdb: Local connection timeout: 60000 ms.
Jun 28 23:40:56.627: vmx| /home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx: Setup symlink /var/run/vmware/95858867c508875639468dd5dab90816 -> /var/run/vmware/arkelsa_1000/1309326056354400_17204
Jun 28 23:40:56.633: vmx| Vix: [17204 mainDispatch.c:374]: VMAutomation: Initializing VMAutomation.
Jun 28 23:40:56.634: vmx| Vix: [17204 mainDispatch.c:397]: VMAutomation: Detected the VM is not managed
Jun 28 23:40:56.634: vmx| Vix: [17204 mainDispatch.c:658]: VMAutomationOpenListenerSocket() listening
Jun 28 23:40:56.657: vmx| Sig_Init already initialized 
Jun 28 23:40:56.674: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1870, success=1
Jun 28 23:40:56.674: vmx| Transitioned vmx/execState/val to poweredOff
Jun 28 23:40:56.674: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Jun 28 23:40:56.674: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=2, newAppState=1877, success=1
Jun 28 23:40:56.674: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=3, newAppState=1881, success=1
Jun 28 23:40:56.684: vmx| UTIL: Change file descriptor limit from soft 1024,hard 4096 to soft 2048,hard 4096.
Jun 28 23:40:56.684: vmx| VMMon_GetkHzEstimate: Calculated 474579 kHz
Jun 28 23:40:56.684: vmx| TSC kHz estimates: vmmon 474579, cpuinfo 1500000, cpufreq 1500000.  Using 1500000 kHz
Jun 28 23:40:56.684: vmx| CPU # 0 TSC = 2892548464700
Jun 28 23:40:56.684: vmx| TSC delta 0
Jun 28 23:40:56.684: vmx| CPU # 0 TSC = 2892548516421
Jun 28 23:40:56.684: vmx| TSC delta 0
Jun 28 23:40:56.684: vmx| CPU # 0 TSC = 2892548560962
Jun 28 23:40:56.685: vmx| TSC delta 0
Jun 28 23:40:56.685: vmx| CPU # 0 TSC = 2892548604630
Jun 28 23:40:56.685: vmx| TSC delta 0
Jun 28 23:40:56.685: vmx| TSC min delta 0
Jun 28 23:40:56.685: vmx| PTSC: RefClockToTSC 1000000Hz -> 1500000000Hz
Jun 28 23:40:56.685: vmx| PTSC: RefClockToTSC ((x * 3145728000) >> 21)
Jun 28 23:40:56.685: vmx| PTSC: using TSC
Jun 28 23:40:56.698: vmx| CPUID[0] vendor: GenuineIntel
Jun 28 23:40:56.698: vmx| CPUID[0]   name:         Intel(R) Pentium(R) M processor 1.50GHz
Jun 28 23:40:56.698: vmx| CPUID[0] level 00000000, 0: 0x00000002 0x756e6547 0x6c65746e 0x49656e69
Jun 28 23:40:56.698: vmx| CPUID[0] level 00000001, 0: 0x000006d8 0x00000816 0x00000180 0xafe9fbff
Jun 28 23:40:56.698: vmx| CPUID[0] level 00000002, 0: 0x02b3b001 0x000000f0 0x00000000 0x2c04307d
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000001, 0: 0x00000000 0x00000000 0x00000000 0x00100000
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000002, 0: 0x20202020 0x20202020 0x65746e49 0x2952286c
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000003, 0: 0x6e655020 0x6d756974 0x20295228 0x7270204d
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000004, 0: 0x7365636f 0x20726f73 0x30352e31 0x007a4847
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| CPUID[0] level 80000008, 0: 0x00002020 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| hostCPUID vendor: GenuineIntel
Jun 28 23:40:56.698: vmx| hostCPUID   name:         Intel(R) Pentium(R) M processor 1.50GHz
Jun 28 23:40:56.698: vmx| hostCPUID level 00000000, 0: 0x00000002 0x756e6547 0x6c65746e 0x49656e69
Jun 28 23:40:56.698: vmx| hostCPUID level 00000001, 0: 0x000006d8 0x00000816 0x00000180 0xafe9fbff
Jun 28 23:40:56.698: vmx| hostCPUID level 00000002, 0: 0x02b3b001 0x000000f0 0x00000000 0x2c04307d
Jun 28 23:40:56.698: vmx| hostCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| hostCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000000 0x00100000
Jun 28 23:40:56.698: vmx| hostCPUID level 80000002, 0: 0x20202020 0x20202020 0x65746e49 0x2952286c
Jun 28 23:40:56.698: vmx| hostCPUID level 80000003, 0: 0x6e655020 0x6d756974 0x20295228 0x7270204d
Jun 28 23:40:56.698: vmx| hostCPUID level 80000004, 0: 0x7365636f 0x20726f73 0x30352e31 0x007a4847
Jun 28 23:40:56.698: vmx| hostCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| hostCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Jun 28 23:40:56.698: vmx| hostCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| hostCPUID level 80000008, 0: 0x00002020 0x00000000 0x00000000 0x00000000
Jun 28 23:40:56.698: vmx| CPUID Maximum Physical Address Bits supported across all CPUs: 32
Jun 28 23:40:56.865: vmx| Host ACPI: can't find SRAT
Jun 28 23:40:56.866: vmx| Host: SRAT tables not found in memory
Jun 28 23:40:56.908: vmx| ConfigCheck: No rules file found. Checks are disabled.
Jun 28 23:40:56.908: vmx| changing directory to /home/arkelsa/vmware/Windows XP Professional/.
Jun 28 23:40:56.909: vmx| Config file: /home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx
Jun 28 23:40:56.909: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Jun 28 23:40:56.909: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=2, newAppState=1878, success=1
Jun 28 23:40:56.981: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Jun 28 23:40:57.209: vmx| VMXVmdbCbVmVmxExecState: Exec state change requested to state poweredOn without reset, hard, softOptionTimeout: 0.
Jun 28 23:40:57.209: vmx| PowerOn
Jun 28 23:40:57.210: vmx| VMX_PowerOn: VMX build 385536, UI build 385536
Jun 28 23:40:57.211: vmx| Host ACPI: can't find SRAT
Jun 28 23:40:57.211: vmx| Host: SRAT tables not found in memory
Jun 28 23:40:57.239: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Jun 28 23:40:57.255: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1871, success=1
Jun 28 23:40:57.255: vmx| HOST sysname Linux, nodename hacker, release 2.6.38-8-generic, version #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011, machine i686, hz=250
Jun 28 23:40:57.255: vmx| DICT --- USER PREFERENCES /home/arkelsa/.vmware/preferences 
Jun 28 23:40:57.255: vmx| DICT       pref.grabOnKeyPress = FALSE
Jun 28 23:40:57.255: vmx| DICT       pref.eula.0.appName = VMware Player
Jun 28 23:40:57.255: vmx| DICT   pref.eula.0.buildNumber = 385536
Jun 28 23:40:57.255: vmx| DICT     pref.trayicon.enabled = true
Jun 28 23:40:57.255: vmx| DICT       pref.usbDev.maxDevs = 0
Jun 28 23:40:57.255: vmx| DICT pref.keyboardAndMouse.maxProfiles = 0
Jun 28 23:40:57.255: vmx| DICT vmWizard.installMediaType = iso
Jun 28 23:40:57.255: vmx| DICT         vmWizard.guestKey = winxppro
Jun 28 23:40:57.255: vmx| DICT pref.vmplayer.vmPos0.index = 0
Jun 28 23:40:57.255: vmx| DICT pref.vmplayer.vmPos0.vmPath = /home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx
Jun 28 23:40:57.255: vmx| DICT pref.vmplayer.vmPos0.geometry = 732x621+282+93
Jun 28 23:40:57.255: vmx| DICT       pref.eula.1.appName = VMware Workstation
Jun 28 23:40:57.255: vmx| DICT   pref.eula.1.buildNumber = 385536
Jun 28 23:40:57.255: vmx| DICT    pref.view.navBar.width = 180
Jun 28 23:40:57.255: vmx| DICT pref.ws.openedObj0.present = TRUE
Jun 28 23:40:57.255: vmx| DICT   pref.ws.openedObj0.dest = /host2/#_client/
Jun 28 23:40:57.255: vmx| DICT  pref.ws.openedObj.maxNum = 2
Jun 28 23:40:57.255: vmx| DICT pref.ws.openedObj1.present = TRUE
Jun 28 23:40:57.255: vmx| DICT   pref.ws.openedObj1.type = vm
Jun 28 23:40:57.255: vmx| DICT   pref.ws.openedObj1.path = /vm/#b8d351f5c83c0f66/
Jun 28 23:40:57.255: vmx| DICT   pref.ws.openedObj1.file = /home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx
Jun 28 23:40:57.255: vmx| DICT   pref.ws.openedObj1.dest = /host2/#_client/
Jun 28 23:40:57.255: vmx| DICT       pref.license.maxNum = 1
Jun 28 23:40:57.255: vmx| DICT     pref.license0.version = 7.0
Jun 28 23:40:57.255: vmx| DICT --- USER DEFAULTS /home/arkelsa/.vmware/config 
Jun 28 23:40:57.255: vmx| DICT --- HOST DEFAULTS /etc/vmware/config 
Jun 28 23:40:57.255: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Jun 28 23:40:57.255: vmx| DICT                vix.libdir = /usr/lib/vmware-vix
Jun 28 23:40:57.255: vmx| DICT                NETWORKING = yes
Jun 28 23:40:57.255: vmx| DICT installerDefaults.dataCollectionEnabled = no
Jun 28 23:40:57.255: vmx| DICT            VMBLOCK_CONFED = yes
Jun 28 23:40:57.255: vmx| DICT           gksu.rootMethod = sudo
Jun 28 23:40:57.255: vmx| DICT                    libdir = /usr/lib/vmware
Jun 28 23:40:57.259: vmx| DICT               VMCI_CONFED = yes
Jun 28 23:40:57.259: vmx| DICT        vix.config.version = 1
Jun 28 23:40:57.259: vmx| DICT              VSOCK_CONFED = yes
Jun 28 23:40:57.260: vmx| DICT             initscriptdir = /etc/init.d
Jun 28 23:40:57.260: vmx| DICT installerDefaults.componentDownloadEnabled = yes
Jun 28 23:40:57.260: vmx| DICT    player.product.version = 3.1.4
Jun 28 23:40:57.260: vmx| DICT installerDefaults.transferVersion = 1
Jun 28 23:40:57.260: vmx| DICT installerDefaults.autoSoftwareUpdateEnabled = yes
Jun 28 23:40:57.260: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Jun 28 23:40:57.260: vmx| DICT                    bindir = /usr/bin
Jun 28 23:40:57.260: vmx| DICT       product.buildNumber = 385536
Jun 28 23:40:57.260: vmx| DICT           product.version = 7.1.4
Jun 28 23:40:57.260: vmx| DICT workstation.product.version = 7.1.4
Jun 28 23:40:57.260: vmx| DICT              product.name = VMware Workstation
Jun 28 23:40:57.260: vmx| DICT --- SITE DEFAULTS /usr/lib/vmware/config 
Jun 28 23:40:57.260: vmx| DICT                  tag.help = introduction.htm
Jun 28 23:40:57.260: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Jun 28 23:40:57.260: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Jun 28 23:40:57.260: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Jun 28 23:40:57.260: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Jun 28 23:40:57.260: vmx| DICT             tag.netConfig = devices_netadapter.htm
Jun 28 23:40:57.260: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Jun 28 23:40:57.260: vmx| DICT          tag.serialConfig = devices_serial.htm
Jun 28 23:40:57.260: vmx| DICT           tag.soundConfig = devices_sound.htm
Jun 28 23:40:57.260: vmx| DICT             tag.memConfig = configvm_memory.htm
Jun 28 23:40:57.260: vmx| DICT            tag.miscConfig = configvm.htm
Jun 28 23:40:57.260: vmx| DICT             tag.usbConfig = devices_usb.htm
Jun 28 23:40:57.260: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Jun 28 23:40:57.260: vmx| DICT                 tag.tools = vmtools.htm
Jun 28 23:40:57.260: vmx| DICT --- COMMAND LINE
Jun 28 23:40:57.260: vmx| DICT            vmx.stdio.keep = TRUE
Jun 28 23:40:57.260: vmx| DICT             gui.available = TRUE
Jun 28 23:40:57.260: vmx| DICT --- CONFIGURATION /home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmx 
Jun 28 23:40:57.260: vmx| DICT            config.version = 8
Jun 28 23:40:57.260: vmx| DICT         virtualHW.version = 7
Jun 28 23:40:57.260: vmx| DICT             scsi0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT                   memsize = 1024
Jun 28 23:40:57.260: vmx| DICT            ide0:0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT           ide0:0.fileName = Windows XP Professional.vmdk
Jun 28 23:40:57.260: vmx| DICT            ide1:0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT           ide1:0.fileName = /dev/scd0
Jun 28 23:40:57.260: vmx| DICT         ide1:0.deviceType = cdrom-raw
Jun 28 23:40:57.260: vmx| DICT    floppy0.startConnected = FALSE
Jun 28 23:40:57.260: vmx| DICT          floppy0.fileName = 
Jun 28 23:40:57.260: vmx| DICT        floppy0.autodetect = TRUE
Jun 28 23:40:57.260: vmx| DICT         ethernet0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT   ethernet0.wakeOnPcktRcv = FALSE
Jun 28 23:40:57.260: vmx| DICT     ethernet0.addressType = generated
Jun 28 23:40:57.260: vmx| DICT ethernet0.linkStatePropagation.enable = TRUE
Jun 28 23:40:57.260: vmx| DICT               usb.present = TRUE
Jun 28 23:40:57.260: vmx| DICT      usb.generic.allowHID = TRUE
Jun 28 23:40:57.260: vmx| DICT              ehci.present = TRUE
Jun 28 23:40:57.260: vmx| DICT             sound.present = TRUE
Jun 28 23:40:57.260: vmx| DICT            sound.fileName = -1
Jun 28 23:40:57.260: vmx| DICT          sound.autodetect = TRUE
Jun 28 23:40:57.260: vmx| DICT              mks.enable3d = TRUE
Jun 28 23:40:57.260: vmx| DICT           serial0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT    serial0.startConnected = FALSE
Jun 28 23:40:57.260: vmx| DICT          serial0.fileType = thinprint
Jun 28 23:40:57.260: vmx| DICT        pciBridge0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT        pciBridge4.present = TRUE
Jun 28 23:40:57.260: vmx| DICT     pciBridge4.virtualDev = pcieRootPort
Jun 28 23:40:57.260: vmx| DICT      pciBridge4.functions = 8
Jun 28 23:40:57.260: vmx| DICT        pciBridge5.present = TRUE
Jun 28 23:40:57.260: vmx| DICT     pciBridge5.virtualDev = pcieRootPort
Jun 28 23:40:57.260: vmx| DICT      pciBridge5.functions = 8
Jun 28 23:40:57.260: vmx| DICT        pciBridge6.present = TRUE
Jun 28 23:40:57.260: vmx| DICT     pciBridge6.virtualDev = pcieRootPort
Jun 28 23:40:57.260: vmx| DICT      pciBridge6.functions = 8
Jun 28 23:40:57.260: vmx| DICT        pciBridge7.present = TRUE
Jun 28 23:40:57.260: vmx| DICT     pciBridge7.virtualDev = pcieRootPort
Jun 28 23:40:57.260: vmx| DICT      pciBridge7.functions = 8
Jun 28 23:40:57.260: vmx| DICT             vmci0.present = TRUE
Jun 28 23:40:57.260: vmx| DICT    roamingVM.exitBehavior = go
Jun 28 23:40:57.260: vmx| DICT               displayName = Windows XP Professional
Jun 28 23:40:57.260: vmx| DICT                   guestOS = winxppro
Jun 28 23:40:57.260: vmx| DICT                     nvram = Windows XP Professional.nvram
Jun 28 23:40:57.260: vmx| DICT virtualHW.productCompatibility = hosted
Jun 28 23:40:57.260: vmx| DICT          gui.exitOnCLIHLT = FALSE
Jun 28 23:40:57.261: vmx| DICT        extendedConfigFile = Windows XP Professional.vmxf
Jun 28 23:40:57.261: vmx| DICT     ide1:0.startConnected = TRUE
Jun 28 23:40:57.261: vmx| DICT ethernet0.generatedAddress = 00:0c:29:15:02:02
Jun 28 23:40:57.261: vmx| DICT            tools.syncTime = FALSE
Jun 28 23:40:57.261: vmx| DICT             uuid.location = 56 4d 1b 16 6b 1c 85 f6-94 da fe 1a b7 15 02 02
Jun 28 23:40:57.261: vmx| DICT                 uuid.bios = 56 4d 1b 16 6b 1c 85 f6-94 da fe 1a b7 15 02 02
Jun 28 23:40:57.261: vmx| DICT             cleanShutdown = TRUE
Jun 28 23:40:57.261: vmx| DICT          replay.supported = FALSE
Jun 28 23:40:57.261: vmx| DICT           replay.filename = 
Jun 28 23:40:57.261: vmx| DICT               ide0:0.redo = 
Jun 28 23:40:57.261: vmx| DICT  pciBridge0.pciSlotNumber = 17
Jun 28 23:40:57.261: vmx| DICT  pciBridge4.pciSlotNumber = 21
Jun 28 23:40:57.261: vmx| DICT  pciBridge5.pciSlotNumber = 22
Jun 28 23:40:57.261: vmx| DICT  pciBridge6.pciSlotNumber = 23
Jun 28 23:40:57.261: vmx| DICT  pciBridge7.pciSlotNumber = 24
Jun 28 23:40:57.261: vmx| DICT       scsi0.pciSlotNumber = 16
Jun 28 23:40:57.261: vmx| DICT         usb.pciSlotNumber = 32
Jun 28 23:40:57.261: vmx| DICT   ethernet0.pciSlotNumber = 33
Jun 28 23:40:57.261: vmx| DICT       sound.pciSlotNumber = 34
Jun 28 23:40:57.261: vmx| DICT        ehci.pciSlotNumber = 35
Jun 28 23:40:57.261: vmx| DICT       vmci0.pciSlotNumber = 36
Jun 28 23:40:57.261: vmx| DICT  vmotion.checkpointFBSize = 134217728
Jun 28 23:40:57.261: vmx| DICT             usb:0.present = TRUE
Jun 28 23:40:57.261: vmx| DICT             usb:1.present = TRUE
Jun 28 23:40:57.261: vmx| DICT ethernet0.generatedAddressOffset = 0
Jun 28 23:40:57.261: vmx| DICT                  vmci0.id = -1223359998
Jun 28 23:40:57.261: vmx| DICT          usb:1.deviceType = hub
Jun 28 23:40:57.261: vmx| DICT          usb:0.deviceType = mouse
Jun 28 23:40:57.261: vmx| DICT                   monitor = debug
Jun 28 23:40:57.261: vmx| DICT --- USER DEFAULTS ~/.vmware/config 
Jun 28 23:40:57.261: vmx| DICT --- HOST DEFAULTS /etc/vmware/config 
Jun 28 23:40:57.261: vmx| DICT           vmware.fullpath = /usr/bin/vmware
Jun 28 23:40:57.261: vmx| DICT                vix.libdir = /usr/lib/vmware-vix
Jun 28 23:40:57.261: vmx| DICT                NETWORKING = yes
Jun 28 23:40:57.261: vmx| DICT installerDefaults.dataCollectionEnabled = no
Jun 28 23:40:57.261: vmx| DICT            VMBLOCK_CONFED = yes
Jun 28 23:40:57.261: vmx| DICT           gksu.rootMethod = sudo
Jun 28 23:40:57.261: vmx| DICT                    libdir = /usr/lib/vmware
Jun 28 23:40:57.261: vmx| DICT               VMCI_CONFED = yes
Jun 28 23:40:57.261: vmx| DICT        vix.config.version = 1
Jun 28 23:40:57.261: vmx| DICT              VSOCK_CONFED = yes
Jun 28 23:40:57.261: vmx| DICT             initscriptdir = /etc/init.d
Jun 28 23:40:57.261: vmx| DICT installerDefaults.componentDownloadEnabled = yes
Jun 28 23:40:57.261: vmx| DICT    player.product.version = 3.1.4
Jun 28 23:40:57.261: vmx| DICT installerDefaults.transferVersion = 1
Jun 28 23:40:57.261: vmx| DICT installerDefaults.autoSoftwareUpdateEnabled = yes
Jun 28 23:40:57.261: vmx| DICT            authd.fullpath = /usr/sbin/vmware-authd
Jun 28 23:40:57.261: vmx| DICT                    bindir = /usr/bin
Jun 28 23:40:57.261: vmx| DICT       product.buildNumber = 385536
Jun 28 23:40:57.261: vmx| DICT           product.version = 7.1.4
Jun 28 23:40:57.261: vmx| DICT workstation.product.version = 7.1.4
Jun 28 23:40:57.261: vmx| DICT              product.name = VMware Workstation
Jun 28 23:40:57.261: vmx| DICT --- SITE DEFAULTS /usr/lib/vmware/config 
Jun 28 23:40:57.261: vmx| DICT                  tag.help = introduction.htm
Jun 28 23:40:57.261: vmx| DICT   tag.configurationEditor = config_editor_newvm.htm
Jun 28 23:40:57.261: vmx| DICT             tag.ideConfig = devices_virtualdrive.htm
Jun 28 23:40:57.261: vmx| DICT          tag.floppyConfig = devices_floppy.htm
Jun 28 23:40:57.261: vmx| DICT           tag.mouseConfig = devices_mouse.htm
Jun 28 23:40:57.261: vmx| DICT             tag.netConfig = devices_netadapter.htm
Jun 28 23:40:57.261: vmx| DICT        tag.parallelConfig = devices_parallel.htm
Jun 28 23:40:57.261: vmx| DICT          tag.serialConfig = devices_serial.htm
Jun 28 23:40:57.261: vmx| DICT           tag.soundConfig = devices_sound.htm
Jun 28 23:40:57.261: vmx| DICT             tag.memConfig = configvm_memory.htm
Jun 28 23:40:57.261: vmx| DICT            tag.miscConfig = configvm.htm
Jun 28 23:40:57.261: vmx| DICT             tag.usbConfig = devices_usb.htm
Jun 28 23:40:57.261: vmx| DICT         tag.displayConfig = configvm_display-problems.htm
Jun 28 23:40:57.261: vmx| DICT                 tag.tools = vmtools.htm
Jun 28 23:40:57.261: vmx| DICT --- GLOBAL SETTINGS /usr/lib/vmware/settings 
Jun 28 23:40:57.274: vmx| Vix: [17204 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=1, newAppState=1873, success=1
Jun 28 23:40:57.300: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Jun 28 23:40:57.323: vmx| hostCpuFeatures = 0x404000f8
Jun 28 23:40:57.324: vmx| hostNumPerfCounters = 2
Jun 28 23:40:57.324: vmx| CPU0:  PMC: unused [c:1 f:1 e:1]
Jun 28 23:40:57.324: vmx| MONITOR MODE: allowed modes          : BT
Jun 28 23:40:57.324: vmx| MONITOR MODE: user requested modes   : BT HV HWMMU
Jun 28 23:40:57.324: vmx| MONITOR MODE: guestOS preferred modes: BT HWMMU HV
Jun 28 23:40:57.324: vmx| MONITOR MODE: filtered list          : BT
Jun 28 23:40:57.324: vmx| HV Settings: virtual exec = 'software'; virtual mmu = 'software'
Jun 28 23:40:57.637: vmx| MsgHint: msg.loader.debug.ws
Jun 28 23:40:57.637: vmx| You are running the virtual machine with the DEBUG option. Please be advised that the additional logging and error checking enabled by this option results in substantially slower execution.
Jun 28 23:40:57.637: vmx| Use the "Gather debugging information" setting in the Advanced panel of the virtual machine settings to change this option.
Jun 28 23:40:57.637: vmx| ---------------------------------------
Jun 28 23:41:11.274: vmx| XINFO X fd is 73
Jun 28 23:41:11.274: vmx| XINFO depth 24 bpp 32 class 4
Jun 28 23:41:11.422: vmx| Host display topology 1280x800.
Jun 28 23:41:11.422: vmx| SVGA: Max size 2560x1600
Jun 28 23:41:11.422: vmx| WSSCAN: reserved mem (in MB) min=32 max=1920 recommended=1920
Jun 28 23:41:11.422: vmx| WSSCAN: used rec mem (in MB) 1920
Jun 28 23:41:11.422: vmx| PShare: enabled 1 adaptive 1 local 1 scanRate [16, 64]
Jun 28 23:41:11.422: vmx| WSSCAN: 296513 9441 262144 32768
Jun 28 23:41:11.422: vmx| WSSCAN 1 0 457369 465561 491520 -1 50 0
Jun 28 23:41:11.423: vmx| MXSemaphoreInitFromPipe: eventfd usage: Enabled
Jun 28 23:41:11.423: vmx| MX: init lock: rank(userlevelLock)=100 lid=0
Jun 28 23:41:11.423: vmx| MX: init lock: rank(bigDeviceLock)=110 lid=1
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=2
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=3
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=4
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=5
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=6
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=7
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=8
Jun 28 23:41:11.423: vmx| MX: init lock: rank(monAct)=65534 lid=9
Jun 28 23:41:11.423: vmx| MX: init lock: rank(stTable)=99 lid=10
Jun 28 23:41:11.423: vmx| MX: init lock: rank(log)=0 lid=11
Jun 28 23:41:11.426: vmx| LICENSE using: '/usr/lib/vmware/licenses/user/license-ws-70-e1-200904' 
Jun 28 23:41:11.562: vmx| BusMem: Alloc'ing region BusError flags 0x890 numPages 1
Jun 28 23:41:11.562: vmx| BusMem: Alloc'ing frames for region BusError with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:11.611: vmx| MX: init condvar: RestoreCond
Jun 28 23:41:11.611: vmx| Host IPI vectors: 0xfc 0xfb
Jun 28 23:41:11.611: vmx| Monitor_PowerOn: HostedVSMP skew tracking is disabled
Jun 28 23:41:11.611: vmx| Monitor_PowerOn: HostedVSMP crosscall yielding is disabled
Jun 28 23:41:11.619: vmx| vmm32-modules: [vmm.vmm32 .data:0x2b000-0x790 .sdata:0x2c000-0x4e4 .statvars:0x2d000-0x3a0 .peer:0x2e000-0x26b40 .shared:0x5b000-0x19d80 .bss:0x76000-0xbae8 .rodata:0x83000-0xe960 .text:0x94000-0xac5d4 .kstatvars:0x3000-0x0, mmu-nohv.vmm32 .rodata:0x91960-0x4a0 .data:0x2b790-0x20 .peer:0x54b40-0x5680 .shared:0x74d80-0x340 .bss:0x81b00-0x609 .text:0x1405e0-0x18622 .comment:0x40000d5c-0x10e .statvars:0x2000-0x0 .kstatvars:0x2000-0x0 .scb:0x40004080-0x180 .shared_meta:0x400048f0-0x360 .peer_meta:0x400011a0-0x210 .patchtext:0x40000500-0xb0, pv-none.vmm32 .shared:0x750c0-0x180 .bss:0x82120-0x84 .text:0x158c04-0x1be .comment:0x40000e6a-0x48 .shared_meta:0x40004c50-0x90, vprobe-none.vmm32 .text:0x158dc4-0x35 .comment:0x40000eb2-0x12, hv-none.vmm32 .rodata:0x91e00-0x4 .data:0x1000-0x0 .peer:0x1000-0x0 .shared:0x1000-0x0 .bss:0x821a4-0x4 .text:0x158dfc-0x26 .comment:0x40000ec4-0x12 .statvars:0x1000-0x0 .kstatvars:0x1000-0x0, gphys-sw.vmm32 .rodata:0x91e04-0x259 .data:0x2b7b0-0x4 .peer:0x5a1c0-0x40 .shared:0x75240-0x80 .bss:0x821a8-0x11 .text:0x158e30-0x1cd7 .comment:0x40000ed6-0x12 .statvars:0x2000-0x0 .kstatvars:0x2000-0x0 .scb:0x40004200-0x60 .shared_meta:0x40004ce0-0x270 .peer_meta:0x400013b0-0x30 .patchtext:0x400005b0-0x10, vassert-none.vmm32 .text:0x15ab08-0x52 .comment:0x40000ee8-0x12, vmsafe-none.vmm32 .text:0x15ab5c-0x37 .comment:0x40000efa-0x12, buslogic-buslogic.vmm32 .shared:0x752c0-0x40 .bss:0x1000-0x0 .text:0x15aba0-0x1a7 .comment:0x40000f0c-0x12 .scb:0x40004260-0x60 .shared_meta:0x40004f50-0x60, {SharedAreaReservations} .shared:0x75300-0x80, <MonSrcFile> .rodata:0x9205d-0x1d09]
Jun 28 23:41:11.630: vmx| KHZEstimate 1500000
Jun 28 23:41:11.630: vmx| MHZEstimate 1500
Jun 28 23:41:11.630: vmx| NumVCPUs 1
Jun 28 23:41:11.630: vmx| MX: init lock: rank(iospaceLock)=120 lid=12
Jun 28 23:41:11.631: vmx| PShare: checkRate 16
Jun 28 23:41:11.631: vmx| UUID: SMBIOS UUID is reported as '44 45 4c 4c 33 00 10 5a-80 4d b5 c0 4f 4d 37 31'.
Jun 28 23:41:11.631: vmx| UUID: location-UUID is 56 4d 1b 16 6b 1c 85 f6-94 da fe 1a b7 15 02 02
Jun 28 23:41:11.631: vmx| MX: init lock: rank(WorkerLock)=65534 lid=13
Jun 28 23:41:11.631: vmx| MX: init condvar: WorkerPending
Jun 28 23:41:11.631: vmx| MX: init condvar: WorkerCompleted
Jun 28 23:41:11.631: vmx| AIOGNRC: numThreads=4 ide=1, scsi=0, passthru=1
Jun 28 23:41:11.631: vmx| WORKER: Creating new group with numThreads=4 (4)
Jun 28 23:41:11.632: vmx| Couldn't init aioLinux: failed to dlopen libaio: libaio.so.1: cannot open shared object file: No such file or directory
Jun 28 23:41:11.703: vmx| SL: nonDeterFxsaveBPs: 0x0 0x0
Jun 28 23:41:11.704: vmx| Replay State = 0
Jun 28 23:41:11.704: vmx| minDEThreshold: 79
Jun 28 23:41:11.766: vmx| MM: Using partialmap, 262144 pages AC 1 CE 1 TM 1 DOHU 0
Jun 28 23:41:11.766: vmx| BusMem: Alloc'ing region MainMem flags 0x2400 numPages 262144
Jun 28 23:41:11.775: vmx| BusMem: Alloc'ing frames for region MainMem with 2048 pages, size 8388608 and 1 frame mapping entries.
Jun 28 23:41:11.811: vmx| MX: init condvar: MMCpt
Jun 28 23:41:11.811: vmx| MX: init lock: rank(MMCpt)=112 lid=14
Jun 28 23:41:11.811: vmx| MMC: Initialized PLS=1 PLR=0 PFS=0 TS=1 BS=1 WZ=0 BufM=576 LOR=0 SOR=1 BlkP=32 W=50 PF=1024
Jun 28 23:41:11.811: vmx| UUID: location-UUID is 56 4d 1b 16 6b 1c 85 f6-94 da fe 1a b7 15 02 02
Jun 28 23:41:11.813: vmx| MM: Opened paging file, '/home/arkelsa/vmware/Windows XP Professional/564d1b16-6b1c-85f6-94da-fe1ab7150202.vmem'.
Jun 28 23:41:11.832: vmx| MMCHK: Disabling checks which are not forced, cannot do checks on certain processors.
Jun 28 23:41:11.832: vmx| MStat: Creating Stat vm.uptime
Jun 28 23:41:11.833: vmx| MStat: Creating Stat vm.suspendTime
Jun 28 23:41:11.833: vmx| MStat: Creating Stat vm.powerOnTimeStamp
Jun 28 23:41:11.833: vmx| VMXAIOMGR: Using: simple=Generic unbuf=Generic
Jun 28 23:41:11.835: vmx| MX: init lock: rank(intrLock)=65531 lid=15
Jun 28 23:41:11.835: vmx| BusMem: Alloc'ing region LocalApic flags 0x1230 numPages 1
Jun 28 23:41:11.835: vmx| BusMem: Alloc'ing frames for region LocalApic with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:11.850: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Jun 28 23:41:11.860: vmx| DISK: OPEN ide0:0 '/home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmdk' persistent R[]
Jun 28 23:41:11.959: vmx| DISKLIB-DSCPTR: Opened [0]: "Windows XP Professional.vmdk" (0x1a)
Jun 28 23:41:11.959: vmx| DISKLIB-LINK  : Opened '/home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmdk' (0x1a): monolithicSparse, 41943040 sectors / 20 GB.
Jun 28 23:41:11.959: vmx| DISKLIB-LIB   : Opened "/home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmdk" (flags 0x1a).
Jun 28 23:41:11.959: vmx| DiskGetGeometry: Reading of disk partition table
Jun 28 23:41:11.959: vmx| Setting thread 36 stack size to 524288.
Jun 28 23:41:11.963: vmx| DISK: OPEN '/home/arkelsa/vmware/Windows XP Professional/Windows XP Professional.vmdk' Geo (16383/16/63) BIOS Geo (2610/255/63)
Jun 28 23:41:12.030: vmx| MX: init lock: rank(timeTracker)=65532 lid=16
Jun 28 23:41:12.030: vmx| TimeTracker host to guest rate conversion 2896787367690 @ 1500000000Hz -> 2896787367690 @ 1500000000Hz
Jun 28 23:41:12.030: vmx| TimeTracker host to guest rate conversion ((x * 2147483648) >> 31) + 0
Jun 28 23:41:12.033: vmx| DISK: DELAY: vide.vtdelay=0 hard-disk.minVirtualTime=0 magicBoot1=0
Jun 28 23:41:12.034: vmx| USB: Initializing 'Generic' backend
Jun 28 23:41:12.034: vmx| USB: Unable to open "/proc/bus/usb/devices" (No such file or directory).
Jun 28 23:41:12.036: vmx| USB: Initializing 'Virtual Hub' backend
Jun 28 23:41:12.036: vmx| USB: Initializing 'Virtual Mouse' backend
Jun 28 23:41:12.036: vmx| USB: Initializing 'Virtual Keyboard' backend
Jun 28 23:41:12.036: vmx| USB: Initializing 'Virtual Mass Storage' backend
Jun 28 23:41:12.036: vmx| USB: Initializing 'Virtual CCID' backend
Jun 28 23:41:12.052: vmx| USB-CCID:  dlopened default libpcsclite.so.1.
Jun 28 23:41:16.973: vmx| USB-CCID: Could not establish resource manager context for card ops: SCARD_E_NO_SERVICE(0x8010001d).
Jun 28 23:41:16.973: vmx| USB: Unable to initialize 'Virtual CCID' backend
Jun 28 23:41:17.011: vmx| MX: init lock: rank(mksLock)=130 lid=17
Jun 28 23:41:17.012: vmx| MX: init lock: rank(PseudoCallUserLock)=128 lid=18
Jun 28 23:41:17.013: vmx| MX: init lock: rank(mksRolePseudoCallLock)=129 lid=19
Jun 28 23:41:17.013: vmx| MX: init condvar: mksRolePseudoCallCondVar
Jun 28 23:41:17.015: vmx| XINFO X fd is 73
Jun 28 23:41:17.015: vmx| XINFO depth 24 bpp 32 class 4
Jun 28 23:41:17.024: vmx| DisplayTopologyInit: using the XRandR backend.
Jun 28 23:41:17.549: vmx| LibGap_Test passed
Jun 28 23:41:17.626: vmx| GLPrimary_Alloc, thread vmx
Jun 28 23:41:17.636: vmx| WORKER: Creating new group with numThreads=1 (5)
Jun 28 23:41:17.636: vmx| MKS: Base polling period is 1000000us
Jun 28 23:41:17.639: vmx| KHBKL: Unable to parse keystring at: ''
Jun 28 23:41:17.639: vmx| MKS REMOTE Loading VNC Configuration from VM config file
Jun 28 23:41:17.642: vmx| VLANCE: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks
Jun 28 23:41:17.642: vmx| VMXNET: send cluster threshold is 80, size = 2 recalcInterval is 2 ticks, dontClusterSize is 128
Jun 28 23:41:17.642: vmx| NetPkt: checksum cycles/kB: C=742 asm1=669 asm2=666
Jun 28 23:41:17.642: vmx| NetPkt: copy and sum cycles/kB: C=988 asm1=739 asm2=744
Jun 28 23:41:17.642: vmx| BusMem: Alloc'ing region pcieMMIO flags 0x1020 numPages 65536
Jun 28 23:41:17.644: vmx| BusMem: Alloc'ing frames for region pcieMMIO with 512 pages, size 2097152 and 1 frame mapping entries.
Jun 28 23:41:17.652: vmx| Chipset version: 0x13
Jun 28 23:41:17.653: vmx| BusMem: Alloc'ing region FlashRam flags 0x10 numPages 128
Jun 28 23:41:17.653: vmx| BusMem: Alloc'ing frames for region FlashRam with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.655: vmx| BusMem: Alloc'ing region ExtCfgDeviceMMIO flags 0x1020 numPages 24
Jun 28 23:41:17.655: vmx| BusMem: Alloc'ing frames for region ExtCfgDeviceMMIO with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.716: vmx| MX: init lock: rank(VIDELock)=111 lid=20
Jun 28 23:41:17.716: vmx| DISKUTIL: ide0:0 : capacity=41943040
Jun 28 23:41:17.743: vmx| SCSI DEVICE (ide0:0): Computed value of ide0:0.useBounceBuffers: default
Jun 28 23:41:17.743: vmx| DISKUTIL: ide0:0 : capacity=41943040
Jun 28 23:41:17.743: vmx| DISKUTIL: ide0:0 : geometry=2610/255/63
Jun 28 23:41:17.744: vmx| SCSI DEVICE (ide1:0): Computed value of ide1:0.useBounceBuffers: default
Jun 28 23:41:17.744: vmx| DISKUTIL: ide1:0 : capacity=0
Jun 28 23:41:17.744: vmx| DISKUTIL: ide1:0 : geometry=0/0/0
Jun 28 23:41:17.744: vmx| MX: init lock: rank(busLogicLock)=111 lid=21
Jun 28 23:41:17.744: vmx| SCSI0: UNTAGGED commands will be converted to ORDER tags.
Jun 28 23:41:17.746: vmx| MX: init lock: rank(vgaLock)=60 lid=22
Jun 28 23:41:17.746: vmx| MX: init lock: rank(svgaLock)=30 lid=23
Jun 28 23:41:17.746: vmx| MX: init lock: rank(svgaIrqMutex)=65530 lid=24
Jun 28 23:41:17.746: vmx| MX: init lock: rank(PseudoCallUserLock)=100 lid=25
Jun 28 23:41:17.746: vmx| MX: init lock: rank(svgaPseudoCallLock)=101 lid=26
Jun 28 23:41:17.747: vmx| MX: init condvar: svgaPseudoCallCondVar
Jun 28 23:41:17.747: vmx| MX: init lock: rank(SVGAGuestMemLock)=65532 lid=27
Jun 28 23:41:17.747: vmx| SVGA: Device capabilities 0x001fc3e2
Jun 28 23:41:17.747: vmx| Host display topology 1280x800.
Jun 28 23:41:17.747: vmx| SVGA: Max size 2560x1600
Jun 28 23:41:17.814: vmx| Host display topology 1280x800 with 1 displays.
Jun 28 23:41:17.814: vmx| SVGA: Max size 2560x1600
Jun 28 23:41:17.815: vmx| SVGA: FIFO capabilities 0x0000007f
Jun 28 23:41:17.815: vmx| USB: Initializing 'UHCI' host controller
Jun 28 23:41:17.817: vmx| MX: init lock: rank(vlanceLock)=30 lid=28
Jun 28 23:41:17.817: vmx| Ethernet0 MAC Address: 00:0c:29:15:02:02
Jun 28 23:41:17.818: vmx| MX: init lock: rank(es1371Lock)=110 lid=29
Jun 28 23:41:17.828: vmx| SOUND 077.828817 Alsa library version: 1.0.24.1.
Jun 28 23:41:17.829: vmx| USB: Initializing 'EHCI' host controller
Jun 28 23:41:17.829: vmx| BusMem: Alloc'ing region EHCI_MemRegRW flags 0x1020 numPages 1
Jun 28 23:41:17.829: vmx| BusMem: Alloc'ing frames for region EHCI_MemRegRW with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.829: vmx| BusMem: Alloc'ing region EHCI_MemRegWO flags 0x1070 numPages 1
Jun 28 23:41:17.829: vmx| BusMem: Alloc'ing frames for region EHCI_MemRegWO with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.850: vmx| MX: init lock: rank(VMCIDgTableVMX)=65534 lid=30
Jun 28 23:41:17.914: vmx| MX: init lock: rank(VSockLookupLock)=65534 lid=31
Jun 28 23:41:17.915: vmx| MX: init lock: rank(timer)=30 lid=32
Jun 28 23:41:17.915: vmx| MStat: Creating Stat vm.heartbeat
Jun 28 23:41:17.916: vmx| TOOLS Generated SessionId 14699505103130066459
Jun 28 23:41:17.920: vmx| VMXVmdbGuest_GetToolsVersion did nothing; tools version has not yet been initialized
Jun 28 23:41:17.920: vmx| DISKUTIL: ide0:0 : toolsVersion = 8326
Jun 28 23:41:17.920: vmx| VMXVmdbGuest_GetToolsVersion did nothing; tools version has not yet been initialized
Jun 28 23:41:17.920: vmx| TOOLS setting legacy tools version to '8326', manifest status is 5
Jun 28 23:41:17.920: vmx| VMXVmdb_SetToolsVersionState: status value set to 'ok'
Jun 28 23:41:17.920: vmx| VMXVmdb_SetToolsVersionState: status value set to 'ok'
Jun 28 23:41:17.921: vmx| TOOLS INSTALL initializing state to IDLE on power on.
Jun 28 23:41:17.921: vmx| MX: init lock: rank(PseudoCallUserLock)=128 lid=33
Jun 28 23:41:17.922: vmx| MX: init lock: rank(vmxPseudoCallLock)=129 lid=34
Jun 28 23:41:17.922: vmx| MX: init condvar: vmxPseudoCallCondVar
Jun 28 23:41:17.971: vmx| MX: init lock: rank(InputEventLock)=65534 lid=35
Jun 28 23:41:17.972: vmx| MX: init lock: rank(paraTime)=65532 lid=36
Jun 28 23:41:17.972: vmx| PTSC to VMI Wallclock (nsec) 2897626071591 @ 1500000000Hz -> 1309326077000000000 @ 1000000000Hz
Jun 28 23:41:17.972: vmx| PTSC to VMI Wallclock (nsec) ((x * 2863311530) >> 32) + 1309324145249286056
Jun 28 23:41:17.972: vmx| PTSC to ParaTime RealCycles 0 @ 1500000000Hz -> 0 @ 1500000000Hz
Jun 28 23:41:17.972: vmx| PTSC to ParaTime RealCycles ((x * 1) >> 0) + 0
Jun 28 23:41:17.972: vmx| ParaTime RealCycles to PTSC 0 @ 1500000000Hz -> 0 @ 1500000000Hz
Jun 28 23:41:17.972: vmx| ParaTime RealCycles to PTSC ((x * 1) >> 0) + 0
Jun 28 23:41:17.973: vmx| memoryHotplug: Current size = 1024MB, Minimum size = 1024MB, Maximum size = 1024MB
Jun 28 23:41:17.973: vmx| memoryHotplug: Entry[0]: 00000000000000A0-00000000000A0000
Jun 28 23:41:17.973: vmx| memoryHotplug: Entry[1]: 00000000001000A0-0000000040000000
Jun 28 23:41:17.973: vmx| BusMem: Alloc'ing region SBIOS flags 0x90 numPages 4
Jun 28 23:41:17.973: vmx| BusMem: Alloc'ing frames for region SBIOS with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.973: vmx| BusMem: Alloc'ing region VBIOS flags 0x90 numPages 8
Jun 28 23:41:17.973: vmx| BusMem: Alloc'ing frames for region VBIOS with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.974: vmx| BusMem: Alloc'ing region VLANCE flags 0x90 numPages 16
Jun 28 23:41:17.974: vmx| BusMem: Alloc'ing frames for region VLANCE with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:17.988: vmx| guestCpuFeatures = 0x404000f8
Jun 28 23:41:17.988: vmx| guestCPUID vendor: GenuineIntel
Jun 28 23:41:17.988: vmx| guestCPUID   name:         Intel(R) Pentium(R) M processor 1.50GHz
Jun 28 23:41:17.988: vmx| guestCPUID level 00000000, 0: 0x00000002 0x756e6547 0x6c65746e 0x49656e69
Jun 28 23:41:17.988: vmx| guestCPUID level 00000001, 0: 0x000006d8 0x00010816 0x80000000 0x0fe9fbff
Jun 28 23:41:17.989: vmx| guestCPUID level 00000002, 0: 0x02b3b001 0x000000f0 0x00000000 0x2c04307d
Jun 28 23:41:17.989: vmx| guestCPUID level 40000000, 0: 0x40000010 0x61774d56 0x4d566572 0x65726177
Jun 28 23:41:17.989: vmx| guestCPUID level 40000010, 0: 0x0016e360 0x000101d0 0x00000000 0x00000000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000000, 0: 0x80000008 0x00000000 0x00000000 0x00000000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000001, 0: 0x00000000 0x00000000 0x00000000 0x00100000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000002, 0: 0x20202020 0x20202020 0x65746e49 0x2952286c
Jun 28 23:41:17.989: vmx| guestCPUID level 80000003, 0: 0x6e655020 0x6d756974 0x20295228 0x7270204d
Jun 28 23:41:17.989: vmx| guestCPUID level 80000004, 0: 0x7365636f 0x20726f73 0x30352e31 0x007a4847
Jun 28 23:41:17.989: vmx| guestCPUID level 80000005, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000006, 0: 0x00000000 0x00000000 0x08006040 0x00000000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000007, 0: 0x00000000 0x00000000 0x00000000 0x00000000
Jun 28 23:41:17.989: vmx| guestCPUID level 80000008, 0: 0x00002028 0x00000000 0x00000000 0x00000000
Jun 28 23:41:17.996: vmx| BusMem: Alloc'ing region SVGAFB flags 0x10 numPages 32768
Jun 28 23:41:17.997: vmx| BusMem: Alloc'ing frames for region SVGAFB with 256 pages, size 1048576 and 1 frame mapping entries.
Jun 28 23:41:18.002: vmx| BusMem: Alloc'ing region SVGAMEM flags 0x10 numPages 512
Jun 28 23:41:18.002: vmx| BusMem: Alloc'ing frames for region SVGAMEM with 4 pages, size 16384 and 1 frame mapping entries.
Jun 28 23:41:18.002: vmx| BusMemSample: initPercent 75 touched 196608
Jun 28 23:41:18.003: vmx| MemSched: 0 1 3288 457348 465540 491520 -1 50
Jun 28 23:41:18.003: vmx| MemSched: VM 0 min 172045 max 303117 share 262144 paged 296513 nonpaged 6604 locked 3288 cowedGlobal 0 usedPct 75
Jun 28 23:41:18.003: vmx| MemSched: locked 3288 target 303117 balloon 0 0 0 swapped 0 0 0 allocd 0 455 state 0 100
Jun 28 23:41:18.003: vmx| MemSched: states: 0 1 : 1 0 : 2 0 : 3 0
Jun 28 23:41:18.003: vmx| MemSched: Balloon enabled 1 guestType 0 maxSize 0
Jun 28 23:41:18.003: vmx| MemSched: PShare checked 0 bad 0 badKey 0 badMPN 0 badCOW 0
Jun 28 23:41:18.003: vmx| MemSched: COWStats VM 0: shared 0 0 totalShared 0 0 0 totalBreaks 0 0
Jun 28 23:41:18.003: vmx| TOOLS received request in VMX to set option 'enableDnD' -> '1'
Jun 28 23:41:18.003: vmx| TOOLS received request in VMX to set option 'copypaste' -> '1'
Jun 28 23:41:18.005: vmx| MX: init lock: rank(pollLock)=65533 lid=37
Jun 28 23:41:18.005: vmx| Vix: [17204 mainDispatch.c:844]: VMAutomation_PowerOn. Powering on.
Jun 28 23:41:18.005: vmx| MX: init lock: rank(VMAutomationConnectionListLock)=0 lid=38
Jun 28 23:41:18.005: vmx| MX: init lock: rank(vmxStateCacheLock)=0 lid=39
Jun 28 23:41:18.005: vmx| VMX_PowerOn: ModuleTable_PowerOn = 1
Jun 28 23:41:18.006: vmx| Setting thread 1 stack size to 1048576.
Jun 28 23:41:18.006: vmx| Setting thread 4 stack size to 524288.
Jun 28 23:41:18.006: mks| Async MKS thread is alive
Jun 28 23:41:18.006: mks| GLPrimaryInit3D, thread mks
Jun 28 23:41:18.009: mks| GLPrimaryHostConnect thread mks
Jun 28 23:41:18.228: mks| OpenGL Version: "1.4 Mesa 7.10.2" (1.4.0)
Jun 28 23:41:18.228: mks| OpenGL Vendor: "Tungsten Graphics, Inc"
Jun 28 23:41:18.228: mks| OpenGL Renderer: "Mesa DRI Intel(R) 915GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2"
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_explicit_attrib_location GL_ARB_fragment_program GL_ARB_fragment_shader
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_EXT_texture_rectangle GL_EXT_vertex_array GL_OES_EGL_image GL_OES_read_format
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_object_purgeable
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_IBM_multimode_draw_arrays
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_MESA_pack_invert GL_MESA_window_pos GL_MESA_ycbcr_texture GL_NV_blend_square
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texgen_reflection
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_program1_1 GL_NV_vertex_program
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
Jun 28 23:41:18.228: mks| OpenGL Extensions: GL_SUN_multi_draw_arrays
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_APPLE_client_storage
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_APPLE_fence
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_APPLE_flush_buffer_range
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_APPLE_texture_range
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_APPLE_ycbcr_422
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_draw_buffers
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_fragment_program
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_fragment_shader
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_ARB_framebuffer_object
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_half_float_pixel
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_ARB_imaging
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_map_buffer_range
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_multitexture
Jun 28 23:41:18.229: mks| VMGL: Extension missing, GL_ARB_occlusion_query
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_pixel_buffer_object
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_point_parameters
Jun 28 23:41:18.229: mks| VMGL: Extension present, GL_ARB_point_sprite
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_shader_objects
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ARB_shader_texture_lod
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_texture_compression
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_texture_cube_map
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_texture_env_combine
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ARB_texture_float
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_texture_non_power_of_two
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_texture_rectangle
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ARB_texture_rg
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ARB_uniform_buffer_object
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ARB_vertex_blend
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_vertex_buffer_object
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_vertex_program
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_vertex_shader
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_ARB_window_pos
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ATI_draw_buffers
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ATI_envmap_bumpmap
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_ATI_shader_texture_lod
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXTX_framebuffer_mixed_formats
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_blend_equation_separate
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_blend_func_separate
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_fog_coord
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_framebuffer_blit
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_framebuffer_object
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXT_gpu_shader4
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_packed_depth_stencil
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_provoking_vertex
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_secondary_color
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_stencil_two_side
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_texture3D
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXT_texture_compression_s3tc
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_texture_cube_map
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_texture_filter_anisotropic
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXT_texture_mirror_clamp
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_EXT_texture_rectangle
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXT_texture_swizzle
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_EXT_vertex_array_bgra
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_NV_fence
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_NV_half_float
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_NV_packed_depth_stencil
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_NV_texgen_reflection
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_NV_texture_env_combine4
Jun 28 23:41:18.230: mks| VMGL: Extension present, GL_NV_texture_rectangle
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_NV_texture_shader
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_NV_texture_shader2
Jun 28 23:41:18.230: mks| VMGL: Extension missing, GL_NV_vertex_array_range
Jun 28 23:41:18.230: mks| VMGL: Extension missing, WGL_ARB_make_current_read
Jun 28 23:41:18.230: mks| VMGL: Extension missing, WGL_ARB_pixel_format
Jun 28 23:41:18.230: mks| VMGL: Extension missing, WGL_ARB_render_texture
Jun 28 23:41:18.232: mks| glx Client Version: 1.4
Jun 28 23:41:18.234: mks| GLManager: Required extension GL_EXT_texture_compression_s3tc is missing.
Jun 28 23:41:18.237: mks| Finish HostDisconnect: thread mks
Jun 28 23:41:18.238: vcpu-0| MX: init lock: rank(offline)=99 lid=40
Jun 28 23:41:18.238: vcpu-0| MX: init lock: rank(monitorPoll)=65533 lid=41
Jun 28 23:41:18.238: vmx| PTSC: using reference clock [TSC: 2892548757538->2897744649787, RC: 3639192191->3660745787]
Jun 28 23:41:18.246: vcpu-0| APIC: version = 0x14, max LVT = 5
Jun 28 23:41:18.247: vcpu-0| APIC: LDR = 0x1000000, DFR = 0xffffffff
Jun 28 23:41:18.248: vmx| DnDRegisterRpc: DnD rpc already set to 1
Jun 28 23:41:18.248: vmx| CopyPasteRegisterRpc: already set to 1
Jun 28 23:41:18.248: vcpu-0| MX: init lock: rank(PAction lock)=65533 lid=42
Jun 28 23:41:18.248: vcpu-0| MX: init lock: rank(stopLock)=1 lid=43
Jun 28 23:41:18.248: vcpu-0| BUSMEM: Initialization (boot-vcpu=1 vmm32=1)
Jun 28 23:41:18.248: vcpu-0| MX: init lock: rank(busMemLock)=80 lid=44
Jun 28 23:41:18.248: vcpu-0| BUSMEM: vmm32 initialization
Jun 28 23:41:18.248: vcpu-0| BUSMEM: Allocating frames for slot 0
Jun 28 23:41:18.248: vcpu-0| BUSMEM: Allocating frames for slot 1
Jun 28 23:41:18.248: vcpu-0| BUSMEM: Allocating frames for slot 2
Jun 28 23:41:18.248: vcpu-0| BUSMEM: Allocating frames for slot 3
Jun 28 23:41:18.257: mks| Connecting to window system.
Jun 28 23:41:18.260: mks| XINFO X fd is 68
Jun 28 23:41:18.260: mks| XINFO depth 24 bpp 32 class 4
Jun 28 23:41:18.281: mks| DisplayTopologyInit: using the XRandR backend.
Jun 28 23:41:18.322: vcpu-0| BUSMEM: Allocating frames for slot 4
Jun 28 23:41:18.754: mks| MKS: Base polling period is 10000us
Jun 28 23:41:18.754: mks| XKeymap_PowerOn: use evdev keycode mapping.
Jun 28 23:41:18.755: mks| rasterops MMXEXT accelerations enabled
Jun 28 23:41:19.170: mks| DisplayTopologyGetEDID: could not obtain EDID data for output with XID 66.
Jun 28 23:41:19.170: mks| DisplayTopologyGetEDID: could not obtain EDID data for output with XID 67.
Jun 28 23:41:19.170: mks| XInfoFetchModes: host display mode 0: 1280x800
Jun 28 23:41:19.170: mks| XInfoFetchModes: host display mode 1: 1024x768
Jun 28 23:41:19.170: mks| XInfoFetchModes: host display mode 2: 800x600
Jun 28 23:41:19.171: mks| XInfoFetchModes: host display mode 3: 640x480
Jun 28 23:41:19.172: mks| XI major version 2, minor version 1
Jun 28 23:41:19.172: mks| NOT_TESTED /build/mts/release/bora-385536/bora/mks/input/mksXInput.c:379
Jun 28 23:41:19.178: mks| Adding local console B916748
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 5
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 6
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 7
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 8
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 9
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 10
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 11
Jun 28 23:41:19.184: vcpu-0| BUSMEM: Allocating frames for slot 12
Jun 28 23:41:19.184: vcpu-0| Balloon: beginning initialization
Jun 28 23:41:19.192: mks| Msg_Post: Information
Jun 28 23:41:19.192: mks| [msg.glBackend.initFailed] 3D graphics acceleration will be disabled. This computer does not have a 3D graphics system supported by VMware Workstation. ----------------------------------------
Jun 28 23:41:19.486: vcpu-0| Balloon: initialized
Jun 28 23:41:19.486: vcpu-0| BUSMEM: mtag {3 frame; size 32}
Jun 28 23:41:19.487: vcpu-0| MX: init lock: rank(mmuInfoLock)=98 lid=45
Jun 28 23:41:19.487: vcpu-0| MX: init lock: rank(mwaitLock)=39 lid=46
Jun 28 23:41:19.487: vcpu-0| BranchTracingInit (before): debugCtl 0x1
Jun 28 23:41:19.487: vcpu-0| BranchTracingInit (after): debugCtl 0x1
Jun 28 23:41:19.487: vcpu-0| Init modules.
Jun 28 23:41:19.487: vcpu-0| BusMem: Alloc'ing region VGA flags 0x1020 numPages 32
Jun 28 23:41:19.487: vcpu-0| BusMem: Alloc'ing frames for region VGA with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:19.487: vcpu-0| BUSMEM: Allocating frames for slot 13
Jun 28 23:41:19.500: mks| PrimaryHostOpsImplForwardvideoFlush: Can't take stats on unknown video overlay format 0
Jun 28 23:41:19.501: mks| HostOps hideCursor before defineCursor!
Jun 28 23:41:19.510: vcpu-0| BusMem: Alloc'ing region IOAPIC flags 0x1020 numPages 1
Jun 28 23:41:19.510: vcpu-0| BusMem: Alloc'ing frames for region IOAPIC with 1 pages, size 4096 and 1 frame mapping entries.
Jun 28 23:41:19.510: vcpu-0| BUSMEM: Allocating frames for slot 14
Jun 28 23:41:19.510: vcpu-0| CPU reset: hard (mode 2)
Jun 28 23:41:19.510: vcpu-0| VT_ClearVirtualTSC(void) -2896787367691
Jun 28 23:41:19.510: vcpu-0| deviceLock.tryLock.failProb debug failure probability = 0.000000
Jun 28 23:41:19.511: vcpu-0| deviceLock.tryLock.seed = 17204
Jun 28 23:41:19.511: vcpu-0| memoryHotplug: Entry[0]: 00000000000000A0-00000000000A0000
Jun 28 23:41:19.511: vcpu-0| memoryHotplug: Entry[1]: 00000000001000A0-0000000040000000
Jun 28 23:41:19.516: vcpu-0| PIIX4: PM Resuming from suspend type 0x0.
Jun 28 23:41:19.661: vcpu-0| VNET: MACVNetConnectToNetwork: Ethernet0: notify available
Jun 28 23:41:19.662: vcpu-0| CDROM: Connecting ide1:0 to '/dev/scd0'. img=0 raw=1 remote=0
Jun 28 23:41:19.800: vcpu-0| CDROM-LIN:  Implementing mediaChange workaround.
Jun 28 23:41:19.938: vcpu-0| CDROM-LIN:  SEND PACKET API Heuristic active.
Jun 28 23:41:19.938: vcpu-0| CDROM-LIN:  Using SG_IO ioctl for pass-through.
Jun 28 23:41:20.110: vcpu-0| Vix: [17209 mainDispatch.c:3661]: VMAutomation_ReportPowerOpFinished: statevar=0, newAppState=1872, success=1
Jun 28 23:41:20.116: vcpu-0| Vix: [17209 mainDispatch.c:3582]: VMAutomationReportPowerStateChange: Reporting power state change (opcode=0, err=0).
Jun 28 23:41:20.116: vcpu-0| Vix: [17209 mainDispatch.c:3582]: VMAutomationReportPowerStateChange: Reporting power state change (opcode=2, err=0).
Jun 28 23:41:20.116: vcpu-0| Transitioned vmx/execState/val to poweredOn
Jun 28 23:41:20.129: vcpu-0| MX: init lock: rank(gbusLock)=65534 lid=47
Jun 28 23:41:20.130: vcpu-0| MX: init lock: rank(tcCohLock)=39 lid=48
Jun 28 23:41:20.380: vmx| VMXVmdb_LoadRawConfig: Loading raw config
Jun 28 23:41:20.631: vcpu-0| sz=2498528
Jun 28 23:41:20.786: mks| KHBKL: Unable to parse keystring at: ''
Jun 28 23:41:20.830: vcpu-0| MX: init lock: rank(barrierLck)=1 lid=49
Jun 28 23:41:20.830: vcpu-0| MX: init condvar: barrierCV
Jun 28 23:41:20.830: vcpu-0| MX: init lock: rank(barrierLck)=1 lid=50
Jun 28 23:41:20.830: vcpu-0| MX: init condvar: barrierCV
Jun 28 23:41:20.830: vcpu-0| MX: init lock: rank(restoreLock)=99 lid=51
Jun 28 23:41:20.836: vcpu-0| vmm32 initialized: BETAbuild-385536. cflags: 0x00000006.00000000.00006000.00090003
Jun 28 23:41:20.846: vcpu-0| MonitorInitNumaUnmapVMM32
Jun 28 23:41:20.900: vmx| Vix: [17204 mainDispatch.c:1717]: VMAutomationAcceptNewConnection: Connection from local (Privileged? Yes).
Jun 28 23:41:20.949: vcpu-0| WRMSR: unknown MSR[0x404]:=0 (sinking): rip=0x15d5 count=1
Jun 28 23:41:20.949: vcpu-0| WRMSR: unknown MSR[0x408]:=0 (sinking): rip=0x15d5 count=1
Jun 28 23:41:20.949: vcpu-0| WRMSR: unknown MSR[0x40c]:=0 (sinking): rip=0x15d5 count=1
Jun 28 23:41:20.949: vcpu-0| WRMSR: unknown MSR[0x410]:=0 (sinking): rip=0x15d5 count=1
Jun 28 23:41:21.144: vcpu-0| WRMSR: unknown MSR[0x8b]:=2000000001 (sinking): rip=0x2ec0 count=1
Jun 28 23:41:21.296: vmx| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 1 numThreadsPerCore 1.
Jun 28 23:41:21.296: vmx| HOSTINFO: This machine has 1 physical CPUS, 1 total cores, and 1 logical CPUs.
Jun 28 23:41:21.701: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:21.701: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=1
Jun 28 23:41:21.714: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:21.714: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=2
Jun 28 23:41:21.736: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:21.736: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=3
Jun 28 23:41:21.806: vcpu-0| RDMSR: unknown MSR[0x2a] (read as zero): rip=0x57cb count=1
Jun 28 23:41:21.806: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x57e7
Jun 28 23:41:21.806: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x5b9f
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x116]:=0 (sinking): rip=0x152c count=1
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x88]:=0 (sinking): rip=0x153a count=1
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x89]:=0 (sinking): rip=0x153a count=1
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x8a]:=0 (sinking): rip=0x153a count=1
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0x153a count=2
Jun 28 23:41:21.821: vcpu-0| RDMSR: unknown MSR[0x119] (read as zero): rip=0x154d count=1
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x119]:=2 (sinking): rip=0x155a count=2
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x11a]:=0 (sinking): rip=0x1568 count=1
Jun 28 23:41:21.821: vcpu-0| RDMSR: unknown MSR[0x11b] (read as zero): rip=0x1573 count=1
Jun 28 23:41:21.821: vcpu-0| RDMSR: unknown MSR[0x116] (read as zero): rip=0x14f1 count=2
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x116]:=60 (sinking): rip=0x152c count=3
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x88]:=0 (sinking): rip=0x153a count=2
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x89]:=0 (sinking): rip=0x153a count=2
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x8a]:=0 (sinking): rip=0x153a count=2
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0x153a count=3
Jun 28 23:41:21.821: vcpu-0| RDMSR: unknown MSR[0x119] (read as zero): rip=0x154d count=3
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x119]:=2 (sinking): rip=0x155a count=4
Jun 28 23:41:21.821: vcpu-0| WRMSR: unknown MSR[0x11a]:=0 (sinking): rip=0x1568 count=2
Jun 28 23:41:21.821: vcpu-0| RDMSR: unknown MSR[0x11b] (read as zero): rip=0x1573 count=2
Jun 28 23:41:21.822: vcpu-0| RDMSR: unknown MSR[0x116] (read as zero): rip=0x14f1 count=4
Jun 28 23:41:21.939: vcpu-0| maxStackDepth(1) = 2832
Jun 28 23:41:22.659: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0x0) and 0xd8000000(0x0)
Jun 28 23:41:22.671: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:23.048: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:23.064: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:23.064: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=4
Jun 28 23:41:23.066: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:23.129: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Jun 28 23:41:23.129: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:23.145: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.147: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.149: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.152: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.154: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.157: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.159: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.162: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.164: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.166: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.169: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.171: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.174: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.177: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.179: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.182: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.184: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.186: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.189: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.191: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.194: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.196: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.199: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.201: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.204: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.206: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.208: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.211: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.213: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.216: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.218: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.221: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:23.480: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:23.480: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=5
Jun 28 23:41:23.483: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:23.483: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=6
Jun 28 23:41:23.992: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x166b
Jun 28 23:41:24.181: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.184: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.187: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.190: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.193: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.195: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.201: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.204: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.207: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.210: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.212: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.215: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.217: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.220: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.222: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.225: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.227: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.230: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.232: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.235: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.237: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.240: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.243: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.245: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.248: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.250: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.253: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.255: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.258: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.260: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.263: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.265: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:24.270: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.270: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=7
Jun 28 23:41:24.285: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.285: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=8
Jun 28 23:41:24.293: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.294: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=9
Jun 28 23:41:24.298: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.298: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=10
Jun 28 23:41:24.317: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.317: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=11
Jun 28 23:41:24.330: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.330: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=12
Jun 28 23:41:24.332: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.332: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=13
Jun 28 23:41:24.333: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.333: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=14
Jun 28 23:41:24.335: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.335: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=15
Jun 28 23:41:24.362: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.362: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=16
Jun 28 23:41:24.372: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 41943040
Jun 28 23:41:24.375: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.375: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=17
Jun 28 23:41:24.377: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.377: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=18
Jun 28 23:41:24.378: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.378: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=19
Jun 28 23:41:24.378: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.378: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=20
Jun 28 23:41:24.379: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.379: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=21
Jun 28 23:41:24.381: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:24.381: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=22
Jun 28 23:41:24.397: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x5903
Jun 28 23:41:24.398: vcpu-0| WRMSR: unknown MSR[0x11e]:=8101 (sinking): rip=0x590e count=23
Jun 28 23:41:24.499: vcpu-0| BIOS-UUID is 56 4d 1b 16 6b 1c 85 f6-94 da fe 1a b7 15 02 02
Jun 28 23:41:24.683: vcpu-0| maxStackDepth(1) = 2836
Jun 28 23:41:25.259: mks| HostOps hideCursor before defineCursor!
Jun 28 23:41:25.375: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:25.375: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=24
Jun 28 23:41:25.399: vcpu-0| RDMSR: MSR[0x11e] (read as 708101): rip=0x4651
Jun 28 23:41:25.399: vcpu-0| WRMSR: unknown MSR[0x11e]:=708001 (sinking): rip=0x4656 count=25
Jun 28 23:41:25.766: vcpu-0| Setting thread 37 stack size to 524288.
Jun 28 23:41:25.836: vmx| Setting thread 38 stack size to 524288.
Jun 28 23:41:26.114: vcpu-0| Unknown int 10h func 0x2000
Jun 28 23:41:26.244: mks| SVGA: display status changed, using optimizations for local consoles.
Jun 28 23:41:26.523: vcpu-0| maxStackDepth(1) = 3104
Jun 28 23:41:26.624: vmx| Setting thread 39 stack size to 524288.
Jun 28 23:41:29.057: vcpu-0| DISKLIB-DDB   : "longContentID" = "8dee94a605cc3fa062a534283c0a7dc7" (was "3df0293fe9dbba57686824a3a5d67b27")
Jun 28 23:41:29.095: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0x804ff9d4 count=4
Jun 28 23:41:31.622: mks| HostOps hideCursor before defineCursor!
Jun 28 23:41:32.124: vcpu-0| maxStackDepth(1) = 3220
Jun 28 23:41:32.436: vcpu-0| WRMSR: unknown MSR[0x277]:=7010600070106 (sinking): rip=0x804ff9d4 count=1
Jun 28 23:41:32.936: vcpu-0| RDMSR: unknown MSR[0x179] (read as zero): rip=0x806d8998 count=1
Jun 28 23:41:32.936: vcpu-0| RDMSR: unknown MSR[0x400] (read as zero): rip=0x806d8998 count=1
Jun 28 23:41:32.937: vcpu-0| RDMSR: unknown MSR[0x179] (read as zero): rip=0x806d8998 count=2
Jun 28 23:41:32.956: vcpu-0| maxStackDepth(0) = 3796
Jun 28 23:41:33.194: vcpu-0| maxStackDepth(1) = 3536
Jun 28 23:41:38.513: vcpu-0| maxStackDepth(0) = 3932
Jun 28 23:41:41.089: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Jun 28 23:41:41.089: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:41.156: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Jun 28 23:41:41.156: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:41:41.171: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.172: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.177: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.178: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.182: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.183: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.187: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.188: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.192: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.193: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.197: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.198: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.202: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.203: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.207: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.208: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.211: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.211: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.215: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.216: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.221: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.221: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.226: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.226: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.231: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.231: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.236: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.237: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.241: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.243: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.247: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.248: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.252: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.252: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.256: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.257: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.261: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.262: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.266: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.267: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.271: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.272: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.276: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.278: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.282: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.283: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.287: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.288: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.291: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.291: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.296: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.297: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.301: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.302: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.306: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.306: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.311: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.312: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.316: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.316: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.321: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.322: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.326: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.327: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:41.424: vmx| LOADAVG: 1.15 0.92 1.37
Jun 28 23:41:47.022: vcpu-0| PCIBridge4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.076: vcpu-0| pciBridge4:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.126: vcpu-0| pciBridge4:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.181: vcpu-0| pciBridge4:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.255: vcpu-0| pciBridge4:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.330: vcpu-0| pciBridge4:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.381: vcpu-0| pciBridge4:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.441: vcpu-0| pciBridge4:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.490: vcpu-0| PCIBridge5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.534: vcpu-0| pciBridge5:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.584: vcpu-0| pciBridge5:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.633: vcpu-0| pciBridge5:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.684: vcpu-0| pciBridge5:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.733: vcpu-0| pciBridge5:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.784: vcpu-0| pciBridge5:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.834: vcpu-0| pciBridge5:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.888: vcpu-0| PCIBridge6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.937: vcpu-0| pciBridge6:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:47.988: vcpu-0| pciBridge6:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.039: vcpu-0| pciBridge6:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.090: vcpu-0| pciBridge6:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.142: vcpu-0| pciBridge6:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.195: vcpu-0| pciBridge6:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.248: vcpu-0| pciBridge6:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.297: vcpu-0| PCIBridge7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.342: vcpu-0| pciBridge7:1: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.389: vcpu-0| pciBridge7:2: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.435: vcpu-0| pciBridge7:3: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.482: vcpu-0| pciBridge7:4: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.543: vcpu-0| pciBridge7:5: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.591: vcpu-0| pciBridge7:6: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:48.642: vcpu-0| pciBridge7:7: ISA/VGA decoding enabled (ctrl 0004)
Jun 28 23:41:49.546: vcpu-0| maxStackDepth(1) = 3740
Jun 28 23:41:50.319: vcpu-0| maxStackDepth(0) = 3940
Jun 28 23:41:50.704: vcpu-0| VIDE: Curr CHS info cyls: 17475 heads: 15 sects: 63 lba_cap: 41943040
Jun 28 23:41:51.765: vmx| CDROM ide1:0: CMD 0x5a (MODE SENSE(10)) FAILED (key 0x5 asc 0x24 ascq 0)
Jun 28 23:41:51.958: vcpu-0| SCSI0: RESET BUS
Jun 28 23:41:52.350: vcpu-0| VIDE: (0x1f0) OUTB Cmd 0xf5, Unknown ATA Command on drive 0
Jun 28 23:41:57.982: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0xf7add318 count=5
Jun 28 23:41:59.676: vcpu-0| RDMSR: unknown MSR[0x17] (read as zero): rip=0xf70b2ea4 count=1
Jun 28 23:41:59.676: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0xf70b2eb8 count=6
Jun 28 23:41:59.676: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0xf70b2eb8 count=7
Jun 28 23:41:59.697: vcpu-0| WRMSR: unknown MSR[0x8b]:=0 (sinking): rip=0xf7add318 count=8
Jun 28 23:42:00.889: vcpu-0| SVGA: Unregistering IOSpace at 0x10f0
Jun 28 23:42:00.889: vcpu-0| SVGA: Unregistering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:42:01.029: vcpu-0| SVGA: Registering IOSpace at 0x10f0
Jun 28 23:42:01.029: vcpu-0| SVGA: Registering MemSpace at 0xd0000000(0xd0000000) and 0xd8000000(0xd8000000)
Jun 28 23:42:04.678: vcpu-0| Guest OS = 0x5008
Jun 28 23:42:04.826: vcpu-0| UHCI: Global Reset
Jun 28 23:42:05.556: vcpu-0| VNET: MACVNetConnectToNetwork: Ethernet0: notify available
Jun 28 23:42:05.618: vcpu-0| Guest: VMXNET: Initialization completed successfully. Version 2.0 Jan 22 2009.
Jun 28 23:42:05.629: vcpu-0| Guest: VMXNET: Features: 
Jun 28 23:42:05.630: vcpu-0| Guest: VMXNET: Vmxnet rx ringLen1 = 100, ringLen2 = 1
Jun 28 23:42:05.948: vcpu-0| maxStackDepth(0) = 4156
Jun 28 23:42:11.422: vmx| LOADAVG: 1.50 1.03 1.39
Jun 28 23:42:12.468: vcpu-0| maxStackDepth(0) = 4224
Jun 28 23:42:17.517: vmx| ide1:0: Command READ(10) took 1.839 seconds (ok)
Jun 28 23:42:20.780: vmx| GuestRpcSendTimedOut: message to toolbox-dnd timed out.
Jun 28 23:42:22.645: vcpu-0| CopyExcFrame: ESP and SS may be invalid
Jun 28 23:42:22.970: mks| MKS enabling SVGA
Jun 28 23:42:25.753: mks| HostOps hideCursor before defineCursor!
Jun 28 23:42:25.779: mks| MKS switching absolute mouse on
Jun 28 23:42:25.790: mks| Guest display topology changed: numDisplays 1
Jun 28 23:42:26.044: vcpu-0| Guest: vmx_fb: This is the primary surface: PPDEV e1608010
Jun 28 23:42:26.045: vcpu-0| Guest: vmx_fb: Display driver is out of sync with virtual hardware.  Disabling 3d.
Jun 28 23:42:26.045: vcpu-0| Guest: vmx_fb:   Current hardware revision: 0.0.
Jun 28 23:42:26.046: vcpu-0| Guest: vmx_fb:   Driver compiled against:   2.0.
Jun 28 23:42:26.046: vcpu-0| Guest: vmx_fb: Display Acceleration: DirectDraw:ok, Direct3D:disabled.
Jun 28 23:42:26.046: vcpu-0| Guest: vmx_fb:   Current hardware revision: 0.0.
Jun 28 23:42:26.046: vcpu-0| Guest: vmx_fb:   Driver compiled against:   2.0.
Jun 28 23:42:26.053: vcpu-0| Guest: vmx_fb: DrvGetDirectDrawInfo: Overlay flags set
Jun 28 23:42:26.054: vcpu-0| Guest: vmx_fb: This is the primary surface: PPDEV e1608010
Jun 28 23:42:26.054: vcpu-0| Guest: vmx_fb: Display driver is out of sync with virtual hardware.  Disabling 3d.
Jun 28 23:42:26.054: vcpu-0| Guest: vmx_fb:   Current hardware revision: 0.0.
Jun 28 23:42:26.054: vcpu-0| Guest: vmx_fb:   Driver compiled against:   2.0.
Jun 28 23:42:26.055: vcpu-0| Guest: vmx_fb: Display Acceleration: DirectDraw:ok, Direct3D:disabled.
Jun 28 23:42:26.055: vcpu-0| Guest: vmx_fb:   Current hardware revision: 0.0.
Jun 28 23:42:26.055: vcpu-0| Guest: vmx_fb:   Driver compiled against:   2.0.
Jun 28 23:42:26.060: vcpu-0| Guest: vmx_fb: DrvGetDirectDrawInfo: Overlay flags set
Jun 28 23:42:26.082: mks| SVGAVideo_HandleEscape: Error flushing video overlay unit 0. See BLOG for details.
Jun 28 23:42:28.919: vcpu-0| maxStackDepth(1) = 3980
```

---

### Post by mörgæs on 2011-06-29
Hi, welcome to the fora.

This does not sound like a problem specific to Dell. I guess you will have more luck posting here:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

