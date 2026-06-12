---
title: "Over-heating and better battery life fix for Vostro 3700"
date: 2012-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shuttleworthwannabe on 2012-02-04
I had to add lines to the grub kernel parameters; here is what my grub.conf file looks like. It has improved battery life, fan is less frantic and tempt read as low as 38.5'C (at rest, like writing this post in FF) to max 65-70 on heavy CPU load. At rest, the palm rests are also very cool to handle, making using Ubuntu a pleasure, again. The [COLOR=red]acpi_osi=Linux[/COLOR] edit was needed to make the Fn key make screen brightness work.
Hope someone finds this useful.
So here is the grub.conf file
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=Red]i915.i915_enable_rc6=1 i915.i915_enable_fbc=1[/COLOR] quiet splash [COLOR=red]pcie_aspm=force[/COLOR] "
GRUB_CMDLINE_LINUX="[COLOR=red]acpi_osi=Linux[/COLOR]"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```To edit that file do this:> sudo gedit /etc/default/grubthen edit the file as above (red font), then do not forget to apply the settings by updating grub, like so > sudo update-grub then reboot.

---

### Post by syshex on 2013-02-21
Did not solve for me. 
I keep on getting my temps at around 65ºC and over. Normally going to around 80ºc.  (Asus K53S laptop).

Noticed that this started happening on this laptop and on my older laptop (which ended up frying... really!) with kernels 3.X 

Installed a oneiric kernel , 2.6.2*something, on my Quantal Quetzal box and overall heating was much much much better... like the laptop stopped sounding like a vacuum cleaner.

The temp on the laptop is mainly coming from the CPU. HDD is pretty cool normally (30 / 40 ºC  ) and I'm also running bumblebee.

So, as far as I can tell, my only solution was kernel downgrade, which is annoying as hell. In fact Quantal Quetzal almost made me revert back to windows after 15 years of linux, just in order to be able to work without burning my hands.... which is saying quite a bit about Quantal Quetzal.

---

