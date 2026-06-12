---
title: "disabling ethernet"
date: 2009-03-10
forum: General Help
---

### Post by leemckelvey on 2009-03-10
hello all,

im kind of new here and new to linux.

I am running intrepid on my new macbook 5,1 and was wondering if there is a way to disable the eth0 connection at startup.

Now i have discovered that the command "sudo ifconfig eth0 down" disables this and thus giving me more battery life.

can this be added somewhere to run at startup? i have tried disabling in the network settings but it says my eth0 is not configured.

any help would be much appreciated.

thanks

lee

---

### Post by kngunn on 2009-03-10
I think you can do this by editing your /etc/network/interfaces file.  You should see a line that says:

auto eth0

Comment out that line (a # character at the start of the line should do) or delete it entirely.

As always, back up your interfaces file before making changes.  I usually just copy it to a backup file:

sudo cp interfaces interfaces.backup

---

### Post by leemckelvey on 2009-03-10
i opened the file to find this

auto lo
iface lo inet loopback

and thats all there is :(

Lee

---

### Post by leemckelvey on 2009-03-11
anyone got any ideas?

i really dont want to retype the same thing every thime i reboot.

lee

---

### Post by plucky on 2009-03-11
> **leemckelvey said:**
> anyone got any ideas?

i really dont want to retype the same thing every thime i reboot.

lee


Not sure if this will work as unable to test,but you could put ```
iface down eth0
``` in the /etc/network/interfaces file.

Type "man interfaces" for further information on that file.


Good Luck

---

### Post by leemckelvey on 2009-03-12
i tried that but it made no difference, any other ideas?

Lee

---

### Post by DGortze380 on 2009-03-12
> **leemckelvey said:**
> i tried that but it made no difference, any other ideas?

Lee

Please reboot your machine.
Before you do anything else, open a terminal and type

```

ifconfig -a

```

post the output here.

```

cat /etc/network/interfaces

```

post the output here.

It appears that eth0 should not be running at start-up according to your interfaces file.

---

### Post by wildman4god on 2009-03-12
you can also disable/enable networking by right clicking the network manager icon in sys tray and select/deselect enable networking, this should power down the card or you can disable the card in your computers bios (cmos settings).

---

