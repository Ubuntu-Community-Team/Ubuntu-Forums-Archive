---
title: "Powertop performances"
date: 2008-02-12
forum: Dell  Ubuntu Support
---

### Post by PsychedelicReaction on 2008-02-12
How many wakeups from idle per second can you reach? I have a 9 cell battery on XPS1330 but its Ubuntu performances are about 20% lower than Windows.

** This is my powertop -d for a 15 seconds normal surfing session:**
```
PowerTOP 1.8    (C) 2007 Intel Corporation 

Raccolta dati per 15 secondi 
Cn	          Avg residency
C0 (cpu occupata)      (17,3%)
C1		  0,0ms ( 0,0%)
C2		  1,4ms ( 5,9%)
C3		  2,1ms (76,9%)
P-states (frequencies)
  2,01 Ghz     9,7%
  2,00 Ghz     0,0%
  1200 Mhz     1,2%
   800 Mhz    89,1%
Wakeups-from-idle per second : 405,9	interval: 15,0s
Power usage (ACPI estimate): 18,3W (4,4 hours) 
Top causes for wakeups:
  54,4% (240,4)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  14,0% ( 62,1)       <interrupt> : nvidia 
   4,8% ( 21,3)              Xorg : do_setitimer (it_real_fn) 
   4,5% ( 20,0)   epiphany-browse : futex_wait (hrtimer_wakeup) 
   4,5% ( 19,9)       compiz.real : schedule_timeout (process_timeout) 
   2,8% ( 12,2)      S20powernowd : queue_delayed_work_on (delayed_work_timer_fn) 
   2,3% ( 10,3)       <interrupt> : libata 
   2,3% ( 10,0)     <kernel core> : ehci_work (ehci_watchdog) 
   2,2% (  9,9)           zmdc.pl : schedule_timeout (process_timeout) 
   1,1% (  4,9)              Xorg : schedule_timeout (process_timeout) 
   0,9% (  3,9)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func) 
   0,7% (  2,9)          trackerd : schedule_timeout (process_timeout) 
   0,5% (  2,2)       <interrupt> : ahci, eth0, iwl4965 
   0,5% (  2,1)   avant-window-na : schedule_timeout (process_timeout) 
   0,5% (  2,0)   multiload-apple : schedule_timeout (process_timeout) 
   0,3% (  1,5)            mysqld : schedule_timeout (process_timeout) 
   0,3% (  1,3)    gnome-terminal : schedule_timeout (process_timeout) 
   0,2% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0,2% (  1,0)           apache2 : schedule_timeout (process_timeout) 
   0,2% (  1,0)            dhcdbd : schedule_timeout (process_timeout) 
   0,2% (  1,0)    NetworkManager : tg3_open (tg3_timer) 
   0,2% (  1,0)      hibernate.sh : queue_delayed_work_on (delayed_work_timer_fn) 
   0,2% (  1,0)    cpufreq-applet : schedule_timeout (process_timeout) 
   0,2% (  0,9)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn) 
   0,2% (  0,7)       gnome-panel : schedule_timeout (process_timeout) 
   0,2% (  0,7)    deskbar-applet : schedule_timeout (process_timeout) 
   0,2% (  0,7)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,1% (  0,5)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,1% (  0,5)    sensors-applet : schedule_timeout (process_timeout) 
   0,1% (  0,5)    NetworkManager : schedule_timeout (process_timeout) 
   0,1% (  0,5)   hald-addon-stor : schedule_timeout (process_timeout) 
   0,1% (  0,5)          nautilus : schedule_timeout (process_timeout) 
   0,1% (  0,5)   update-notifier : schedule_timeout (process_timeout) 
   0,1% (  0,4)            python : schedule_timeout (process_timeout) 
   0,1% (  0,3)   gnome-power-man : schedule_timeout (process_timeout) 
   0,1% (  0,3)   awn-applet-acti : schedule_timeout (process_timeout) 
   0,1% (  0,3)   nvidia-settings : schedule_timeout (process_timeout) 
   0,0% (  0,2)              mono : do_nanosleep (hrtimer_wakeup) 
   0,0% (  0,2)          gnome-do : schedule_timeout (process_timeout) 
   0,0% (  0,2)    mapping-daemon : schedule_timeout (process_timeout) 
   0,0% (  0,2)              Xorg : __netdev_watchdog_up (dev_watchdog) 
   0,0% (  0,1)        zmwatch.pl : do_nanosleep (hrtimer_wakeup) 
   0,0% (  0,1)              Xorg : inet_twsk_schedule (inet_twdr_hangman) 
   0,0% (  0,1)              hald : schedule_timeout (process_timeout) 
   0,0% (  0,1)   gnome-volume-ma : schedule_timeout (process_timeout) 
   0,0% (  0,1)     <kernel core> : end_that_request_last (laptop_timer_fn) 
   0,0% (  0,1)           syslogd : do_setitimer (it_real_fn) 
   0,0% (  0,1)         iwl4965/0 : sta_info_start (sta_info_cleanup) 
   0,0% (  0,1)         ssh-agent : schedule_timeout (process_timeout) 
   0,0% (  0,1)         ssh-agent : do_setitimer (it_real_fn) 
```

**And this is on idle, without compiz**

```
PowerTOP 1.8    (C) 2007 Intel Corporation 

Raccolta dati per 15 secondi 
Cn	          Avg residency
C0 (cpu occupata)      ( 4,0%)
C1		  0,0ms ( 0,0%)
C2		  2,0ms ( 1,5%)
C3		  6,1ms (94,5%)
P-states (frequencies)
  2,01 Ghz     1,4%
  2,00 Ghz     0,0%
  1,60 Ghz     0,0%
   800 Mhz    98,6%
Wakeups-from-idle per second : 161,5	interval: 15,0s
Power usage (ACPI estimate): 14,8W (5,4 hours) 
Top causes for wakeups:
  43,9% ( 61,0)       <interrupt> : nvidia 
   9,0% ( 12,5)      S20powernowd : queue_delayed_work_on (delayed_work_timer_fn) 
   8,4% ( 11,7)       <interrupt> : libata 
   7,2% ( 10,0)           zmdc.pl : schedule_timeout (process_timeout) 
   7,2% ( 10,0)     <kernel core> : ehci_work (ehci_watchdog) 
   3,3% (  4,5)              Xorg : do_setitimer (it_real_fn) 
   2,8% (  3,9)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func) 
   2,1% (  2,9)       <interrupt> : ahci, eth0, iwl4965 
   2,1% (  2,9)          trackerd : schedule_timeout (process_timeout) 
   1,4% (  2,0)   multiload-apple : schedule_timeout (process_timeout) 
   1,2% (  1,7)    gnome-terminal : schedule_timeout (process_timeout) 
   1,1% (  1,5)            mysqld : schedule_timeout (process_timeout) 
   0,8% (  1,1)    cpufreq-applet : schedule_timeout (process_timeout) 
   0,7% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0,7% (  1,0)      hibernate.sh : queue_delayed_work_on (delayed_work_timer_fn) 
   0,7% (  1,0)           apache2 : schedule_timeout (process_timeout) 
   0,7% (  1,0)            dhcdbd : schedule_timeout (process_timeout) 
   0,7% (  1,0)    NetworkManager : tg3_open (tg3_timer) 
   0,7% (  1,0)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn) 
   0,5% (  0,7)    NetworkManager : schedule_timeout (process_timeout) 
   0,4% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,4% (  0,5)   hald-addon-stor : schedule_timeout (process_timeout) 
   0,4% (  0,5)   update-notifier : schedule_timeout (process_timeout) 
   0,4% (  0,5)            python : schedule_timeout (process_timeout) 
   0,3% (  0,5)    deskbar-applet : schedule_timeout (process_timeout) 
   0,3% (  0,5)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,3% (  0,5)    sensors-applet : schedule_timeout (process_timeout) 
   0,3% (  0,4)       gnome-panel : schedule_timeout (process_timeout) 
   0,2% (  0,3)   awn-applet-acti : schedule_timeout (process_timeout) 
   0,2% (  0,3)              mono : do_nanosleep (hrtimer_wakeup) 
   0,2% (  0,3)   gnome-power-man : schedule_timeout (process_timeout) 
   0,1% (  0,2)          nautilus : schedule_timeout (process_timeout) 
   0,1% (  0,2)              Xorg : __netdev_watchdog_up (dev_watchdog) 
   0,1% (  0,2)          gnome-do : schedule_timeout (process_timeout) 
   0,1% (  0,2)    mapping-daemon : schedule_timeout (process_timeout) 
   0,1% (  0,1)              Xorg : inet_twsk_schedule (inet_twdr_hangman) 
   0,1% (  0,1)          gconfd-2 : schedule_timeout (process_timeout) 
   0,1% (  0,1)         ssh-agent : schedule_timeout (process_timeout) 
   0,1% (  0,1)         ssh-agent : do_setitimer (it_real_fn) 
   0,1% (  0,1)              Xorg : neigh_update (neigh_timer_handler) 
   0,1% (  0,1)        zmwatch.pl : do_nanosleep (hrtimer_wakeup) 
   0,0% (  0,1)    NetworkManager : do_nanosleep (hrtimer_wakeup) 
   0,0% (  0,1)              hald : schedule_timeout (process_timeout) 
   0,0% (  0,1)   gnome-volume-ma : schedule_timeout (process_timeout) 
   0,0% (  0,1)           syslogd : do_setitimer (it_real_fn) 
   0,0% (  0,1)         iwl4965/0 : sta_info_start (sta_info_cleanup) 
   0,0% (  0,1)     <kernel core> : end_that_request_last (laptop_timer_fn) 

```

Is there any way to cut off all those touchpad and nvidia wakeups?

---

### Post by sdennie on 2008-03-13
> 
Is there any way to cut off all those touchpad and nvidia wakeups?


This may be a bit late but, yes, you can get rid of the nvidia wakeups.  Just add:

```

    Option      "OnDemandVBlankInterrupts" "True"

```

to the Device section that describes your nvidia card in /etc/X11/xorg.conf.  This should completely get rid of wakeups when not using compiz (well, all but 1-2) but, to get rid of them with compiz enabled you'll have to disable sync to vblank.  This can be done automatically with acpi scripts and gconftool-2.

---

### Post by bruce89 on 2008-03-14
I'm a bit suspcious of epiphany's "futex_wait".

---

### Post by PsychedelicReaction on 2008-03-14
> **vor said:**
> This may be a bit late but, yes, you can get rid of the nvidia wakeups.  Just add:

```

    Option      "OnDemandVBlankInterrupts" "True"

```

to the Device section that describes your nvidia card in /etc/X11/xorg.conf.  This should completely get rid of wakeups when not using compiz (well, all but 1-2) but, to get rid of them with compiz enabled you'll have to disable sync to vblank.  This can be done automatically with acpi scripts and gconftool-2.

awesome, it works!

```
PowerTOP 1.9    (C) 2007 Intel Corporation 

Raccolta dati per 15 secondi 
Cn                Avg residency
C0 (cpu occupata)      ( 9,2%)
C1                0,0ms ( 0,0%)
C2                3,2ms (12,1%)
C3                2,8ms (78,8%)
P-states (frequencies)
  2,01 Ghz     0,0%
  2,00 Ghz     0,0%
  1,60 Ghz     0,0%
   800 Mhz   100,0%
Wakeups-from-idle per second : 314,9    interval: 15,0s
Power usage (ACPI estimate): 16,1W (5,6 hours) 
Top causes for wakeups:
  74,8% (227,7)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   5,3% ( 16,3)   epiphany-browse : futex_wait (hrtimer_wakeup) 
   5,3% ( 16,0)       <interrupt> : extra timer interrupt 
   4,0% ( 12,2)              Xorg : do_setitimer (it_real_fn) 
   3,1% (  9,4)     <kernel core> : ehci_work (ehci_watchdog) 
   1,6% (  4,9)              Xorg : schedule_timeout (process_timeout) 
   0,7% (  2,0)       <interrupt> : nvidia 
   0,7% (  2,0)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn) 
   0,6% (  1,9)   multiload-apple : schedule_timeout (process_timeout) 
   0,5% (  1,7)       gnome-panel : schedule_timeout (process_timeout) 
   0,4% (  1,3)    gnome-terminal : schedule_timeout (process_timeout) 
   0,3% (  1,0)            dhcdbd : schedule_timeout (process_timeout) 
   0,3% (  1,0)          ifconfig : tg3_open (tg3_timer) 
   0,3% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0,3% (  1,0)    cpufreq-applet : schedule_timeout (process_timeout) 
   0,2% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,2% (  0,5)    sensors-applet : schedule_timeout (process_timeout) 
   0,2% (  0,5)   update-notifier : schedule_timeout (process_timeout) 
   0,1% (  0,4)       <interrupt> : ahci, iwl4965, eth0 
   0,1% (  0,3)      avahi-daemon : schedule_timeout (process_timeout) 
   0,1% (  0,3)   gnome-power-man : schedule_timeout (process_timeout) 
   0,1% (  0,3)    deskbar-applet : schedule_timeout (process_timeout) 
   0,1% (  0,2)    mapping-daemon : schedule_timeout (process_timeout) 
   0,1% (  0,2)     <kernel core> : __netdev_watchdog_up (dev_watchdog) 
   0,1% (  0,2)   <modulo del kernel> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0,1% (  0,2)          gnome-do : schedule_timeout (process_timeout) 
   0,0% (  0,1)    sensors-applet : inet_twsk_schedule (inet_twdr_hangman) 
   0,0% (  0,1)               cli : do_nanosleep (hrtimer_wakeup) 
   0,0% (  0,1)         ssh-agent : schedule_timeout (process_timeout) 
   0,0% (  0,1)         ssh-agent : do_setitimer (it_real_fn) 
   0,0% (  0,1)   epiphany-browse : schedule_timeout (process_timeout) 
   0,0% (  0,1)           preload : schedule_timeout (process_timeout) 
   0,0% (  0,1)          metacity : schedule_timeout (process_timeout) 
   0,0% (  0,1)     <kernel core> : sk_reset_timer (tcp_delack_timer) 
   0,0% (  0,1)           syslogd : do_setitimer (it_real_fn) 
   0,0% (  0,1)    gnome-terminal : end_that_request_last (laptop_timer_fn) 
   0,0% (  0,1)              hald : schedule_timeout (process_timeout) 
   0,0% (  0,1)     <kernel core> : seqgen_init (delayed_work_timer_fn) 
   0,0% (  0,1)   gnome-volume-ma : schedule_timeout (process_timeout) 

```

but is there a performances loss when connected to the grid too? vblank is already unselected in compiz's general preferences.

---

### Post by sdennie on 2008-03-14
> **bruce89 said:**
> I'm a bit suspcious of epiphany's "futex_wait".

I think the futex_waits in epiphany (and, actually, all mozilla browsers) are related to javascript (specifically AJAX type stuff like gmail).  You can verify this by bringing up a clean instance of epiphany to wikipedia and see that there are few if any futex_wait calls and then logging into gmail and they generally spike up to about 20+/sec.

[QUOTE=PsychedelicReaction]but is there a performances loss when connected to the grid too?[/QUOTE]

I'm not sure what you mean by this.  If you are asking whether or not connecting to a network will drain power, the answer is yes.  A wifi card, while connected to the network will generate interrupts and, even if it's not connected will still use power for the radio.  If you aren't using the wifi and want to save power, on the XPS m1330 there is a little switch on the right side that, by default, turns off both the wifi and bluetooth radios.

Also, the keyboard/mouse/touchpad stuff you are seeing is normal and basically means you moved the mouse or typed stuff while powertop was collecting data.  

There is a lot of great information about power saving at [www.lesswatts.org](www.lesswatts.org).

With a 9 cell battery on an XPS m1330, properly configured, with wifi/bluetooth turned off and the LCD turned all the way down, it's possible to get down to less than 13W of power (which translates into nearly 8 hours of battery life).  Although, that's an artificial number and in actual use, the average power consumption will be closer to 16W.

---

### Post by PsychedelicReaction on 2008-03-14
> 'm not sure what you mean by this. If you are asking whether or not connecting to a network will drain power, the answer is yes. A wifi card, while connected to the network will generate interrupts and, even if it's not connected will still use power for the radio. If you aren't using the wifi and want to save power, on the XPS m1330 there is a little switch on the right side that, by default, turns off both the wifi and bluetooth radios.

sorry but im not english, i meant if with this setting performance could be affected when connected to eletricity too.

im gonna give a look to lesswatts, thank you :)

---

### Post by sdennie on 2008-03-14
> **PsychedelicReaction said:**
> sorry but im not english, i meant if with this setting performance could be affected when connected to eletricity too.

im gonna give a look to lesswatts, thank you :)

It shouldn't, no.  I found the 8400M GS to be a bit tricky to setup for maximum performance on AC and lowest power on battery, though.  I wrote a small HOWTO on the nvidia linux forums with some scripts that will force the card to maximum power while on AC and let it drop down to low power while on battery.  You can find the post here:

[http://www.nvnews.net/vbulletin/showthread.php?t=109744](http://www.nvnews.net/vbulletin/showthread.php?t=109744)

Apparently there is a bug where it doesn't work quite right after a reboot (I never reboot so didn't test that case) but, if you find it useful I'll post an update that should fix the problem.

---

### Post by simoncullen on 2008-05-17
> **vor said:**
> This may be a bit late but, yes, you can get rid of the nvidia wakeups.  Just add:

```

    Option      "OnDemandVBlankInterrupts" "True"

```

to the Device section that describes your nvidia card in /etc/X11/xorg.conf.  This should completely get rid of wakeups when not using compiz (well, all but 1-2) but, to get rid of them with compiz enabled you'll have to disable sync to vblank.  This can be done automatically with acpi scripts and gconftool-2.

I have compiz sync to vblank enabled (the performance is terrible without it).  When the machine is idle, is there a way to have it temporarily disable sync to vblank in Compiz?  It seems like a very natural thing to do . . .

---

### Post by sdennie on 2008-05-17
I'm not sure how you'd get this to execute on idle but, the command to turn off compiz vsync is:

```

gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0

```

And to turn it back on:

```

gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1

```

---

### Post by simoncullen on 2008-05-23
Thanks!

Anyone? :

> **vor said:**
> I'm not sure how you'd get this to execute on idle . . . 

---

