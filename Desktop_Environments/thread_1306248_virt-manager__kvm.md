---
title: "virt-manager / kvm"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Komir on 2009-10-30
I use virt-manager 0.8 (kvm) on ubuntu 9.10 64, and I have problem with usb.
USB is attached to machine, but not showed on virtual XP.
My XP /etc/libvirt/qemu/xp.xml

```
<domain type='kvm'>
  <name>xp</name>
  <uuid>682aa76e-489a-7d31-2627-33272a38c347</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/xp-1.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='network'>
      <mac address='54:52:00:5c:a6:83'/>
      <source network='default'/>
    </interface>
    <interface type='network'>
      <mac address='54:52:00:4d:24:09'/>
      <source network='default'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='hr'/>
    <sound model='es1370'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
    [B][I][COLOR="Red"]<hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x152d'/>
        <product id='0x2329'/>[/COLOR][/I][/B]
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x064f'/>
        <product id='0x03e9'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x064f'/>
        <product id='0x03e9'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x064f'/>
        <product id='0x03e9'/>
      </source>
    </hostdev>
  </devices>
</domain>
```
and there is my USB attached but not showed in my virtual machine.
PS.Sorry for my english  :redface::redface::redface:

---

### Post by sdowney717 on 2009-11-02
[http://ubuntuforums.org/showthread.php?t=1311130&highlight=kvm+usb](http://ubuntuforums.org/showthread.php?t=1311130&highlight=kvm+usb)

then after you allow usb passthru, in the vm before you start, plug in the usb, open the vm console, goto details and add the hardware
but it is only usb 1.0!

---

