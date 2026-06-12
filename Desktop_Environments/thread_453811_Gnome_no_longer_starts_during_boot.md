---
title: "Gnome no longer starts during boot"
date: 2007-05-24
forum: Desktop Environments
---

### Post by sdd on 2007-05-24
Original install of 6.06 LTS. 
Various updates over time.
System upgraded itself to 7.04 via Synaptic (took 3 hours)
Started failing to allocate mem resource after that. No other problems.

Today (After installing some ALSA utils to get Audacity to record from line in (never got it to work))
and adding a TTF font, Gnome login stops starting.

	My startup screen displays the 'Failed to allocate mem resource' message
	Shows the normal Ubuntu progress bar. 
	Then drops out in to command line mode just before the end.

Screen as follows:
------------------------------------
Starting up...
[     0.204846] PCI:Failed to allocate mem resource #6:20000@d0000000 for 0000:01:0.0
Loading, please wait...
Ubuntu 7.04 stuart-laptop tty1
stuart-laptop login:_
..
.. I then log in!
..
Linux stuart-laptop 2.6.20-15-generic #2 SMP
...
-------------------------------------

My laptop is a HP dv9288ea Dual boot with that other OS (Vista)

I now have to manually start X by typing startx.
Once started everything seems normal.

When I select system -> preferences -> Sessions
the Session options page has only two items:

[] Automatically save changes to session
	[Save the current session]

No other options are visible.

Can anyone help?

Stuart

---

