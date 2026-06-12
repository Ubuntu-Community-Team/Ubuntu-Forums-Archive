---
title: "powertop suggestion"
date: 2008-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ryan2009 on 2008-11-24
Hey all, I'm new to Ubuntu on my Dell D620.  Here is the output of my powertop suggestions, please see my comment after the code, my question is there.

```
PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 60 seconds 


Cn	          Avg residency
C0 (cpu running)        (14.0%)
polling		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.7ms ( 1.1%)
C3		  2.0ms (84.9%)
P-states (frequencies)
  1.67 Ghz     2.3%
  1333 Mhz     0.0%
  1000 Mhz    97.7%
Wakeups-from-idle per second : 440.4	interval: 60.0s
Power usage (ACPI estimate): 19.5W (1.7 hours) 
Top causes for wakeups:
  18.9% (116.0)      <kernel IPI> : Rescheduling interrupts 
  16.0% ( 98.4)       <interrupt> : HDA Intel 
  15.4% ( 94.5)       <interrupt> : extra timer interrupt 
  11.8% ( 72.5)       <interrupt> : i915@pci:0000:00:02.0 
  11.4% ( 70.0)      npviewer.bin : schedule_timeout (process_timeout) 
   8.6% ( 52.9)           firefox : futex_wait (hrtimer_wakeup) 
   8.0% ( 49.0)      npviewer.bin : futex_wait (hrtimer_wakeup) 
   2.9% ( 18.1)       <interrupt> : iwl3945 
   2.0% ( 12.5)      <kernel IPI> : function call interrupts 
   1.6% ( 10.0)     <kernel core> : scan_async (ehci_watchdog) 
   1.2% (  7.2)       <interrupt> : ata_piix 
   0.4% (  2.4)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.3% (  1.7)    gnome-terminal : schedule_timeout (process_timeout) 
   0.2% (  1.3)              Xorg : schedule_timeout (process_timeout) 
   0.2% (  1.2)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.2% (  1.0)    NetworkManager : tg3_open (tg3_timer) 
   0.2% (  1.0)   <kernel module> : HostIF_InitUptime (HostIFUptimeResyncMono) 
   0.1% (  0.5)           iwl3945 : ieee80211_sta_work (ieee80211_sta_timer) 
   0.1% (  0.5)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.1% (  0.5)   hald-addon-stor : schedule_timeout (process_timeout) 
   0.1% (  0.4)        pulseaudio : schedule_timeout (process_timeout) 
   0.1% (  0.3)    NetworkManager : schedule_timeout (process_timeout) 
   0.0% (  0.3)   gnome-power-man : schedule_timeout (process_timeout) 
   0.0% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   0.0% (  0.2)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.2)           firefox : schedule_timeout (process_timeout) 
   0.0% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.0% (  0.2)      npviewer.bin : hrtick_start_fair (hrtick) 
   0.0% (  0.1)     <kernel core> : neigh_add_timer (neigh_timer_handler) 
   0.0% (  0.1)     <kernel core> : inet_twsk_schedule (inet_twdr_hangman) 
   0.0% (  0.1)              nmbd : schedule_timeout (process_timeout) 
   0.0% (  0.1)   <kernel module> : sta_info_start (sta_info_cleanup) 
   0.0% (  0.1)     <kernel core> : rs_tx_status (iwl3945_bg_rate_scale_flush) 
   0.0% (  0.1)          gconfd-2 : schedule_timeout (process_timeout) 
   0.0% (  0.1)              hald : schedule_timeout (process_timeout) 
   0.0% (  0.1)      <kernel IPI> : TLB shootdowns 
   0.0% (  0.1)   dellWirelessCtl : hrtick_start_fair (hrtick) 
   0.0% (  0.0)           syslogd : do_setitimer (it_real_fn) 
   0.0% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)              smbd : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : cfq_arm_slice_timer (cfq_idle_slice_timer) 
   0.0% (  0.0)              sudo : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.0)       compiz.real : schedule_timeout (process_timeout) 
   0.0% (  0.0)       dbus-daemon : schedule_timeout (process_timeout) 
   0.0% (  0.0)         iwl3945/0 : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)              cron : do_nanosleep (hrtimer_wakeup) 
   0.0% (  0.0)      transmission : sk_reset_timer (tcp_write_timer) 
   0.0% (  0.0)         nm-applet : schedule_timeout (process_timeout) 
   0.0% (  0.0)           firefox : sk_reset_timer (tcp_delack_timer) 

A USB device is active 100.0% of the time:
/sys/bus/usb/devices/5-2.3

Suggestion: Enable USB autosuspend by pressing the U key or adding 
usbcore.autosuspend=1 to the kernel command line in the grub config

Suggestion: Enable wireless power saving mode by executing the following command:
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/power_level 
This will sacrifice network performance slightly to save power.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
100.0%	USB device 5-2.3.2 : O2Micro CCID SC Reader (O2)
100.0%	/sys/bus/usb/devices/5-2.3
100.0%	/sys/bus/usb/devices/5-2
100.0%	USB device usb5 : EHCI Host Controller (Linux 2.6.27-7-generic ehci_hcd)


```

The part that I'm not sure of how to do is about the USB device that is on 100% of the time.  Any ideas on this one?  I'm not sure how to edit the kernel command line in the grub config.

---

### Post by Ryan2009 on 2008-11-25
anyone?

I'm still trying to figure out how to disable the 'O2Micro CCID SC Reader' device as powertop suggests

---

### Post by iggykoopa on 2008-11-25
it saying to add that line to grub is a bug in powertop, its actually set correctly.

---

### Post by Ryan2009 on 2008-11-25
How can I verify it is set correctly?

Secondly, if it is reporting that those usb devices are 100% active, how can I disable them?  I don't have any usb devices plugged in.  Do you know of any way for me to disable the card reader? there is no option in the bios.

---

### Post by iggykoopa on 2008-11-25
you can try removing all the usb modules and see if that works. if not the hard way (I haven't tested this but it should work) is to go to:
/sys/bus/usb/devices
find your device you wanna turn off and go to the power directory i.e.:
/sys/bus/usb/devices/2-2/power
then:
sudo su
to switch to root, then:
echo suspend > level
should suspend the device

edit: and heres [https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549](https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549) the bug about the grub suggestion

---

### Post by Ryan2009 on 2008-11-25
I did as suggested and it's no longer at 100%.  thanks!

will this stay suspended or will I have to run this after a reboot?

---

### Post by iggykoopa on 2008-11-26
I'm actually not sure, let me know when you reboot if it stays that way. If not you could write a script to run at startup to turn it off.

---

