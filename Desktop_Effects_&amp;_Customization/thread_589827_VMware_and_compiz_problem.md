---
title: "VMware and compiz problem"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by danstah on 2007-10-24
I installed xgl so my compiz would work correctly (using 7.10) and have everything the way i like it but when i try to use vmware server the screen is black but things are still working. Why is the video not outputting? Here are the messages i get...Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

---

### Post by Olin Shivers on 2008-02-01
I think that I, too, am having this problem. I have also seen it reported 
multiple times at various other forums, including the vmware boards, but
never with a resolution.

Here is my situation:

    * I'm running VMWare Workstation 6, on a vm that ran fine under
      Workstation 5.

    * Host is Ubuntu 7.10
      AMD64 cpu, Asus mobo, NVidia chipset
      NVidia 7800 graphics card, NVidia's propietary X drivers for xorg.

    * Guest is Windows XP.

    * I sudo to root and run

        vmware VirtXP.vmx

      The virtual machine comes up, but after the POST, the screen goes black.
      The machine is alive -- the disk & network icons flash, showing activity,
      and the screen resizes to the right size as Windows comes up. But the
      screen stays black, permanently. (And, by the way, the vmx file has
      rwxr-xr-x perms, so it's not the no-execute problem.)

      In more detail: When I click on run, vmware pops up a notification box
      saying

        Unable to query the valid mode lines from your X server; will not try
        to change host resolution when entering fullscreen mode.

      and prints out on stdout/stderr

        Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".

      Then the vmware window shows the vm posting and then it goes black.

    * If, however, I log in on my machine's console as root, instead of
      sudoing, I win. I still get the messages, however.

    * If I ssh to localhost as root, or ssh to localhost as myself then
      sudo, I win and no messages. But... if, after winning, I then alter my
      $DISPLAY from ssh's proxy setting of
        localhost:11.0
      to the direct-to-the-X-server setting of
        :1.0
      then I'm back to losing as described above, with the messages. So it
      really seems to be something about the X connection.

Oh, and if I switch my X server back to the less-performant open-source nv driver,
instead of NVidia's nvidia driver, I win.

I have no idea what to do. As I said above, I have seen this problem reported
by multiple people as various forums I found by googling around, but never
with a resolution. It simply appears to be an unfixed bug that has no known
workaround.

Can anyone shed some light on this?
-Olin

---

### Post by koniu on 2008-02-29
Exactly same problem here. 

NVidia 7900GS , Ubuntu 7.10, VMWare guest system - WIndows XP running from physical partition. When driver changed to nv , everything works fine (VMWare, not compiz ) . Otherwise black screen just after hardware profile selection ( I've got two profiles , VMWare and Normal boot). Any help welcome .

Ta,
Koniu

---

